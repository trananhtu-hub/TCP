import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;

public class Data_Cau_10 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 807;
        String studentCode = "B22DCCN749";
        String qCode = "";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);
            DataInputStream dis = new DataInputStream(socket.getInputStream());
            DataOutputStream dos = new DataOutputStream(socket.getOutputStream());

            // a. Gui studentCode;qCode
            dos.writeUTF(studentCode + ";" + qCode);
            dos.flush();

            // b. Nhan k va chuoi mang so nguyen phan tach boi ","
            int k = dis.readInt();
            String received = dis.readUTF().trim();
            String[] parts = received.split(",");
            int n = parts.length;
            String[] rotated = new String[n];
            int shift = ((k % n) + n) % n;

            for (int i = 0; i < n; i++) {
                rotated[(i + shift) % n] = parts[i].trim();
            }

            // c. Gui chuoi mang da xoay phai k buoc len server
            String result = String.join(",", rotated);
            dos.writeUTF(result);
            dos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
