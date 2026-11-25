import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.ArrayList;
import java.util.List;

public class Character_Cau_1 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2208;
        String studentCode = "B22DCCN749";
        String qCode = "sY007xif";

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

            // b. Nhan danh sach ten mien
            String received = reader.readLine();
            if (received == null) {
                return;
            }

            // c. Loc cac ten mien .edu va gui len server
            String[] domains = received.split(",");
            List<String> eduDomains = new ArrayList<>();
            for (String domain : domains) {
                String trimmed = domain.trim();
                if (trimmed.toLowerCase().endsWith(".edu")) {
                    eduDomains.add(trimmed);
                }
            }

            writer.write(String.join(", ", eduDomains));
            writer.newLine();
            writer.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
