
/*
BY:ADITYA KUMAR  
Topic:INHERITANCE
*/

import java.util.*;
class employee{
	String name,email,address;
	double basicpay;
	long  id,mobile;
	double da, hra, pf, cf;
void cal(double basicpay) {
		da = 0.97 * basicpay;
		hra = 0.1 * basicpay;
		pf = 0.12 * basicpay;
		cf = 0.01 * basicpay;
	}
void getData() {
        System.out.println("Employee details: ");
		System.out.println("Name : " + name);
		System.out.println("ID : " +  id);
		System.out.println("Email : " +  email);
		System.out.println("Mobile : " +  mobile);
		System.out.println("Basic Pay : Rs " + basicpay);
		System.out.println("D.A. : Rs " + da);
		System.out.println("H.R.A. : Rs " + hra);
		System.out.println("P.F. : Rs " + pf);
		System.out.println("C.F. : Rs " + cf);
		System.out.println("Gross Salary  = Rs " +  (basicpay + da + hra + pf));
		System.out.println("Net Salary  = Rs " +  (basicpay + da + hra - pf - cf) + "\n");
	}
	void inputData() {
		Scanner sc = new Scanner(System.in);
		System.out.print("Enter the name of the Employee : ");
		name = sc.next();
		System.out.print("Enter the id of the Employee : ");
		id = sc.nextInt();
		System.out.print("Enter the email of the Employee : ");
		email = sc.next();
		while(email.contains("@")==false || email.contains(".")==false) {
			System.out.print("invalid email of employee, Please type again");
			email = sc.next();
		}
		System.out.print("Enter the mobile no. of the Employee : ");
		mobile = sc.nextLong();
		
		while(String.valueOf(mobile).length()!=10) {
			System.out.print("invalid mobile of employee, Please type again");
			mobile = sc.nextInt();
		}
		System.out.print("Enter the address of the Employee : ");
		address = sc.next();
	}
}
class TeamLead extends employee{
	void setData(double a) {
		basicpay = a;
		cal(basicpay);
	}
};
class AssProjectManager extends employee{
	void setData(double a) {
		basicpay = a;
		cal(basicpay);
	}
};
class ProjectManager extends employee{
	void setData(double a) {
		basicpay = a;
		cal(basicpay);	}
};
class Programmer extends employee{
	void setData(double a) {
		basicpay = a;
		cal(basicpay);
	}
};
public class inheritence {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		Programmer a = new Programmer();
		TeamLead b = new TeamLead();
		AssProjectManager c = new AssProjectManager();
		ProjectManager d = new ProjectManager();
		
		int x=0;
		int y=1;
		double basicPay = 0.0;
		while(y!=0) {
		
			System.out.println(" Enter the choice for operation :\n 1. Programmer \n 2. Team Lead\n 3. Assistant Project Manager\n 4. Project Manager\n 5. exit!\n");
			x = sc.nextInt();
         switch(x) {
			case 1:
			
				a.inputData();
				System.out.print("Enter the basic pay of the Programmer: ");
				basicPay = sc.nextFloat();
				a.setData(basicPay);
				a.getData();
				break;
			case 2:
				
				b.inputData();
				System.out.print("Enter the basic pay of the Team Lead: ");
				basicPay = sc.nextFloat();
				b.setData(basicPay);
				b.getData();
				break;
			case 3:
				
				c.inputData();
				System.out.print("Enter the basic pay of the Assistant Project Manager: ");
				basicPay = sc.nextFloat();
				c.setData(basicPay);
				c.getData();
				break;
			case 4:
				
				d.inputData();
				System.out.print("Enter the basic pay of the Project Manager: ");
				basicPay = sc.nextFloat();
				d.setData(basicPay);
				d.getData();
				break;
				
			case 5:
				y = 0;
				break;
			}
	
		}
				
		sc.close();
		
	}
}






