Make ATM transactions in the same project using "Switch-Case"

import java.util.Scanner;
public class Odev25 {
    public static void main(String[] args) {

        String userName, password;
        Scanner input = new Scanner(System.in);
        int right = 3;
        int balance = 1500;
        int select;
        boolean session = true;

        while (right > 0) {                                                                     // Deneme hakkı
            System.out.print("Enter your username: ");
            userName = input.nextLine();
            System.out.print("Enter your password: ");
            password = input.nextLine();

            if (userName.equals("patika") && password.equals("dev123")) {                      // Bilgiler doğru girildiğinde girilen döngü
                System.out.println("Hello, welcome to the bank ! ");
                while(session) {
                    System.out.println("1-Deposit Money\n" + "2-Withdraw Money\n" + "3-Balance Inquiry\n" + "4-Sign Out");
                    System.out.print("Please enter your selection: ");

                    select = input.nextInt();

                    switch (select) {
                        case 1:
                            System.out.print("Amount of money to be loaded : ");               // Yüklenecek para miktarını giriniz.
                            int price = input.nextInt();
                            balance += price;
                            System.out.println("Your balance = " + balance);
                            break;
                        case 2:
                            System.out.print("The amount of money to be withdrawn : ");      // Çekilecek para miktarını giriniz.
                            price = input.nextInt();
                            if (price > balance) {                                           // Bakiyeniz yetersiz.
                                System.out.print("Your balance is insufficient. ");
                            } else {
                                balance -= price;
                                System.out.println("Your balance = " + balance);
                            }
                            break;
                        case 3:
                            System.out.print("Your balance " + balance);                                  // Bakiye sorgulama
                            break;
                        case 4:
                            System.out.println("Exit");
                            right =-1;
                        default:
                            System.out.println("Please try again");
                            session = false;
                            break;
                    }
                }

            } else {
                right--;
                System.out.println("Incorrect username or password.Try again.");
                if (right == 0) {
                    System.out.println("Your account has been blocked, please contact the bank. ");      // Hesabınız bloke olmuştur lütfen banka ile iletişime geçiniz.
                } else {
                    System.out.println("Your Remaining Right : " + right);
                }
            }
        }
    }
}



