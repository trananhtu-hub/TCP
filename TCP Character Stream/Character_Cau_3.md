import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;

public class Character_Cau_3 {
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

            // c. Tach thanh chuoi chu/so va chuoi ky tu dac biet, gui lan luot
            StringBuilder alnum = new StringBuilder();
            StringBuilder special = new StringBuilder();
            for (int i = 0; i < received.length(); i++) {
                char c = received.charAt(i);
                if (Character.isLetterOrDigit(c)) {
                    alnum.append(c);
                } else {
                    special.append(c);
                }
            }

            writer.write(alnum.toString());
            writer.newLine();
            writer.write(special.toString());
            writer.newLine();
            writer.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
