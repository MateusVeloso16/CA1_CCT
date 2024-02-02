package ca1mateusveloso5;

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;

public class CA1mateusVeloso {

    public static void main(String[] args) {

        try (BufferedReader reader = new BufferedReader(new FileReader("students.txt"))) {
            String line;

           
            while ((line = reader.readLine()) != null) {
              
                while (line.trim().isEmpty()) {
                    line = reader.readLine();
                }

           
                String firstSecondName = line;
                System.out.println("Full name is: " + firstSecondName);
                String[] names = firstSecondName.split("\\s+");
                String lastName, firstName;
                if (names.length >= 2) {
                    firstName = names[0];
                    lastName = names[1];

                    if (!(firstName.matches("[a-zA-Z]+") && lastName.matches("[a-zA-Z0-9 ]+"))) {
                        System.out.println("Invalid input for first and second name. Please provide both first and second names again!.");
                        return;
                    }
                } else {
                    System.out.println("Invalid input for first and second name. Please provide both first and second names.");
                    return;
                }

         
                int numClasses = Integer.parseInt(reader.readLine());
                System.out.println("Number of classes is: " + numClasses);
                if (!(numClasses >= 1 && numClasses <= 8)) {
                    System.out.println("The number of classes should be between 1 and 8. Please try again! ");
                    return;
                }

                String workLoad = determineWorkLoad(numClasses);

      
                String studentNumber = reader.readLine();
                System.out.println("Student number is: " + studentNumber);
                if (!studentNumber.matches("[a-zA-Z0-9 ]+")) {
                    System.out.println("You informed an invalid student number. Please try again!");
                    return;
                }

                System.out.println();
                System.out.print(studentNumber + " - " + lastName + "\n" + workLoad + "\n");

                try (PrintWriter writer = new PrintWriter(new FileWriter("status.txt", true))) {
                    writer.println(studentNumber + " - " + lastName);
                    writer.println(workLoad);
                    writer.println();
                    System.out.println();
                    System.out.println();
                    System.out.println();	
                } catch (IOException e) {
                    System.out.println("Error writing to file: " + e.getMessage());
                }
            }

        } catch (IOException | NumberFormatException e) {
            System.out.println("Error reading file or invalid input. Please check the file format and try again.");
        }
    }

    private static String determineWorkLoad(int numClasses) {
        if (numClasses == 1) {
            return "Very Light";
        } else if (numClasses == 2) {
            return "Light";
        } else if (numClasses >= 3 && numClasses <= 5) {
            return "Part Time";
        } else if (numClasses > 5 && numClasses <= 8) {
            return "Full Time";
        } else {
            return "Unknown Workload";
        }
    }
}
