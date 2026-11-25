import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;

public class Data_Cau_2 {
    private static int gcd(int a, int b) {
        a = Math.abs(a);
        b = Math.abs(b);
        while (b != 0) {
            int tmp = a % b;
            a = b;
            b = tmp;
        }
        return a;
    }

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

            // b. Nhan hai so nguyen a va b
            int a = dis.readInt();
            int b = dis.readInt();

            // c. Tinh UCLN, BCNN, tong, tich va gui lan luot len server
            int ucln = gcd(a, b);
            int bcnn = (ucln == 0) ? 0 : Math.abs((a / ucln) * b);
            int sum = a + b;
            int product = a * b;

            dos.writeInt(ucln);
            dos.writeInt(bcnn);
            dos.writeInt(sum);
            dos.writeInt(product);
            dos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
