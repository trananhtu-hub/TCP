import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;

public class Data_Cau_4 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2207;
        String studentCode = "B22DCCN749";
        String qCode = "ybncbvbG";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);
            DataInputStream dis = new DataInputStream(socket.getInputStream());
            DataOutputStream dos = new DataOutputStream(socket.getOutputStream());

            // a. Gui studentCode;qCode
            dos.writeUTF(studentCode + ";" + qCode);
            dos.flush();

            // b. Nhan chuoi ma hoa caesar va gia tri dich chuyen s
            String encoded = dis.readUTF();
            int s = dis.readInt();

            // c. Theo de: "de giai ma ... voi s = 3 thi 'A' -> 'D'" (dich +s)
            // Neu server ma hoa theo chieu +s va yeu cau giai ma -s, doi +shift thanh
            // -shift
            int shift = ((s % 26) + 26) % 26;
            StringBuilder decoded = new StringBuilder();
            for (int i = 0; i < encoded.length(); i++) {
                char c = encoded.charAt(i);
                if (c >= 'A' && c <= 'Z') {
                    decoded.append((char) ('A' + (c - 'A' + shift) % 26));
                } else if (c >= 'a' && c <= 'z') {
                    decoded.append((char) ('a' + (c - 'a' + shift) % 26));
                } else {
                    decoded.append(c);
                }
            }

            dos.writeUTF(decoded.toString());
            dos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
