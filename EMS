/********************** Importing Essential Libraries **********************/

import java.util.*;
import java.io.*;

/*********************** Employee Management System Menu *********************/

class EMSMenu {
    public void displayMenu() {
        System.out.println("\n\t==============================");
        System.out.println("\t  Employee Management System");
        System.out.println("\t==============================");
        System.out.println("\t       ~ Designed by You ~");
        System.out.println("\nChoose an option:");
        System.out.println("1 - Add New Employee");
        System.out.println("2 - View Employee Details");
        System.out.println("3 - Remove an Employee");
        System.out.println("4 - Update Employee Information");
        System.out.println("5 - Exit the System");
    }
}

/*********************** Adding Employee Details ***************************/

class EmployeeAdder {
    public void addEmployee() {
        Scanner scanner = new Scanner(System.in);
        EmployeeDetails emp = new EmployeeDetails();
        emp.collectDetails();

        try {
            File file = new File("employee_" + emp.employeeID + ".txt");
            if (file.createNewFile()) {
                FileWriter writer = new FileWriter(file);
                writer.write("Employee ID: " + emp.employeeID + "\n" +
                             "Name: " + emp.name + "\n" +
                             "Department: " + emp.department + "\n" +
                             "Contact: " + emp.contact + "\n" +
                             "Email: " + emp.email + "\n" +
                             "Position: " + emp.position + "\n" +
                             "Salary: " + emp.salary);
                writer.close();
                System.out.println("\nSuccess: Employee has been added!");
            } else {
                System.out.println("\nError: Employee with this ID already exists.");
            }
        } catch (IOException e) {
            System.out.println("\nError: " + e.getMessage());
        }

        System.out.print("\nPress Enter to continue...");
        scanner.nextLine();
    }
}

/*********************** Capturing Employee Details **************************/

class EmployeeDetails {
    String name;
    String department;
    String email;
    String position;
    String employeeID;
    String salary;
    String contact;

    public void collectDetails() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter Employee Name: ");
        name = scanner.nextLine();
        System.out.print("Enter Department: ");
        department = scanner.nextLine();
        System.out.print("Enter Employee ID: ");
        employeeID = scanner.nextLine();
        System.out.print("Enter Email Address: ");
        email = scanner.nextLine();
        System.out.print("Enter Position: ");
        position = scanner.nextLine();
        System.out.print("Enter Contact Number: ");
        contact = scanner.nextLine();
        System.out.print("Enter Salary: ");
        salary = scanner.nextLine();
    }
}

/*********************** Viewing Employee Details ***************************/

class EmployeeViewer {
    public void viewEmployee(String id) {
        try {
            File file = new File("employee_" + id + ".txt");
            if (file.exists()) {
                Scanner scanner = new Scanner(file);
                while (scanner.hasNextLine()) {
                    System.out.println(scanner.nextLine());
                }
                scanner.close();
            } else {
                System.out.println("\nError: Employee with ID " + id + " does not exist.");
            }
        } catch (IOException e) {
            System.out.println("\nError: " + e.getMessage());
        }
    }
}

/*********************** Removing Employee Details ***************************/

class EmployeeRemover {
    public void removeEmployee(String id) {
        File file = new File("employee_" + id + ".txt");
        if (file.exists()) {
            if (file.delete()) {
                System.out.println("\nSuccess: Employee has been removed.");
            } else {
                System.out.println("\nError: Unable to delete the file.");
            }
        } else {
            System.out.println("\nError: Employee with ID " + id + " does not exist.");
        }
    }
}

/*********************** Updating Employee Details **************************/

class EmployeeUpdater {
    public void updateEmployee(String id, String oldInfo, String newInfo) {
        try {
            File file = new File("employee_" + id + ".txt");
            if (file.exists()) {
                Scanner scanner = new Scanner(file);
                StringBuilder fileContent = new StringBuilder();
                while (scanner.hasNextLine()) {
                    fileContent.append(scanner.nextLine()).append("\n");
                }
                scanner.close();

                String updatedContent = fileContent.toString().replace(oldInfo, newInfo);
                FileWriter writer = new FileWriter(file);
                writer.write(updatedContent);
                writer.close();

                System.out.println("\nSuccess: Employee information has been updated.");
            } else {
                System.out.println("\nError: Employee with ID " + id + " does not exist.");
            }
        } catch (IOException e) {
            System.out.println("\nError: " + e.getMessage());
        }
    }
}

/*********************** Exiting the System ***************************/

class SystemExit {
    public void exitSystem() {
        System.out.println("\n=========================================");
        System.out.println("Thank you for using the EMS. Goodbye!");
        System.out.println("=========================================");
        System.exit(0);
    }
}

/************************ Main Class ***********************************/

class EmployeeManagementSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        EMSMenu menu = new EMSMenu();

        EmployeeAdder adder = new EmployeeAdder();
        EmployeeViewer viewer = new EmployeeViewer();
        EmployeeRemover remover = new EmployeeRemover();
        EmployeeUpdater updater = new EmployeeUpdater();
        SystemExit exit = new SystemExit();

        while (true) {
            menu.displayMenu();
            System.out.print("\nEnter your choice: ");
            int choice = Integer.parseInt(scanner.nextLine());

            switch (choice) {
                case 1:
                    adder.addEmployee();
                    break;
                case 2:
                    System.out.print("\nEnter Employee ID to view details: ");
                    String viewID = scanner.nextLine();
                    viewer.viewEmployee(viewID);
                    break;
                case 3:
                    System.out.print("\nEnter Employee ID to remove: ");
                    String removeID = scanner.nextLine();
                    remover.removeEmployee(removeID);
                    break;
                case 4:
                    System.out.print("\nEnter Employee ID to update: ");
                    String updateID = scanner.nextLine();
                    System.out.print("Enter the detail to update: ");
                    String oldInfo = scanner.nextLine();
                    System.out.print("Enter the new information: ");
                    String newInfo = scanner.nextLine();
                    updater.updateEmployee(updateID, oldInfo, newInfo);
                    break;
                case 5:
                    exit.exitSystem();
                    break;
                default:
                    System.out.println("\nInvalid choice. Please try again.");
            }
        }
    }
}
