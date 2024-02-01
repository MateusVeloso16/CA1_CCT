package ca1mateusveloso5;

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class CA1mateusVeloso {

    public static void main(String[] args) {
        
        int numClasses;
        String studentNumber;
        String workLoad = null;
        String firstSecondName;

        try (BufferedReader reader = new BufferedReader(new FileReader("students.txt"))) {

            firstSecondName = reader.readLine();
            String[] names = firstSecondName.split("\\s+");
            if (names.length >= 2) {
                String firstName = names[0];
                String lastName = names[1];

                if (!(firstName.matches("[a-zA-Z]+") && lastName.matches("[a-zA-Z0-9 ]+"))) {
                    System.out.println("Invalid input for first and second name. Please provide both first and second names again!.");
                    return;
                }
            } else {
                System.out.println("Invalid input for first and second name. Please provide both first and second names again!.");
                return;
            }
            
            System.out.println("Enter number of classes: ");
            numClasses = Integer.parseInt(reader.readLine());
            if (!(numClasses >= 1 && numClasses <= 8)) {
                System.out.println("The number of classes should be between 1 and 8. Please try again! ");
                return;
            }

            
            if (numClasses == 1) {
                workLoad = "Very Light";
            } else if (numClasses == 2) {
                workLoad = "Light";
            } else if (numClasses >= 3 && numClasses <= 5) {
                workLoad = "Part Time";
            } else if (numClasses > 5 && numClasses <= 8) {
                workLoad = "Full Time";
            }

            
            System.out.println("Enter student number: ");
            studentNumber = reader.readLine();
            if (!studentNumber.matches("[a-zA-Z0-9 ]+")) {
                System.out.println("You informed an invalid input. Please try again!");
                return;
            }

            System.out.print(studentNumber + " - " + firstSecondName + "\n" + workLoad + "\n");

        } catch (IOException | NumberFormatException e) {
            System.out.println("Error reading file or invalid input. Please check the file format and try again.");
        }
    }
}
