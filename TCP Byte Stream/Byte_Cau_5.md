import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.Arrays;

public class Byte_Cau_5 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2206;
        String studentCode = "B22DCCN749";
        String qCode = "wkRvOh1v";

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

            // c. Tim khoang cach nho nhat va hai gia tri lon nhat tao nen khoang cach do
            String[] parts = received.split(",");
            int[] nums = new int[parts.length];
            for (int i = 0; i < parts.length; i++) {
                nums[i] = Integer.parseInt(parts[i].trim());
            }
            Arrays.sort(nums);

            long minDiff = Long.MAX_VALUE;
            int first = nums[0];
            int second = nums[1];
            for (int i = 0; i < nums.length - 1; i++) {
                long diff = (long) nums[i + 1] - nums[i];
                // Dung <= de uu tien cap gia tri lon nhat khi khoang cach bang nhau
                if (diff <= minDiff) {
                    minDiff = diff;
                    first = nums[i];
                    second = nums[i + 1];
                }
            }

            String result = minDiff + "," + first + "," + second;
            out.write(result.getBytes(StandardCharsets.UTF_8));
            out.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
