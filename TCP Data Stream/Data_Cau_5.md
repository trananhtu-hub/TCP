import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.IOException;
import java.net.Socket;

public class Data_Cau_5 {
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

            // b. Nhan n va mang n so nguyen
            int n = dis.readInt();
            int[] arr = new int[n];
            int sum = 0;
            for (int i = 0; i < n; i++) {
                arr[i] = dis.readInt();
                sum += arr[i];
            }

            // c. Tinh tong, trung binh cong (float) va phuong sai (float)
            float avg = (float) sum / n;
            double sumSq = 0.0;
            for (int i = 0; i < n; i++) {
                double diff = arr[i] - avg;
                sumSq += diff * diff;
            }
            float variance = (float) (sumSq / n);

            dos.writeInt(sum);
            dos.writeFloat(avg);
            dos.writeFloat(variance);
            dos.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
