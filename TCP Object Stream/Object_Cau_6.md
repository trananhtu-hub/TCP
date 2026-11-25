import TCP.EmployeePerformance;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.net.Socket;
import java.util.List;

public class Object_Cau_6 {
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

            // b. Nhan doi tuong TCP.EmployeePerformance, tinh avgScore va rating
            EmployeePerformance ep = (EmployeePerformance) ois.readObject();
            List<Integer> scores = ep.getMonthlyScores();
            float avgScore = 0.0f;
            if (scores != null && !scores.isEmpty()) {
                long sum = 0;
                for (Integer score : scores) {
                    if (score != null) {
                        sum += score;
                    }
                }
                avgScore = (float) sum / scores.size();
            }

            String rating;
            if (avgScore >= 90.0f) {
                rating = "Excellent";
            } else if (avgScore >= 75.0f) {
                rating = "Good";
            } else if (avgScore >= 60.0f) {
                rating = "Average";
            } else {
                rating = "Poor";
            }

            ep.setAvgScore(avgScore);
            ep.setRating(rating);

            // c. Gui doi tuong da cap nhat len server
            oos.writeObject(ep);
            oos.flush();
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
