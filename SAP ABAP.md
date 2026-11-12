
# 1. DDIC – Data Dictionary

### Q1. What is DDIC (Data Dictionary)?

**DDIC** is a central repository in SAP ABAP used to define and manage database objects such as tables, views, data elements, domains, structures and table types. And DDIC can be Accessed by 
Using the Transaction Code ( T-Code ) - **SE11** .

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
### Q8. What is a Primary Key in ABAP?

A Primary Key is a field or combination of fields that uniquely identifies each record in a database table.

- It does not allow duplicate or NULL values.
- A table can have only one primary key.

### Q9. What is a Foreign Key in ABAP?

A Foreign Key is a field in one table that refers to the Primary Key of another table to establish a relationship between the two tables.

- It is used to maintain referential integrity between tables.
- Created in SE11 using the Foreign Key relationship.
### Q10. What is a Check Table and Value Table?

- **Check Table:** A table that contains valid values used to check the entries in a foreign key field.

- **Value Table:** A table assigned to a Domain that suggests valid values for fields using that Domain.

### Q11. What is Cardinality in ABAP?

Cardinality defines the number of records that can be related between two tables through a Foreign Key relationship.

Types of Cardinality:

| Cardinality | Meaning                                                                                | Example                                 |
| ----------- | -------------------------------------------------------------------------------------- | --------------------------------------- |
| 1:1         | One check table record is related to exactly one foreign key table record.             | One person – One ID Card                |
| 1:C         | One check table record is related to zero or one foreign key table record..            | One student – Zero or One ID Card       |
| 1:N         | One check table record is related to one or more foreign key table records.            | One student – Multiple ID Cards         |
| 1:CN        | One check table record is related to zero, one, or multiple foreign key table records. | One student – Zero or Multiple ID Cards |

**Note:** `C` indicates optional (zero records allowed), and `N` indicates multiple records allowed.

### Q12. What is a Foreign Key Relationship in ABAP?

A Foreign Key Relationship connects two tables by linking a Foreign Key field in the dependent table with the Primary Key of the check table.

- It maintains data consistency.
- It includes cardinality and foreign key field assignments.

# 4.Structure and Table Type 

### Q13. What is a Structure in ABAP?

A Structure is a DDIC object used to group multiple fields of different data types under a single name. It does not store data permanently in the database.

- It contains multiple fields with different data types.
- It is used to organize and process related data.
- Created using the T-Code: SE11.

### Q14. What is a Table Type in ABAP?

A Table Type is a DDIC object used to define the structure and properties of an internal table.
Only used While Creating or Defining an "Internal Table" ( Local Object ) .

- It defines the line type, table category and key.
- It is used to create internal tables with a predefined structure.
- We should select the Type of Table while creating a Table Type
- Created using the T-Code: SE11.

### Q15. Types of Table Types Or Internal Tables (SE11)

**1. Standard Table:** A Standard Table stores records in sequential order and allows duplicate key entries or non-unique Keys. Data is accessed mainly using an index.

**2. Sorted Table:** A Sorted Table automatically stores records in sorted order based on its key and supports unique or non-unique keys.

**3. Hashed Table:** A Hashed Table stores records using a hash algorithm and requires a unique key. Data is accessed using the key rather than an index.

### Q16. What is a Lock Object in SAP ABAP?

A Lock Object is a DDIC object used to prevent multiple users from simultaneously changing the same data, ensuring data consistency in the SAP system.

- It prevents conflicts when multiple users access or modify the same data.
- It Locks a Development Object ( Object can't be Edited or Manipulated )
- Created using the T-Code: SE11.
- SAP automatically generates two Function Modules:
     
    - `ENQUEUE_<Lock_Object>` – To lock the data.
    - `DEQUEUE_<Lock_Object>` – To unlock the data.
    
- Until You DEQUEUE the Object or Data it cant be Used or changed By Other Users .(Don't Need to Do anything Manually , Everything will be Done Automatically )

# 5.Search Help 

### Q17. What is Search Help in SAP ABAP?

Search Help is a DDIC object used to provide possible input values for a field, helping users select the correct value instead of entering it manually.

Main Points:

- It is used to provide F4 help (input help) for fields.
- Created using T-Code: SE11.
- It can be assigned to individual fields in a Data Element or directly to fields in a Database Table.
- It is commonly used in selection screens and screen fields.

### Q18. What are the Types of Search Help?

There are two types of Search Help:

**1. Elementary Search Help:**

- An Elementary Search Help provides F4 help using a single selection method (usually one database table or view).
- It contains the search help parameters and selection conditions.

**2. Collective Search Help:**

- A Collective Search Help combines multiple Elementary Search Helps into a single search help.
- It allows users to search using different search methods.

### Q19. What is a Selection Method in Search Help?

A Selection Method specifies the source from which the search help retrieves values for displaying in the F4 hit list.

- It can be a Database Table or a View.
- Example: `MARA` (Material Master Table).

### Q20. What are Import and Export Parameters in Search Help?

**1. Import Parameter (IMP):** It passes the existing field value from the screen to the Search Help to filter the available records.

**2. Export Parameter (EXP):** It returns the selected value from the Search Help hit list back to the screen field.

- A parameter can be both Import and Export at the same time.

### Q21. What are LPOS and SPOS in Search Help?

- LPOS (List Position): Defines the column position of a parameter in the Search Help hit list.

- SPOS (Selection Position): Defines the position of a parameter in the value restriction screen, where users can enter search criteria.

### Q22. What are the Dialog Types in Search Help?

Dialog Type defines how the values are displayed when the user presses F4.

There are three dialog types:

|Dialog Type|Meaning|
|---|---|
|A – Dialog Depends on Set of Values|If there are fewer than 100 records, the hit list appears directly; otherwise, a restriction screen appears first.|
|C – Dialog with Value Restriction|A restriction screen appears first, allowing users to filter values before displaying the hit list.|
|D – Display Values Immediately|The hit list is displayed directly when the user presses F4.|

### Q23. What is a Hot Key in Search Help?

A Hot Key is a single-character shortcut assigned to an Elementary Search Help within a Collective Search Help to access a particular search method directly.

- It helps users select a specific Elementary Search Help.
- Each Elementary Search Help inside a Collective Search Help should have a different Hot Key.
- Defined in SE11.

### Q24. What is Search Help Assignment?

Search Help can be assigned in the following ways:

**1. Data Element:** Assigned to a Data Element so that fields using that Data Element can inherit the F4 help.
**2. Database Table Field:** Assigned directly to an individual field in a Database Table.
**3. Selection Screen Parameter:** Assigned directly using ABAP code.

### Q25. How to use Search Help in an ABAP Selection Screen?

We can attach an existing Search Help to a selection screen parameter using the `MATCHCODE OBJECT` addition.

Syntax:

```
PARAMETERS: P_DEPT TYPE ZDEPT_ID
            MATCHCODE OBJECT ZSH_DEPT.
```

- `P_DEPT` – Selection screen parameter.
- `ZDEPT_ID` – Data type.
- `ZSH_DEPT` – Search Help object name.

### Q26. What is a Search Help Exit?

A Search Help Exit is a Function Module used to modify or control the standard search help process when additional custom logic is required.

- It is used for special filtering and processing requirements.






