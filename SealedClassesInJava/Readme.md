# Using SEALED CLASSES IN JAVA

Sealed class in JAVA restricts the classes being extended by other classes, except the permitted classes. In other words, it is more efficient to define sealed class when there is a requirement to restrict inheritance to certain class.

**The Following are important points to be considered when Creating and Using Sealed Classes in JAVA Programming:**

•	A sealed class should be abstract and declared with sealed modifier.

•	Sealed modifier cannot be used along with other modifiers like final or non-sealed.

•	A sealed abstract class should be extended with permits clause.

The Example in this POC, illustrates the Usage of Sealed Classes in JAVA Programming. The steps to implement the sealed classes a java program are as follows: 

1.	An Abstract sealed class named Person is created which will permit the Employee and Manager class to extend it. The permits clause allows only Employee and Manager classes to extend sealed class Person.
 
2.	The Class Employee with final keyword is created, which restricts other classes extending it.
 
3.	The Manager class is declared with non-sealed, other classes can extend it, without any restriction.
 
 

4.	The complete java program illustrating the usage of Sealed Class is shown below:

        package com.example.Bank;
        public class Bank 
        {
        public static void main(String[] args)
         {
        Person manager = new Manager(111, "Ram");
        manager.name = "Ram";
        System.out.println(getId(manager));
        }
        public static int getId(Person person) 
        {
        if (person instanceof Employee) 
        {
        return ((Employee) person).getEmployeeId();
        }
        else if (person instanceof Manager) 
        {
        return ((Manager) person).getManagerId();
        }
        return -1;
        }
        }
        /* Define Sealed Class and Permits other classes to extend it */
        abstract sealed class Person permits Employee, Manager 
        {
        String name;
        String getName()
        {
        return name;
        }
        }
        /* Class Extends the Sealed Class */
        final class Employee extends Person
        {
        String name;
        int id;
        Employee(int id, String name)
        {
        this.id = id;
        this.name = name;
        }
        int getEmployeeId()
         {
        return id;
        }
        }
        /* Define Exclusively a non-sealed class */
        non-sealed class Manager extends Person 
        {
        int id;
        Manager(int id, String name)
        {
        this.id = id;
        this.name = name;
        }
        int getManagerId()
         {
        return id;
        }
        }

 Output: On Execution of the code, the manager Id is be displayed shown below.
 

5.	Further, the Below Code Snippet illustrates, that a non-permitted class cannot extend a sealed class. The Class named Security doesn’t have the permission to extend Person class as it is not Permitted.
 

 Runtime Error: Since, the class name Security is not given permission to extend Person class and it throws an runtime error, indicating that Security class must give permission in sealed class to extend it as shown below.



