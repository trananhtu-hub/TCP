import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.util.HashSet;
import java.util.Set;

public class Character_Cau_6 {
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

            // b. Nhan lan luot 2 chuoi ngau nhien
            String s1 = reader.readLine();
            String s2 = reader.readLine();
            if (s1 == null || s2 == null) {
                return;
            }

            // c. Loai bo cac ky tu trong s1 xuat hien trong s2, giu nguyen thu tu
            Set<Character> toRemove = new HashSet<>();
            for (int i = 0; i < s2.length(); i++) {
                toRemove.add(s2.charAt(i));
            }

            StringBuilder sb = new StringBuilder();
            for (int i = 0; i < s1.length(); i++) {
                char c = s1.charAt(i);
                if (!toRemove.contains(c)) {
                    sb.append(c);
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
