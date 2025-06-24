# Employee-Management-System

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Employee{
    private int id;
    private String name;
    private String email;
    private String password;

    public int getId(){
        return id;
    }
    public void setId(int id){
        this.id=id;
    }
    @Override
    public String toString() {
        return "Employee [id=" + id + ", name=" + name + ", email=" + email + ", password=" + password + "]";
    }
    public String getName(){
        return name;
    }
    public void setName(String name){
        this.name=name;
    }
    public String getEmail(){
        return email;
    }
    public void setEmail(String email){
        this.email=email;
    }
    public String getPassword(){
        return password;
    }
    public void setPassword(String password){
        this.password=password;
    }

    public Employee(){

    }

    public Employee(int id,String name,String email,String password){
        this.id=id;
        this.name=name;
        this.email=email;
        this.password=password;
    }

}
class EmployeeList{
    public static List<Employee> employees;

    static{
        employees=new ArrayList<>();
        employees.add(new Employee(1,"Aravind","Aravind@gamil.com","Aravin@123"));
        employees.add(new Employee(2,"Harish","gamil.com","234"));
    }

}
class EmployeeService {

    public void listEmployee(){
        for(Employee a:EmployeeList.employees){
            //System.out.println("[id:"+a.getId()+",name:"+a.getName()+",email:"+a.getPassword()+"]");
            System.out.println(a);
        }
    }

    public void addEmployee(int id,String name,String email,String password){
        EmployeeList.employees.add(new Employee(id,name,email,password));
        System.out.println("Employee Added Successfully");

    }
    public void searchById(int id){
        for(Employee emp:EmployeeList.employees){
            if(id==emp.getId()){
                System.out.println(emp);
                return;
            }
        }
        System.out.println("Id "+id+" not Found");
    }
    public void UpdateEmployee(int id , String name,String email,String password){
        for(Employee emp:EmployeeList.employees){
            if(id==emp.getId()){
                emp.setName(name);
                emp.setEmail(email);
                emp.setPassword(password);
                System.out.println("Upadated Successfully");
            }
            else{
                System.out.println("Id not Found");
            }
        }
    }
    public void deleteEmployee(int id){
        for(Employee emp:EmployeeList.employees){
            if(id==emp.getId()){
                EmployeeList.employees.remove(emp); 
                System.out.println("Delete SuccessFully");
                return;
            }
           
            }
            System.out.println("Id not Found");
        }
        
    }

    

public class App {
    public static void main(String[] args) throws Exception {
        Scanner sc=new Scanner(System.in);
        EmployeeService service=new EmployeeService();
        

        int choice ;
        boolean enteredApp=true;
       while(enteredApp){
        System.out.println("\n------EMPLOYEE MANAGEMENT SYSTEM------\n");
        System.out.println("1.Show All Employee");
        System.out.println("2.Add Employee");
        System.out.println("3.Update Employee");
        System.out.println("4.Delete Employee");
        System.out.println("5.Search Employee");
        System.out.println("6.Exit\n");
        System.out.print("Enter ur choice:");
        choice = sc.nextInt();

        switch(choice){
            case 1:
                System.out.println("Employee");
                service.listEmployee();
                break;
            case 2:
                System.out.println("Add Employee");
                System.out.print("Enter the id:");
                int id=sc.nextInt();
                sc.nextLine();
                System.out.print("Enter the name:");
                String name=sc.nextLine();
                System.out.print("Enter the email:");
                String email=sc.nextLine();
                System.out.print("Enter the password:");
                String password=sc.nextLine();

                service.addEmployee(id, name, email, password);
                break;
            case 3:
                System.out.println("Update Employee");
                System.out.println("Enter the Id");
                int Uid=sc.nextInt();
                 sc.nextLine();
                System.out.print("Enter the name:");
                String Uname=sc.nextLine();
                System.out.print("Enter the email:");
                String Uemail=sc.nextLine();
                System.out.print("Enter the password:");
                String Upassword=sc.nextLine();
                service.UpdateEmployee(Uid, Uname, Uemail, Upassword);
                break;
            case 4:
                System.out.println("Delete Employee");
                System.out.println("Enter the id");
                int rid=sc.nextInt();
                service.deleteEmployee(rid);
                break;
            case 5:
                System.out.print("Enter Id:");
                int sid=sc.nextInt();
                service.searchById(sid);
                break;
                
            case 6:
                System.out.println("Exited");
                enteredApp=false;
                break;
            default:
                System.out.println("Invalid option. TRY AGAIN!!!");

        }
       }
    }
}
