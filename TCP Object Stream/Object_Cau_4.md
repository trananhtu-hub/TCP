import TCP.Customer;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.net.Socket;

public class Object_Cau_4 {
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

            // b. Nhan doi tuong TCP.Customer
            Customer customer = (Customer) ois.readObject();

            // c. Chuan hoa name, dayOfBirth, va tao userName
            String rawName = customer.getName() == null ? "" : customer.getName().trim();
            if (!rawName.isEmpty()) {
                String[] words = rawName.toLowerCase().split("\\s+");
                String lastName = words[words.length - 1];

                StringBuilder formattedName = new StringBuilder(lastName.toUpperCase());
                StringBuilder userName = new StringBuilder();
                if (words.length > 1) {
                    formattedName.append(",");
                    for (int i = 0; i < words.length - 1; i++) {
                        String w = words[i];
                        formattedName.append(" ")
                                .append(Character.toUpperCase(w.charAt(0)))
                                .append(w.substring(1));
                        userName.append(w.charAt(0));
                    }
                }
                userName.append(lastName);

                customer.setName(formattedName.toString());
                customer.setUserName(userName.toString());
            }

            String dob = customer.getDayOfBirth() == null ? "" : customer.getDayOfBirth().trim();
            String[] dobParts = dob.split("-");
            if (dobParts.length == 3) {
                customer.setDayOfBirth(dobParts[1] + "/" + dobParts[0] + "/" + dobParts[2]);
            }

            oos.writeObject(customer);
            oos.flush();
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
