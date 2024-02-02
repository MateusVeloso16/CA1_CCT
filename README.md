package ca1mateusveloso5;

// GITHUB>>>   https://github.com/MateusVeloso16/CA1.git

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;

public class CA1mateusVeloso {

    public static void main(String[] args) {

// here i opened the students.txt for checking the imput/data for the code
        try (BufferedReader reader = new BufferedReader(new FileReader("students.txt"))) {
            String line;

//here i put the code to read lines from the file
            while ((line = reader.readLine()) != null) {

 //that was the part I spent hours until I dicover that the code was trying to read an empty lines haha(but no!)
                while (line.trim().isEmpty()) {
                    line = reader.readLine();
                }

 //here I read and put the verifications for the first and last names
                String firstSecondName = line;
                System.out.println("Full name is: " + firstSecondName);
                String[] names = firstSecondName.split("\\s+");
                String lastName, firstName;
                if (names.length >= 2) {
                    firstName = names[0];
                    lastName = names[1];

// Here I was trying to see if first the first name was only letters and last name was letters and numbers
                    if (!(firstName.matches("[a-zA-Z]+") && lastName.matches("[a-zA-Z0-9 ]+"))) {
                        System.out.println("Invalid input for first and second name. Please provide both first and second names again!.");
                        return;
                    }
                } else {
                    System.out.println("Invalid input for first and second name. Please provide both first and second names.");
                    return;
                }

//here I took the number of classes and verificated if it was between 1 and 8 including these two.
                int numClasses = Integer.parseInt(reader.readLine());
                System.out.println("Number of classes is: " + numClasses);
                if (!(numClasses >= 1 && numClasses <= 8)) {
                    System.out.println("The number of classes should be between 1 and 8. Please try again! ");
                    return;
                }

//According to the number of classes, give the correct workload according to the table provided by the scope of the activity.
                String workLoad = determineWorkLoad(numClasses);

//here i got the student number from the student.txt file
                String studentNumber = reader.readLine();
                System.out.println("Student number is: " + studentNumber);

//here I checked if the student number was in ther correct format
                if (!isValidStudentNumber(studentNumber)) {
                    System.out.println("You informed an invalid student number. Please try again! It should be a minimum of 6 characters with the first 2 characters being numbers, the 3rd  and 4th characters (and possibly 5th ) being a letter, and everything after the last letter character being a number.\r\n"
                    		+ "");
                    return;
                }

//this part I inserted to check in the console if the variables were getting the imput from the file. It was easier for me to see.
                System.out.println();
                System.out.print(studentNumber + " - " + lastName + "\n" + workLoad + "\n");

// here I wrote to the ile status.txt the results from the imput,file after the verifications.
                try (PrintWriter writer = new PrintWriter(new FileWriter("status.txt", true))) {
                    writer.println(studentNumber + " - " + lastName);
                    writer.println(workLoad);
                    writer.println();
                    System.out.println();
                    System.out.println();
                    System.out.println();
                } catch (IOException e) {
//I am still having difficult to understand the exceptions(how it works )so I copied it from a video in youtube.
                    System.out.println("Error writing to file: " + e.getMessage());
                }
            }

        } catch (IOException | NumberFormatException e) {
            System.out.println("Error reading file or invalid input. Please check the file format and try again.");
        }
    }

//Here I checked which workload should be selected according to the number of classes
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

// Here I checked if the studentNumber was in the correct format according to the instructions
    private static boolean isValidStudentNumber(String studentNumber) {
        if (studentNumber.length() < 6) {
            return false;
        }

        if (!Character.isDigit(studentNumber.charAt(0)) || !Character.isDigit(studentNumber.charAt(1))) {
            return false;
        }

        
        int year;
        try {
            year = Integer.parseInt(studentNumber.substring(0, 2));
        } catch (NumberFormatException e) {
            return false;
        }

    
        if (year < 20) {
            return false;
        }

     
        if (!Character.isLetter(studentNumber.charAt(2)) || !Character.isLetter(studentNumber.charAt(3))) {
            return false;
        }

     
        int numberAfterLetter;
        try {
            numberAfterLetter = Integer.parseInt(studentNumber.substring(4));
        } catch (NumberFormatException e) {
            return false;
        }

//here i checked if the number after the letters was between 1 and 200
        return numberAfterLetter >= 1 && numberAfterLetter <= 200;
    }
}
