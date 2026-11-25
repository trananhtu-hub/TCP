import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;
import java.nio.charset.StandardCharsets;

public class Byte_Cau_2 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 806;
        String studentCode = "B22DCCN749";
        String qCode = "";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);
            InputStream in = socket.getInputStream();
            OutputStream out = socket.getOutputStream();

            // a. Gui studentCode;qCode
            String request = studentCode + ";" + qCode;
            out.write(request.getBytes(StandardCharsets.UTF_8));
            out.flush();

            // b. Nhan chuoi so nguyen phan tach boi "|"
            byte[] buffer = new byte[4096];
            int bytesRead = in.read(buffer);
            if (bytesRead == -1) {
                return;
            }
            String received = new String(buffer, 0, bytesRead, StandardCharsets.UTF_8).trim();

            // c. Tinh tong cac so nguyen va gui len server
            String[] parts = received.split("\\|");
            long sum = 0;
            for (String part : parts) {
                if (!part.trim().isEmpty()) {
                    sum += Long.parseLong(part.trim());
                }
            }

            String result = String.valueOf(sum);
            out.write(result.getBytes(StandardCharsets.UTF_8));
            out.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
