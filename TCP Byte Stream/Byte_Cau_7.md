import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;
import java.nio.charset.StandardCharsets;

public class Byte_Cau_7 {
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

            // b. Nhan chuoi so nguyen phan tach boi ","
            byte[] buffer = new byte[4096];
            int bytesRead = in.read(buffer);
            if (bytesRead == -1) {
                return;
            }
            String received = new String(buffer, 0, bytesRead, StandardCharsets.UTF_8).trim();

            // c. Tim do dai chuoi con tang dan lien tiep dai nhat
            String[] parts = received.split(",");
            int[] nums = new int[parts.length];
            for (int i = 0; i < parts.length; i++) {
                nums[i] = Integer.parseInt(parts[i].trim());
            }

            int maxLen = nums.length > 0 ? 1 : 0;
            int curLen = 1;
            for (int i = 1; i < nums.length; i++) {
                if (nums[i] > nums[i - 1]) {
                    curLen++;
                } else {
                    curLen = 1;
                }
                if (curLen > maxLen) {
                    maxLen = curLen;
                }
            }

            String result = String.valueOf(maxLen);
            out.write(result.getBytes(StandardCharsets.UTF_8));
            out.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
