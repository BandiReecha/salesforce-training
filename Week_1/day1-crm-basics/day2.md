###DAY-2
###TASK-2

What is an App in Salesforce?

An App in Salesforce is a collection of tools, tabs, objects, and features grouped together for a specific business purpose.
Example: Sales App, Service App, Marketing App.

It helps users work efficiently in one place.


What is an Object?

An Object in Salesforce is like a database table used to store data.

Examples:

* Account → stores company details
* Contact → stores customer details
* Opportunity → stores sales deals

Objects contain records and fields.


 What is a Tab?

A **Tab** in Salesforce is a user interface element used to access objects, records, dashboards, or apps.

Example:

Accounts Tab
Contacts Tab
Reports Tab

Tabs help users quickly navigate inside Salesforce.


  ###TASK-3
 Configuration (No Code)

Use **Configuration** in Salesforce when requirements can be achieved using built-in tools without programming.

Examples:

1. Creating validation rules to prevent incorrect data entry.
2. Building workflows/flows to send automatic email alerts.

 Coding (Apex)

Use Coding (Apex) in Salesforce when complex logic or advanced customization is required.

Examples:

1. Creating custom logic for automatic calculations across multiple objects.
2. Integrating Salesforce with external applications using APIs.

###Task 4: Real System Thinking
###Example: College Management System

### App Name

College Management App

### Objects Inside the App

In Salesforce, the app can contain these objects:

1. **Student** – stores student details
2. **Faculty** – stores teacher information
3. **Course** – stores course subjects
4. **Attendance** – stores attendance records
5. **Examination** – stores marks and results


### How Users Will Interact With It

Students can check attendance, marks, and course details.
Faculty can update attendance and marks.
Admin staff can manage student records and schedules.
Users interact through tabs, forms, reports, and dashboards inside Salesforce.

  
  | Configuration                  | Coding                            |
| ------------------------------ | --------------------------------- |
| No programming required        | Requires programming knowledge    |
| Uses clicks and built-in tools | Uses Apex, Visualforce, LWC, APIs |
| Faster and easier              | More flexible and powerful        |
| Best for simple automation     | Best for complex business logic   |
| Example: Flow, Validation Rule | Example: Apex Trigger             |


| App                                      | Object                      |
| ---------------------------------------- | --------------------------- |
| Collection of features and tabs          | Stores specific data        |
| Used for navigation and business process | Used for data storage       |
| Contains multiple objects                | Contains records and fields |
| Example: Sales App                       | Example: Account Object     |

  
What is Multi-Tenant Architecture?

In Salesforce, multi-tenant architecture means many customers share the same software and servers, but each customer’s data is kept secure and separate.

Similar to multiple families living in one apartment building with separate rooms.

  ## 1. What is an App in Salesforce?

An **App** in Salesforce is a collection of tabs, objects, tools, and features designed for a specific business purpose.
Example: Sales App, Service App.

---

## 2. What is an Object?

An **Object** in Salesforce is like a database table used to store data.
Examples: Account, Contact, Opportunity.

---

## 3. Difference: Configuration vs Coding

| Configuration                  | Coding                            |
| ------------------------------ | --------------------------------- |
| No programming required        | Requires programming knowledge    |
| Uses clicks and built-in tools | Uses Apex, Visualforce, LWC, APIs |
| Faster and easier              | More flexible and powerful        |
| Best for simple automation     | Best for complex business logic   |
| Example: Flow, Validation Rule | Example: Apex Trigger             |

---

## 4. Difference between App and Object

| App                                      | Object                      |
| ---------------------------------------- | --------------------------- |
| Collection of features and tabs          | Stores specific data        |
| Used for navigation and business process | Used for data storage       |
| Contains multiple objects                | Contains records and fields |
| Example: Sales App                       | Example: Account Object     |

---

## 5. What is Multi-Tenant Architecture?

In Salesforce, **multi-tenant architecture** means many customers share the same software and servers, but each customer’s data is kept secure and separate.

Similar to multiple families living in one apartment building with separate rooms.

---

## 6. When should we use configuration instead of code?

Use **configuration** when the requirement can be solved using built-in Salesforce tools without programming.

Examples:

* Creating approval processes
* Sending automated email alerts
* Creating reports and dashboards

It is faster, easier to maintain, and cost-effective.

---

## 7. How does Salesforce allow developers to extend functionality?

Salesforce allows developers to extend functionality using:

* **Apex** → backend programming language
* **Lightning Web Components (LWC)** → custom UI development
* **APIs** → integration with external systems
* **Visualforce** → custom pages
* **Triggers** → automation using code
