# stream_api_coding_questions-
### Table of Contents


### Table of Contents
| No. | Questions                                                                                                                      |
| --- | ------------------------------------------------------------------------------------------------------------------------------ |
| 1   | [Group the Employees by city](#link-1)                                                                                         |
| 2   | [Group the Employees by age](#link-2)                                                                                          |
| 3   | [Find the count of male and female employees present in the organization](#link-3)                                             |
| 4   | [Print the names of all departments in the organization](#link-4)                                                              |
| 5   | [Print employee details whose age is greater than 28](#link-5)                                                                 |
| 6   | [Find maximum age of employee](#link-6)                                                                                        |
| 7   | [Print Average age of Male and Female Employees](#link-7)                                                                      |
| 8   | [Print the number of employees in each department](#link-8)                                                                    |
| 9   | [Find oldest employee](#link-9)                                                                                                |
| 10  | [Find youngest female employee](#link-10)                                                                                      |
| 11  | [Find employees whose age is greater than 30 and less than 30](#link-11)                                                       |
| 12  | [Find the department name which has the highest number of employees](#link-12)                                                 |
| 13  | [Find if there are any employees from HR Department](#link-13)                                                                 |
| 14  | [Find the department names that these employees work for, where the number of employees in the department is over 3](#link-14) |
| 15  | [Find distinct department names that employees work for](#link-15)                                                             |
| 16  | [Find all employees who live in ‘Blore’ city, sort them by their name and print the names of employees](#link-16)              |
| 17  | [Number of employees in the organization](#link-17)                                                                            |
| 18  | [Find employee count in every department](#link-18)                                                                            |
| 19  | [Find the department which has the highest number of employees](#link-19)                                                      |
| 20  | [Sorting a Stream by age and name fields](#link-20)                                                                            |
| 21  | [Highest experienced employees in the organization](#link-21)                                                                  |
| 22  | [Print average and total salary of the organization](#link-22)                                                                 |
| 23  | [Print Average salary of each department](#link-23)                                                                            |
| 24  | [Find Highest salary in the organization](#link-24)                                                                            |
| 25  | [Find Second Highest salary in the organization](#link-25)                                                                     |
| 26  | [Nth Highest salary](#link-26)                                                                                                 |
| 27  | [Find highest paid salary in the organization based on gender](#link-27)                                                       |
| 28  | [Find lowest paid salary in the organization](#link-28)                                                                        |
| 29  | [Sort the employees' salary in the organization in ascending order](#link-29)                                                  |
| 30  | [Sort the employees' salary in the organization in descending order](#link-30)                                                 |
| 31  | [Highest salary based on department](#link-31)                                                                                 |

1. ### Group the Employees by city.

```java
Map<String,List<Employee>>empCity=
 empList
 .stream()
.collect(Collectors.groupingBy(Employee::getCity));

```

2. ### Group the Employees by age.

```java
 
 Map<String,List<Employee>> empByAge=
 empList.stream().collect(Collectors.groupingBy(Employee::getAge));

 ```
 3. ###   Find the count of male and female employees present in the organization.

```java
Map<String,Long> noOfMaleAndFemale=
empList.stream().collect(Collectors.groupingBy(Employee::getGender,Collectors.counting()));

```
4. ### Print the names of all departments in the organization.

```java

List<String>department=
empList.stream().map(e->e.getDeptName()).distinct().collect(Collectors.toList());

```
5. ### Print employee details whose age is greater than 28.

```java

List<Employee> empResult=
empList().stream().filter(e->e.getAge()>28).collect(Collectors.toList());
```

6. ### Find the Maximum age of employee.

```java
int maxAge=
empList.stream().mapToInt(Employee::getAge).max().getAsInt();

```

7. ### Print Average age of Male and Female Employees.

```java
Map<String,Double> avgAge=
empList.stream().collect(Collectors.groupingBy(Employee::getGender,Collectors.averagingInt(Employee::getAge)));

```

8. ### Print the number of employees in each department.

```java
Map<String,Long>countByDept=
empList.stream().collect(Collectors.groupingBy(Employee::getDeptName,Collectors.counting()));

```

9. ### Find oldest employee.
```java
Optional<Employee> oldestEmp=
empList.stream().max(Comparator.comparingInt(Employee::getAge));
System.out.println(oldestEmp.get());
```

10. ### Find youngest female employee.
```java
Employee youngestFemaleEmp=
empList.stream().filter(e->e.getGender().equals("Female")).min(Comparator.comparingInt(Employee::getAge)).get();
```

11. ### Find employees whose age is greater than 30 and less than 30.

```java
Map<Boolean,List<Employee>>partitioningEmp=
empList.stream().collect(Collectors.partitioningBy(e->e.getAge()>30));

for(Map.Entry<Boolean,List<Employee>>entry: partitioningBY.entrySet()){
    if(entry.getkey.equals(TRUE)){
           System.out.println("Employees greater than 30 years ::" + entry.getValue());
    }else{
          System.out.println("Employees less than 30 years ::" + entry.getValue());
    }
}
```
12. ### Find the department name which has the highest number of employees.

```java
String department=
empList.stream().collect(Collectors.groupingBy(Employee::getDeptName,collectors.counting()))
.entrySet().stream().max(Comparator.comparing(Map.Entry::getValue)).map(e->e.getKey());
```
13. ### Find if there any employees from HR Department.

```java
Optional<Employee> emp=
empList.stream().filter(e->e.getDepatName().equalsIgnoreCase("HR")).findAny();

emp.ifPresent(employee-> System.out.println("Found employees from HR department " + employee));

```
14. ### Find the department names that these employees work for, where the number of employees in the department is over 3.

```java
empList.stream().collect(Collectors.groupingBy(Employee::getDepatName,Collectors.counting()))
.entrySet().stream().filter(e->e.getValue()>3).map(e->e.getKey()).forEach(System.out::println);
```

15. ### Find distinct department names that employees work for.

```java
empList.stream().map(e->e.getDepatName()).distinct(). forEach(System.out::println);
```

16. ### . Find all employees who lives in ‘Blore’ city, sort them by their name and print the names of employees.


```java
empList.stream().filter(e->e.getCity().equalsIgnoreCase("Blore")).sorted(Comparator.comparing(Employee::getName)).map(e->e.getName()).
forEach(System.out::println);
```

17. ### No of employees in the organisation.

```java
    long count=empList.stream().count();
```

18. ### Find employee count in every department.

```java
Map<String, Long> employeeCountInDepartmentMap = empList.stream().collect(Collectors.
                                                 groupingBy(Employee::getDeptName, Collectors.counting()));
 System.out.print("Employee department and its count :- \n"
                + employeeCountInDepartmentMap);
```

19. ###  Find the department which has the highest number of employees.

```java
Optional<Employee> highestNoEmp=
empList.stream().collect(Collectors.groupingBy(Employee::getDeptName,Collectors.counting()))
.entrySet().max(Map.Entry.comparingByValue());

highestNoEmp.ifPresent(System.out:: println);
```

20. ### Sorting a Stream by age and name fields.

```java
empList.stream().sorted(Comparator.comparingInt(Employee::getAge).thenComparing(Employee::getName)).forEach(System.out::println);
```

21. ###  Highest experienced employees in the organization.

```java
Optional<Employee> seniorEmp=
empList.stream().min(Comparator.comparing(Employee::getYearOFJoining));
System.out.println("Senior Employee Details :" + seniorEmp.get());
```

22. ### Print average and total salary of the organization.

```java
DoubleSummaryStatics empSalary=
empList.stream().collect(Collectors.summarizingDouble(Employee::getSalary));

System.out.println("Average Salary in the organisation = " + empSalary.getAverage());
System.out.println("Total Salary in the organisation  = " + empSalary.getSum());
```

23. ### Print Average salary of each department.
```java
Map<String,Double> avgSalary=
empList.stream().collect(Collectors.groupingBy(Employee::getDeptName,Collectors.averageingDouble(Employee::getSalary)));
 for (Map.Entry<String, Double> entry : avgSalary.entrySet) {
            System.out.println(entry.getKey() + " : " + entry.getValue());
 }
```
24. ### Find Highest salary in the organisation.

```java
OptionalDouble maxSalary = empList.stream()
    .mapToDouble(Employee::getSalary) // Map each employee's salary to a double
    .max(); // Get the maximum salary

// Optionally handle the result
if (maxSalary.isPresent()) {
    System.out.println("Max Salary: " + maxSalary.getAsDouble());
} else {
    System.out.println("No employees found.");
}
```
25. ###  Find Second Highest salary in the organisation.

```Java
Optional<Employee> secondHighest=
empList.stream().sorted(Comparator.comparingDouble(Employee::getSalary).reversed()).skip(1).findFirst();
System.out.println("Second Highest Salary in the organisation : " + secondHighest.get().getSalary());
```

26. ### Nth Highest salary.
```java
int n=10;
Optional<Employee> nthHighestSalary=
empList.stream().sorted(Comparator.comparingDouble(Employee::getSalary).reversed()).skip(n-1).findFirst();
```

27. ### Find highest paid salary in the organisation based on gender.

```java

Map<String, Optional<Employee>> highestPaidMFEmployee 
=empList.stream().collect(collectors.groupingBy(Employee::getGender,Collectors.maxBy(Comparator.comparingDouble(Employee::getSalary))));
System.out.println("Highest paid male and female employee : " + highestPaidMFEmployee);
```

28. ### Find lowest paid salary in the organisation based in the organisation.

```java

Map<String, Optional<Employee>> lowestPaidMFEmployee =
empList.stream().collect(Collectors.groupingBy(Employee::getDeptName,Collectors.minBy((t1,t2)->int(t1.getSalary()-t2.getSalary()))));
```

29. ###  Sort the employees salary in the organisation in ascending order

```java
empList.stream().sorted(Comparator.comparingDouble(Employee::getSalary)).toList().forEach(System.out::println);
```

30. ###  Sort the employees salary in the organisation in descending order.

```java
empList.stream().sorted(Comparator.comparingDouble(Employee::getSalary).reversed()).toList().
forEach(System.out::println);
```

31. ### Highest salary based on department.

```java
empList.stream().collect(Colllectors.groupingBy(Employee::getDeptName,Collectors.maxBy(Comparator.comparingDouble(Employee::getSalary))));
```

32. ### Print list of employee’s second highest record based on department
```java
empList.stream().collect(Collectors.groupingBy(Employee::getDeptName,Collectors.collectingAndThen(Collectors. toList(),list->list.stream().sorted(Comparator.comparingDouble(EMployee::getSalary).reversed()).skip(1).findFirst())));
```

33. ### Sort the employees salary in each department in ascending order

```java
System.out.println("Sorting the department wise employee salary in ascending order:: ");
Map<String, Stream<Employee>> sortedEmployeeAsc = empList.stream().collect(Collectors.groupingBy(Employee::getDeptName, 
                                                   Collectors.collectingAndThen(Collectors.toList(),
                                                   list -> list.stream().sorted(Comparator.comparingDouble(Employee::getSalary)))));
```

34. ###  Sort the employees salary in each department in descending order

```java
  Map<String, Stream<Employee>> sortedEmployeeDesc =
  empList.stream().collect(Collectors.groupingBy(Employee::getDeptName,Collectors.collectintAndThen(Collectors.toList(),list-> list.stream().sorted(Comparator.comparingDouble(Employee::getSalary).reversed())));

sortedEmployeeDesc.forEach((k,v)->{
            System.out.println(k);
            System.out.println(v.collect(Collectors.toList()));
        });
```
