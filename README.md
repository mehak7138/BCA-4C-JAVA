# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-
import java.util.Scanner;

class EMPLOYEE {
    private String NameOfEmp;
    private int EmpId;
    private double BasicSalary;
    private double GrossSalary;

    public void input() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter Name of Employee: ");
        NameOfEmp = scanner.nextLine();

        System.out.print("Enter Employee ID: ");
        EmpId = scanner.nextInt();

        System.out.print("Enter Basic Salary: ");
        BasicSalary = scanner.nextDouble();
    }

    private double calculateHRA() {
        return 0.25 * BasicSalary;
    }

    private double calculateDA() {
        return 0.40 * BasicSalary;
    }

    public void calculateGrossSalary() {
        double HRA = calculateHRA();
        double DA = calculateDA();
        GrossSalary = BasicSalary + HRA + DA;
    }

    public void display() {
        System.out.println("Name of Employee: " + NameOfEmp);
        System.out.println("Employee ID: " + EmpId);
        System.out.println("Gross Salary: " + GrossSalary);
    }

    public String getNameOfEmp() {
        return NameOfEmp;
    }

    public int getEmpId() {
        return EmpId;
    }

    public double getGrossSalary() {
        return GrossSalary;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the total number of employees: ");
        int numEmployees = scanner.nextInt();

        EMPLOYEE[] employees = new EMPLOYEE[numEmployees];

        for (int i = 0; i < numEmployees; i++) {
            System.out.println("\nEnter details for Employee " + (i + 1) + ":");
            employees[i] = new EMPLOYEE();
            employees[i].input();
            employees[i].calculateGrossSalary();
        }

        // Query a) Display the NameOfEmp and GrossSalary of employees whose name starts with a consonant.
        System.out.println("\nEmployees whose names start with a consonant:");
        for (EMPLOYEE emp : employees) {
            if (!emp.getNameOfEmp().matches("[aeiouAEIOU].*")) {
                emp.display();
            }
        }

        // Query b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
        System.out.println("\nEmployees whose Emp-Id is between 101 and 150:");
        for (EMPLOYEE emp : employees) {
            if (emp.getEmpId() >= 101 && emp.getEmpId() <= 150) {
                emp.display();
            }
        }

        // Query c) Count the total number of Employees whose GrossSalary is less than 35000/-
        int count = 0;
        for (EMPLOYEE emp : employees) {
            if (emp.getGrossSalary() < 35000) {
                count++;
            }
        }
        System.out.println("\nTotal number of Employees whose GrossSalary is less than 35000/-: " + count);
    }
}
