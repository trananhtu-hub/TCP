import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.HashMap;
import java.util.Map;

public class Byte_Cau_3 {
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

            // b. Nhan chuoi ky tu tu server
            byte[] buffer = new byte[4096];
            int bytesRead = in.read(buffer);
            if (bytesRead == -1) {
                return;
            }
            String s = new String(buffer, 0, bytesRead, StandardCharsets.UTF_8).replaceAll("[\\r\\n]+$", "");

            // c. Tim chuoi con dai nhat khong co ky tu lap lai
            Map<Character, Integer> lastSeen = new HashMap<>();
            int left = 0;
            int bestStart = 0;
            int maxLen = 0;
            for (int right = 0; right < s.length(); right++) {
                char c = s.charAt(right);
                Integer prev = lastSeen.get(c);
                if (prev != null && prev >= left) {
                    left = prev + 1;
                }
                lastSeen.put(c, right);
                int curLen = right - left + 1;
                if (curLen > maxLen) {
                    maxLen = curLen;
                    bestStart = left;
                }
            }

            String longestSub = s.substring(bestStart, bestStart + maxLen);
            String result = longestSub + ";" + maxLen;
            out.write(result.getBytes(StandardCharsets.UTF_8));
            out.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
