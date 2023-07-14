
/*
BY:ADITYA KUMAR  
Topic:BANK MANAGEMENT
*/

// FILE NAME: Bank.java

import java.util.*;
class Customer
{
    Scanner sc = new Scanner(System.in);
    String name;
    int age;

    public String getName()
    {
        return name;
    }

    void setName()
    {
        System.out.print("Enter name: ");
        name = sc.nextLine();
    }

    public int getCustomerAge()
    {
        return age;
    }

    void setCustomerAge()
    {
        try
        {
            System.out.print("Minimum age for creating an account is 18.\nEnter age: ");
            age = sc.nextInt();
            if(age<18)
            {
                throw new Exception("You are not old enough to create an account");
            }
        }
        catch(Exception e)
        {
            System.out.println(e);
            System.exit(0);
        }
    }
}


// FILE NAME: SavingsAccount.java


class Account
{
    Scanner sc = new Scanner(System.in);
    String accType;
    int accId;
    int balance;
    public String getAccountType()
    {
        return accType;
    }
    

    public int getAccId()
    {
        return accId;
    }
    
    public int getBalance()
    {
        return balance;
    }

    void setAccountType()
    {
        System.out.print("Enter your account type: ");
        accType = sc.next();
       
    }

    void setAccId()
    {
        System.out.print("Enter Account Id: ");
        accId = sc.nextInt();
    }
    
    void setBalance()
    {  
        System.out.print("Enter balance: ");
        balance = sc.nextInt();
    }

}

class SavingsAccount
{ 
    Scanner sc = new Scanner(System.in);
    int minBalance; 
    public int getMinimumBalance()
    {
        return minBalance;
    }
  
    void setMinimumBalance()
    {
        System.out.print("Enter minimum balance: ");
        minBalance = sc.nextInt();
    }
    

   
}
class Bank
{
    Scanner sc = new Scanner(System.in);
    Customer c1 = new Customer();
    SavingsAccount s1 = new SavingsAccount();
    Account a1 = new Account();
    
    void createAccount()
    {
        c1.setCustomerName();
        c1.setCustomerAge();
        a1.setAccId();
        a1.setAccountType();
        a1.setBalance();
        s1.setMinimumBalance();
    }


    void withdrawAmount()
    {
        int withdraw;
        System.out.print("Enter the amount you want to withdraw: ");
        withdraw = sc.nextInt();
        
        if(a1.getBalance() - withdraw < s1.getMinimumBalance())
        {
            System.out.println("Withdrawal Failed. Not enough balance.");
        }
        
        else if(withdraw > s1.getMinimumBalance())
        {
            System.out.println("Withdrawal Failed. Maximum limit of one transaction is "+s1.getMinimumBalance()+".");
        }
        
        else
        {
            a1.balance = a1.getBalance() - withdraw;
        }
    }

    void displayInfo()
    {
        String name = c1.getCustomerName();
        int age = c1.getCustomerAge();
        int accId = a1.getAccId();
        String accType = a1.getAccountType();
        int balance = a1.getBalance();
        int minBalance = s1.getMinimumBalance();
        System.out.println("Name "+name);
        System.out.println("Age: "+age);
        System.out.println("Account Type: "+accType);
        System.out.println("Account Id: "+accId);
        System.out.println("Balance: "+balance);
        System.out.println("Minimum Balance: "+minBalance);
    }
    
    void depositAmount()
    {
        int deposit;
        System.out.print("Enter the amount you want to deposit: ");
        deposit = sc.nextInt();
        a1.balance = a1.getBalance()+deposit ;
    }

    void checkBalance()
    {
        int balance;
        balance = a1.getBalance();
        System.out.println("Balance: "+balance);
    }
    
}



// FILE NAME: Account.java




// FILE NAME: Customer.java





public class Assignment_9
{
    public static void main(String[]args)
    {  Scanner sc = new Scanner(System.in);
        int x=0;
        int y=1;
      
        Bank b1 = new Bank();
        while(y!=0)
        {
            System.out.print("1 - Create Account\n2 - Display Account\n3 - Check Balance\n4 - Deposit Amount\n5 - Withdraw Amount\n6 - Exit\n");
            
           x = sc.nextInt();
            
            
            switch(x)
            {
                case 1: 
                b1.createAccount();
                break;
                
                case 2: 
                b1.displayInfo();
                break;
                
                case 3:
                 b1.checkBalance();
                break;
                
                case 4:
                 b1.depositAmount();
                break;
                
                case 5: 
                b1.withdrawAmount();
                break;
                
                case 6: 
                y=0;
                break;
                
               
            }
        }
        sc.close();
    }
}


