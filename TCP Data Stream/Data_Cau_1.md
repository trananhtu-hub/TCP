import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;

public class Data_Cau_1 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2207;
        String studentCode = "B22DCCN749";
        String qCode = "VvO7QbgT";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);
            DataInputStream dis = new DataInputStream(socket.getInputStream());
            DataOutputStream dos = new DataOutputStream(socket.getOutputStream());

            // a. Gui studentCode;qCode
            dos.writeUTF(studentCode + ";" + qCode);
            dos.flush();

            // b. Nhan lan luot hai so nguyen a va b
            int a = dis.readInt();
            int b = dis.readInt();

            // c. Tinh tong, tich va gui lan luot len server
            int sum = a + b;
            int product = a * b;
            dos.writeInt(sum);
            dos.writeInt(product);
            dos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
