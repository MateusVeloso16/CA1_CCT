TEST5

package ca1mateusveloso3;

import java.util.Scanner;

public class CA1MATEUSVELOSO3 {

    public static void main(String[] args) {
        
        try (Scanner scanner = new Scanner(System.in)) {
            System.out.println("Enter first and second name: ");
            String firstSecondName = scanner.nextLine();
            if (!firstSecondName.matches("[a-zA-Z0-9 ]+")){
                System.out.println("You informed an invalid name. Please try again! ");
            }
            System.out.println("Enter number of classes: ");
            int numClasses = Integer.parseInt(scanner.nextLine());
            if (!(numClasses >= 1 && numClasses <= 8)) {
                System.out.println("You informed an invalid number of classes. Please try again! ");
            }
            System.out.println("Enter student number: ");
            String studentNumber = scanner.nextLine();
            if (!studentNumber.matches("[a-zA-Z0-9 ]+")) {
                System.out.println("You informed an invalid student number. Please try again: ");
            }
            // Close resources
        }
    }

    
        
/**

 -- I still have to work in this part--

 
    private static String (int numClasses) {
        if (numClasses == 1) {
            return "Very Light";
        } else if (numClasses == 2) {
            return "Light";
        } else if (numClasses >= 3 && numClasses <= 5) {
            return "Part Time";
        } else {
            return "Full Time";
        }
    } */
}
