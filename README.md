package ca1mateusveloso3;

import java.util.Scanner;
import java.io.FileWriter;
import java.io.PrintWriter;

public class CA1MATEUSVELOSO3 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            FileWriter fileWriter = new FileWriter("status.txt");
            PrintWriter printWriter = new PrintWriter(fileWriter);

            while (true) {
                System.out.println("Enter first and second name, number of classes, and student number: ");
                
                String firstandSecondName = scanner.nextLine();
                int numClasses = Integer.parseInt(scanner.nextLine());
                String studentNumber = scanner.nextLine();

                if (isValidData(firstandSecondName, numClasses, studentNumber)) {
                
                    String workload = determineWorkload(numClasses);

                    // Saving to the file status.txt
                    printWriter.println(studentNumber + " – " + secondName.split(" ")[1]);
                    printWriter.println(workload);
                    printWriter.println();
                } else {
                    System.out.println("Error: Invalid data. Please enter valid information.");
                }
            }

            scanner.close();
            printWriter.close();
            fileWriter.close();

        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }
