import TCP.Student;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.net.Socket;

public class Object_Cau_1 {
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

            // b. Nhan doi tuong TCP.Student va quy doi gpa -> gpaLetter
            Student student = (Student) ois.readObject();
            float gpa = student.getGpa();
            String letter;
            if (gpa > 3.7f) {
                letter = "A";
            } else if (gpa > 3.0f) {
                letter = "B";
            } else if (gpa > 2.0f) {
                letter = "C";
            } else if (gpa > 1.0f) {
                letter = "D";
            } else {
                letter = "F";
            }
            student.setGpaLetter(letter);

            // c. Gui doi tuong da xu ly len server
            oos.writeObject(student);
            oos.flush();
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
