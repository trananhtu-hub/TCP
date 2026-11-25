import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;
import java.nio.charset.StandardCharsets;

public class Byte_Cau_1 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2206;
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

            // c. Tim gia tri lon thu hai va vi tri xuat hien cua no
            String[] parts = received.split(",");
            int[] nums = new int[parts.length];
            int max1 = Integer.MIN_VALUE;
            for (int i = 0; i < parts.length; i++) {
                nums[i] = Integer.parseInt(parts[i].trim());
                if (nums[i] > max1) {
                    max1 = nums[i];
                }
            }

            int max2 = Integer.MIN_VALUE;
            int idx2 = -1;
            for (int i = 0; i < nums.length; i++) {
                if (nums[i] < max1 && nums[i] > max2) {
                    max2 = nums[i];
                    idx2 = i;
                }
            }
            if (idx2 == -1 && nums.length > 1) {
                max2 = nums[1];
                idx2 = 1;
            } else if (idx2 == -1) {
                max2 = nums[0];
                idx2 = 0;
            }

            String result = max2 + "," + idx2;
            out.write(result.getBytes(StandardCharsets.UTF_8));
            out.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
