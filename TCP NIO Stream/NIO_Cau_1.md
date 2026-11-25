import java.io.EOFException;
import java.io.IOException;
import java.net.InetSocketAddress;
import java.net.SocketTimeoutException;
import java.nio.ByteBuffer;
import java.nio.channels.SelectionKey;
import java.nio.channels.Selector;
import java.nio.channels.SocketChannel;
import java.nio.charset.StandardCharsets;

public class NIO_Cau_1 {
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

    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2211;
        String studentCode = "B22DCCN749";
        String qCode = "nZb9Fhpb";

        try (Selector selector = Selector.open();
                SocketChannel channel = SocketChannel.open()) {
            channel.configureBlocking(false);
            connectWithTimeout(channel, selector, new InetSocketAddress(serverHost, serverPort));

            // a. Gui studentCode;qCode theo giao thuc frame (4 byte int32 + payload UTF-8)
            sendFrame(channel, selector, studentCode + ";" + qCode);

            // b. Nhan dung 3 frame lien tiep va noi lai thanh HTTP request hoan chinh
            StringBuilder httpReq = new StringBuilder();
            for (int i = 0; i < 3; i++) {
                httpReq.append(readFrame(channel, selector));
            }

            // c. Trich xuat METHOD;PATH;HOST (PATH giu nguyen ca query-string)
            String[] lines = httpReq.toString().split("\r\n");
            String method = "";
            String path = "";
            String host = "";

            if (lines.length > 0) {
                String[] reqParts = lines[0].trim().split("\\s+");
                if (reqParts.length >= 2) {
                    method = reqParts[0];
                    path = reqParts[1];
                }
            }
            for (int i = 1; i < lines.length; i++) {
                String line = lines[i];
                if (line.isEmpty()) {
                    break;
                }
                int colon = line.indexOf(':');
                if (colon > 0) {
                    String headerName = line.substring(0, colon).trim();
                    if (headerName.equalsIgnoreCase("Host")) {
                        host = line.substring(colon + 1).trim();
                        break;
                    }
                }
            }

            String result = method + ";" + path + ";" + host;
            sendFrame(channel, selector, result);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
