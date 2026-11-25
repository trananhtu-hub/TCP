package TCP;

import java.io.Serializable;
import java.util.List;

public class BankAccount implements Serializable {
    private static final long serialVersionUID = 20210601L;

    private int accountId;
    private String accountHolder;
    private double balance;
    private List<Double> transactions;
    private String balanceSummary;

    public BankAccount() {
    }

    public BankAccount(int accountId, String accountHolder, double balance, List<Double> transactions,
            String balanceSummary) {
        this.accountId = accountId;
        this.accountHolder = accountHolder;
        this.balance = balance;
        this.transactions = transactions;
        this.balanceSummary = balanceSummary;
    }

    public int getAccountId() {
        return accountId;
    }

    public void setAccountId(int accountId) {
        this.accountId = accountId;
    }

    public String getAccountHolder() {
        return accountHolder;
    }

    public void setAccountHolder(String accountHolder) {
        this.accountHolder = accountHolder;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    public List<Double> getTransactions() {
        return transactions;
    }

    public void setTransactions(List<Double> transactions) {
        this.transactions = transactions;
    }

    public String getBalanceSummary() {
        return balanceSummary;
    }

    public void setBalanceSummary(String balanceSummary) {
        this.balanceSummary = balanceSummary;
    }

    @Override
    public String toString() {
        return "BankAccount{accountId=" + accountId + ", accountHolder='" + accountHolder
                + "', balance=" + balance + ", transactions=" + transactions
                + ", balanceSummary='" + balanceSummary + "'}";
    }
}
