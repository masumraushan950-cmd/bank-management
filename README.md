# bank-management

public class Account {
    private String name;
    private String accountNumber;
    private double balance;

    public Account(String name, String accountNumber) {
        this.name = name;
        this.accountNumber = accountNumber;
        this.balance = 0.0;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited: " + amount);
    }

    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawn: " + amount);
        } else {
            System.out.println("Insufficient balance!");
        }
    }

    public double getBalance() {
        return balance;
    }

    public void displayDetails() {
        System.out.println("\n--- Account Details ---");
        System.out.println("Name: " + name);
        System.out.println("Account Number: " + accountNumber);
        System.out.println("Balance: " + balance);
        System.out.println("------------------------\n");
    }
}


import java.util.HashMap;

public class Bank {
    private HashMap<String, Account> accounts = new HashMap<>();

    public void createAccount(String name, String accNo) {
        if (accounts.containsKey(accNo)) {
            System.out.println("Account already exists!");
        } else {
            accounts.put(accNo, new Account(name, accNo));
            System.out.println("Account created successfully!");
        }
    }

    public Account getAccount(String accNo) {
        return accounts.get(accNo);
    }
}


import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Bank bank = new Bank();
        Scanner sc = new Scanner(System.in);

        int choice;

        do {
            System.out.println("\n==== BANK MANAGEMENT SYSTEM ====");
            System.out.println("1. Create Account");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Check Balance");
            System.out.println("5. Account Details");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");

            choice = sc.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter Name: ");
                    String name = sc.next();
                    System.out.print("Enter Account Number: ");
                    String accNo = sc.next();
                    bank.createAccount(name, accNo);
                    break;

                case 2:
                    System.out.print("Enter Account Number: ");
                    accNo = sc.next();
                    Account acc = bank.getAccount(accNo);
                    if (acc != null) {
                        System.out.print("Enter Amount: ");
                        double amt = sc.nextDouble();
                        acc.deposit(amt);
                    } else {
                        System.out.println("Account Not Found!");
                    }
                    break;

                case 3:
                    System.out.print("Enter Account Number: ");
                    accNo = sc.next();
                    acc = bank.getAccount(accNo);
                    if (acc != null) {
                        System.out.print("Enter Amount: ");
                        double amt = sc.nextDouble();
                        acc.withdraw(amt);
                    } else {
                        System.out.println("Account Not Found!");
                    }
                    break;

                case 4:
                    System.out.print("Enter Account Number: ");
                    accNo = sc.next();
                    acc = bank.getAccount(accNo);
                    if (acc != null) {
                        System.out.println("Balance: " + acc.getBalance());
                    } else {
                        System.out.println("Account Not Found!");
                    }
                    break;

                case 5:
                    System.out.print("Enter Account Number: ");
                    accNo = sc.next();
                    acc = bank.getAccount(accNo);
                    if (acc != null) {
                        acc.displayDetails();
                    } else {
                        System.out.println("Account Not Found!");
                    }
                    break;

                case 6:
                    System.out.println("Thank you for using the system!");
                    break;

                default:
                    System.out.println("Invalid choice!");
            }

        } while (choice != 6);

        sc.close();
    }
}


<!DOCTYPE html>
<html>
<head>
    <title>Simple Bank Management System</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

<div class="box">
    <h1>Bank Management System</h1>
    <p>Mini Project using HTML, CSS and Basic Java</p>

    <button>Create Account</button>
    <button>Deposit Money</button>
    <button>Withdraw Money</button>
    <button>Check Balance</button>
    <button>Account Details</button>
</div>

</body>
</html>


body {
    background: #eef7ff;
    font-family: Arial, sans-serif;
}

.box {
    width: 350px;
    margin: 100px auto;
    padding: 20px;
    background: white;
    text-align: center;
    border-radius: 8px;
    box-shadow: 0 0 10px #999;
}

button {
    width: 90%;
    padding: 10px;
    margin: 8px;
    background: #007bff;
    border: none;
    color: white;
    font-size: 16px;
    border-radius: 4px;
}

button:hover {
    background: #0059b3;
    cursor: pointer;
}
