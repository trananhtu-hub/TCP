import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;

public class Data_Cau_8 {
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

            // b. Nhan so nguyen he thap phan
            int n = dis.readInt();

            // c. Chuyen sang he co so 8 va 16, gui lan luot len server
            String octal = Integer.toOctalString(n);
            String hex = Integer.toHexString(n).toUpperCase();
            dos.writeUTF(octal);
            dos.writeUTF(hex);
            dos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
