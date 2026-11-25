import TCP.BankAccount;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.math.BigDecimal;
import java.net.Socket;
import java.util.List;

public class Object_Cau_7 {
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

            // b. Nhan doi tuong TCP.BankAccount va tinh tong giao dich
            BankAccount account = (BankAccount) ois.readObject();
            BigDecimal total = BigDecimal.ZERO;
            List<Double> transactions = account.getTransactions();
            if (transactions != null) {
                for (Double amount : transactions) {
                    if (amount != null) {
                        total = total.add(BigDecimal.valueOf(amount));
                    }
                }
            }

            account.setBalanceSummary("Total Transactions: " + total.doubleValue());

            // c. Gui doi tuong da cap nhat len server
            oos.writeObject(account);
            oos.flush();
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
