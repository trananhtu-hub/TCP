import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.ArrayList;
import java.util.List;

public class Character_Cau_8 {
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

            // c. Phan loai tu theo do dai: < 4, 4..7, > 7
            List<String> shortWords = new ArrayList<>();
            List<String> mediumWords = new ArrayList<>();
            List<String> longWords = new ArrayList<>();

            String trimmed = received.trim();
            if (!trimmed.isEmpty()) {
                String[] words = trimmed.split("\\s+");
                for (String word : words) {
                    int len = word.length();
                    if (len < 4) {
                        shortWords.add(word);
                    } else if (len <= 7) {
                        mediumWords.add(word);
                    } else {
                        longWords.add(word);
                    }
                }
            }

            String result = shortWords.toString() + "," + mediumWords.toString() + "," + longWords.toString();
            writer.write(result);
            writer.newLine();
            writer.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
