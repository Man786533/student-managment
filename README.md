import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        StudentManager manager = new StudentManager();

        while (true) {
            System.out.println("\n===== Student Management System =====");
            System.out.println("1. Add Student");
            System.out.println("2. View All Students");
            System.out.println("3. Search Student by ID");
            System.out.println("4. Update Student");
            System.out.println("5. Delete Student");
            System.out.println("6. Exit");
            System.out.print("Enter choice: ");

            int choice = sc.nextInt();
            sc.nextLine(); // clear buffer

            switch (choice) {
                case 1:
                    System.out.print("Enter ID: ");
                    int id = sc.nextInt();
                    sc.nextLine();
                    System.out.print("Enter Name: ");
                    String name = sc.nextLine();
                    System.out.print("Enter Age: ");
                    int age = sc.nextInt();
                    sc.nextLine();
                    System.out.print("Enter Course: ");
                    String course = sc.nextLine();

                    manager.addStudent(new Student(id, name, age, course));
                    break;

                case 2:
                    manager.viewAllStudents();
                    break;

                case 3:
                    System.out.print("Enter ID: ");
                    int sid = sc.nextInt();
                    Student found = manager.findStudentById(sid);
                    System.out.println(found != null ? found : "❌ Not found!");
                    break;

                case 4:
                    System.out.print("Enter ID: ");
                    int uid = sc.nextInt();
                    sc.nextLine();
                    System.out.print("Enter New Name: ");
                    String newName = sc.nextLine();
                    System.out.print("Enter New Age: ");
                    int newAge = sc.nextInt();
                    sc.nextLine();
                    System.out.print("Enter New Course: ");
                    String newCourse = sc.nextLine();

                    manager.updateStudent(uid, newName, newAge, newCourse);
                    break;

                case 5:
                    System.out.print("Enter ID: ");
                    int did = sc.nextInt();
                    manager.deleteStudent(did);
                    break;

                case 6:
                    System.out.println("👋 Exiting... Goodbye!");
                    sc.close();
                    return;

                default:
                    System.out.println("❌ Invalid choice!");
            }
        }
    }
}
