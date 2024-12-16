import java.util.ArrayList;
import java.util.Scanner;

public class StudentGradeTracker {

    // Method to calculate the average grade
    public static double calculateAverage(ArrayList<Integer> grades) {
        if (grades.isEmpty()) return 0.0;
        
        double sum = 0;
        for (int grade : grades) {
            sum += grade;
        }
        return sum / grades.size();
    }

    // Method to find the highest grade
    public static int findHighest(ArrayList<Integer> grades) {
        if (grades.isEmpty()) return -1; // Return -1 for clarity if no grades exist
        int highest = grades.get(0);
        for (int grade : grades) {
            if (grade > highest) {
                highest = grade;
            }
        }
        return highest;
    }

    // Method to find the lowest grade
    public static int findLowest(ArrayList<Integer> grades) {
        if (grades.isEmpty()) return -1; // Return -1 for clarity if no grades exist
        int lowest = grades.get(0);
        for (int grade : grades) {
            if (grade < lowest) {
                lowest = grade;
            }
        }
        return lowest;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Integer> grades = new ArrayList<>();

        System.out.println("Welcome to the Student Grade Tracker!");
        while (true) {
            System.out.println("\nOptions:");
            System.out.println("1. Add a student's grade");
            System.out.println("2. Display average grade");
            System.out.println("3. Display highest grade");
            System.out.println("4. Display lowest grade");
            System.out.println("5. Exit");
            System.out.print("Choose an option: ");

            int choice = scanner.nextInt();
            switch (choice) {
                case 1:
                    System.out.print("Enter the student's grade (0-100): ");
                    int grade = scanner.nextInt();
                    if (grade >= 0 && grade <= 100) {
                        grades.add(grade);
                        System.out.println("Grade added successfully!");
                    } else {
                        System.out.println("Invalid grade. Please enter a value between 0 and 100.");
                    }
                    break;
                case 2:
                    if (grades.isEmpty()) {
                        System.out.println("No grades have been entered yet.");
                    } else {
                        double average = calculateAverage(grades);
                        System.out.printf("The average grade is: %.2f\n", average);
                    }
                    break;
                case 3:
                    if (grades.isEmpty()) {
                        System.out.println("No grades have been entered yet.");
                    } else {
                        int highest = findHighest(grades);
                        System.out.println("The highest grade is: " + highest);
                    }
                    break;
                case 4:
                    if (grades.isEmpty()) {
                        System.out.println("No grades have been entered yet.");
                    } else {
                        int lowest = findLowest(grades);
                        System.out.println("The lowest grade is: " + lowest);
                    }
                    break;
                case 5:
                    System.out.println("Exiting the program. Goodbye!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }
}
