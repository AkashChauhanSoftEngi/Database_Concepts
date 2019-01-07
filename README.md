# Database_Concepts

## Relationship mappings in database design
* OneToOne
  - A Person has a PAN (Card) is a perfect example of One To One association. (stock and stock details)
  - Unidirectional : Person can refer to PAN entity
  - Bidirectional : PAN entity can refer back to Person
```java
    /*-----------------------------------------------------*/
    @Entity
    public class Person {
    @Id private int id;
    @OneToOne
    @JoinColumn(name="PAN_ID")
    private PAN pan;
    }

    @Entity
    public class PAN {
    @Id private int id;
    @OneToOne(mappedBy="pan")
    private Person person;
    }
    /*-----------------------------------------------------*/
    /*At one column*/
    @OneToOne(mappedBy = "pen")
   
    /*At another column*/
    @OneToOne()
    @PrimaryKeyJoinColumn
   
    /*Or*/
    @OneToOne()
    @JoinColumn(name = "person_id", nullable = false)
    /*-----------------------------------------------------*/
    public class Employee {
    @OneToOne(mappedBy = "emp")
    private Phone phone;
    }

    public class Phone {
    @OneToOne
    @JoinColumn(name = "EMP_ID")
    private Employee emp;
    }
    https://www.devglan.com/hibernate/hibernate-one-to-one-mapping-example
```
* OneToMany
  - Department & Employee mapping
  - @OneToMany annotation
* ManyToMany
  - Books & Authers
  - @ManyToMany annotation
* Reference: https://www.mkyong.com/hibernate/hibernate-one-to-one-relationship-example-annotation/

## Inner and Outer Joins
* Inner Join
  - combine result on given predicate
  ```sql
  /*Explicit Join Notation*/
  SELECT *
  FROM employee INNER JOIN department
  ON employee.DepartmentID = department.DepartmentID;
  
  /*Implicit Join Notation*/
  SELECT *
  FROM employee, department
  WHERE employee.DepartmentID = department.DepartmentID;
  ```
* Outer Join (even if no record but still return the row with empty valuse)
  - Left Outer Join
    - left all + if right not present[against predicate] still return empty row
    ```sql
    SELECT *
    FROM employee LEFT OUTER JOIN department
    ON employee.DepartmentID = department.DepartmentID;
    ```
  - RIght Outer Join
    - right all + if left not present[against predicate] still return empty row
    ```sql
    SELECT *
    FROM employee RIGHT OUTER JOIN department
    ON employee.DepartmentID = department.DepartmentID;
    ```
  - Full Outer Join
    - contains all records of both the left and right tables

## Drop, Truncate and Delete commands in SQL
* Delete is used to delete rows from a table with optional where clause, we need to commit or rollback after
calling this operation. This operation will cause all DELETE triggers to be fired on the table.
```sql
  DELETE FROM Employee WHERE age < 14;
```
* Truncate removes all rows from table, this operation can not be rolled back and no triggers are fired, thus it is
faster in performance as well.
```sql
  Truncate Table Employee;
```
* Drop command will remove a table from the schema, all data rows, indexes, privileges will be removed, no
triggers will be fired and no rollback.
```sql
  Drop Table Employee;
```

## Use of @Transectional in Spring
```text
  Reference: https://stackoverflow.com/questions/1099025/spring-transactional-what-happens-in-background
```

## Oracle Vs Mysql
* https://www.youtube.com/watch?v=fSPBmXKGCJ8&t=60s
