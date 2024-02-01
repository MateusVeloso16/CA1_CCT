import java.util.Scanner;

public class CA1Assignment4 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        boolean validInput = false;

        do {
            int numClasses;
            String studentNumber;
            String firstSecondName;
            String workLoad;
            String firstName;
            String lastName;

            System.out.println("Enter first and second name: ");
            firstSecondName = scanner.nextLine();
            String[] names = firstSecondName.split("\\s+");
            if (names.length >= 2) {
                firstName = names[0];
                lastName = names[1];

                if (!firstName.matches("[a-zA-Z]+") || !lastName.matches("[a-zA-Z0-9 ]+")) {
                    System.out.println("You informed an invalid name. Please try again! ");
                    continue;
                }
            }

            System.out.println("Enter number of classes: ");
            try {
                numClasses = Integer.parseInt(scanner.nextLine());
                if (!(numClasses >= 1 && numClasses <= 8)) {
                    System.out.println("You informed an invalid number of classes. Please try again! ");
                    continue;
                }
            } catch (NumberFormatException e) {
                System.out.println("Invalid input for number of classes. Please enter a valid number.");
                continue;
            }

            System.out.println("Enter student number: ");
            studentNumber = scanner.nextLine();
            if (!studentNumber.matches("[a-zA-Z0-9 ]+")) {
                System.out.println("You informed an invalid student number. Please try again: ");
                continue;
            }

            if (numClasses == 1) {
                workLoad = "Very Light";
            } else if (numClasses == 2) {
                workLoad = "Light";
            } else if (numClasses >= 3 && numClasses <= 5) {
                workLoad = "Part Time";
            } else if (numClasses > 5 && numClasses <= 8) {
                workLoad = "Full Time";
            } else {
                System.out.println("The number of classes should be between 1 and 8. Please try again! ");
                continue;
            }

            System.out.print(studentNumber + " - " + firstSecondName + "\n" + workLoad + "\n");
            validInput = true;

        } while (!validInput);

        scanner.close();
    }
}
