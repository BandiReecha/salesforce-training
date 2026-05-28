# Salesforce SOQL and Apex Trigger 
## 1. What is SOQL?

SOQL (Salesforce Object Query Language) is a query language used in Salesforce to retrieve data from Salesforce objects such as Accounts, Contacts, Leads, Opportunities, and custom objects.

It is similar to SQL, but SOQL is specially designed for Salesforce data.

### Features of SOQL

* Used to fetch records from Salesforce database
* Can retrieve data from standard and custom objects
* Supports filtering, sorting, and relationships
* Used inside Apex classes, triggers, and developer tools

### Example SOQL Query

```sql
SELECT Name, Industry FROM Account WHERE Industry = 'Technology'
```

This query retrieves the Name and Industry fields from Account records where the industry is Technology.

---

# 2. What is an Apex Trigger?

An Apex Trigger is a piece of Apex code that executes automatically when specific events occur on Salesforce records.

Triggers help automate business processes when records are:

* Inserted
* Updated
* Deleted
* Undeleted

Triggers run either before or after the database operation.

### Example Apex Trigger

```java
trigger ContactTrigger on Contact (before insert) {
    for(Contact con : Trigger.new) {
        if(con.Description == null) {
            con.Description = 'New Contact Created';
        }
    }
}
```

This trigger automatically adds a default description before a new Contact record is inserted.

---

# 3. Difference Between Flow vs Trigger

| Feature             | Flow                              | Trigger                           |
| ------------------- | --------------------------------- | --------------------------------- |
| Type                | Declarative Automation Tool       | Programmatic Automation Tool      |
| Coding Required     | No                                | Yes (Apex)                        |
| Complexity Handling | Best for simple to medium logic   | Best for complex logic            |
| Performance         | Slower for heavy operations       | Faster and optimized              |
| Maintenance         | Easy for admins                   | Requires developer knowledge      |
| Use Case            | Approvals, notifications, updates | Complex validations, integrations |

## Before Trigger vs After Trigger

| Feature       | Before Trigger                  | After Trigger                            |
| ------------- | ------------------------------- | ---------------------------------------- |
| Executes      | Before record saved to database | After record saved to database           |
| Main Purpose  | Validate or modify values       | Access record IDs and related records    |
| Database Save | Not completed yet               | Already completed                        |
| Common Usage  | Field updates and validation    | Sending emails, creating related records |

---

# 4. Trigger Use Cases (5 Examples)

## 1. Automatic Field Update

When a new Contact is created, automatically set a default status or description.

## 2. Email Notification

Send an email notification to managers when a high-value Opportunity is created.

## 3. Data Validation

Prevent users from saving records if mandatory business conditions are not satisfied.

## 4. Create Related Records

Automatically create a follow-up task whenever a Case is opened.

## 5. Audit and Logging

Store changes made to important fields such as salary, status, or customer priority.

---

# 5. Query Examples (English Query Ideas)

## Example 1

Retrieve all Accounts from the Technology industry.

```sql
SELECT Name FROM Account WHERE Industry = 'Technology'
```

## Example 2

Find all Contacts created this month.

```sql
SELECT FirstName, LastName FROM Contact WHERE CreatedDate = THIS_MONTH
```

## Example 3

Get Opportunities with amount greater than 1 lakh.

```sql
SELECT Name, Amount FROM Opportunity WHERE Amount > 100000
```

## Example 4

Retrieve all Cases with status Open.

```sql
SELECT Subject, Status FROM Case WHERE Status = 'Open'
```

## Example 5

Find students/customers whose city is Vijayawada.

```sql
SELECT Name, City__c FROM Student__c WHERE City__c = 'Vijayawada'
```

---

# 6. Reflection: Why Enterprise Systems React Automatically to Data Changes

Enterprise systems handle large amounts of business data every day. Manual monitoring of every change is difficult and time-consuming. Automatic reactions to data changes help organizations improve efficiency, accuracy, and speed.

### Reasons Why Automatic Reactions Are Important

## 1. Faster Business Operations

Automation instantly performs tasks when data changes occur, reducing delays.

## 2. Reduced Human Errors

Triggers and flows minimize manual work and improve data consistency.

## 3. Better Customer Experience

Customers receive faster responses, notifications, and updates.

## 4. Real-Time Processing

Systems can immediately validate data, create records, or send alerts.

## 5. Improved Productivity

Employees can focus on important tasks instead of repetitive manual operations.

### Conclusion

Automatic reactions using tools like Flows and Apex Triggers are essential in modern enterprise systems. They improve reliability, scalability, and operational efficiency while ensuring that business rules are enforced consistently.
