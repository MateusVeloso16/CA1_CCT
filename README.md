package ca1mateusveloso3;

import java.util.Scanner;

public class CA1MATEUSVELOSO3 {
    

    public static void main(String[] args) {
        
        int numClasses;
        String studentNumber;
        String firstSecondName;
        String workLoad = null;
        
        
        try (Scanner scanner = new Scanner(System.in)) {
            System.out.println("Enter first and second name: ");
            firstSecondName = scanner.nextLine();
            if (!firstSecondName.matches("[a-zA-Z0-9 ]+")){
                System.out.println("You informed an invalid name. Please try again! ");
            }
            System.out.println("Enter number of classes: ");
            numClasses = Integer.parseInt(scanner.nextLine());
            if (!(numClasses >= 1 && numClasses <= 8)) {
                System.out.println("You informed an invalid number of classes. Please try again! ");   
            }
            System.out.println("Enter student number: ");
            studentNumber = scanner.nextLine();
            if (!studentNumber.matches("[a-zA-Z0-9 ]+")) {
                System.out.println("You informed an invalid student number. Please try again: ");
            }
            if (numClasses == 1) {
            workLoad = "Very Light";
            }
            if (numClasses == 2) {
            workLoad = "Light";
            }
            if (numClasses >= 3 && numClasses <=5) {
            workLoad = "Part Time";
            }
            if (numClasses >5 && numClasses <=8) {
            workLoad = "Full Time";
            }
            if (numClasses <1 && numClasses >8){
            System.out.println("The number of classes should be between 1 and 8. Please try again! ");
            }
            
            System.out.println(workLoad);
            System.out.println(studentNumber);
            System.out.println(numClasses);
            System.out.println(firstSecondName);
            
            scanner.close();
            
        }
            
           
            
            
    }        
            
}
   
   
