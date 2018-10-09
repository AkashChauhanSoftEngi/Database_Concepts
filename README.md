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
  - RIght Outer Join
    - right all + if left not present[against predicate] still return empty row

