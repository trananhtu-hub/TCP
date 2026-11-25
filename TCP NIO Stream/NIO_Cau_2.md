import java.io.EOFException;
import java.io.IOException;
import java.net.InetSocketAddress;
import java.net.SocketTimeoutException;
import java.nio.ByteBuffer;
import java.nio.channels.SelectionKey;
import java.nio.channels.Selector;
import java.nio.channels.SocketChannel;
import java.nio.charset.StandardCharsets;
import java.util.HashMap;
import java.util.Map;

public class NIO_Cau_2 {
    private static final int TIMEOUT_MS = 5000;

    private static void awaitEvent(SocketChannel channel, Selector selector, int interestOps, long deadlineMs)
            throws IOException {
        long remaining = deadlineMs - System.currentTimeMillis();
        if (remaining <= 0) {
            throw new SocketTimeoutException("Timeout waiting for NIO socket event");
        }
        SelectionKey key = channel.register(selector, interestOps);
        try {
            int ready = selector.select(remaining);
            if (ready == 0) {
                throw new SocketTimeoutException("NIO operation timed out after " + TIMEOUT_MS + " ms");
            }
            selector.selectedKeys().clear();
        } finally {
            key.cancel();
            selector.selectNow();
        }
    }

    private static void connectWithTimeout(SocketChannel channel, Selector selector, InetSocketAddress addr)
            throws IOException {
        long deadlineMs = System.currentTimeMillis() + TIMEOUT_MS;
        if (!channel.connect(addr)) {
            while (!channel.finishConnect()) {
                awaitEvent(channel, selector, SelectionKey.OP_CONNECT, deadlineMs);
            }
        }
    }

    private static void writeFully(SocketChannel channel, Selector selector, ByteBuffer buf) throws IOException {
        long deadlineMs = System.currentTimeMillis() + TIMEOUT_MS;
        while (buf.hasRemaining()) {
            int written = channel.write(buf);
            if (written == 0) {
                awaitEvent(channel, selector, SelectionKey.OP_WRITE, deadlineMs);
            }
        }
    }

    private static void readFully(SocketChannel channel, Selector selector, ByteBuffer buf) throws IOException {
        long deadlineMs = System.currentTimeMillis() + TIMEOUT_MS;
        while (buf.hasRemaining()) {
            int read = channel.read(buf);
            if (read == -1) {
                throw new EOFException("Connection closed before reading full frame");
            }
            if (read == 0) {
                awaitEvent(channel, selector, SelectionKey.OP_READ, deadlineMs);
            }
        }
    }

    private static void sendFrame(SocketChannel channel, Selector selector, String message) throws IOException {
        byte[] payload = message.getBytes(StandardCharsets.UTF_8);
        ByteBuffer buf = ByteBuffer.allocate(4 + payload.length);
        buf.putInt(payload.length);
        buf.put(payload);
        buf.flip();
        writeFully(channel, selector, buf);
    }

    private static String readFrame(SocketChannel channel, Selector selector) throws IOException {
        ByteBuffer lenBuf = ByteBuffer.allocate(4);
        readFully(channel, selector, lenBuf);
        lenBuf.flip();
        int len = lenBuf.getInt();
        if (len < 0 || len > 10 * 1024 * 1024) {
            throw new IOException("Invalid frame length: " + len);
        }
        ByteBuffer payloadBuf = ByteBuffer.allocate(len);
        readFully(channel, selector, payloadBuf);
        return new String(payloadBuf.array(), StandardCharsets.UTF_8);
    }

    private static int skipWhitespace(String s, int idx) {
        while (idx < s.length() && Character.isWhitespace(s.charAt(idx))) {
            idx++;
        }
        return idx;
    }

    private static int parseStringEnd(String s, int quoteIdx, StringBuilder out) {
        int i = quoteIdx + 1;
        while (i < s.length()) {
            char c = s.charAt(i);
            if (c == '"') {
                return i + 1;
            }
            if (c == '\\' && i + 1 < s.length()) {
                char esc = s.charAt(i + 1);
                if (esc == '"' || esc == '\\' || esc == '/') {
                    out.append(esc);
                    i += 2;
                } else if (esc == 'n') {
                    out.append('\n');
                    i += 2;
                } else if (esc == 'r') {
                    out.append('\r');
                    i += 2;
                } else if (esc == 't') {
                    out.append('\t');
                    i += 2;
                } else if (esc == 'b') {
                    out.append('\b');
                    i += 2;
                } else if (esc == 'f') {
                    out.append('\f');
                    i += 2;
                } else if (esc == 'u' && i + 5 < s.length()) {
                    out.append((char) Integer.parseInt(s.substring(i + 2, i + 6), 16));
                    i += 6;
                } else {
                    out.append(esc);
                    i += 2;
                }
            } else {
                out.append(c);
                i++;
            }
        }
        return i;
    }

    private static int skipNested(String s, int startIdx) {
        int depth = 0;
        int i = startIdx;
        while (i < s.length()) {
            char c = s.charAt(i);
            if (c == '"') {
                i = parseStringEnd(s, i, new StringBuilder());
                continue;
            }
            if (c == '{' || c == '[') {
                depth++;
            } else if (c == '}' || c == ']') {
                depth--;
                if (depth == 0) {
                    return i + 1;
                }
            }
            i++;
        }
        return i;
    }

    private static Map<String, String> parseTopLevelJson(String json) {
        Map<String, String> map = new HashMap<>();
        int i = skipWhitespace(json, 0);
        if (i >= json.length() || json.charAt(i) != '{') {
            return map;
        }
        i++;
        while (i < json.length()) {
            i = skipWhitespace(json, i);
            if (i >= json.length() || json.charAt(i) == '}') {
                break;
            }
            if (json.charAt(i) == ',') {
                i++;
                continue;
            }
            if (json.charAt(i) != '"') {
                break;
            }
            StringBuilder keyBuf = new StringBuilder();
            i = parseStringEnd(json, i, keyBuf);
            String key = keyBuf.toString();

            i = skipWhitespace(json, i);
            if (i < json.length() && json.charAt(i) == ':') {
                i++;
            }
            i = skipWhitespace(json, i);
            if (i >= json.length()) {
                break;
            }

            char first = json.charAt(i);
            if (first == '"') {
                StringBuilder valBuf = new StringBuilder();
                i = parseStringEnd(json, i, valBuf);
                map.put(key, valBuf.toString());
            } else if (first == '{' || first == '[') {
                int end = skipNested(json, i);
                map.put(key, json.substring(i, end));
                i = end;
            } else {
                int start = i;
                while (i < json.length() && json.charAt(i) != ',' && json.charAt(i) != '}') {
                    i++;
                }
                map.put(key, json.substring(start, i).trim());
            }
        }
        return map;
    }

    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2211;
        String studentCode = "B22DCCN749";
        String qCode = "wu4O0Vg9";

        try (Selector selector = Selector.open();
                SocketChannel channel = SocketChannel.open()) {
            channel.configureBlocking(false);
            connectWithTimeout(channel, selector, new InetSocketAddress(serverHost, serverPort));

            // a. Gui studentCode;qCode theo giao thuc frame (4 byte int32 + payload UTF-8)
            sendFrame(channel, selector, studentCode + ";" + qCode);

            // b. Nhan dung 2 frame lien tiep va noi lai thanh chuoi JSON hoan chinh
            String frame1 = readFrame(channel, selector);
            String frame2 = readFrame(channel, selector);
            String json = frame1 + frame2;

            // c. Trich xuat cac truong event, user, ok va gui
            // "event=<event>;user=<user>;ok=<0|1>"
            Map<String, String> fields = parseTopLevelJson(json);
            String event = fields.getOrDefault("event", "");
            String user = fields.getOrDefault("user", "");
            String okRaw = fields.getOrDefault("ok", "");
            String ok = (okRaw.equalsIgnoreCase("true") || okRaw.equals("1")) ? "1" : "0";

            String result = "event=" + event + ";user=" + user + ";ok=" + ok;
            sendFrame(channel, selector, result);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
