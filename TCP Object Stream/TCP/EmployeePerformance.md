package TCP;

import java.io.Serializable;
import java.util.List;

public class EmployeePerformance implements Serializable {
    private static final long serialVersionUID = 20220915L;

    private int id;
    private String name;
    private List<Integer> monthlyScores;
    private float avgScore;
    private String rating;

    public EmployeePerformance() {
    }

    public EmployeePerformance(int id, String name, List<Integer> monthlyScores, float avgScore, String rating) {
        this.id = id;
        this.name = name;
        this.monthlyScores = monthlyScores;
        this.avgScore = avgScore;
        this.rating = rating;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public List<Integer> getMonthlyScores() {
        return monthlyScores;
    }

    public void setMonthlyScores(List<Integer> monthlyScores) {
        this.monthlyScores = monthlyScores;
    }

    public float getAvgScore() {
        return avgScore;
    }

    public void setAvgScore(float avgScore) {
        this.avgScore = avgScore;
    }

    public String getRating() {
        return rating;
    }

    public void setRating(String rating) {
        this.rating = rating;
    }

    @Override
    public String toString() {
        return "EmployeePerformance{id=" + id + ", name='" + name + "', monthlyScores=" + monthlyScores
                + ", avgScore=" + avgScore + ", rating='" + rating + "'}";
    }
}
