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

            scanner.close();
            printWriter.close();
            fileWriter.close();

        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }
