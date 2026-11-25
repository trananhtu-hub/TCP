import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.Arrays;

public class Byte_Cau_9 {
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

            // c. Tim 2 so co trung binh (tong / 2) gan nhat voi gia tri trung binh toan day (target = 2 * avg)
            String[] parts = received.split(",");
            int[] nums = new int[parts.length];
            long totalSum = 0;
            for (int i = 0; i < parts.length; i++) {
                nums[i] = Integer.parseInt(parts[i].trim());
                totalSum += nums[i];
            }
            Arrays.sort(nums);

            double avg = (double) totalSum / nums.length;
            double target = 2.0 * avg;
            double minDiff = Double.MAX_VALUE;
            int num1 = nums[0];
            int num2 = nums[1];

            for (int i = 0; i < nums.length; i++) {
                for (int j = i + 1; j < nums.length; j++) {
                    double diff = Math.abs((nums[i] + nums[j]) - target);
                    if (diff < minDiff - 1e-9
                            || (Math.abs(diff - minDiff) <= 1e-9 && Math.abs(nums[j] - nums[i]) < Math.abs(num2 - num1))) {
                        minDiff = diff;
                        num1 = nums[i];
                        num2 = nums[j];
                    }
                }
            }

            String result = num1 + "," + num2;
            out.write(result.getBytes(StandardCharsets.UTF_8));
            out.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
