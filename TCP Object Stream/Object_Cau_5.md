import TCP.Address;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.net.Socket;

public class Object_Cau_5 {
    public static void main(String[] args) {
        String serverHost = "36.50.135.242";
        int serverPort = 809;
        String studentCode = "B22DCCN749";
        String qCode = "";

        try (Socket socket = new Socket(serverHost, serverPort)) {
            socket.setSoTimeout(5000);
            ObjectOutputStream oos = new ObjectOutputStream(socket.getOutputStream());
            oos.flush();
            ObjectInputStream ois = new ObjectInputStream(socket.getInputStream());

            // a. Gui doi tuong chuoi studentCode;qCode
            oos.writeObject(studentCode + ";" + qCode);
            oos.flush();

            // b. Nhan doi tuong TCP.Address va chuan hoa addressLine, postalCode
            Address address = (Address) ois.readObject();

            String rawAddr = address.getAddressLine() == null ? "" : address.getAddressLine().trim();
            if (!rawAddr.isEmpty()) {
                String[] words = rawAddr.split("\\s+");
                StringBuilder normalized = new StringBuilder();
                for (int i = 0; i < words.length; i++) {
                    if (i > 0) {
                        normalized.append(" ");
                    }
                    String w = words[i];
                    normalized.append(Character.toUpperCase(w.charAt(0)))
                            .append(w.substring(1).toLowerCase());
                }
                address.setAddressLine(normalized.toString());
            }

            String rawPostal = address.getPostalCode() == null ? "" : address.getPostalCode().trim();
            String digits = rawPostal.replaceAll("[^0-9]", "");
            if (digits.length() == 6) {
                address.setPostalCode(digits.substring(0, 3) + "-" + digits.substring(3));
            } else if (digits.length() > 3) {
                address.setPostalCode(digits.substring(0, 3) + "-" + digits.substring(3));
            }

            // c. Gui doi tuong da chuan hoa len server
            oos.writeObject(address);
            oos.flush();
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
