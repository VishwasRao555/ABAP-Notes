# SAP ABAP – HCLTech Technical Interview Guide

**Core ABAP | Modern ABAP | SAP Fundamentals | Interview Practice**

## Contents

Click any topic to jump directly to its section. Use **Back to contents** to return here.

**Core ABAP**

- [SE11 – Original DDIC Notes](#1-ddic--data-dictionary)
- [DDIC Keys and Table Relationships](#ddic-keys-and-table-relationships)
- [Classical DDIC Views](#classical-ddic-views)
- [Internal Tables and Basic ABAP](#internal-tables-and-basic-abap)
- [Modularization and Function Modules](#modularization-and-function-modules)
- [Object-Oriented ABAP](#object-oriented-abap)
- [Reports and Selection Screens](#reports-and-selection-screens)
- [ALV Reports, OO ALV and Event Handlers](#alv-reports)
- [Smart Forms](#smart-forms)
- [Module Pool Programming](#module-pool-programming)
- [Transactions, Packages and Transports](#transactions-packages-and-transports)
- [ABAP SQL and Performance](#abap-sql-and-performance)
- [Core ABAP Debugging - SAP GUI](#core-abap-debugging---sap-gui)
- [Enhancements, Interfaces and Data Migration](#enhancements-interfaces-and-data-migration)

**Modern ABAP and S/4HANA**

- [Modern ABAP](#modern-abap)
- [SAP HANA, CDS and AMDP](#sap-hana-cds-and-amdp)
- [CDS Views - Important Interview Questions](#cds-views---important-interview-questions)
- [RAP, OData, Fiori and ABAP Cloud](#rap-odata-fiori-and-abap-cloud)
- [Modern ABAP Debugging - ADT, CDS and RAP](#modern-abap-debugging---adt-cds-and-rap)
- [ATC Checks and Code Quality](#atc-checks-and-code-quality)

**SAP fundamentals and interview practice**

- [SAP Fundamentals](#sap-fundamentals)
- [SAP Implementation and S/4HANA Migration](#sap-implementation-and-s4hana-migration)
- [Practical SAP ABAP Interview Questions](#practical-sap-abap-interview-questions)
- [Personal Interview Questions - SAP ABAP](#personal-interview-questions---sap-abap)

**Quick revision**

- [Important T-Codes](#quick-revision--important-t-codes)
- [Final revision checklist](#final-revision-checklist)
- [SAP references](#official-sap-references-for-the-added-topics)
- [HCLTech preparation sources](#hcltech-role-alignment-and-interview-preparation-sources)

Use the short answers to explain the definition, purpose and key features in your own words. Code snippets are revision examples, not complete tested programs. The questions are selected for junior ABAP interview relevance, not confirmed HCLTech interview frequencies. The original SE11 notes are preserved.

---

# 1. DDIC – Data Dictionary

### Q1. What is DDIC (Data Dictionary)?

**DDIC** is a central repository in SAP ABAP used to define and manage database objects such as tables, views, data elements, domains, structures and table types. And DDIC can be Accessed by 
Using the Transaction Code ( T-Code ) - **SE11 .

### Q2. What is SE11?

**SE11** is the SAP Transaction Code used to create, modify, display and manage Data Dictionary objects. 
Main Objects Available in **SE11** are :-
1. Database Tables
2. Views
3. Data Types
4. Domains
5. Data Elements
6. Structures
7. Table Types
8. Search Helps
9. Lock Objects

### Q3. What are the types of DDIC objects?

DDIC objects are mainly classified into three categories:

| Category         | Objects                                         |
| ---------------- | ----------------------------------------------- |
| Database objects | Database Tables, Views                          |
| Data Types       | Data Elements, Domains, Structures, Table Types |
| Other objects    | Search Helps, Lock Objects                      |

# 2. Domain And  Data Element

### Q4. What is a Domain?

A Domain defines the technical properties of a field  such as data type, field length, decimal places and possible value ranges.

- It defines the technical characteristics of a field.
- Also Multiple data elements can use the same domain.
- Created using the T-Code : SE11 

### Q5. What is a Data Element?

A Data Element defines the semantic meaning of a field, including its business description, field labels and documentation. It refers to a Domain for its technical properties or a predefined data type .

- It provides business meaning to a field.
- It uses a domain to obtain technical properties.
- Created using the T-Code : SE11 .

### Q6. What is the difference between a Domain and a Data Element ?

- A **Domain** Defines how the Data is Stored in a Field where as a **Data Element** defines how the data is Represented in a Field . 
- A **Domain** Defines the Technical Properties of a Field where as a **Data Element** defines business meaning of a Field .

# 3.Database Table

### Q7. What is a Database Table in ABAP ?

A Database Table is a DDIC object used to store application data permanently in the underlying database in the form of a table with rows and columns .  

- Each column represents a field.
- Each row represents a record.
- Created using the T-Code : SE11 .

### Q8. What are the types of Database Tables in SAP ABAP?

There are three main types:

1. **Transparent Table:** Has a one-to-one relationship with a physical database table and is used to store application data. 

2. **Pooled Table:** Multiple logical tables were stored together in a table pool in older SAP systems.
 
3. **Cluster Table:** Multiple logical tables were stored together in a table cluster in older SAP systems.

**NOTE :** Pooled and Cluster Tables are "legacy concepts" . "Modern SAP systems", "particularly SAP HANA", primarily use transparent table

### Q9. What are Delivery Class and Data Class?

**Delivery Class** : It indicates the category and delivery behaviour of the table data.
Example: Class A is commonly used for application data.

**Data Class :** Specifies the category of database storage for a table.
Example: APPL0 for master data and APPL1 for transaction data.

### Q10. Difference Between Client-Dependent Table And 
### Client-Independent Table ?

| Client-Dependent Table                               | Client-Independent Table                                      |
| ---------------------------------------------------- | ------------------------------------------------------------- |
| It generally contains MANDT as its first key field.  | It does not contain MANDT as its key field.                   |
| It stores data separately for different SAP clients. | Its data is shared across clients within the same SAP system. |
### Q11. What is a Primary Key in ABAP?

A Primary Key is a field or combination of fields that uniquely identifies each record in a database table.

- It does not allow duplicate or NULL values.
- A table can have only one primary key.

### Q12. What is a Foreign Key in ABAP?

A Foreign Key is a field in one table that refers to the Primary Key of another table to establish a relationship between the two tables.

- It is used to maintain referential integrity between tables.
- Created in SE11 using the Foreign Key relationship.
### Q13. What is a Check Table and Value Table?

- **Check Table:** A table that contains valid values used to check the entries in a foreign key field.

- **Value Table:** A table assigned to a Domain that suggests valid values for fields using that Domain.

### Q14. What is Cardinality in ABAP?

Cardinality defines the number of records that can be related between two tables through a Foreign Key relationship.

Types of Cardinality:

| Cardinality | Meaning                                                                                | Example                                 |
| ----------- | -------------------------------------------------------------------------------------- | --------------------------------------- |
| 1:1         | One check table record is related to exactly one foreign key table record.             | One person – One ID Card                |
| 1:C         | One check table record is related to zero or one foreign key table record..            | One student – Zero or One ID Card       |
| 1:N         | One check table record is related to one or more foreign key table records.            | One student – Multiple ID Cards         |
| 1:CN        | One check table record is related to zero, one, or multiple foreign key table records. | One student – Zero or Multiple ID Cards |

**Note:** `C` indicates optional (zero records allowed), and `N` indicates multiple records allowed.

### Q15. What is a Foreign Key Relationship in ABAP?

A Foreign Key Relationship connects two tables by linking a Foreign Key field in the dependent table with the Primary Key of the check table.

- It maintains data consistency.
- It includes cardinality and foreign key field assignments.

# 4.Structure and Table Type 

### Q16. What is a Structure in ABAP?

A Structure is a DDIC object used to group multiple fields of different data types under a single name. It does not store data permanently in the database.

- It contains multiple fields with different data types.
- It is used to organize and process related data.
- Created using the T-Code: SE11.

### Q17. What is a Table Type in ABAP?

A Table Type is a DDIC object used to define the structure and properties of an internal table.
Only used While Creating or Defining an "Internal Table" ( Local Object ) .

- It defines the line type, table category and key.
- It is used to create internal tables with a predefined structure.
- We should select the Type of Table while creating a Table Type
- Created using the T-Code: SE11.

### Q18. Types of Table Types Or Internal Tables (SE11)

**1. Standard Table:** A Standard Table stores records in sequential order and allows duplicate key entries or non-unique Keys. Data is accessed mainly using an index.

**2. Sorted Table:** A Sorted Table automatically stores records in sorted order based on its key and supports unique or non-unique keys.

**3. Hashed Table:** A Hashed Table stores records using a hash algorithm and requires a unique key. Data is accessed using the key rather than an index.

### Q19. What is a Lock Object in SAP ABAP?

A Lock Object is a DDIC object used to prevent multiple users from simultaneously changing the same data, ensuring data consistency in the SAP system.

- It prevents conflicts when multiple users access or modify the same data.
- It Locks a Development Object ( Object can't be Edited or Manipulated )
- Created using the T-Code: SE11.
- SAP automatically generates two Function Modules:
     
    - `ENQUEUE_<Lock_Object>` – To lock the data.
    - `DEQUEUE_<Lock_Object>` – To unlock the data.
    
- Until You DEQUEUE the Object or Data it cant be Used or changed By Other Users .(Don't Need to Do anything Manually , Everything will be Done Automatically )

# 5.Search Help 

### Q20. What is Search Help in SAP ABAP?

Search Help is a DDIC object used to provide possible input values for a field, helping users select the correct value instead of entering it manually.

Main Points:

- It is used to provide F4 help (input help) for fields.
- Created using T-Code: SE11.
- It can be assigned to individual fields in a Data Element or directly to fields in a Database Table.
- It is commonly used in selection screens and screen fields.

### Q21. What are the Types of Search Help?

There are two types of Search Help:

**1. Elementary Search Help:**

- An Elementary Search Help provides F4 help using a single selection method (usually one database table or view).
- It contains the search help parameters and selection conditions.

**2. Collective Search Help:**

- A Collective Search Help combines multiple Elementary Search Helps into a single search help.
- It allows users to search using different search methods.

### Q22. What is a Selection Method in Search Help?

A Selection Method specifies the source from which the search help retrieves values for displaying in the F4 hit list.

- It can be a Database Table or a View.
- Example: `MARA` (Material Master Table).

### Q23. What are Import and Export Parameters in Search Help?

**1. Import Parameter (IMP):** It passes the existing field value from the screen to the Search Help to filter the available records.

**2. Export Parameter (EXP):** It returns the selected value from the Search Help hit list back to the screen field.

- A parameter can be both Import and Export at the same time.

### Q24. What are LPOS and SPOS in Search Help?

- LPOS (List Position): Defines the column position of a parameter in the Search Help hit list.

- SPOS (Selection Position): Defines the position of a parameter in the value restriction screen, where users can enter search criteria.

### Q25. What are the Dialog Types in Search Help?

Dialog Type defines how the values are displayed when the user presses F4.

There are three dialog types:

|Dialog Type|Meaning|
|---|---|
|A – Dialog Depends on Set of Values|If there are fewer than 100 records, the hit list appears directly; otherwise, a restriction screen appears first.|
|C – Dialog with Value Restriction|A restriction screen appears first, allowing users to filter values before displaying the hit list.|
|D – Display Values Immediately|The hit list is displayed directly when the user presses F4.|

### Q26. What is a Hot Key in Search Help?

A Hot Key is a single-character shortcut assigned to an Elementary Search Help within a Collective Search Help to access a particular search method directly.

- It helps users select a specific Elementary Search Help.
- Each Elementary Search Help inside a Collective Search Help should have a different Hot Key.
- Defined in SE11.

### Q27. What is Search Help Assignment?

Search Help can be assigned in the following ways:

**1. Data Element:** Assigned to a Data Element so that fields using that Data Element can inherit the F4 help.
**2. Database Table Field:** Assigned directly to an individual field in a Database Table.
**3. Selection Screen Parameter:** Assigned directly using ABAP code.

### Q28. How to use Search Help in an ABAP Selection Screen?

We can attach an existing Search Help to a selection screen parameter using the `MATCHCODE OBJECT` addition.

Syntax:

```
PARAMETERS: P_DEPT TYPE ZDEPT_ID
            MATCHCODE OBJECT ZSH_DEPT.
```

- `P_DEPT` – Selection screen parameter.
- `ZDEPT_ID` – Data type.
- `ZSH_DEPT` – Search Help object name.

### Q29. What is a Search Help Exit?

A Search Help Exit is a Function Module used to modify or control the standard search help process when additional custom logic is required.

- It is used for special filtering and processing requirements.







---

> **Interview accuracy note (separate from your unchanged SE11 notes):** A DDIC lock object protects application data, not development objects. Applications use the generated ENQUEUE and DEQUEUE function modules as part of their locking logic; other users are prevented from conflicting changes when they follow the same locking protocol. A DDIC foreign key is not automatically an enforced database constraint. A domain value table proposes a check table; by itself, it does not perform an input check.

[Back to contents](#contents)

---

## DDIC Keys and Table Relationships

[Back to contents](#contents)

These are additional explanations for the original SE11 notes above.

### Q30. What is a composite key?

A composite key is a key made up of two or more fields. We use it when one field alone cannot uniquely identify a record. For example, in VBAP, `VBELN` and `POSNR` identify a sales order item within a client; `MANDT` is also part of the full table key.

### Q31. What is the difference between a primary index and a secondary index?

A primary index supports access using the primary key. A secondary index provides another access path, often for fields used in searches. I would add one only after checking performance because indexes also consume storage and add maintenance work.

### Q32. What is an append structure? How is it different from an include structure?

An append structure adds custom fields to an existing extensible table or structure without modifying its original definition. An include structure lets us reuse a group of fields in multiple definitions. I use supported extension options for SAP standard objects.

### Q33. What is table buffering? When should you avoid it?

Table buffering keeps suitable table data in application-server memory to reduce database reads. It works well for small, rarely changed tables, but is generally unsuitable for frequently updated transaction data. SAP supports single-record, generic and full buffering.

---


## Classical DDIC Views

[Back to contents](#contents)

### Q34. What is a view in SAP ABAP?

A view is a logical way to look at data from one or more tables. It lets us fetch exactly the fields and records we need without storing a separate copy.

### Q35. What are the four types of views in SE11?

SAP Dictionary has four classical view types:

| View | Main use |
|---|---|
| Database view | Read selected fields from one or more tables using an inner join when combining tables |
| Projection view | Show selected fields of a single table |
| Help view | Provide data for search helps |
| Maintenance view | Maintain related table data together |

### Q36. What is the difference between a database table and a view?

A table stores the actual data, while a view shows data from existing tables. So when the underlying records change, we see the updated data the next time we read the view.

### Q37. What is a Table Maintenance Generator (TMG)?

TMG generates a maintenance dialog for a table or maintenance view. We use SE54 or the maintenance generator in SE11 to create it and SM30 to maintain entries, subject to authorization and settings.

---


## Internal Tables and Basic ABAP

[Back to contents](#contents)

### Q38. What is an internal table? What is a work area?

An internal table is a temporary table in ABAP memory. We use it to hold and process multiple records during execution, while a work area holds just one record.

### Q39. What is a structure in an ABAP program?

A structure groups related fields under one name, even if they have different data types. We use it to represent a single record, such as a student with an ID, name and marks. A structure does not have permanent database storage of its own.

### Q40. What is a table type in ABAP?

A table type defines how an internal table should be built. It specifies the row type, table category and key. We can create a reusable table type in SE11 or define one locally using `TYPES`.

### Q41. What is the difference between a structure, table type, work area and internal table?

A structure type defines the fields of a record, and a table type defines the layout and key of a collection of records. A work area holds one record, while an internal table holds multiple records in memory.

| Concept | Simple example |
|---|---|
| Structure type | Student ID, name and marks |
| Table type | Definition of a table of students |
| Work area | One student's data |
| Internal table | A list of students |

### Q42. How do you declare a structure, table type, work area and internal table?

We use `TYPES` to define reusable types and `DATA` to create actual data objects. Here, the structure type defines one row and the table type defines the collection.

```abap
TYPES: BEGIN OF ty_student,
         id    TYPE i,
         name  TYPE string,
         marks TYPE i,
       END OF ty_student.
TYPES ty_students TYPE STANDARD TABLE OF ty_student WITH EMPTY KEY.

DATA ls_student TYPE ty_student.
DATA lt_students TYPE ty_students.

ls_student = VALUE #( id = 1 name = 'Ravi' marks = 85 ).
APPEND ls_student TO lt_students.
```

### Q43. What is the difference between an internal table and a database table?

A database table stores data permanently after it is committed. An internal table stores data temporarily in ABAP memory. We often fetch records from a database table into an internal table for processing or display.

### Q44. What is the difference between TYPES, DATA and CONSTANTS?

`TYPES` defines a data type, while `DATA` creates a variable using a type. `CONSTANTS` creates a named value that cannot be changed. We use constants instead of repeating fixed values throughout the code.

```abap
TYPES ty_marks TYPE i.
DATA lv_marks TYPE ty_marks.
CONSTANTS lc_pass TYPE i VALUE 40.
```

### Q45. What are the types of internal tables?

ABAP has three types of internal tables. The main difference is how they store and find records.

- **Standard:** Stores rows by index and allows duplicate keys.
- **Sorted:** Keeps rows sorted by key; the key can be unique or non-unique.
- **Hashed:** Uses a unique key for fast full-key searches and does not support index access.

**Syntax:**

```abap
DATA lt_std TYPE STANDARD TABLE OF ty_item WITH EMPTY KEY.
DATA lt_sort TYPE SORTED TABLE OF ty_item WITH NON-UNIQUE KEY id.
DATA lt_hash TYPE HASHED TABLE OF ty_item WITH UNIQUE KEY id.
```

Here, `ty_item` is a structure type with an `id` field.

### Q46. What is the difference between TYPE and LIKE?

With `TYPE`, we declare a variable using a data type. With `LIKE`, we reuse the type of a variable that already exists.

**Syntax:**

```abap
DATA lv_matnr TYPE mara-matnr.
DATA lv_copy LIKE lv_matnr.
```

### Q47. What is a field symbol? How is it different from a work area?

A field symbol is an alias for an existing data object. A work area usually holds a copy of a row, but a field symbol lets us work directly with the original row, within the table’s rules.

**Syntax:**

```abap
LOOP AT lt_items ASSIGNING FIELD-SYMBOL(<ls_item>).
  <ls_item>-status = 'A'.
ENDLOOP.
```

Check `IS ASSIGNED` if an assignment can fail. The example assumes the row has a `status` field.

### Q48. What are the common internal table operations?

Internal table operations help us manage records in memory.

- `APPEND` / `INSERT` – add records.
- `READ TABLE` / `LOOP AT` – read or process records.
- `MODIFY` / `DELETE` – change or remove records.
- `SORT` / `DELETE ADJACENT DUPLICATES` – sort and remove neighboring duplicates.

For binary search or removing duplicates throughout a standard table, sort by the relevant fields first.

**Syntax:**

```abap
APPEND ls_item TO lt_items.
READ TABLE lt_items INTO ls_item WITH KEY id = 10.
IF sy-subrc = 0.
  ls_item-name = 'Updated'.
  MODIFY lt_items FROM ls_item INDEX sy-tabix.
ENDIF.
DELETE lt_items WHERE id = 20.
```

```abap
SORT lt_items BY id.
DELETE ADJACENT DUPLICATES FROM lt_items COMPARING id.
READ TABLE lt_items INTO ls_item
  WITH KEY id = 10 BINARY SEARCH.
```

The examples use a standard table. Check `sy-subrc` immediately after `READ TABLE`.

### Q49. What is the difference between APPEND and INSERT in an internal table?

APPEND adds a row at the end of an index table, subject to its ordering rules. INSERT TABLE adds a row according to the table's category and key. I use INSERT TABLE for sorted and hashed tables to respect their keys.

### Q50. What is the difference between LOOP AT INTO and ASSIGNING?

INTO copies each row into a work area. ASSIGNING binds a field symbol directly to the row, so allowed changes affect the original table. I use ASSIGNING when I need to update rows directly.

### Q51. What is BINARY SEARCH in ABAP?

BINARY SEARCH finds a row by repeatedly narrowing the search range. For a standard table, we must sort it in ascending order by the search fields in the correct sequence first. Sorted tables already support efficient access using their sorted key.

### Q52. What are SY-SUBRC, SY-TABIX, SY-INDEX and SY-DBCNT?

These are SAP system fields that tell us what happened during execution.

- `SY-SUBRC` – return code; zero usually means success.
- `SY-TABIX` – row index in applicable table operations.
- `SY-INDEX` – current DO or WHILE iteration.
- `SY-DBCNT` – number of database rows processed.

I check SY-SUBRC immediately after the relevant statement.

### Q53. What is COLLECT in ABAP?

`COLLECT` is useful for calculating totals by key. It inserts a new record if the key does not exist; otherwise, it adds the numeric non-key values to the existing record.

**Syntax:**

```abap
TYPES: BEGIN OF ty_total,
         id TYPE i,
         qty TYPE i,
       END OF ty_total.
DATA lt_totals TYPE HASHED TABLE OF ty_total WITH UNIQUE KEY id.
COLLECT VALUE ty_total( id = 1 qty = 10 ) INTO lt_totals.
COLLECT VALUE ty_total( id = 1 qty = 5 ) INTO lt_totals.
```

### Q54. What is the difference between CLEAR, REFRESH and FREE?

`CLEAR` resets a variable or empties an internal table without a header line. `REFRESH` is the older way to empty a table, while `FREE` also releases its allocated table memory more fully.

### Q55. What is the difference between CHECK, CONTINUE and EXIT?

Inside a loop, `CHECK` skips an iteration if a condition is false, `CONTINUE` skips it directly, and `EXIT` ends the loop. Outside a loop, CHECK and EXIT can leave the processing block.

---


## Modularization and Function Modules

[Back to contents](#contents)

### Q56. What is modularization? What are its techniques?

Modularization means breaking a large program into smaller, reusable blocks. Instead of repeating logic, we put it in subroutines, function modules or methods. Includes, macros and dialog modules also help organize ABAP code.

### Q57. What is a subroutine? What are FORM and PERFORM?

A subroutine is a reusable block in classical ABAP. We define it with `FORM ... ENDFORM` and call it with `PERFORM`. USING passes inputs, while CHANGING passes values we may update.

**Syntax:**

```abap
PERFORM calculate USING 10 20 CHANGING lv_total.

FORM calculate USING iv_a TYPE i iv_b TYPE i
               CHANGING cv_total TYPE i.
  cv_total = iv_a + iv_b.
ENDFORM.
```

### Q58. What is a function module?

A function module is a reusable block that different ABAP programs can call. It belongs to a function group, has a defined interface, and is created or tested in SE37. We execute it using `CALL FUNCTION`.

### Q59. What are the parameters of a function module?

Function module parameters allow us to exchange data with the calling program.

- IMPORTING – input to the function module.
- EXPORTING – output from it.
- CHANGING – input and output.
- TABLES – legacy table interface.
- EXCEPTIONS – classical error handling.

In the caller, EXPORTING sends input and IMPORTING receives output.

**Syntax:**

```abap
CALL FUNCTION 'ZFM_CALCULATE'
  EXPORTING iv_amount = lv_amount
  IMPORTING ev_total  = lv_total
  EXCEPTIONS OTHERS = 1.
IF sy-subrc <> 0.
  " Handle the error
ENDIF.
```

### Q60. What is an include program?

An include helps us keep a large ABAP program organized. For example, TOP contains declarations and F01 contains subroutines. Includes become part of the main program rather than running on their own.

**Syntax:**

```abap
INCLUDE z_demo_top.
INCLUDE z_demo_f01.
```

The include programs must already exist.

### Q61. What is a method? How is it different from a function module?

A method is a block of logic inside a class. We use `->` for instance methods and `=>` for static methods. A function module belongs to a function group and uses `CALL FUNCTION`, while a subroutine normally uses `PERFORM` within a program.

**Syntax:**

```abap
METHODS calculate
  IMPORTING iv_a TYPE i iv_b TYPE i
  RETURNING VALUE(rv_total) TYPE i.

METHOD calculate.
  rv_total = iv_a + iv_b.
ENDMETHOD.
```

Declare the method in the class definition and write its logic in the implementation.

### Q62. What is a function group?

A function group is a container for related function modules. It lets them share global data and common routines. Each function module belongs to one group, which we can manage in SE80.

### Q63. What are the types of function modules?

There are three main types of function modules:

- **Normal:** Runs locally when called.
- **Remote-enabled:** Can be called through RFC, including from another system.
- **Update:** Runs registered update logic when the SAP transaction is committed.

---


## Object-Oriented ABAP

[Back to contents](#contents)

### Q64. What is a class and an object in ABAP?

A class is a blueprint that defines attributes and methods. An object is an instance of that class that we use at runtime. We can create global classes in SE24 or ADT.

**Syntax:**

```abap
CLASS lcl_demo DEFINITION.
  PUBLIC SECTION.
    METHODS display.
ENDCLASS.

CLASS lcl_demo IMPLEMENTATION.
  METHOD display.
    WRITE 'Hello SAP'.
  ENDMETHOD.
ENDCLASS.
```

Create an object with `DATA(lo_demo) = NEW lcl_demo( ).` and call `lo_demo->display( ).`.

### Q65. What are the four pillars of OOP in ABAP?

The four pillars of OOP help us organize and reuse code.

- **Encapsulation:** Protect data and control access through methods.
- **Inheritance:** Reuse and extend a parent class; ABAP supports single class inheritance.
- **Polymorphism:** Run different method implementations through a common reference.
- **Abstraction:** Expose essential behavior without showing the internal logic.

### Q66. What is the difference between PUBLIC, PROTECTED and PRIVATE?

PUBLIC, PROTECTED and PRIVATE control access to class members. PUBLIC allows outside access, PROTECTED allows access within the class and its subclasses, and PRIVATE normally limits access to the defining class.

### Q67. What is the difference between instance and static methods?

An instance method needs an object, so we call it with `->`. A static method belongs to the class itself and uses `=>`, without creating an object. Static attributes are shared within the internal session.

**Syntax:**

```abap
DATA(lo_service) = NEW zcl_service( ).
lo_service->process( ).
zcl_service=>get_version( ).
```

### Q68. What are a constructor, abstract class, final class and interface?

A constructor initializes an object; a class constructor runs once before the class is first used. An abstract class cannot be instantiated, and a final class cannot be inherited. An interface defines a contract that classes implement; ABAP allows multiple interfaces.

### Q69. What is method redefinition? Does ABAP support overloading?

Method redefinition lets a child class provide its own logic for an inherited method. The signature stays the same. ABAP does not support traditional method overloading, so we use optional parameters or different names.

**Syntax:**

```abap
CLASS lcl_child DEFINITION INHERITING FROM lcl_parent.
  PUBLIC SECTION.
    METHODS display REDEFINITION.
ENDCLASS.
```

### Q70. What is the difference between an abstract class and an interface?

An abstract class can contain shared implementation and attributes, but we cannot create an object of it directly. An interface defines a contract that implementing classes follow. ABAP supports one direct superclass and multiple interfaces.

### Q71. What is an event and an event handler in OO ABAP?

An event is a notification that something has happened in an object. An event handler is a method that responds to that event. We declare the event using `EVENTS`, trigger it using `RAISE EVENT` and connect the handler using `SET HANDLER`.

For example, an ALV grid raises a double-click event, and our handler method opens the selected record.


---


## Reports and Selection Screens

[Back to contents](#contents)

### Q72. What is a report in SAP ABAP? What are its types?

A report is an executable ABAP program that reads, processes and displays data. Classical reports use WRITE, interactive reports provide drill-down, and ALV reports offer features such as sorting and filtering.

### Q73. What are the important report events?

Report events are processing blocks triggered by SAP at different stages.

- `INITIALIZATION` – sets default values.
- `AT SELECTION-SCREEN OUTPUT` – changes the selection screen before display.
- `AT SELECTION-SCREEN` – validates input.
- `START-OF-SELECTION` – runs the main logic.
- `END-OF-SELECTION` – handles final processing.
- `TOP-OF-PAGE` / `END-OF-PAGE` – list headings and footers.
- `AT LINE-SELECTION` – handles interactive line selection.

**Syntax:**

```abap
INITIALIZATION.
  p_carr = 'LH'.

AT SELECTION-SCREEN.
  IF p_carr IS INITIAL.
    MESSAGE 'Enter an airline' TYPE 'E'.
  ENDIF.

START-OF-SELECTION.
  PERFORM get_data.
```

The example assumes the parameter and subroutine already exist.

### Q74. What is the difference between PARAMETERS and SELECT-OPTIONS?

`PARAMETERS` accepts one value, while `SELECT-OPTIONS` can accept multiple values, ranges and exclusions. SELECT-OPTIONS stores these in a selection table with SIGN, OPTION, LOW and HIGH, which we can use with `IN` in ABAP SQL.

**Syntax:**

```abap
DATA gv_carrid TYPE sflight-carrid.
PARAMETERS p_carr TYPE sflight-carrid.
SELECT-OPTIONS s_carr FOR gv_carrid.

SELECT carrid, connid FROM sflight
  WHERE carrid IN @s_carr
  INTO TABLE @DATA(lt_flights).
```

### Q75. What is an interactive report? What is HIDE?

An interactive report lets users select a record to see more details. The first output is the basic list, and further outputs are secondary lists. `AT LINE-SELECTION` handles selection, and `HIDE` stores values for the selected line.

### Q76. What is a report variant? Can it be used in a background job?

A report variant saves selection-screen input values so users do not have to enter them every time. It is also useful for scheduling reports with predefined inputs through SM36.

---


## ALV Reports

[Back to contents](#contents)

### Q77. What is ALV? Why do we use it?

ALV stands for ABAP List Viewer. It displays data in a ready-made list or grid with sorting, filtering, totals and export. The benefit is that we do not have to build these features ourselves.

### Q78. What are the types of ALV?

Classical ALV uses `REUSE_ALV_LIST_DISPLAY` or `REUSE_ALV_GRID_DISPLAY`. For object-oriented ALV, we use `CL_SALV_TABLE` for simple display and `CL_GUI_ALV_GRID` for editing or more control.

### Q79. What is a field catalog in ALV?

A field catalog tells ALV how to display each column, including its heading, length and editability. The internal table holds the actual data; the catalog controls how it looks.

**Syntax:**

```abap
DATA lt_fcat TYPE lvc_t_fcat.
APPEND VALUE #( fieldname = 'CARRID'
                coltext   = 'Airline'
                outputlen = 10 ) TO lt_fcat.
```

This example uses the OO Grid catalog type `LVC_T_FCAT`.

### Q80. How do you display a classical ALV grid?

I fetch the required records into an internal table, prepare the field catalog or a matching DDIC structure, and call `REUSE_ALV_GRID_DISPLAY` to show the result.

**Syntax:**

```abap
CALL FUNCTION 'REUSE_ALV_GRID_DISPLAY'
  EXPORTING i_structure_name = 'SFLIGHT'
  TABLES t_outtab = lt_flights.
```

The internal table must match the SFLIGHT structure in this example.

### Q81. What is SALV? How do you display data using it?

`CL_SALV_TABLE` is an object-oriented ALV class used mainly for displaying data. We pass the internal table to its FACTORY method, enable the required functions and call DISPLAY.

**Syntax:**

```abap
cl_salv_table=>factory(
  IMPORTING r_salv_table = DATA(lo_alv)
  CHANGING  t_table      = lt_data ).
lo_alv->get_functions( )->set_all( abap_true ).
lo_alv->display( ).
```

Handle the relevant SALV exception in the actual program.

### Q82. What is CL_GUI_ALV_GRID? How is it different from SALV?

`CL_GUI_ALV_GRID` is an object-oriented SAP GUI control for displaying and editing table data. I use it when a report needs more interaction or control than a simple SALV display.

**Syntax:**

```abap
lo_grid->set_table_for_first_display(
  EXPORTING i_structure_name = 'SFLIGHT'
  CHANGING  it_outtab        = lt_flights ).
```

Create the grid first. Use `REFRESH_TABLE_DISPLAY` after changing data and `CHECK_CHANGED_DATA` to collect pending user edits before saving.

### Q83. What is a custom container?

A custom container is an area on a SAP GUI screen where we display controls such as an ALV grid. We create the screen area in SE51 and connect it using `CL_GUI_CUSTOM_CONTAINER`.

**Syntax:**

```abap
IF lo_grid IS NOT BOUND.
  CREATE OBJECT lo_container
    EXPORTING container_name = 'CC_ALV'.
  CREATE OBJECT lo_grid
    EXPORTING i_parent = lo_container.
ENDIF.
```

Create the objects once in PBO. The custom control CC_ALV and object references must already be defined.

### Q84. How do you handle events in OO ALV?

OO ALV events let us respond to user actions like a double-click, a hotspot click or a data change. We define a handler method using `FOR EVENT`, implement its logic and register it using `SET HANDLER`. Classical ALV usually handles user commands through callback subroutines.

**Syntax:**

```abap
METHODS on_double_click
  FOR EVENT double_click OF cl_gui_alv_grid
  IMPORTING e_row e_column.
```

Implement the handler method in a local or global class and register it after creating the grid and handler object. The grid calls the method automatically when the event occurs.

### Q85. What is OO ALV? How is it different from classical ALV?

OO ALV is a class-based way of displaying data in SAP GUI. Classical ALV uses function modules and callbacks, while OO ALV uses classes, methods and event handlers. I prefer `CL_GUI_ALV_GRID` when I need more control over editing and user interaction.

### Q86. What are the main steps to develop an OO ALV grid?

I fetch the data into an internal table and prepare the field catalog and layout. Then I create the container and grid objects, register the required event handlers and call `SET_TABLE_FOR_FIRST_DISPLAY`. In a dynpro application, I normally create the controls only once in PBO.

### Q87. What are the common events in OO ALV?

These events help us respond to user actions on a grid:

- `DOUBLE_CLICK` – opens details for a selected cell or record.
- `HOTSPOT_CLICK` – handles a single click on a clickable column.
- `DATA_CHANGED` – validates edited values.
- `TOOLBAR` – adds or changes toolbar buttons.
- `USER_COMMAND` – handles custom function codes from the grid.

### Q88. How do you create and register an event handler class in OO ALV?

I define a local or global class with a method for the required grid event. After creating the handler object, I register its method using `SET HANDLER` for the grid instance. SAP then calls that method whenever the event occurs.

**Example: Double-click event handler**

```abap
CLASS lcl_handler DEFINITION.
  PUBLIC SECTION.
    METHODS on_double_click
      FOR EVENT double_click OF cl_gui_alv_grid
      IMPORTING e_row e_column.
ENDCLASS.

CLASS lcl_handler IMPLEMENTATION.
  METHOD on_double_click.
    MESSAGE 'Cell selected' TYPE 'S'.
  ENDMETHOD.
ENDCLASS.
```

**Registration (after the grid is created):**

```abap
DATA(lo_handler) = NEW lcl_handler( ).
SET HANDLER lo_handler->on_double_click FOR lo_grid.
```

Keep the grid and handler references available for the screen's lifetime. In a real handler, use the event's row and column information to identify the selected record correctly.

### Q89. What is the difference between a double-click and a hotspot click in ALV?

A double-click event occurs when the user clicks twice on a grid cell. A hotspot makes a particular column clickable with a single click. For example, I can mark a sales order number as a hotspot to open its details.

For an OO ALV field catalog entry, set `HOTSPOT = abap_true` and handle `HOTSPOT_CLICK`.

### Q90. What is an ALV layout? How is it different from a field catalog?

A layout controls the overall appearance and behavior of an ALV grid, such as alternating row colors or selection mode. A field catalog controls individual columns, including headings, visibility and editability. In OO ALV, we use `LVC_S_LAYO` for layout and `LVC_T_FCAT` for the field catalog.

### Q91. How do you make an OO ALV grid editable and validate user input?

I set the `EDIT` property for the required columns in the field catalog. Then I enable grid input as needed, register an edit event and handle `DATA_CHANGED` to validate values. Before saving, I call `CHECK_CHANGED_DATA` to collect pending edits and check whether they are valid.

**Syntax reminders:**

```abap
lo_grid->set_ready_for_input( i_ready_for_input = 1 ).
lo_grid->register_edit_event(
  i_event_id = cl_gui_alv_grid=>mc_evt_modified ).
lo_grid->check_changed_data( IMPORTING e_valid = DATA(lv_valid) ).
```

The field catalog and event handler must already be configured. Saving to the database is separate business logic, not an automatic ALV feature.

### Q92. What is the difference between SET_TABLE_FOR_FIRST_DISPLAY and REFRESH_TABLE_DISPLAY?

`SET_TABLE_FOR_FIRST_DISPLAY` initializes the grid with its data and display settings. Once the grid is displayed, `REFRESH_TABLE_DISPLAY` updates it when the internal table changes. We normally refresh the existing grid instead of creating it again.

```abap
lo_grid->refresh_table_display( ).
```

### Q93. How do you add a custom button to an OO ALV toolbar?

I handle the `TOOLBAR` event to add a button with a custom function code. When the user presses that button, the `USER_COMMAND` event lets me execute the related logic. For example, a custom button could open a detail screen or start a validation.


---


## Smart Forms

[Back to contents](#contents)

### Q94. What is a Smart Form?

Smart Forms is a SAP tool for designing documents such as invoices and purchase orders. We build the layout in SMARTFORMS, and activation generates a function module that our driver program calls.

### Q95. What are the main components of Smart Forms?

Smart Forms has an interface for passing data and global definitions for shared variables and logic. Pages and windows control the layout; the main window can flow across pages, while secondary windows stay in fixed areas. Tables, templates, text and graphics display the content.

### Q96. What is a driver program? How does a Smart Form work?

A driver program is an ABAP program that fetches and prepares data for a Smart Form. It calls the generated function module, and the form uses its layout to produce the document.

### Q97. Why do we use SSF_FUNCTION_MODULE_NAME?

`SSF_FUNCTION_MODULE_NAME` finds the generated function module for a Smart Form at runtime. Since the generated name can differ across SAP systems, we use this function instead of hard-coding the name.

**Syntax:**

```abap
CALL FUNCTION 'SSF_FUNCTION_MODULE_NAME'
  EXPORTING formname = 'ZSF_INVOICE'
  IMPORTING fm_name  = lv_fm_name
  EXCEPTIONS OTHERS  = 1.
```

```abap
IF sy-subrc = 0.
  CALL FUNCTION lv_fm_name
    EXPORTING is_header = ls_header.
ENDIF.
```

Use the actual form interface in the second call. IS_HEADER is an example parameter.

### Q98. What is the difference between SAPscript, Smart Forms and Adobe Forms?

SAPscript, Smart Forms and Adobe Forms are SAP document technologies. SAPscript is the older tool (SE71), Smart Forms provides a graphical designer and generated function module, and Adobe Forms focuses on PDF output (SFP).

---


## Module Pool Programming

[Back to contents](#contents)

### Q99. What is module pool programming?

Module pool programming is used to build interactive SAP GUI applications. It lets users enter, validate, change and save data across screens. We usually start the application through a dialog transaction.

### Q100. What is a dynpro? What are Screen Painter and Menu Painter?

A dynpro is a SAP GUI screen with fields, layout, attributes and flow logic. SE51 is where we design the screen, and SE41 is where we maintain its menus, toolbar and function codes.

### Q101. What are PBO and PAI? Explain screen flow logic.

PBO means Process Before Output, and PAI means Process After Input. PBO prepares the screen before display, while PAI handles user input and commands. Screen flow logic connects these events to ABAP modules.

**Syntax:**

```abap
PROCESS BEFORE OUTPUT.
  MODULE status_0100.
PROCESS AFTER INPUT.
  MODULE user_command_0100.
```

Implement PBO with `MODULE ... OUTPUT` and PAI with `MODULE ... INPUT` in the ABAP program.

### Q102. What are OK_CODE and SY-UCOMM?

`SY-UCOMM` is a system field that holds the current function code. `OK_CODE` is our own screen-linked variable for handling commands like SAVE or BACK. In PAI, I copy and clear OK_CODE before processing it.

**Syntax:**

```abap
MODULE status_0100 OUTPUT.
  SET PF-STATUS 'MAIN'.
ENDMODULE.

MODULE user_command_0100 INPUT.
  DATA(lv_command) = ok_code.
  CLEAR ok_code.
  CASE lv_command.
    WHEN 'BACK'.
      LEAVE TO SCREEN 0.
  ENDCASE.
ENDMODULE.
```

The screen must be linked to OK_CODE and the GUI status must define BACK.

### Q103. What is the difference between CALL SCREEN, SET SCREEN and LEAVE SCREEN?

These statements control screen navigation.

- `CALL SCREEN` – starts a nested screen sequence.
- `SET SCREEN` – sets the next screen.
- `LEAVE SCREEN` – leaves the current screen for the next one.
- `LEAVE TO SCREEN` – sets and leaves for the next screen.

Screen 0 ends the current screen sequence.

### Q104. What is CHAIN ... ENDCHAIN? What is LOOP AT SCREEN?

`CHAIN ... ENDCHAIN` groups related screen fields for validation in PAI. We use `LOOP AT SCREEN` with `MODIFY SCREEN` in PBO to change field properties such as visibility or input readiness.

**Syntax:**

```abap
CHAIN.
  FIELD gv_start.
  FIELD gv_end.
  MODULE validate_dates.
ENDCHAIN.
```

The example belongs under PROCESS AFTER INPUT in the screen flow logic.

### Q105. What are the main include programs in a module pool?

Includes divide a module pool into smaller parts so it is easier to read and maintain. Common naming conventions are:

| Include | Purpose |
|---|---|
| TOP | Global data, types, constants and screen variables |
| SEL | Selection-screen declarations, if the program uses them |
| F01 | FORM routines and reusable procedural logic |
| O01 | PBO modules (output processing) |
| I01 | PAI modules (input processing) |

These suffixes are conventions, not mandatory names. SEL is optional; normal dynpro fields are designed in SE51.

**Example main program:**

```abap
PROGRAM sapmz_student.
INCLUDE mz_student_top.
INCLUDE mz_student_sel.
INCLUDE mz_student_o01.
INCLUDE mz_student_i01.
INCLUDE mz_student_f01.
```

The named includes must exist. Omit SEL if no selection-screen declarations are needed.

### Q106. What is the difference between a report and a module pool?

A report is mainly used to retrieve, process and display data. A module pool is used to build interactive screens where users can enter, validate and save data. A report can also call screens, but a module pool is designed around dialog processing.

### Q107. How do you create a module pool application?

I create a type M program in SE80, define the global data and create screens in SE51. Then I write PBO and PAI modules, create the GUI status in SE41 and assign a dialog transaction in SE93.

### Q108. What are POV and POH in module pool programming?

POV (Process On Value-Request) handles custom F4 input help. POH (Process On Help-Request) handles custom F1 field help. Both are optional events in dynpro flow logic.

```abap
PROCESS ON VALUE-REQUEST.
  FIELD gv_id MODULE value_help.
PROCESS ON HELP-REQUEST.
  FIELD gv_id MODULE field_help.
```

### Q109. What is GUI status? What are SET PF-STATUS and SET TITLEBAR?

A GUI status defines the available menus, toolbar buttons and function codes. We create it in SE41 and normally set it in PBO using `SET PF-STATUS`. `SET TITLEBAR` sets the screen title.

### Q110. What is a table control in module pool programming?

A table control displays multiple records in rows and columns on a dynpro. It supports scrolling and user input. We use screen flow logic and ABAP modules to transfer data between the control and an internal table.

### Q111. How do you handle SAVE in a module pool?

In PAI, I check the SAVE function code and validate the entered data. Then I call the required business logic or update a custom table with proper authorization and locking, and commit only when the transaction is successful.

---


## Transactions, Packages and Transports

[Back to contents](#contents)

### Q112. What is a transaction code? How do you create one?

A transaction code is a shortcut to a SAP application or program. We create custom T-codes in SE93 by assigning a report or a module pool program with its starting screen.

### Q113. What is a package in SAP?

A package groups related SAP development objects, such as reports, classes and tables. It helps organize development and manage transports. We maintain packages in SE21 or SE80.

### Q114. What is a local package in SAP?

A local package, usually `$TMP`, keeps development objects in the current SAP system. It is useful for practice or testing without a normal transport request. To transport an object later, we assign it to a transportable package and record the change.

### Q115. What is a transport request? How do you release it?

A transport request records changes that need to move between SAP systems. We release the tasks first, then the main request in SE09 or SE10. STMS is used to import it into the target system.

### Q116. What are the types of transport requests?

A Workbench request carries development objects such as reports and classes. A Customizing request usually carries client-specific configuration. A Transport of Copies lets us move selected objects for testing without releasing the original request.

### Q117. What are the three main statuses of a transport request?

A transport request has three main statuses:

- **Modifiable:** We can still add or change objects.
- **Release Started:** SAP has started the release process.
- **Released:** The request is released and normally cannot be edited.

Released does not mean imported; we check imports in STMS.

### Q118. What is the difference between releasing and importing a transport request?

Releasing prepares a transport request to move out of the source system. Importing applies its changes in the target system. For example, releasing in DEV does not mean the object is already available in QAS.

---


## ABAP SQL and Performance

[Back to contents](#contents)

### Q119. What is Open SQL? How is it different from Native SQL?

Open SQL, now called ABAP SQL, is the standard way to read and change database data from ABAP. It works across supported databases and handles clients where applicable. Native SQL is database-specific.

### Q120. What is the difference between SELECT SINGLE and UP TO 1 ROWS?

`SELECT SINGLE` retrieves one matching record, usually using its full key. `UP TO 1 ROWS` with `ORDER BY` lets us choose a specific result, such as the latest record. Without a unique condition, SELECT SINGLE does not guarantee which row we get.

**Syntax:**

```abap
SELECT SINGLE carrname FROM scarr
  WHERE carrid = @p_carr INTO @DATA(lv_name).

SELECT fldate FROM sflight
  WHERE carrid = @p_carr
  ORDER BY fldate DESCENDING
  INTO @DATA(lv_date) UP TO 1 ROWS.
ENDSELECT.
```

### Q121. What are the types of joins in ABAP SQL?

The main join types differ in which rows they return:

| Join | What it returns |
|---|---|
| INNER JOIN | Only matching rows from both sources |
| LEFT OUTER JOIN | All left-side rows and matching right-side rows |
| RIGHT OUTER JOIN | All right-side rows and matching left-side rows |
| CROSS JOIN | Every possible combination of rows |

A full outer join is a general SQL concept, but it is not a direct ABAP SQL join type. Support for some newer join syntax depends on the ABAP release.

### Q122. What is the difference between INNER JOIN and LEFT OUTER JOIN?

An INNER JOIN keeps only matching records from both tables. A LEFT OUTER JOIN keeps every record from the left table, even if there is no match on the right. I choose based on whether unmatched records must appear.

**Syntax:**

```abap
SELECT a~carrid, a~carrname, b~connid
  FROM scarr AS a
  INNER JOIN spfli AS b ON b~carrid = a~carrid
  INTO TABLE @DATA(lt_result).
```

### Q123. What is the difference between ON and WHERE in a join?

`ON` defines how rows match, while `WHERE` filters the result. With a left outer join, filtering the right-side fields in WHERE can remove unmatched left-side rows. I place conditions based on which rows the requirement needs to retain.

### Q124. What is FOR ALL ENTRIES? What precautions should we take?

FOR ALL ENTRIES retrieves database records using keys already stored in an internal table. I always check that the table is not empty, because otherwise the WHERE condition is ignored. It also removes duplicate result rows.

**Syntax:**

```abap
IF lt_keys IS NOT INITIAL.
  SELECT carrid, connid FROM sflight
    FOR ALL ENTRIES IN @lt_keys
    WHERE carrid = @lt_keys-carrid
    INTO TABLE @DATA(lt_flights).
ENDIF.
```

### Q125. What is the difference between JOIN and FOR ALL ENTRIES?

A join combines database sources in one SQL query. FOR ALL ENTRIES uses values already available in an internal table to select matching records. I normally consider a join for database-to-database relationships and use FOR ALL ENTRIES when the driving keys are already in ABAP memory, after checking the table is not empty.

### Q126. What is an SAP LUW? What are COMMIT WORK and ROLLBACK WORK?

An SAP LUW (Logical Unit of Work) groups related changes into one business transaction. `COMMIT WORK` ends the LUW and triggers registered updates, while `ROLLBACK WORK` cancels pending changes. `COMMIT WORK AND WAIT` waits for high-priority updates; committed changes cannot be rolled back this way.

### Q127. What are INSERT, UPDATE, MODIFY and DELETE in ABAP SQL?

ABAP SQL uses `INSERT` to add, `UPDATE` to change, `MODIFY` to insert or update, and `DELETE` to remove database records. For SAP standard business data, I use the appropriate business API rather than directly changing tables.

**Syntax:**

```abap
INSERT zstudent FROM @ls_student.
UPDATE zstudent SET status = @lv_status WHERE id = @lv_id.
MODIFY zstudent FROM @ls_student.
DELETE FROM zstudent WHERE id = @lv_id.
```

These are separate examples for a custom table, not steps to run together.

### Q128. How do you improve ABAP performance?

To improve ABAP performance, I first measure the runtime using ST05 or SAT. I select only required fields and rows, avoid repeated SELECTs inside loops, use suitable joins and choose efficient internal table keys. I also avoid unnecessary data copies.

### Q129. What is AUTHORITY-CHECK? What are message types?

`AUTHORITY-CHECK` verifies whether a user has permission for an action; we check SY-SUBRC before allowing it. SAP message types are S (status), I (information), W (warning), E (error), A (termination) and X (runtime error). Message classes are maintained in SE91.

**Syntax:**

```abap
AUTHORITY-CHECK OBJECT 'S_TCODE'
  ID 'TCD' FIELD 'ZDEMO'.
IF sy-subrc <> 0.
  MESSAGE 'Not authorized' TYPE 'E'.
ENDIF.
```

This example checks only transaction authorization. Business operations need their own relevant checks.

### Q130. Why should you avoid SELECT inside LOOP?

It can make repeated database requests for every internal table row. I normally retrieve the required data in one suitable query using a join, CDS or FOR ALL ENTRIES, then process the results in memory. I measure performance before choosing the final approach.

---


## Core ABAP Debugging - SAP GUI

[Back to contents](#contents)

### Q131. What is debugging? What are breakpoints and watchpoints?

Debugging means following program execution to find the cause of an issue. A breakpoint stops at a chosen statement, and a watchpoint stops when a selected value changes, optionally with a condition. For runtime dumps, I check ST22.

### Q132. How do you start debugging in SAP GUI?

I can set a breakpoint in SE38 or SE80 and execute the program. For an active SAP GUI transaction, I can enter `/h` in the command field and trigger the next action to open the debugger.

### Q133. What are the types of breakpoints in ABAP?

A session breakpoint is used for execution in the current user session. An external breakpoint is useful when code runs in another session, such as an HTTP or RFC request. The `BREAK-POINT` statement is a breakpoint written directly in the code; avoid leaving it in productive code.

### Q134. What are F5, F6, F7 and F8 in the SAP GUI debugger?

| Key | Purpose |
|---|---|
| F5 | Single step (step into a called block) |
| F6 | Execute (step over a called block) |
| F7 | Return from the current processing block |
| F8 | Continue to the next breakpoint or end |

### Q135. How do you debug a module pool screen?

I set breakpoints in the PBO or PAI modules for the affected screen. For a button issue, I check the function code and OK_CODE in PAI; for a display issue, I check field values and attributes in PBO.

### Q136. What is update debugging?

Update debugging lets us debug a function module registered with `IN UPDATE TASK`. We enable the debugger's update-debugging option before the relevant commit and follow the update execution. SM13 helps us investigate failed update requests.

### Q137. What is ST22 and how do you analyze a short dump?

ST22 displays ABAP runtime errors. I check the error description, affected program, source line, call stack and relevant variables. Then I reproduce the issue and fix the actual cause.

### Q138. What is the difference between ST05, SAT and the debugger?

ST05 traces database access and SQL performance. SAT measures ABAP runtime and identifies expensive processing blocks. The debugger lets us inspect program execution and data step by step to find logic errors.

### Q139. A user receives an authorization error. How would you investigate it?

I ask the user to reproduce the issue and check SU53 immediately afterward. If needed, I coordinate an authorization trace with the security team and review the relevant AUTHORITY-CHECK. I do not bypass the authorization logic.

---


## Enhancements, Interfaces and Data Migration

[Back to contents](#contents)

### Q140. What are enhancements, user exits, customer exits and BAdIs?

Enhancements add custom logic to SAP standard processes without directly changing standard code. User exits are older application-specific options, customer exits are SAP-provided options (SMOD/CMOD), and BAdIs are object-oriented enhancements (SE18/SE19).

### Q141. What is a BAdI?

A BAdI (Business Add-In) is an object-oriented enhancement option in SAP. It lets us add custom business logic without changing the original SAP code. For example, we can add a purchase order validation at a suitable BAdI.

### Q142. What is the difference between a BAdI definition and implementation?

The BAdI definition describes the available methods and properties. The implementation contains the custom code that runs when the BAdI is called. We inspect the definition in SE18, then create, code and activate the implementation in SE19.

### Q143. What is a filter-dependent BAdI?

A filter-dependent BAdI selects implementations based on filter values. For example, a country filter can select different validation logic for India and Germany. We define matching filter conditions in the implementation.

### Q144. What are implicit and explicit enhancements?

Implicit enhancements are available at predefined locations, such as the beginning or end of certain procedures. Explicit enhancements are deliberately provided in the code through enhancement points or sections. I prefer supported, released extension options when they meet the requirement.

### Q145. How do you find and debug a BAdI?

I check the application documentation, enhancement definitions and relevant standard code for BAdI calls. Then I set a breakpoint in the implementation method and run the business process. If it does not stop, I check activation, filters and whether the application reaches that calling point.

### Q146. What is the difference between RFC and BAPI?

RFC (Remote Function Call) allows us to call remote-enabled function modules. A BAPI (Business Application Programming Interface) provides a defined business operation, such as creating a document. Many BAPIs support RFC, but not every RFC is a BAPI; we follow the BAPI's commit and error-handling rules.

### Q147. What is RFC?

RFC (Remote Function Call) is SAP's mechanism for calling remote-enabled function modules. We use it to exchange data or execute functions between systems, or in a separate RFC context within the same system.

### Q148. What is an RFC destination? What is SM59?

An RFC destination defines how SAP connects to another system or service. We maintain connection settings and run connection tests in SM59. A successful connection test does not by itself confirm business authorizations.

### Q149. What are the different types of RFC?

RFC supports different ways of calling functions depending on timing and reliability.

- **sRFC:** The caller waits for the response.
- **aRFC:** The caller continues while the function runs separately.
- **tRFC:** Stores transactional calls for reliable execution and retry.
- **qRFC:** Adds queue-based ordering to transactional calls.
- **bgRFC:** A newer background communication mechanism supporting transactional or queued processing.

### Q150. What is a BAPI?

A BAPI (Business Application Programming Interface) is a defined SAP business interface for operations such as creating a purchase order or reading customer details. Traditional BAPIs are implemented as RFC-enabled function modules. We use suitable supported BAPIs to work with business data through SAP's own logic.

### Q151. What are some commonly used BAPIs?

Examples in classical SAP systems include `BAPI_PO_CREATE1` for purchase orders, `BAPI_SALESORDER_CREATEFROMDAT2` for sales orders and `BAPI_MATERIAL_SAVEDATA` for material data. I select the API based on the business requirement and confirm it is supported in the target system.

### Q152. What is BAPIRET2? Why do we check RETURN?

BAPIRET2 is a standard structure used by many BAPIs to return messages. It contains fields such as TYPE, ID, NUMBER and MESSAGE. I check the return messages for errors or aborts, even if the function call itself completes successfully.

### Q153. Why do we use BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK?

Many change BAPIs leave the transaction open so the caller can decide whether to save. We call `BAPI_TRANSACTION_COMMIT` after successful processing or `BAPI_TRANSACTION_ROLLBACK` on failure, according to the BAPI documentation. For remote calls, transaction handling must use the same appropriate RFC context.

### Q154. How do you call a BAPI and handle errors?

I fill the required input structures and tables, call the BAPI and check its RETURN messages. If processing succeeds, I commit when required; otherwise, I roll back and report the errors.

```abap
" Example: after a change BAPI returns a BAPIRET2 table
IF line_exists( lt_return[ type = 'E' ] ) OR
   line_exists( lt_return[ type = 'A' ] ) OR
   line_exists( lt_return[ type = 'X' ] ).
  CALL FUNCTION 'BAPI_TRANSACTION_ROLLBACK'.
ELSE.
  CALL FUNCTION 'BAPI_TRANSACTION_COMMIT'
    EXPORTING wait = abap_true
    IMPORTING return = ls_commit_return.
ENDIF.
```

This is a local transaction-handling example, not a complete BAPI program. Check the actual BAPI requirements, commit response and any relevant warnings; use matching remote context for a remote transaction.

### Q155. What is the difference between a BAPI and a BAdI?

A BAPI lets us call a defined business operation, while a BAdI lets us extend an existing business operation. For example, a BAPI can create a purchase order, and a suitable BAdI can add a custom check during that process.

### Q156. What is an IDoc? What are ALE and EDI?

An IDoc (Intermediate Document) is a standard format for exchanging business data, often asynchronously. It contains control, data and status records. ALE distributes data between SAP systems, EDI exchanges documents between organizations, and WE02/WE05 show IDoc status.

### Q157. What is BDC? How is it different from BAPI?

BDC (Batch Data Communication) automates data entry through classical SAP screens, using session processing (SM35) or CALL TRANSACTION. A BAPI uses a business interface instead of screens, so I prefer a suitable supported BAPI when available.

### Q158. What is the difference between BDC session method and CALL TRANSACTION?

The session method creates a batch-input session that can be processed and monitored in SM35. CALL TRANSACTION runs the transaction directly from ABAP and can collect messages immediately. Both depend on classical screen behavior.

---


## Modern ABAP

[Back to contents](#contents)

### Q159. What is modern ABAP?

Modern ABAP uses newer language features such as inline declarations, constructor expressions and table expressions. The idea is to write clearer code with fewer unnecessary statements. Feature availability depends on the SAP release.

### Q160. What is an inline declaration?

An inline declaration creates a variable right where we need it. ABAP determines the type automatically, so we do not need a separate declaration in many cases.

**Syntax:**

```abap
DATA(lv_name) = 'SAP'.
SELECT carrid, connid FROM spfli
  INTO TABLE @DATA(lt_connections).
LOOP AT lt_connections INTO DATA(ls_connection).
  " Process one row
ENDLOOP.
```

### Q161. What are VALUE, NEW and CONV?

VALUE, NEW and CONV are constructor operators. VALUE builds data values, NEW creates objects or anonymous data and returns a reference, and CONV converts values to another type. We use `#` when ABAP can infer the required type; otherwise, we specify it.

**Syntax:**

```abap
DATA(lt_numbers) = VALUE int4_table( ( 10 ) ( 20 ) ).
DATA(lv_text) = CONV string( 100 ).
```

### Q162. What is a table expression? How is it different from READ TABLE?

A table expression is a short way to access a row by index or key. Unlike READ TABLE, it does not set SY-SUBRC and normally raises an exception if the row is missing. We can handle that using LINE_EXISTS, OPTIONAL or exception handling.

**Syntax:**

```abap
IF line_exists( lt_items[ id = 10 ] ).
  DATA(ls_item) = lt_items[ id = 10 ].
ENDIF.
```

### Q163. What are COND and SWITCH?

`COND` returns a value based on conditions, like IF/ELSE. `SWITCH` returns a value by matching an input, like CASE. Both make assignments more concise.

**Syntax:**

```abap
DATA(lv_result) = COND string(
  WHEN lv_marks >= 40 THEN 'Pass'
  ELSE 'Fail' ).
```

### Q164. What are FOR, REDUCE and FILTER?

`FOR` loops through values inside an expression, `REDUCE` combines values into a result such as a total, and `FILTER` selects rows from an internal table using supported key conditions. We use them to write shorter table-processing logic.

**Syntax:**

```abap
DATA(lt_double) = VALUE int4_table(
  FOR n IN lt_numbers ( n * 2 ) ).

DATA(lv_total) = REDUCE i(
  INIT sum = 0 FOR n IN lt_numbers
  NEXT sum = sum + n ).
```

The examples assume an integer internal table named lt_numbers.

### Q165. What is CORRESPONDING?

`CORRESPONDING` copies matching fields between structures or tables into a new result. We use it instead of assigning each field manually. MAPPING handles different field names; MOVE-CORRESPONDING updates an existing target.

**Syntax:**

```abap
ls_target = CORRESPONDING #( ls_source ).
```

### Q166. What is modern ABAP SQL?

Modern ABAP SQL provides features such as inline declarations, expressions, joins and database calculations. The `@` symbol identifies ABAP host variables. We use these features to simplify data access and processing.

**Syntax:**

```abap
SELECT carrid, COUNT( * ) AS flight_count
  FROM sflight
  GROUP BY carrid
  INTO TABLE @DATA(lt_counts).
```

### Q167. How do you handle exceptions in modern ABAP?

Class-based exception handling lets us manage runtime problems using `TRY ... CATCH`. We put the risky statement inside TRY and handle expected exceptions in CATCH so the program can respond appropriately.

**Syntax:**

```abap
TRY.
    DATA(ls_item) = lt_items[ id = 10 ].
  CATCH cx_sy_itab_line_not_found.
    " Handle the missing row
ENDTRY.
```

### Q168. What are string templates in modern ABAP?

String templates let us combine text, variables and expressions inside `|...|`. We use them instead of several CONCATENATE statements, and they also support formatting.

```abap
DATA(lv_text) = |Material: { lv_matnr }|.
```

---


## SAP HANA, CDS and AMDP

[Back to contents](#contents)

### Q169. What is SAP HANA? How is it different from S/4HANA?

SAP HANA is an in-memory database designed for fast data processing and analytics. S/4HANA is the ERP business suite that runs on HANA. HANA stores and processes data, while S/4HANA handles business processes.

### Q170. What is code pushdown?

Code pushdown means letting the database do suitable processing instead of bringing all the raw data into ABAP. We perform filtering, joins or calculations near the data and return only the required results. CDS, ABAP SQL and AMDP help us do this.

### Q171. What is CDS? How is it different from a classical DDIC view?

CDS stands for Core Data Services. It helps us create reusable data models with joins, associations, annotations and calculations. Compared with a classical DDIC view, it provides richer modeling features and is developed in ADT.

**Syntax:**

```sql
@EndUserText.label: 'Airline connections'
@AccessControl.authorizationCheck: #NOT_REQUIRED
define view entity ZI_Connection
  as select from spfli
{
  key carrid,
  key connid,
      cityfrom,
      cityto
}
```

This is CDS DDL, written in ADT, not inside a report. Use appropriate authorization settings in real applications. We can read the activated entity using ABAP SQL:

```abap
SELECT carrid, connid FROM zi_connection
  WHERE carrid = @lv_carr
  INTO TABLE @DATA(lt_connections).
```

### Q172. What is DCL in CDS?

DCL (Data Control Language) defines access rules for CDS data. We use it to restrict which records a user can see based on authorization. DDL defines the data model; DCL controls read access, while other operations may need separate checks.

### Q173. What is AMDP? How is it different from CDS?

AMDP (ABAP Managed Database Procedures) lets us write database-specific logic, such as HANA SQLScript, in an ABAP class method. CDS mainly models data, while AMDP is useful for more complex database-side processing.

---


## CDS Views - Important Interview Questions

[Back to contents](#contents)

### Q174. What is the difference between DEFINE VIEW and DEFINE VIEW ENTITY?

`DEFINE VIEW` is the older CDS syntax and requires a separate SQL view name through `@AbapCatalog.sqlViewName`. `DEFINE VIEW ENTITY` is the newer approach and does not generate a separate DDIC SQL view. SAP recommends view entities for new development where supported.

### Q175. What are basic, composite and consumption CDS views?

These are common layers in SAP's Virtual Data Model (VDM). A basic view reads data from underlying sources, a composite view combines reusable models, and a consumption view prepares data for a particular reporting or application requirement. They are modeling roles, not mandatory CDS syntax types.

### Q176. What is an interface view and a projection view?

An interface view provides a reusable data model with business fields and relationships. A projection view exposes only the parts required by a particular service or application. We often use names such as `ZI_` and `ZC_` as conventions in RAP projects.

### Q177. What is the difference between a join and an association in CDS?

A join directly combines data sources in the query. An association defines a reusable relationship, which can be exposed and followed when related fields are needed. When we follow it to retrieve data, CDS generally generates a join.

### Q178. What is cardinality in a CDS association?

Cardinality tells us how many target records can match a source record. For example, `[0..1]` means zero or one and `[0..*]` means zero or many. I define it based on the actual data relationship, not just to improve performance.

### Q179. What is the difference between association and composition in CDS?

An association defines a reusable relationship between entities. A composition is a special association that defines a parent-child relationship where the child depends on its parent for its existence. In RAP, we use composition to build the business object hierarchy and ordinary associations to connect related entities outside that ownership relationship.

| Association | Composition |
|---|---|
| General relationship | Parent-child ownership relationship |
| No ownership implied | Child belongs to the parent |
| Example: Sales order → Customer | Example: Sales order → Order items |

### Q180. How do you define an association in CDS?

We define the target, cardinality, alias and matching condition, then expose the association if consumers need it. For example, an order can expose its customer details through `_Customer`.

```sql
association [0..1] to ZI_Customer as _Customer
  on $projection.CustomerID = _Customer.CustomerID
```

Include `_Customer` in the element list to expose it. The example assumes existing CDS entities and matching fields.

### Q181. What are some important CDS annotations?

Annotations describe how a CDS model should be interpreted by SAP frameworks and tools.

| Annotation | Purpose |
|---|---|
| `@EndUserText.label` | Readable description |
| `@AccessControl.authorizationCheck` | CDS access control handling |
| `@UI.lineItem` | Fields shown in a Fiori elements list |
| `@Semantics.amount.currencyCode` | Links an amount to its currency field |
| `@Consumption.valueHelpDefinition` | Defines value help for supported consumers |
| `@Metadata.allowExtensions` | Permits metadata extensions |

A metadata extension keeps supported annotations, such as UI settings, separate from the data definition.

---


## RAP, OData, Fiori and ABAP Cloud

[Back to contents](#contents)

### Q182. What is RAP?

RAP stands for ABAP RESTful Application Programming Model. We use it to build modern business applications and services in ABAP. CDS defines the data, behavior defines the business operations, and service bindings expose the application through protocols such as OData.

### Q183. What are the main components of RAP?

RAP has five main components:

- **CDS model:** Defines the root entity, its child entities and relationships.
- **Behavior definition:** Defines allowed operations.
- **Behavior implementation:** Holds custom business logic.
- **Service definition:** Selects entities to expose.
- **Service binding:** Exposes them through a protocol such as OData.

**Syntax:**

```sql
define service ZUI_Travel {
  expose ZC_Travel as Travel;
}
```

Create the projection entity and service binding separately in ADT.

### Q184. What is the difference between managed and unmanaged RAP?

In managed RAP, the framework handles standard create, update, delete, buffering and saving, so we focus on business rules. In unmanaged RAP, we implement the required operations and save logic ourselves. I would choose unmanaged when existing business logic needs to be reused.

### Q185. What is a behavior definition and behavior implementation in RAP?

A behavior definition tells RAP what a business object can do, such as create, update, delete or approve. The behavior implementation is where we write the custom ABAP logic for actions, validations and other operations.

### Q186. What is the difference between service definition and service binding?

A service definition decides what data and entities to expose. A service binding decides how clients access them, such as through OData V4. In RAP, we expose the CDS projection in a service definition and publish it through the service binding. UI annotations help Fiori elements display the data.

### Q187. What is draft in RAP?

Draft in RAP allows users to save unfinished changes separately from active business data. They can continue editing later and activate the draft when it is ready.

### Q188. What are locking and ETags in RAP?

Locking helps prevent conflicting changes when multiple users edit a record. An ETag checks whether the record has changed since a user last read it. Together, they help avoid overwriting newer data.

### Q189. What are validations, determinations and actions in RAP?

Validations check whether data is correct, determinations automatically calculate or fill values, and actions carry out a business operation. For example, an action can approve an order.

### Q190. What is EML in RAP?

EML (Entity Manipulation Language) is used to access RAP business objects from ABAP. We use READ ENTITIES or MODIFY ENTITIES to work through the defined business behavior instead of directly changing database tables.

**Syntax:**

```abap
READ ENTITIES OF zi_travel
  ENTITY Travel
  ALL FIELDS WITH VALUE #( ( TravelID = lv_id ) )
  RESULT DATA(lt_travel)
  FAILED DATA(ls_failed).
```

The example assumes an existing RAP business object with the specified entity and key.

### Q191. What is OData? What is SAP Fiori?

OData (Open Data Protocol) is a standard way to expose and consume data services over HTTP. SAP Fiori is SAP's modern, role-based user experience. Fiori apps can use OData services to read and update business data.

### Q192. What are ADT, ABAP Cloud and Clean Core?

ADT is the Eclipse-based development tool for ABAP, CDS and RAP. ABAP Cloud is a development model that uses released APIs and restricted language versions. Clean Core means avoiding unnecessary changes to standard SAP and using supported extensions.

---


## Modern ABAP Debugging - ADT, CDS and RAP

[Back to contents](#contents)

### Q193. How do you debug modern ABAP in Eclipse ADT?

I open the source code in ADT, set a breakpoint and execute the program or trigger the related application. When the breakpoint is reached, the Debug perspective opens and I can inspect variables, internal tables and the call stack.

### Q194. How do you debug a Fiori or OData request?

I set an external-capable breakpoint in the relevant backend ABAP method or RAP handler and trigger the request from the application. I make sure the breakpoint is for the actual backend user and system, with the required authorization.

### Q195. Can we debug a CDS view? How do you troubleshoot incorrect results?

A normal CDS view is a database query, so we cannot step through it like ABAP code. I use Data Preview to check the source data, filters, joins, cardinality and authorizations. If needed, I use SQL traces to investigate further.

### Q196. How do you debug RAP business logic?

I set a breakpoint in the relevant behavior implementation method, such as a validation, determination or action. Then I trigger the operation from Fiori, a service request or EML and inspect the input keys and business data.

### Q197. Why might an ADT breakpoint not be triggered?

I check whether the correct system, user and active code are being used and whether the application actually reaches that logic. For HTTP or RFC requests, I also check the execution user and breakpoint settings.

---


## ATC Checks and Code Quality

[Back to contents](#contents)

### Q198. What is ATC in SAP ABAP?

ATC stands for ABAP Test Cockpit. It checks our code for errors, performance issues, security risks and compatibility problems, depending on the check variant. I run it in ADT or supported SAP GUI tools, fix the findings and recheck before release.

### Q199. What is an ATC check variant?

An ATC check variant is a collection of checks that ATC should perform. We choose the variant based on the project's needs, such as general code quality or S/4HANA readiness.

### Q200. What are ATC priority levels and exemptions?

ATC findings usually have priorities 1, 2 and 3, with 1 being the highest. We fix issues according to the project's release rules. If a finding does not apply or cannot be fixed reasonably, we may request a justified, approved exemption where supported.

### Q201. What is the difference between SCI, ATC and ABAP Unit?

SCI checks code for quality issues, while ATC adds centralized checks and finding management, including transport checks where configured. ABAP Unit runs automated tests to check whether our program logic returns the expected results. These tools complement each other.

---


## SAP Fundamentals

[Back to contents](#contents)

### Q202. What is SAP? What is ERP?

SAP provides software for managing business processes. ERP stands for Enterprise Resource Planning. It connects areas like finance, sales, purchasing and production so they can work with shared business data.

### Q203. What is the difference between SAP ECC and SAP S/4HANA?

SAP ECC is the older ERP suite that can run on different supported databases. S/4HANA is the newer ERP suite designed for HANA, with a simpler data model and modern technologies such as Fiori.

### Q204. What are the main SAP functional modules?

SAP functional modules support specific business processes. For example, MM handles purchasing, SD handles sales, and FI handles accounting.

| Module | Full form / purpose |
|---|---|
| FI | Financial Accounting – accounts, payments and financial statements |
| CO | Controlling – internal costs and profitability |
| MM | Materials Management – purchasing and inventory |
| SD | Sales and Distribution – sales orders, deliveries and billing |
| PP | Production Planning – planning and managing production |
| QM | Quality Management – quality inspections |
| PM | Plant Maintenance – maintenance of equipment and plants |
| HCM | Human Capital Management – employee-related processes |
| EWM | Extended Warehouse Management – warehouse operations |

### Q205. What are functional and technical (non-functional) areas in SAP?

Functional areas support business processes, while technical areas help develop, maintain, secure and integrate SAP systems. Technical areas is a more accurate term than non-functional modules.

| Technical area | Purpose |
|---|---|
| ABAP | Develop reports, interfaces, forms and applications |
| SAP Basis | Install, configure and maintain SAP systems |
| SAP Security / Authorizations | Manage user access and roles |
| SAP Fiori / SAPUI5 | Build modern user interfaces |
| SAP BTP / Integration Suite | Extend applications and connect systems |

### Q206. What is the difference between an SAP functional consultant and an ABAP technical consultant?

A functional consultant understands business requirements and configures SAP processes. An ABAP technical consultant builds the required programs, interfaces or enhancements. For example, the MM consultant defines a purchase order report and the developer builds it.

### Q207. What are functional and non-functional requirements in SAP?

Functional requirements define what an application must do, such as displaying purchase orders. Non-functional requirements define how well it must work, such as performance, security, reliability and usability.

### Q208. What is SAP three-tier architecture?

SAP three-tier architecture divides a system into three layers:

- **Presentation:** SAP GUI or browser used by the user.
- **Application:** Runs ABAP logic and processes requests.
- **Database:** Stores and retrieves business data, using HANA in S/4HANA.

A request goes from the screen to the application server, which reads the database and returns the result.

**Simple flow:**

```text
Presentation Layer (SAP GUI / Browser)
                 ↕
Application Layer (ABAP / Business Logic)
                 ↕
Database Layer (Data Storage)
```

### Q209. What is an SAP system landscape? How is it different from three-tier architecture?

An SAP landscape is a group of systems used for different stages of development.

- **DEV:** Create and change objects.
- **QAS:** Test changes.
- **PRD:** Run live business operations.

We move approved changes through transports instead of directly changing production. A landscape describes separate systems, while three-tier architecture describes the layers within a system.

**Transport flow:**

```text
DEV (Develop) → QAS (Test) → PRD (Go Live)
```

### Q210. What is the difference between master data and transaction data?

Master data is reusable business information, such as customer, supplier and material details. Transaction data records business activities, such as purchase orders, sales orders and invoices.

### Q211. What are some important SAP standard tables?

Common SAP tables include MARA (material), MARC (plant-level material), MAKT (material description), EKKO/EKPO (purchase order header/items), and VBAK/VBAP (sales document header/items). We use them based on the business data needed.

### Q212. What is RICEFW? Explain its objects with examples.

RICEFW stands for Reports, Interfaces, Conversions, Enhancements, Forms and Workflows. We use it to classify SAP development requirements. RICEF omits workflows; WRICEF uses a different order for the same six areas.

| Object | Purpose and example |
|---|---|
| Report | Display business data, such as an ALV purchase order report |
| Interface | Exchange data with another system using RFC, IDoc or OData |
| Conversion | Migrate data, such as legacy material master records |
| Enhancement | Add custom logic, such as a BAdI validation |
| Form | Generate documents, such as a Smart Form invoice or Adobe Form |
| Workflow | Automate tasks, such as a purchase order approval |

### Q213. What is the difference between functional and technical specifications?

A functional specification explains what the business needs and the expected result. A technical specification explains how we will build it, including tables, logic and technical objects.

### Q214. What is a background job?

A background job runs an ABAP program without requiring the user to keep a screen open. We use it for long-running or scheduled tasks. SM36 schedules jobs and SM37 monitors them.

### Q215. What is SAP BTP?

SAP BTP (Business Technology Platform) provides services for application development, integration, data, analytics and automation. We use it to extend SAP applications and connect systems, including supported cloud ABAP development.

---


## SAP Implementation and S/4HANA Migration

[Back to contents](#contents)

### Q216. What is the difference between Greenfield and Brownfield?

Greenfield is a fresh SAP implementation where we redesign processes and migrate selected data. Brownfield converts an existing SAP ERP system to S/4HANA while retaining much of its data and configuration. The choice depends on what the business wants to retain or change.

### Q217. What is the difference between an implementation, rollout and support project?

An implementation project sets up or converts a SAP solution. A rollout extends an existing solution to another location or business unit. A support project maintains the live system, fixes issues and delivers approved improvements.

### Q218. What is Clean Core and why is it important?

Clean Core means keeping the SAP standard as clean as possible by using supported extension options. We prefer released APIs and BAdIs over direct standard-code changes. That makes upgrades and maintenance easier.

---


## Practical SAP ABAP Interview Questions

[Back to contents](#contents)

### Q219. How would you handle a production issue?

I would collect the issue details and check logs, dumps, data and authorizations. After reproducing the issue in a test system, I would fix the cause, test the solution and follow the approved transport process.

### Q220. What would you do if a report shows no data?

I would check selection values, client, authorizations and whether the data exists. Then I would debug the SELECT statement and filtering logic to find where records are being lost, without bypassing necessary checks.

### Q221. How would you design a report showing purchase order headers and items?

I would confirm the selection criteria and output with the functional consultant. In classical ABAP, I can read EKKO and EKPO using a suitable join, select only required fields and display the result in ALV. For modern development, I would check for suitable released CDS entities or APIs first.

### Q222. How would you add a custom validation to a standard purchase order transaction?

I would identify a supported enhancement point or BAdI for the requirement, check its interface, and implement the validation without modifying SAP standard. I would test both valid and invalid cases and run ATC before transporting the change.

---


## Personal Interview Questions - SAP ABAP

[Back to contents](#contents)

These are sample fresher answers. Adapt them to your real experience, training and projects; do not claim work or skills you have not actually completed.

### Q223. Tell me about yourself as an SAP ABAP fresher.

I am a [degree/branch] student or graduate with an interest in software development and business applications. I have been learning SAP ABAP, including [topics you have actually practiced]. I am looking for an opportunity to apply my knowledge and grow as an ABAP developer.

### Q224. Why did you choose SAP ABAP?

What drew me to SAP ABAP is that the code has a direct connection to business processes. I like the idea of turning a business requirement into a working solution, and I want to build on that with CDS and RAP.

### Q225. Why should we hire you as an SAP ABAP fresher?

As a fresher, I bring a willingness to learn and a practical approach to problem-solving. I focus on understanding the requirement and writing clear code, and I am open to feedback from experienced developers.

### Q226. How would you explain your SAP ABAP project or practice assignment?

I worked on [actual project or practice assignment] to solve [requirement]. I used [actual SAP objects or tools] to implement the logic and tested it using [actual test cases]. The main thing I learned was [genuine learning or challenge].

### Q227. Why do you want to join HCLTech for an SAP ABAP role?

I am interested in HCLTech because its SAP work covers core ABAP and modern S/4HANA development. I want to apply my technical foundation to real business requirements, learn from experienced teams and grow into a capable SAP developer.

---


## Quick Revision – Important T-Codes

[Back to contents](#contents)

| T-Code | Purpose |
|---|---|
| SE11 | ABAP Dictionary |
| SE38 | ABAP Editor / executable programs |
| SE80 | Object Navigator |
| SE21 | Package Builder |
| SE37 | Function Builder |
| SE24 | Class Builder |
| SE51 | Screen Painter |
| SE54 | Table maintenance generator |
| SM30 | Maintain table / view entries |
| SE41 | Menu Painter |
| SE93 | Transaction maintenance |
| SMARTFORMS | Smart Forms |
| SFP | Adobe Forms |
| SE09 / SE10 | Transport Organizer |
| STMS | Transport Management System |
| SE91 | Message maintenance |
| ST22 | Runtime errors / dumps |
| ST05 | SQL trace |
| ATC | ABAP Test Cockpit / code quality checks |
| SCI | Code Inspector |
| SAT | Runtime analysis |
| SU53 | Recent failed authorization check information |
| SE18 / SE19 | BAdI definitions / implementations |
| SMOD / CMOD | Classical customer enhancements |
| SE16N | Table data display (subject to authorization) |
| SPRO | Implementation Guide / customizing |
| PFCG | Role maintenance |
| SM36 / SM37 | Background job scheduling / monitoring |
| SM35 | Batch input sessions |
| WE02 / WE05 | IDoc monitoring |
| SM59 | RFC destination maintenance |
| BAPI | BAPI Explorer |
| SM58 | Transactional RFC monitoring |
| SMQ1 / SMQ2 | Outbound / inbound qRFC queues |
| SBGRFCMON | Background RFC monitoring |
| SM12 | Lock entry monitoring |
| SM13 | Update request monitoring |
| SLG1 | Application log display |
| SE54 | Table maintenance generator / maintenance objects |
| SHDB | BDC transaction recording |
| BD87 | IDoc status monitoring and supported reprocessing |
| SP01 | Spool request monitoring |
| /IWFND/ERROR_LOG | SAP Gateway frontend error log (where available) |
| /IWBEP/ERROR_LOG | SAP Gateway backend error log (where available) |

---


## Final revision checklist

[Back to contents](#contents)

1. **Core:** DDIC, internal tables, modularization, reports, ALV (including OO ALV and event handlers), Smart Forms, dynpro, SQL and SAP GUI debugging.
2. **Integration:** BAPI, BAdI, RFC, IDoc and RICEFW.
3. **Modern:** inline syntax, CDS, associations and composition, AMDP, RAP, ADT debugging and ATC.
4. **Interview practice:** explain a real practice project, solve a simple SQL or internal-table problem, and explain how you would troubleshoot an issue.

Practice syntax separately and adapt personal answers to your real experience.

---


## Official SAP references for the added topics

[Back to contents](#contents)

- [ATC for developers](https://help.sap.com/docs/ABAP_PLATFORM_NEW/ba879a6e2ea04d9bb94c7ccd7cdac446/145568d2a3434ef5bf8352c74853c5eb.html)
- [ATC check variants](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/selecting-atc-check-variant)
- [RAP standard behavior](https://help.sap.com/docs/abap-cloud/abap-rap/defining-standard-behavior)
- [SAP Selective Data Transition](https://support.sap.com/en/offerings-programs/support-services/data-management-landscape-transformation/selective-data-transition-engagement.html)
- [SAP Transport Organizer and request statuses](https://help.sap.com/docs/abap-cloud/abap-development-tools-for-visual-studio-code/transport-organizer)
- [SAP transport release and import process](https://help.sap.com/docs/SAP_NETWEAVER_AS_ABAP_751_IP/4a368c163b08418890a406d413933ba7/0e70a0ed3b6943de93b083496b0f42a0.html)

### References for this expansion

- [SAP Dictionary view types](https://help.sap.com/docs/SAP_NETWEAVER_AS_ABAP_FOR_SOH_740/ec1c9c8191b74de98feb94001a95dd76/cf21ec5d446011d189700000e8322d00.html?locale=en-US&state=PRODUCTION&version=7.40.30)
- [SAP dynpro flow logic](https://help.sap.com/docs/SAP_NETWEAVER_700/a85596deeb19418982bee031d1fd1427/4a43f2175bc52baee10000000a421937.html)
- [SAP CDS view entities](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/8b3e8e8b8797432abecd7d1fbb6d5c12.html)
- [SAP CDS associations](https://help.sap.com/docs/abap-cloud/abap-keyword/cds-ddl-cds-view-entity-association?locale=en-US)
- [SAP debugging ABAP in ADT](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/debugging-abap-code)
- [SAP AMDP troubleshooting tools](https://help.sap.com/docs/ABAP_PLATFORM_NEW/6811c09434084fd1bc4f40e66913ce11/e8a39d549365499481b6e3e1cbd9f041.html?locale=en-US&state=PRODUCTION&version=202210.000)

[Back to contents](#contents)

### References for keys and relationships

- [SAP DDIC foreign keys](https://help.sap.com/docs/abap-cloud/abap-keywords/ddic-foreign-keys)
- [SAP ABAP SQL join syntax](https://help.sap.com/docs/abap-cloud/abap-keyword/ABAPSELECT_JOIN.html)
- [SAP CDS associations and compositions](https://help.sap.com/docs/abap-cloud/abap-data-models/cds-associations?version=sap_cross_product_abap)
- [SAP CDS cardinality](https://help.sap.com/docs/abap-cloud/abap-data-models/405446ac899b4bbc9d5cf9dced34bebe.html)

[Back to contents](#contents)


### References for ABAP basics, BAPI, RFC and BAdI

- [SAP Dictionary table types](https://help.sap.com/saphelp_snc70/helpdata/en/90/8d7304b1af11d194f600a0c929b3c3/content.htm)
- [SAP ABAP internal tables](https://help.sap.com/docs/SAP_NETWEAVER_731_BW_ABAP/cfae740a0a21455dbe6e510c2d86e36a/fceb367a358411d1829f0000e829fbfe.html)
- [SAP working with structures](https://help.sap.com/docs/abap-cloud/abap-concepts/working-with-structures?locale=en-US)
- [SAP Business Add-Ins](https://help.sap.com/docs/SAP_NETWEAVER_AS_ABAP_752/46a2cfc13d25463b8b9a3d2a3c3ba0d9/8ff2e540f8648431e10000000a1550b0.html)
- [SAP BAdI multiple-use property](https://help.sap.com/docs/SAP_NETWEAVER_AS_ABAP_752/46a2cfc13d25463b8b9a3d2a3c3ba0d9/e45c3642eca5033be10000000a1550b0.html)
- [SAP RFC variants](https://help.sap.com/docs/ABAP_PLATFORM_NEW/753088fc00704d0a80e7fbd6803c8adb/4899b53cee2b73e7e10000000a42189b.html)
- [SAP RFC destinations](https://help.sap.com/saphelp_snc700_ehp04/helpdata/en/48/99b539ee2b73e7e10000000a42189b/content.htm)
- [SAP BAPI transaction model](https://help.sap.com/SAPHELP_SCM700_EHP02/helpdata/EN/4d/5b102ba1483d8fe10000000a42189e/content.htm)
- [SAP purchasing BAPIs](https://help.sap.com/docs/SUPPORT_CONTENT/spmm/3362167428.html)
- [RICEF / WRICEF terminology – SAP Community](https://community.sap.com/t5/enterprise-resource-planning-q-a/what-is-the-wricef-when-we-use-it-in-fico-module-and-how-we-use/qaq-p/11056083)

[Back to contents](#contents)



### References for OO ALV and event handling

- [SAP: Events of CL_GUI_ALV_GRID](https://help.sap.com/docs/SAP_NETWEAVER_702/ff58ed046c55101496f8c5172ef85dc4/22a3f5f5d2fe11d2b467006094192fe3.html)
- [SAP: SET HANDLER](https://help.sap.com/docs/abap-cloud/abap-keyword/set-handler)
- [SAP: Editable ALV and CHECK_CHANGED_DATA](https://help.sap.com/docs/SUPPORT_CONTENT/abap/3353523611.html?locale=en-US)
- [SAP: REFRESH_TABLE_DISPLAY](https://help.sap.com/docs/ABAP_PLATFORM_NEW/70396d7dec4c4f19b9ca3b2e47559d12/0ab5531ed30911d2b467006094192fe3.html)

[Back to contents](#contents)


## HCLTech role alignment and interview preparation sources

[Back to contents](#contents)

The following public sources informed the new practice questions. The wording and model answers are original revision material, not an official or leaked question bank. Senior-role listings are used only to identify possible advanced follow-ups; they do not establish fresher eligibility or exact interview requirements.

- [HCLTech – SAP ABAP Analyst](https://careers.hcltech.com/job/SAP-ABAP-Analyst/86101-en_US): ABAP development, maintenance, debugging, troubleshooting and tuning.
- [HCLTech – Associate Consultant, SAP ABAP](https://careers.hcltech.com/job/Associate-Consultant-SAP-ABAP/174662-en_US/): RICEF and collaboration on SAP application requirements.
- [HCLTech – SAP ABAP S4 HANA Senior Technical Lead](https://careers.hcltech.com/job/SAP-ABAP-S4-Hana-Senior-Technical-Lead/187255-en_US/): OO ABAP, CDS, AMDP, SQL, RAP and performance.
- [HCLTech – Technical Specialist](https://careers.hcltech.com/job/Technical-Specialist/172035-en_US): RAP, OData, custom entities, virtual elements and extensibility.
- [Glassdoor – SAP ABAP interview reports](https://www.glassdoor.com/Interview/ludhiana-sap-abap-interview-questions-SRCH_IL.0%2C8_KO9%2C17_SDRD.htm): anecdotal technical interview reports, including HCLTech-tagged questions on transaction handling and RFC.
- [SAP Help – RFC destinations](https://help.sap.com/docs/ABAP_PLATFORM_NEW/753088fc00704d0a80e7fbd6803c8adb/4899b539ee2b73e7e10000000a42189b.html): DESTINATION NONE and RFC context.
- [SAP Help – BAPI transaction model](https://help.sap.com/SAPHELP_SCM700_EHP02/helpdata/EN/4d/5b102ba1483d8fe10000000a42189e/content.htm): transaction ownership.
- [SAP Help – RAP unmanaged query](https://help.sap.com/docs/abap-cloud/abap-rap/implementing-unmanaged-query): custom entity query implementation.

[Back to contents](#contents)
