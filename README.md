     import java.util.*;

     public class ATM 
    {
    private double b;
    private Scanner s;

    public ATM(double initialBalance) 
    {
        this.b = initialBalance;
        this.s = new Scanner(System.in);
    }

    public void showMenu()
    {
        int ch;

        do {
            System.out.println("\n--- ATM Menu ---");
            System.out.println("1. Check Balance");
            System.out.println("2. Deposit Money");
            System.out.println("3. Withdraw Money");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            ch = s.nextInt();

            switch (ch)
            {
                case 1:
                    checkBalance();
                    break;
                case 2:
                    deposit();
                    break;
                case 3:
                    withdraw();
                    break;
                case 4:
                    System.out.println("Thank you for using the ATM.");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }

        } while (ch != 4);
    }

    public void checkBalance()
    {
        System.out.println("Current Balance: $" + b);
    }

    public void deposit()
    {
        System.out.print("Enter amount to deposit: ");
        double amount = s.nextDouble();
        if (amount > 0)
        {
            b += amount;
            System.out.println("Deposited $" + amount);
        }
        else
        {
            System.out.println("Invalid amount.");
        }
    }


    public void withdraw() 
    {
        System.out.print("Enter amount to withdraw: ");
        double amount = s.nextDouble();
        if (amount > 0 && amount <= b) 
        {
            b -= amount;
            System.out.println("Withdrew $" + amount);
        }
       else
        {
            System.out.println("Invalid or insufficient funds.");
        }
    }

    public static void main(String[] args) 
    {
        ATM atm = new ATM(500.00); // Initial balance
        atm.showMenu();
    }
}
