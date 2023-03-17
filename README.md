# Oasis-Infobyte-

package OasisInfoByte;

import java.util.*;

class BankAccount {
	String name = "Xyz";
	String PIN = "1234";
	String accountNo = "1234";
	float Balance = 100000f;
	float transactions = 0;
	String transactionH = "";
	Scanner sc = new Scanner(System.in);
	String TPin;
	String TAccN;
	String ReciverName;

// Login with Account and PIN :	
	public void Login() {
		boolean loginIs = false;
		System.out.print("\n ---------LOGIN--------\n ");

		while (!loginIs) {
			System.out.println("enter your A/C number :");
			TAccN = sc.nextLine();
			if (TAccN.equals(accountNo)) {
				while (!loginIs) {
					System.out.println("\n enter your PIN :");
					TPin = sc.nextLine();
					if (TPin.equals(PIN)) {
						loginIs = true;
					} else {
						System.out.print("\nXXXXXXXX Wrong PIN XXXXXXXX\n ");
					}
				}
			} else {
				System.out.print("\n Wrong Account number \n\n");
			}
		}
	}

	// Balance INQURIY
	public void Balance() {

		System.out.print("\n ---------BALANCE INQURIY--------\n\n ");
		System.out.print("Availabel Balance :" + Balance + " RS"+"\n");
	}

	// withdrawal money

	public void Withdraw() {
		System.out.print("\n ---------WITHDRAW MONEY--------\n ");
		while(!false) {
		System.out.print("Enter Amount :");
		float Amount = sc.nextFloat();
		if (Amount > Balance) {
			System.out.print("\n incificent Balance \n");
		} else {
			transactions++;
			Balance -= Amount;
			System.out.print("\n Withdraw  sccussefull :" + Balance +"\n");
			String str = Amount + " Rs Withdraw\n";
			transactionH = transactionH.concat(str);
			return;
		}
	}
		}

	// Deposit money
	public void Deposit() {
		System.out.print("\n ---------DEPOSIT MONEY--------\n\n ");

		boolean Enter = false;
		while (!Enter) {
			System.out.print("Enter Amount :");
			float Amount = sc.nextFloat();
			if (Amount == 0) {
				System.out.print("\n Please enter Amount :");
			} else {
				transactions++;
				Balance += Amount;
				System.out.print("\n Deposit sccussesfull \n");
				String str = Amount + " Rs Deposit \n";
				transactionH = transactionH.concat(str);
				return;
			}
		}
	}

	// Money Transfer
	public void Transfer() {
		int Amount;
		System.out.print("\n ---------MONEY TRANSFER--------\n\n ");
		System.out.print("Enter the sander Name :");
		ReciverName = sc.next();
		while (!false) {
			System.out.print("\n Enter Amount :");
			Amount = sc.nextInt();

			if (Amount == 0) {
				System.out.print("\n please enter Amount :");
			} else 
			{
				if (Amount>15000) {
					System.out.print("\n invalid amount limit is 15000 RS only ");
				} else
				{
					if(Amount > Balance){
						System.out.print("\n insificent Balance ");
						}
				else {
					System.out.print("\n Transfer Sccussesfull");
					transactions++;
					String str = Amount + ".  Rs Transfer To " + ReciverName +"\n";
					transactionH = transactionH.concat(str);
					return;
				}
			}}
		}
	}

// Transaction History 
	public void TransactionHistory() {
		System.out.print("\n ---------TRANSACTION HISTORY--------\n\n ");

		if (transactions == 0) {
			System.out.println("\nEmpty");
		} else {
			System.out.println("\n" + transactionH);
		}
	}
}

public class ATMinterface {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner sc = new Scanner(System.in);
		BankAccount Obj = new BankAccount();
		Obj.Login();
		boolean InterMain = false;
		while (!InterMain) {
			System.out.print("\n********" + "MAIN MENU" + "********\n");
			System.out.print("\t\t\t"+Obj.name+"\n");
			System.out.println("\n" + " 1. Withdraw " + "\n" + " 2. Balance " + "\n" + " 3. Transfer " + "\n"
					+ " 4. Transaction History " + "\n" + " 5. Deposit " + "\n" + " 6. Exit \n");
			System.out.println("Enter your choice :");
			int choice = sc.nextInt();

			switch (choice) {
			case 1:
				Obj.Withdraw();
				break;
			case 2:
				Obj.Balance();
				break;
			case 3:
				Obj.Transfer();
				break;
			case 4:
				Obj.TransactionHistory();
				break;
			case 5:
				Obj.Deposit();
				break;
			case 6:
				System.exit(0);
				break;
			}
		}
	}
}
