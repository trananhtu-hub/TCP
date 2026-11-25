import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.Arrays;

public class Character_Cau_7 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 808;
        String studentCode = "B22DCCN749";
        String qCode = "";

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

            // b. Nhan chuoi chua nhieu tu phan tach boi khoang trang
            String received = reader.readLine();
            if (received == null) {
                return;
            }

            // c. Tach tu va sap xep theo thu tu tu dien (phan biet hoa thuong)
            String trimmed = received.trim();
            String result = "";
            if (!trimmed.isEmpty()) {
                String[] words = trimmed.split("\\s+");
                Arrays.sort(words);
                result = String.join(" ", words);
            }

            // d. Gui chuoi da sap xep len server
            writer.write(result);
            writer.newLine();
            writer.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
