import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.LinkedHashSet;
import java.util.Set;

public class Character_Cau_4 {
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

            // c. Loai bo ky tu dac biet, so, ky tu trung va giu nguyen thu tu xuat hien
            Set<Character> uniqueLetters = new LinkedHashSet<>();
            for (int i = 0; i < received.length(); i++) {
                char c = received.charAt(i);
                if (Character.isLetter(c)) {
                    uniqueLetters.add(c);
                }
            }

            StringBuilder sb = new StringBuilder();
            for (char c : uniqueLetters) {
                sb.append(c);
            }

            writer.write(sb.toString());
            writer.newLine();
            writer.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
