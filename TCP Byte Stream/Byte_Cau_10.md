import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.HashMap;
import java.util.Map;

public class Byte_Cau_10 {
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

            // c. Tim day con lien tiep dai nhat co tong chia het cho 3 -> gui "start,end"
            String[] parts = received.split(",");
            Map<Integer, Integer> firstIndexByMod = new HashMap<>();
            firstIndexByMod.put(0, -1);

            long prefixSum = 0;
            int maxLen = 0;
            int bestStart = -1;
            int bestEnd = -1;

            for (int i = 0; i < parts.length; i++) {
                prefixSum += Long.parseLong(parts[i].trim());
                int mod = (int) (((prefixSum % 3) + 3) % 3);
                Integer prevIdx = firstIndexByMod.get(mod);
                if (prevIdx != null) {
                    int len = i - prevIdx;
                    if (len > maxLen) {
                        maxLen = len;
                        bestStart = prevIdx + 1;
                        bestEnd = i;
                    }
                } else {
                    firstIndexByMod.put(mod, i);
                }
            }

            String result = bestStart + "," + bestEnd;
            out.write(result.getBytes(StandardCharsets.UTF_8));
            out.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
