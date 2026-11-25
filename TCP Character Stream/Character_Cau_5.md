import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.LinkedHashMap;
import java.util.Map;

public class Character_Cau_5 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2208;
        String studentCode = "B22DCCN749";
        String qCode = "ugoAP4QS";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);
            BufferedWriter writer = new BufferedWriter(
                    new OutputStreamWriter(socket.getOutputStream(), StandardCharsets.UTF_8));
            BufferedReader reader = new BufferedReader(
                    new InputStreamReader(socket.getInputStream(), StandardCharsets.UTF_8));

            // a. Gui studentCode;qCode
            writer.write(studentCode + ";" + qCode);
            writer.newLine();
            writer.flush();

            // b. Nhan chuoi ngau nhien
            String received = reader.readLine();
            if (received == null) {
                return;
            }

            // c. Dem cac ky tu (chu hoac so) xuat hien nhieu hon 1 lan
            Map<Character, Integer> counts = new LinkedHashMap<>();
            for (int i = 0; i < received.length(); i++) {
                char c = received.charAt(i);
                if (Character.isLetterOrDigit(c)) {
                    counts.put(c, counts.getOrDefault(c, 0) + 1);
                }
            }

            StringBuilder sb = new StringBuilder();
            for (Map.Entry<Character, Integer> entry : counts.entrySet()) {
                if (entry.getValue() > 1) {
                    sb.append(entry.getKey()).append(":").append(entry.getValue()).append(",");
                }
            }

            writer.write(sb.toString());
            writer.newLine();
            writer.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
