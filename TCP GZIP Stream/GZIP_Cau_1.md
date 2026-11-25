import java.io.ByteArrayOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.Base64;
import java.util.zip.GZIPInputStream;
import java.util.zip.GZIPOutputStream;

public class GZIP_Cau_1 {
    private static String readLineUtf8(InputStream in) throws IOException {
        ByteArrayOutputStream baos = new ByteArrayOutputStream();
        int b;
        while ((b = in.read()) != -1) {
            if (b == '\n') {
                break;
            }
            baos.write(b);
        }
        if (b == -1 && baos.size() == 0) {
            return null;
        }
        byte[] bytes = baos.toByteArray();
        int len = bytes.length;
        if (len > 0 && bytes[len - 1] == '\r') {
            len--;
        }
        return new String(bytes, 0, len, StandardCharsets.UTF_8);
    }

    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2210;
        String studentCode = "B22DCCN749";
        String qCode = "iRDJcMeL";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);

            // Mo GZIPOutputStream voi syncFlush = true truoc khi tao GZIPInputStream de
            // tranh deadlock header
            GZIPOutputStream gzipOut = new GZIPOutputStream(socket.getOutputStream(), true);

            // a. Gui studentCode;qCode ket thuc bang '\n'
            String request = studentCode + ";" + qCode + "\n";
            gzipOut.write(request.getBytes(StandardCharsets.UTF_8));
            gzipOut.flush();

            // b. Doc truc tiep tung byte tu GZIPInputStream den '\n' (tranh BufferedReader
            // bi chan do available() == 1)
            GZIPInputStream gzipIn = new GZIPInputStream(socket.getInputStream());
            String received = readLineUtf8(gzipIn);
            if (received == null) {
                return;
            }

            // c. Dao nguoc chuoi va ma hoa Base64 cua chuoi da dao nguoc
            String reversed = new StringBuilder(received).reverse().toString();
            String base64 = Base64.getEncoder().encodeToString(reversed.getBytes(StandardCharsets.UTF_8));
            String result = reversed + "|" + base64 + "\n";

            gzipOut.write(result.getBytes(StandardCharsets.UTF_8));
            gzipOut.flush();
            gzipOut.finish();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
