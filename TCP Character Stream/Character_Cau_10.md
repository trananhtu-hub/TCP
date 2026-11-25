import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.ArrayList;
import java.util.List;

public class Character_Cau_10 {
    private static boolean hasAtLeastTwoVowels(String word) {
        int count = 0;
        for (int i = 0; i < word.length(); i++) {
            char c = Character.toLowerCase(word.charAt(i));
            if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
                count++;
                if (count >= 2) {
                    return true;
                }
            }
        }
        return false;
    }

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

            // c. Tim tat ca cac tu chua it nhat 2 ky tu nguyen am
            List<String> matched = new ArrayList<>();
            String trimmed = received.trim();
            if (!trimmed.isEmpty()) {
                String[] words = trimmed.split("\\s+");
                for (String word : words) {
                    if (hasAtLeastTwoVowels(word)) {
                        matched.add(word);
                    }
                }
            }

            writer.write(String.join(", ", matched));
            writer.newLine();
            writer.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
