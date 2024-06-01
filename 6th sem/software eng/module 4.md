Unified Modeling Language Class diagram, interaction diagram: collaboration
diagram, sequence diagram, state chart diagram, activity diagram, implementation
diagram.


### Unified Modeling Language (UML) Diagrams

UML provides various diagrams to model different aspects of a system. Here's an overview of some key UML diagrams:

#### 1. Class Diagram

**Definition:**
A Class Diagram represents the static structure of a system by showing its classes, attributes, operations, and the relationships among objects.

**Components:**
- **Classes:** Rectangles divided into three compartments: class name, attributes, and operations.
- **Relationships:** Lines connecting classes, representing associations, aggregations, compositions, inheritances, and dependencies.

**Example:**
A simplified class diagram for an e-commerce system might include classes such as `Customer`, `Order`, `Product`, and `Payment`.

```
+---------------+
|   Customer    |
+---------------+
| -name         |
| -email        |
+---------------+
| +placeOrder() |
+---------------+

       1
       |
       |
       *  
+---------------+
|     Order     |
+---------------+
| -orderDate    |
| -status       |
+---------------+
| +calculateTotal() |
+---------------+

       1
       |
       |
       *
+---------------+
|    Product    |
+---------------+
| -productName  |
| -price        |
+---------------+
| +applyDiscount() |
+---------------+

       1
       |
       |
       *
+---------------+
|    Payment    |
+---------------+
| -amount       |
| -paymentDate  |
+---------------+
| +processPayment() |
+---------------+
```

#### 2. Interaction Diagram: Collaboration Diagram

**Definition:**
A Collaboration Diagram focuses on the interactions between objects, emphasizing the structural organization.

**Components:**
- **Objects:** Instances of classes involved in the interaction.
- **Links:** Lines connecting objects, indicating relationships.
- **Messages:** Labeled arrows showing the flow of messages between objects.

**Example:**
For processing an order, the collaboration diagram might include `Customer`, `Order`, `Payment`, and `Product` objects and the messages exchanged to complete the transaction.

#### 3. Interaction Diagram: Sequence Diagram

**Definition:**
A Sequence Diagram shows how objects interact in a particular sequence of time.

**Components:**
- **Lifelines:** Vertical dashed lines representing the lifespan of an object.
- **Messages:** Horizontal arrows showing the messages exchanged between lifelines.
- **Activation Bars:** Thin rectangles on lifelines indicating when an object is active.

**Example:**
For the order processing scenario:

```
Customer      Order      Payment      Product
  |            |            |            |
  | placeOrder |            |            |
  |----------->|            |            |
  |            | calculateTotal()        |
  |            |---------------->|       |
  |            |                |        |
  |            | processPayment()        |
  |            |---------------->|       |
  |            |                |        |
  |            | applyDiscount()         |
  |            |---------------->|       |
  |            |                |        |
```

#### 4. State Chart Diagram

**Definition:**
A State Chart Diagram models the different states of an object and the transitions between those states.

**Components:**
- **States:** Rounded rectangles representing different states of an object.
- **Transitions:** Arrows indicating the movement from one state to another.

**Example:**
For an `Order` object:
```
[New] --> [Processing] --> [Shipped] --> [Delivered]
             |               |
             v               v
          [Cancelled]      [Returned]
```

#### 5. Activity Diagram

**Definition:**
An Activity Diagram represents the workflow of activities and actions, focusing on the flow of control.

**Components:**
- **Activities:** Rounded rectangles representing tasks.
- **Transitions:** Arrows showing the flow from one activity to another.
- **Start/End:** Solid circle (start) and a bullseye (end).

**Example:**
For the order processing workflow:
```
(Start) --> [Receive Order] --> [Process Order] --> [Ship Order] --> [Deliver Order] --> (End)
                               |
                               v
                          [Cancel Order]
```

#### 6. Implementation Diagram: Deployment Diagram

**Definition:**
A Deployment Diagram shows the physical deployment of artifacts (software components) on hardware nodes.

**Components:**
- **Nodes:** Physical devices or execution environments.
- **Artifacts:** Representations of physical files or software components.
- **Associations:** Lines showing relationships between nodes and artifacts.

**Example:**
For an e-commerce system:
```
+---------------+         +---------------+
| Web Server    |         | Database Server|
|---------------|         |--------------- |
| - Apache      |         | - MySQL        |
| - Tomcat      |         |--------------- |
+---------------+         +---------------+
         |                        |
         | HTTP Request/Response  | JDBC
         |                        |
         v                        v
+---------------+         +---------------+
| Application   |         | Data Storage  |
|---------------|         |---------------|
| - eCommerceApp|         | - CustomerDB  |
|---------------|         | - OrderDB     |
+---------------+         +---------------+
```

### Summary

- **Class Diagram:** Represents the static structure of a system.
- **Collaboration Diagram:** Focuses on object interactions and their structural organization.
- **Sequence Diagram:** Shows the sequence of messages exchanged over time.
- **State Chart Diagram:** Models the states of an object and transitions between them.
- **Activity Diagram:** Represents the workflow of activities and control flow.
- **Deployment Diagram:** Shows the physical deployment of software components on hardware.