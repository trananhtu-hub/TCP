import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class Character_Cau_2 {
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

            // b. Nhan chuoi ngau nhien
            String received = reader.readLine();
            if (received == null) {
                return;
            }

            // c. Tim tu dai nhat va vi tri bat dau trong chuoi ban dau
            String longestWord = "";
            int startPos = 0;
            Matcher matcher = Pattern.compile("\\S+").matcher(received);
            while (matcher.find()) {
                String word = matcher.group();
                if (word.length() > longestWord.length()) {
                    longestWord = word;
                    startPos = matcher.start();
                }
            }

            // d. Gui lan luot tu dai nhat va vi tri bat dau
            writer.write(longestWord);
            writer.newLine();
            writer.write(String.valueOf(startPos));
            writer.newLine();
            writer.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
