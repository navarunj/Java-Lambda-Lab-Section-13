# Java-Lambda-Lab-Section-13

Lambda expressions give us the ability to quickly define an implementation for a
functional interface. This feature adds flexibility to an app, with the least amount of
code possible!

In this lab, you will explore an array to store MyDate objects.
Specifically, in this lab you will:
* Create a functional interface
* Implement a lambda expression

Scenario

Certain orders can be flagged as “priority orders,” where they will be placed ahead
in the shipping queue and sent via next day shipping. The criteria that determines
what orders should be prioritized may change at any point. However, when the
criteria changes, it changes for all orders (rather than allowing each order to
determine its own rules). To handle this use case, a functional interface called
Rushable defines a single “isRushable” method. The method is passed an orderDate
and orderAmount. It is up to the implementation to decide if they will use either,
both, or none of these parameters.

## Step 1: Create the Rushable functional interface.

1.1 In the com.acme.domain package, create an interface called Rushable.

1.2 Add the following method to it:

```java
public abstract boolean isRushable(MyDate orderDate, double
amount);
```

## Step 2: Add a private static Rushable variable to Order.java with a getter/setter pair.

```java
private static Rushable rushable;
public static Rushable getRushable()
{
 return rushable;
}
public static void setRushable(Rushable rushable)
{
 Order.rushable = rushable;
}
```

## Step 3: Create the isPriorityOrder method which delegates to the Rushable object.

```java
public boolean isPriorityOrder()
{
    boolean priorityOrder = false;
    if( rushable != null ) {
    priorityOrder = rushable.isRushable(orderDate,orderAmount);
}
    return priorityOrder;
}
```

## Step 4: On Your Own: In TestOrders.java pass in a Lambda expression to setRushable which returns true if the orderAmount is over 1500.

