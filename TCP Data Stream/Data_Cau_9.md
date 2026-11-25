import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class Data_Cau_9 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 807;
        String studentCode = "B22DCCN749";
        String qCode = "";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);
            DataInputStream dis = new DataInputStream(socket.getInputStream());
            DataOutputStream dos = new DataOutputStream(socket.getOutputStream());

            // a. Gui studentCode;qCode
            dos.writeUTF(studentCode + ";" + qCode);
            dos.flush();

            // b. Nhan chuoi mang so nguyen phan tach boi ","
            String received = dis.readUTF().trim();
            String[] parts = received.split(",");
            int n = parts.length;
            int[] arr = new int[n];
            for (int i = 0; i < n; i++) {
                arr[i] = Integer.parseInt(parts[i].trim());
            }

            // c. Tim day con tang dan dai nhat (LIS)
            int[] dp = new int[n];
            int[] prev = new int[n];
            Arrays.fill(dp, 1);
            Arrays.fill(prev, -1);

            int maxLen = n > 0 ? 1 : 0;
            int bestEnd = 0;
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < i; j++) {
                    if (arr[j] < arr[i] && dp[j] + 1 > dp[i]) {
                        dp[i] = dp[j] + 1;
                        prev[i] = j;
                    }
                }
                if (dp[i] > maxLen) {
                    maxLen = dp[i];
                    bestEnd = i;
                }
            }

            List<Integer> lis = new ArrayList<>();
            for (int cur = bestEnd; cur != -1 && n > 0; cur = prev[cur]) {
                lis.add(arr[cur]);
            }
            Collections.reverse(lis);

            StringBuilder sb = new StringBuilder();
            for (int i = 0; i < lis.size(); i++) {
                if (i > 0) {
                    sb.append(",");
                }
                sb.append(lis.get(i));
            }

            dos.writeUTF(sb.toString());
            dos.writeInt(maxLen);
            dos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
