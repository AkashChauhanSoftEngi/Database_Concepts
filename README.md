# Database_Concepts

## Relationship mappings in database design
* OneToOne
  - A Person has a PAN (Card) is a perfect example of One To One association. (stock and stock details)
  - Unidirectional : Person can refer to PAN entity
  - Bidirectional : PAN entity can refer back to Person
```java
   /*-----------------------------------------------------*/
   /*At one column*/
   @OneToOne(fetch = FetchType.LAZY, mappedBy = "stock")
   
   /*-----------------------------------------------------*/
   /*At another column*/
   @OneToOne(fetch = FetchType.LAZY)
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
* Outer Join
  - Left Outer Join
  - RIght Outer Join
