import TCP.Laptop;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.net.Socket;

public class Object_Cau_2 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 2209;
        String studentCode = "B22DCCN749";
        String qCode = "1xX5HkFw";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);
            ObjectOutputStream oos = new ObjectOutputStream(socket.getOutputStream());
            oos.flush();
            ObjectInputStream ois = new ObjectInputStream(socket.getInputStream());

            // a. Gui doi tuong chuoi studentCode;qCode
            oos.writeObject(studentCode + ";" + qCode);
            oos.flush();

            // b. Nhan doi tuong TCP.Laptop
            Laptop laptop = (Laptop) ois.readObject();

            // c. Sua ten (dao nguoc tu dau va tu cuoi) va so luong (dao nguoc chu so)
            String rawName = laptop.getName() == null ? "" : laptop.getName().trim();
            if (!rawName.isEmpty()) {
                String[] words = rawName.split("\\s+");
                if (words.length > 1) {
                    String tmp = words[0];
                    words[0] = words[words.length - 1];
                    words[words.length - 1] = tmp;
                }
                laptop.setName(String.join(" ", words));
            }

            int qty = laptop.getQuantity();
            int sign = qty < 0 ? -1 : 1;
            String reversedDigits = new StringBuilder(String.valueOf(Math.abs(qty))).reverse().toString();
            laptop.setQuantity(sign * Integer.parseInt(reversedDigits));

            oos.writeObject(laptop);
            oos.flush();
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
