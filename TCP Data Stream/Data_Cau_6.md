import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;

public class Data_Cau_6 {
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

            // b. Nhan n lan tung xuc xac va n gia tri tuong ung
            int n = dis.readInt();
            int[] counts = new int[7];
            for (int i = 0; i < n; i++) {
                int val = dis.readInt();
                if (val >= 1 && val <= 6) {
                    counts[val]++;
                }
            }

            // c. Tinh xac suat xuat hien cua [1, 2, 3, 4, 5, 6] va gui lan luot
            for (int face = 1; face <= 6; face++) {
                float prob = (float) counts[face] / n;
                dos.writeFloat(prob);
            }
            dos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
