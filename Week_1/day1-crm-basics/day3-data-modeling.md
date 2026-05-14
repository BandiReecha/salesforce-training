###Task -1

| Term       | Meaning                                                                      | Example                  |
| ---------- | ---------------------------------------------------------------------------- | ------------------------ |
| **App**    | A collection of related objects, tabs, and tools used for a specific purpose | Student Management App   |
| **Object** | A database table that stores a type of data                                  | Student, Course, Faculty |
| **Record** | A single row/data entry inside an object                                     | Student: “Rahul Kumar”   |
| **Field**  | A column/attribute in an object                                              | Name, Email, Roll Number |

---

# Easy Real-Life Analogy

Imagine a **school notebook system**:

| Salesforce Term | Real-Life Example                 |
| --------------- | --------------------------------- |
| App             | Entire school management software |
| Object          | One notebook for Students         |
| Record          | One student’s details             |
| Field           | Name, Age, Phone columns          |

---

# Example

## Object: Student

| Name  | Roll No | Email                                     |
| ----- | ------- | ----------------------------------------- |
| Rahul | 101     | [rahul@gmail.com](mailto:rahul@gmail.com) |

* **Object** = Student
* **Record** = Rahul’s row
* **Fields** = Name, Roll No, Email

---

# Standard Objects vs Custom Objects in Salesforce

| Feature    | Standard Object                          | Custom Object                                  |
| ---------- | ---------------------------------------- | ---------------------------------------------- |
| Definition | Pre-built objects provided by Salesforce | Objects created by users based on requirements |
| Created By | Salesforce                               | User/Admin/Developer                           |
| Purpose    | Common business needs                    | Organization-specific needs                    |
| Editable   | Limited customization                    | Fully customizable                             |
| API Name   | Normal name                              | Ends with `__c`                                |
| Examples   | Account, Contact, Lead, Opportunity      | Student__c, Faculty__c, Course__c              |

---

# Standard Objects

These already exist in Salesforce.

Used for:

* Sales
* CRM
* Customer management

## Examples

* Account
* Contact
* Lead
* Opportunity

### Example

A company storing customer information uses:

* Account → Company details
* Contact → Customer person details

---

# Custom Objects

Created when standard objects are not enough.

## Examples

For a college system:

* Student__c
* Department__c
* Faculty__c

### Why “__c”?

Salesforce automatically adds `__c` to custom objects and fields.

Example:

```text id="6pdjru"
Student__c
Course__c
Roll_Number__c
```

---

# Key Difference

## Standard Object

Already available in Salesforce.

## Custom Object

Created manually for your own project/business needs.

---

# College Data Model in Salesforce

## Objects

### 1. Student

Stores student details.

* Student Name
* Roll Number
* Email
* Phone

### 2. Faculty

Stores faculty information.

* Faculty Name
* Employee ID
* Department

### 3. Course

Stores course details.

* Course Name
* Course Code
* Credits
* Faculty

### 4. Department

Stores department information.

* Department Name
* HOD Name

### 5. Enrollment (Junction Object)

Used to connect Students and Courses.

* Student
* Course
* Enrollment Date
* Grade

---

# Relationships

| Parent Object | Child Object | Relationship Type           |
| ------------- | ------------ | --------------------------- |
| Department    | Faculty      | One-to-Many (Lookup)        |
| Department    | Course       | One-to-Many (Lookup)        |
| Faculty       | Course       | One-to-Many (Lookup)        |
| Student       | Enrollment   | One-to-Many (Master-Detail) |
| Course        | Enrollment   | One-to-Many (Master-Detail) |

---

# Data Model Diagram

```text id="dr7iyg"
                Department
                /       \
               /         \
          Faculty       Course
                             \
                              \
                           Enrollment
                              /    \
                             /      \
                        Student    Course
```

---

# Better Structured Diagram

```text id="2zwct5"
+----------------+
|  Department    |
+----------------+
        |
        | Lookup
        |
+----------------+
|    Faculty     |
+----------------+

        |
        | Lookup
        v

+----------------+
|     Course     |
+----------------+
        |
        | Master-Detail
        |
+----------------+
|   Enrollment   |
+----------------+
        |
        | Master-Detail
        |
+----------------+
|    Student     |
+----------------+
```

---

# Explanation

## Department

Acts as the parent object for:

* Faculty
* Course

## Faculty

Teaches Courses.

## Course

Contains many enrolled students.

## Enrollment

Acts as a bridge between:

* Student
* Course

This creates a **Many-to-Many relationship** between Student and Course.

---

# Real Example

| Student | Course               |
| ------- | -------------------- |
| Rahul   | EMWTL                |
| Rahul   | Analog Communication |
| Priya   | EMWTL                |

One student can join many courses, and one course can contain many students.
# Formula Fields in Salesforce

## What is a Formula Field?

A **Formula Field** automatically calculates a value using other fields.

* No manual entry needed
* Updates automatically when related field values change

---

# Syntax Idea

```text id="d9j73r"
Formula Field = Calculation using other fields
```

Example:

```text id="jlwm6h"
Marks_Obtained__c / Total_Marks__c * 100
```

---

# College Data Model Formula Field Examples

---

# 1. Student Percentage Formula

## Object:

Student

## Fields Used:

* Marks_Obtained__c
* Total_Marks__c

## Formula:

\frac{Marks_Obtained}{Total_Marks}\times100

## Output Example

| Marks Obtained | Total Marks | Percentage |
| -------------- | ----------- | ---------- |
| 450            | 500         | 90%        |

### Explanation

Salesforce automatically calculates percentage.

---

# 2. Course Duration Remaining

## Object:

Course

## Fields Used:

* End_Date__c
* TODAY()

## Formula:

```text id="3v42an"
End_Date__c - TODAY()
```

## Output Example

| End Date    | Remaining Days |
| ----------- | -------------- |
| 30-May-2026 | 16             |

### Explanation

Shows how many days are left for course completion.

---

# 3. Full Student Name

## Object:

Student

## Fields Used:

* First_Name__c
* Last_Name__c

## Formula:

```text id="ojtklh"
First_Name__c & " " & Last_Name__c
```

## Output Example

| First Name | Last Name | Full Name   |
| ---------- | --------- | ----------- |
| Rahul      | Kumar     | Rahul Kumar |

### Explanation

Combines first and last name automatically.

---

# 4. Pass/Fail Status

## Object:

Student

## Fields Used:

* Percentage__c

## Formula:

```text id="a2s3x9"
IF(Percentage__c >= 40, "Pass", "Fail")
```

## Output Example

| Percentage | Result |
| ---------- | ------ |
| 75         | Pass   |
| 32         | Fail   |

### Explanation

Automatically checks whether the student passed.

---

# Advantages of Formula Fields

* Automatic calculations
* Reduces manual work
* Prevents human errors
* Real-time updates
* Useful for reports and dashboards

---

# Common Formula Functions

| Function     | Purpose                |
| ------------ | ---------------------- |
| IF()         | Conditional logic      |
| TODAY()      | Current date           |
| ROUND()      | Rounds numbers         |
| TEXT()       | Converts value to text |
| ISPICKVAL()  | Checks picklist values |
| AND() / OR() | Multiple conditions    |
# Validation Rules in Salesforce

## What is a Validation Rule?

A **Validation Rule** checks data before saving a record.

If the condition is true:

* Salesforce shows an error
* Record is not saved

Used to maintain **correct and valid data**.

---

# Syntax Idea

```text id="u7m3u4"
IF condition is TRUE → Show Error
```

---

# 1. Student Age Validation

## Requirement

Student age must be greater than 17.

## Object

Student

## Formula

```text id="dql3r8"
Age__c < 18
```

## Error Message

```text id="6ej1gx"
Student age must be at least 18.
```

### Explanation

If age is below 18, Salesforce blocks saving the record.

---

# 2. Course Fee Cannot Be Negative

## Object

Course

## Formula

```text id="x2zj5r"
Course_Fee__c < 0
```

## Error Message

```text id="i1r0s2"
Course fee cannot be negative.
```

### Explanation

Prevents invalid fee values.

---

# 3. Email Must Contain “@”

## Object

Student

## Formula

```text id="w5n2ak"
NOT(CONTAINS(Email__c, "@"))
```

## Error Message

```text id="v9h7lm"
Enter a valid email address.
```

### Explanation

Checks whether the email format is valid.

---

# 4. Attendance Cannot Exceed 100%

## Object

Student

## Formula

```text id="t4k8py"
Attendance__c > 100
```

## Error Message

```text id="b3q1cx"
Attendance cannot be more than 100%.
```

### Explanation

Ensures attendance percentage is realistic.

---

# 5. Roll Number Must Be 10 Digits

## Object

Student

## Formula

```text id="m8z4nd"
LEN(TEXT(Roll_Number__c)) <> 10
```

## Error Message

```text id="f2y6wr"
Roll number must contain exactly 10 digits.
```

### Explanation

Validates proper roll number length.

---

# Advantages of Validation Rules

* Improves data accuracy
* Prevents incorrect entries
* Reduces duplicate or incomplete data
* Enforces business rules automatically

---

# Common Functions Used

| Function   | Purpose                        |
| ---------- | ------------------------------ |
| IF()       | Conditional logic              |
| AND()      | Multiple conditions            |
| OR()       | Either condition               |
| NOT()      | Opposite condition             |
| ISBLANK()  | Checks empty fields            |
| LEN()      | Counts characters              |
| CONTAINS() | Finds text inside another text |

---

# Real-Time Example

If a user enters:

| Age | Result       |
| --- | ------------ |
| 16  | Error        |
| 20  | Record Saved |

Validation rules automatically stop invalid data from entering the system.
# Why Structured Enterprise Data Matters

Structured enterprise data is very important in systems like Salesforce because it helps organizations store, manage, and use information efficiently.

---

# 1. Better Organization of Data

Structured data stores information in proper:

* Objects
* Fields
* Records
* Relationships

This makes data easy to:

* Search
* Update
* Analyze

### Example

In a college system:

* Student data is stored separately
* Course data is stored separately
* Relationships connect them properly

---

# 2. Improves Accuracy

Using:

* Validation Rules
* Formula Fields
* Relationships

helps reduce:

* Duplicate data
* Wrong entries
* Missing information

### Example

A validation rule can stop invalid email formats.

---

# 3. Faster Decision Making

Well-structured data helps organizations generate:

* Reports
* Dashboards
* Analytics

quickly and accurately.

### Example

College management can easily check:

* Student performance
* Faculty workload
* Course enrollments

---

# 4. Better Automation

Structured data supports automation tools such as:

* Workflows
* Flows
* Notifications

### Example

When a student enrolls in a course, Salesforce can automatically:

* Send confirmation emails
* Update enrollment count

---

# 5. Easy Relationship Management

Enterprise systems need connected data.

Relationships help connect:

* Students ↔ Courses
* Faculty ↔ Departments
* Customers ↔ Orders

This improves real-world data management.

---

# 6. Scalability

As organizations grow, structured data helps manage thousands or millions of records efficiently.

Without structure:

* Data becomes confusing
* Searching becomes slow
* Errors increase

---

# 7. Security and Access Control

Structured systems allow organizations to control:

* Who can view data
* Who can edit records
* Department-wise access

This improves data privacy and security.

---

# Conclusion

Structured enterprise data is the foundation of modern business systems because it:

* Organizes information properly
* Improves accuracy
* Enables automation
* Supports analytics
* Helps businesses make faster and smarter decisions

Without structured data, managing large organizations would become difficult and inefficient.
## 1. Why can’t companies manage everything using Excel sheets?

Using only Excel sheets becomes difficult when data grows large.

Problems with Excel:

* Duplicate data
* No proper relationships between data
* Difficult multi-user access
* Higher chance of human errors
* Weak security
* No automation
* Hard to generate advanced reports

Large organizations need systems like Salesforce because they provide:

* Centralized data storage
* Relationships
* Automation
* Security
* Real-time collaboration

### Example

A college managing:

* 10,000 students
* 500 faculty
* Hundreds of courses

would become difficult using only spreadsheets.

---

## 2. Why are relationships important between objects?

Relationships connect related data together.

They help:

* Avoid duplicate data
* Improve organization
* Make reporting easier
* Reflect real-world connections

### Example

* One Department has many Faculty members
* One Course has many Students

Without relationships, data becomes disconnected and difficult to manage.

---

## 3. What problems happen if data is inconsistent?

Inconsistent data means different or incorrect versions of the same information exist.

Problems include:

* Wrong reports
* Poor decision making
* Duplicate records
* Customer/student confusion
* System errors

### Example

If one student’s phone number appears differently in multiple places, communication problems may occur.

Data consistency improves trust and reliability.

---

## 4. Why should repetitive calculations be automated?

Automation saves:

* Time
* Effort
* Human mistakes

Formula Fields and automation tools calculate values automatically.

### Example

Student percentage calculation:
\frac{Marks_Obtained}{Total_Marks}\times100

Instead of manually calculating every student’s percentage, Salesforce updates it automatically.

Benefits:

* Faster work
* Accurate results
* Real-time updates

---

## 5. Why should invalid data be blocked early?

Blocking invalid data early prevents bad information from entering the system.

This is done using:

* Validation Rules
* Required Fields
* Data restrictions

### Example

If email format is wrong:

```text id="oh7r3v"
rahulgmail.com
```

the system should reject it immediately.

Benefits:

* Cleaner database
* Better reports
* Fewer future errors
* Improved system reliability

---

## 6. Why is Salesforce called a metadata-driven platform?

Salesforce is called metadata-driven because most configurations are created using metadata instead of hard coding.

Metadata means:

* Information about the structure of data
* Objects
* Fields
* Relationships
* Validation Rules
* Flows
* Page layouts

Admins can build applications by configuration rather than writing large amounts of code.

### Example

Creating:

* Custom Objects
* Formula Fields
* Validation Rules

does not require traditional programming.

Benefits:

* Faster development
* Easy customization
* Low-code/no-code platform
* Easier maintenance
