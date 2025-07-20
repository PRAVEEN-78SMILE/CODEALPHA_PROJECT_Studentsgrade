import java.util.ArrayList;
import java.util.Scanner;

public class StudentGradeManagerConsole {
 public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
  ArrayList<String> studentNames = new ArrayList<>();
  ArrayList<Integer> studentGrades = new ArrayList<>();


   System.out.print("Enter the number of students: ");
        int numStudents = scanner.nextInt();
        scanner.nextLine(); // consume newline

  // Input student data
        for (int i = 0; i < numStudents; i++) {
            System.out.print("\nEnter name for student " + (i + 1) + ": ");
            String name = scanner.nextLine();
            studentNames.add(name);

   int grade;
            while (true) {
                System.out.print("Enter grade for " + name + " (0-100): ");
                grade = scanner.nextInt();
                if (grade >= 0 && grade <= 100) {
                    studentGrades.add(grade);
                    scanner.nextLine(); // consume newline
                    break;
                } else {
                    System.out.println("Invalid grade. Please enter a value between 0 and 100.");
                }
            }
        }

   // Display report
        System.out.println("\n===== Student Grades Summary =====");
        int total = 0;
        int highest = studentGrades.get(0);
        int lowest = studentGrades.get(0);
        String topStudent = studentNames.get(0);
        String lowStudent = studentNames.get(0);

   for (int i = 0; i < studentNames.size(); i++) {
            String name = studentNames.get(i);
            int grade = studentGrades.get(i);
            System.out.println(name + " - " + grade);

   total += grade;

  if (grade > highest) {
                highest = grade;
                topStudent = name;
            }

  if (grade < lowest) {
                lowest = grade;
                lowStudent = name;
            }
        }

   double average = (double) total / studentGrades.size();

   System.out.printf("\nAverage Grade: %.2f\n", average);
        System.out.println("Highest Grade: " + highest + " (Student: " + topStudent + ")");
        System.out.println("Lowest Grade: " + lowest + " (Student: " + lowStudent + ")");
    }
}
