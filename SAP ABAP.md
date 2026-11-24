# SAP ABAP – Interview Revision Guide

**Simple spoken answers | Core ABAP | Modern ABAP | SAP fundamentals**

Use each short answer to explain what a concept is, why we use it and its main features. Give an example or show syntax only when asked. Code blocks are short syntax reminders, not complete programs; custom objects, variables and demo tables must exist, and newer syntax depends on the SAP release.

## Contents

Click a topic to jump directly to that section. Use **Back to contents** to return here.

**Quick links – newly added topics**

- [Local package ($TMP)](#q77a-what-is-a-local-package-in-sap)
- [Three transport request statuses](#q79a-what-are-the-three-main-statuses-of-a-transport-request)
- [Release vs. import](#q79b-what-is-the-difference-between-releasing-and-importing-a-transport-request)
- [SAP three-tier architecture](#q135-what-is-sap-three-tier-architecture)
- [SAP system landscape (DEV / QAS / PRD)](#q135a-what-is-an-sap-system-landscape)
- [Architecture vs. landscape](#q135b-what-is-the-difference-between-sap-three-tier-architecture-and-sap-landscape)

**Complete guide**

- [SE11 – Data Dictionary (original notes)](#1-ddic--data-dictionary)
- [Internal Tables and Basic ABAP](#internal-tables-and-basic-abap)
- [Modularization and Function Modules](#modularization-and-function-modules)
- [Object-Oriented ABAP](#object-oriented-abap)
- [Reports and Selection Screens](#reports-and-selection-screens)
- [ALV Reports](#alv-reports)
- [Smart Forms](#smart-forms)
- [Module Pool Programming](#module-pool-programming)
- [Transactions, Packages and Transports](#transactions-packages-and-transports)
- [ABAP SQL, Performance and Debugging](#abap-sql-performance-and-debugging)
- [Enhancements, Interfaces and Data Migration](#enhancements-interfaces-and-data-migration)
- [Modern ABAP](#modern-abap)
- [SAP HANA, CDS and AMDP](#sap-hana-cds-and-amdp)
- [RAP, OData, Fiori and ABAP Cloud](#rap-odata-fiori-and-abap-cloud)
- [ATC Checks and Code Quality](#atc-checks-and-code-quality)
- [SAP Fundamentals](#sap-fundamentals)
- [SAP Implementation and S/4HANA Migration](#sap-implementation-and-s4hana-migration)
- [Practical SAP ABAP Interview Questions](#practical-sap-abap-interview-questions)
- [Quick Revision – Important T-Codes](#quick-revision--important-t-codes)
- [Final revision checklist](#final-revision-checklist)
- [Official SAP references for the added topics](#official-sap-references-for-the-added-topics)

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

---

## Internal Tables and Basic ABAP

[Back to contents](#contents)

### Q27. What is an internal table? What is a work area?

An internal table is a temporary table in ABAP memory. We use it to store and process multiple records while a program runs. A work area holds one record at a time.

### Q28. What are the types of internal tables?

ABAP has three types of internal tables. We choose one based on how we access the data.

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

### Q29. What is the difference between TYPE and LIKE?

`TYPE` defines a variable using a known data type. `LIKE` defines it using the type of an existing data object.

**Syntax:**

```abap
DATA lv_matnr TYPE mara-matnr.
DATA lv_copy LIKE lv_matnr.
```

### Q30. What is a field symbol? How is it different from a work area?

A field symbol is an alias that gives us direct access to a data object. Unlike a work area that holds a copy of a row, an assigned field symbol can change the original row directly, within the table's rules.

**Syntax:**

```abap
LOOP AT lt_items ASSIGNING FIELD-SYMBOL(<ls_item>).
  <ls_item>-status = 'A'.
ENDLOOP.
```

Check `IS ASSIGNED` if an assignment can fail. The example assumes the row has a `status` field.

### Q31. What are the common internal table operations?

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

### Q32. What are SY-SUBRC, SY-TABIX, SY-INDEX and SY-DBCNT?

These are SAP system fields that tell us what happened during execution.

- `SY-SUBRC` – return code; zero usually means success.
- `SY-TABIX` – row index in applicable table operations.
- `SY-INDEX` – current DO or WHILE iteration.
- `SY-DBCNT` – number of database rows processed.

I check SY-SUBRC immediately after the relevant statement.

### Q33. What is COLLECT in ABAP?

`COLLECT` adds a record if its key is new. If the key already exists, it adds the numeric non-key values to that record. We use it to calculate totals by key.

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

### Q34. What is the difference between CLEAR, REFRESH and FREE?

`CLEAR` resets a variable or empties a modern internal table. `REFRESH` is an older way to empty a table, while `FREE` also releases its allocated memory more fully. I use FREE when the table is no longer needed.

### Q35. What is the difference between CHECK, CONTINUE and EXIT?

Inside a loop, `CHECK` skips an iteration if a condition is false, `CONTINUE` skips it directly, and `EXIT` ends the loop. Outside a loop, CHECK and EXIT can leave the processing block.

---

## Modularization and Function Modules

[Back to contents](#contents)

### Q36. What is modularization? What are its techniques?

Modularization means dividing a large program into smaller, reusable parts. It makes the code easier to understand, test and maintain. ABAP techniques include subroutines, function modules, methods, includes, macros and dialog modules.

### Q37. What is a subroutine? What are FORM and PERFORM?

A subroutine is a reusable block of code in classical ABAP. We define it using `FORM ... ENDFORM` and call it using `PERFORM`. USING passes inputs and CHANGING passes values that may be changed.

**Syntax:**

```abap
PERFORM calculate USING 10 20 CHANGING lv_total.

FORM calculate USING iv_a TYPE i iv_b TYPE i
               CHANGING cv_total TYPE i.
  cv_total = iv_a + iv_b.
ENDFORM.
```

### Q38. What is a function module?

A function module is a reusable block of code that can be called from different programs. It belongs to a function group and has an interface for inputs and outputs. We create or test it in SE37 and call it using `CALL FUNCTION`.

### Q39. What are the parameters of a function module?

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

### Q40. What is an include program?

An include is a source-code unit used to organize a large ABAP program. For example, TOP holds global declarations and F01 holds subroutines. Includes become part of the main program and do not run independently.

**Syntax:**

```abap
INCLUDE z_demo_top.
INCLUDE z_demo_f01.
```

The include programs must already exist.

### Q41. What is a method? How is it different from a function module?

A method is a block of logic defined inside a class. We call instance methods using `->` and static methods using `=>`. A function module belongs to a function group and is called using `CALL FUNCTION`; a subroutine normally belongs to a program and uses `PERFORM`.

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

### Q42. What is pass by value and pass by reference?

Pass by value gives the called block its own copy of a value. Pass by reference gives it access to the original data, so permitted changes can affect the caller. A CHANGING value parameter can copy its result back on normal completion.

### Q43. What is a function group?

A function group is a container for related function modules. It allows them to share global data, screens and routines. Each function module belongs to one group, which we can manage in SE80.

### Q44. What are the types of function modules?

There are three main types of function modules:

- **Normal:** Runs locally when called.
- **Remote-enabled:** Can be called through RFC, including from another system.
- **Update:** Runs registered update logic when the SAP transaction is committed.

---

## Object-Oriented ABAP

[Back to contents](#contents)

### Q45. What is a class and an object in ABAP?

A class defines the data and behavior of an object through attributes and methods. An object is an instance of that class. We create global classes in SE24 or ADT and use object references to access them.

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

### Q46. What are the four pillars of OOP in ABAP?

The four pillars of OOP help us organize and reuse code.

- **Encapsulation:** Protect data and control access through methods.
- **Inheritance:** Reuse and extend a parent class; ABAP supports single class inheritance.
- **Polymorphism:** Run different method implementations through a common reference.
- **Abstraction:** Expose essential behavior without showing the internal logic.

### Q47. What is the difference between PUBLIC, PROTECTED and PRIVATE?

PUBLIC, PROTECTED and PRIVATE control access to class members. PUBLIC allows outside access, PROTECTED allows access within the class and its subclasses, and PRIVATE normally limits access to the defining class.

### Q48. What is the difference between instance and static methods?

An instance method belongs to an object and uses `->`. A static method belongs to the class and uses `=>`, so we do not need to create an object. Static attributes are shared within the relevant internal session.

**Syntax:**

```abap
DATA(lo_service) = NEW zcl_service( ).
lo_service->process( ).
zcl_service=>get_version( ).
```

### Q49. What are a constructor, abstract class, final class and interface?

A constructor initializes an object; a class constructor runs once before the class is first used. An abstract class cannot be instantiated, and a final class cannot be inherited. An interface defines a contract that classes implement; ABAP allows multiple interfaces.

### Q50. What is method redefinition? Does ABAP support overloading?

Method redefinition lets a child class change the logic of an inherited method without changing its signature. ABAP does not support traditional method overloading. We can use optional parameters or different method names instead.

**Syntax:**

```abap
CLASS lcl_child DEFINITION INHERITING FROM lcl_parent.
  PUBLIC SECTION.
    METHODS display REDEFINITION.
ENDCLASS.
```

---

## Reports and Selection Screens

[Back to contents](#contents)

### Q51. What is a report in SAP ABAP? What are its types?

A report is an executable ABAP program used to read, process and display data. Classical reports use `WRITE`, interactive reports allow drill-down, and ALV reports display data with features like sorting and filtering.

### Q52. How does a classical report work?

A classical report uses traditional ABAP list output. The user enters selection criteria, we fetch the required data, and `WRITE` displays the results.

**Syntax:**

```abap
REPORT z_demo_report.
PARAMETERS p_carr TYPE sflight-carrid.
START-OF-SELECTION.
  SELECT carrid, connid FROM sflight
    WHERE carrid = @p_carr INTO TABLE @DATA(lt_flights).
  LOOP AT lt_flights INTO DATA(ls_flight).
    WRITE: / ls_flight-carrid, ls_flight-connid.
  ENDLOOP.
```

This example uses the SAP flight demo table SFLIGHT.

### Q53. What are the important report events?

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

### Q54. What is the difference between PARAMETERS and SELECT-OPTIONS?

`PARAMETERS` accepts a single input value. `SELECT-OPTIONS` accepts multiple values, ranges and exclusions using SIGN, OPTION, LOW and HIGH. We can use its selection table with `IN` in ABAP SQL.

**Syntax:**

```abap
DATA gv_carrid TYPE sflight-carrid.
PARAMETERS p_carr TYPE sflight-carrid.
SELECT-OPTIONS s_carr FOR gv_carrid.

SELECT carrid, connid FROM sflight
  WHERE carrid IN @s_carr
  INTO TABLE @DATA(lt_flights).
```

### Q55. What is an interactive report? What is HIDE?

An interactive report lets users select a record to see more details. The first output is the basic list, and further outputs are secondary lists. `AT LINE-SELECTION` handles selection, and `HIDE` stores values for the selected line.

---

## ALV Reports

[Back to contents](#contents)

### Q56. What is ALV? Why do we use it?

ALV stands for ABAP List Viewer. It displays internal table data in a standard list or grid with built-in features like sorting, filtering, totals and export. We use it to avoid writing these features ourselves.

### Q57. What are the types of ALV?

Classical ALV uses `REUSE_ALV_LIST_DISPLAY` or `REUSE_ALV_GRID_DISPLAY`. For object-oriented ALV, we use `CL_SALV_TABLE` for simple display and `CL_GUI_ALV_GRID` for editing or more control.

### Q58. What is a field catalog in ALV?

A field catalog defines how ALV columns appear. It contains properties such as field name, heading, length, visibility and editability. The internal table holds the data, while the catalog controls its presentation.

**Syntax:**

```abap
DATA lt_fcat TYPE lvc_t_fcat.
APPEND VALUE #( fieldname = 'CARRID'
                coltext   = 'Airline'
                outputlen = 10 ) TO lt_fcat.
```

This example uses the OO Grid catalog type `LVC_T_FCAT`.

### Q59. What is an ALV layout and layout variant?

An ALV layout controls the appearance of the report, such as row colors and display options. A layout variant saves user preferences like sorting, filters and column order for later use.

### Q60. How do you display a classical ALV grid?

To display a classical ALV grid, I fetch data into an internal table, prepare a field catalog or matching DDIC structure, and call `REUSE_ALV_GRID_DISPLAY`.

**Syntax:**

```abap
CALL FUNCTION 'REUSE_ALV_GRID_DISPLAY'
  EXPORTING i_structure_name = 'SFLIGHT'
  TABLES t_outtab = lt_flights.
```

The internal table must match the SFLIGHT structure in this example.

### Q61. What is SALV? How do you display data using it?

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

### Q62. What is CL_GUI_ALV_GRID? How is it different from SALV?

`CL_GUI_ALV_GRID` is an object-oriented SAP GUI control for displaying and editing tabular data. It supports more control over events, columns and input than SALV, but requires more setup.

**Syntax:**

```abap
lo_grid->set_table_for_first_display(
  EXPORTING i_structure_name = 'SFLIGHT'
  CHANGING  it_outtab        = lt_flights ).
```

Create the grid first. Use `REFRESH_TABLE_DISPLAY` after changing data and `CHECK_CHANGED_DATA` to collect pending user edits before saving.

### Q63. What is a custom container?

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

### Q64. How do you handle events in OO ALV?

OO ALV events allow us to respond to user actions such as double-clicking a row. We define a handler method and register it using `SET HANDLER`. Classical ALV usually uses callback subroutines instead.

**Syntax:**

```abap
METHODS on_double_click
  FOR EVENT double_click OF cl_gui_alv_grid
  IMPORTING e_row e_column.
```

Implement the handler method and register it with `SET HANDLER lo_handler->on_double_click FOR lo_grid.`

---

## Smart Forms

[Back to contents](#contents)

### Q65. What is a Smart Form?

Smart Forms is a SAP tool for designing business documents like invoices and purchase orders. We create forms in SMARTFORMS. On activation, SAP generates a function module that the driver program calls to produce output.

### Q66. What are the main components of Smart Forms?

Smart Forms has an interface for passing data and global definitions for shared variables and logic. Pages and windows control the layout; the main window can flow across pages, while secondary windows stay in fixed areas. Tables, templates, text and graphics display the content.

### Q67. What is a driver program? How does a Smart Form work?

A driver program is an ABAP program that fetches and prepares data for a Smart Form. It calls the generated function module, and the form uses its layout to produce the document.

### Q68. Why do we use SSF_FUNCTION_MODULE_NAME?

`SSF_FUNCTION_MODULE_NAME` returns the generated function module name for a Smart Form. We use it because that name may differ between DEV, QAS and PRD, so hard-coding it can cause problems.

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

### Q69. What is the difference between SAPscript, Smart Forms and Adobe Forms?

SAPscript, Smart Forms and Adobe Forms are SAP document technologies. SAPscript is the older tool (SE71), Smart Forms provides a graphical designer and generated function module, and Adobe Forms focuses on PDF output (SFP).

---

## Module Pool Programming

[Back to contents](#contents)

### Q70. What is module pool programming?

Module pool programming is a classical ABAP technique for building interactive SAP GUI screens. We use it when users need to enter, validate, change or save data across screens, usually through a dialog transaction.

### Q71. What is a dynpro? What are Screen Painter and Menu Painter?

A dynpro is a SAP GUI screen with fields, layout, attributes and flow logic. Screen Painter (SE51) designs the screen, while Menu Painter (SE41) defines menus, toolbars and function codes.

### Q72. What are PBO and PAI? Explain screen flow logic.

PBO (Process Before Output) runs before the screen appears and prepares its data and controls. PAI (Process After Input) runs after a user action to validate input and handle commands. Screen flow logic defines which modules run in each event.

**Syntax:**

```abap
PROCESS BEFORE OUTPUT.
  MODULE status_0100.
PROCESS AFTER INPUT.
  MODULE user_command_0100.
```

Implement PBO with `MODULE ... OUTPUT` and PAI with `MODULE ... INPUT` in the ABAP program.

### Q73. What are OK_CODE and SY-UCOMM?

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

### Q74. What is the difference between CALL SCREEN, SET SCREEN and LEAVE SCREEN?

These statements control screen navigation.

- `CALL SCREEN` – starts a nested screen sequence.
- `SET SCREEN` – sets the next screen.
- `LEAVE SCREEN` – leaves the current screen for the next one.
- `LEAVE TO SCREEN` – sets and leaves for the next screen.

Screen 0 ends the current screen sequence.

### Q75. What is CHAIN ... ENDCHAIN? What is LOOP AT SCREEN?

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

---

## Transactions, Packages and Transports

[Back to contents](#contents)

### Q76. What is a transaction code? How do you create one?

A transaction code is a shortcut to a SAP application or program. We create custom T-codes in SE93 by assigning a report or a module pool program with its starting screen.

### Q77. What is a package in SAP?

A package groups related SAP development objects, such as reports, classes and tables. It helps organize development and manage transports. We maintain packages in SE21 or SE80.

### Q77A. What is a local package in SAP?

A local package (`$TMP`) is used for objects that stay in the current SAP system. We usually use it for practice or testing without a transport request. To move an object later, we assign it to a transportable package and record the change.

### Q78. What is a transport request? How do you release it?

A transport request records changes so we can move them between SAP systems. We release the developer tasks first and then the main request using SE09 or SE10. STMS handles imports into the target systems.

### Q79. What are the types of transport requests?

A Workbench request carries development objects such as reports and classes. A Customizing request usually carries client-specific configuration. A Transport of Copies lets us move selected objects for testing without releasing the original request.

### Q79A. What are the three main statuses of a transport request?

A transport request has three main statuses:

- **Modifiable:** We can still add or change objects.
- **Release Started:** SAP has started the release process.
- **Released:** The request is released and normally cannot be edited.

Released does not mean imported; we check imports in STMS.

### Q79B. What is the difference between releasing and importing a transport request?

Releasing prepares a transport request to move out of the source system. Importing applies its changes in the target system. For example, releasing in DEV does not mean the object is already available in QAS.

---

## ABAP SQL, Performance and Debugging

[Back to contents](#contents)

### Q80. What is Open SQL? How is it different from Native SQL?

Open SQL, now called ABAP SQL, is SAP's standard way to access database data from ABAP. It works across supported databases and handles clients where applicable. Native SQL uses database-specific statements, so it is less portable.

### Q81. What is the difference between SELECT SINGLE and UP TO 1 ROWS?

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

### Q82. What is the difference between INNER JOIN and LEFT OUTER JOIN?

An INNER JOIN returns only records that match in both tables. A LEFT OUTER JOIN returns all records from the left table, even when there is no match on the right.

**Syntax:**

```abap
SELECT a~carrid, a~carrname, b~connid
  FROM scarr AS a
  INNER JOIN spfli AS b ON b~carrid = a~carrid
  INTO TABLE @DATA(lt_result).
```

### Q83. What is FOR ALL ENTRIES? What precautions should we take?

FOR ALL ENTRIES fetches database records using values from an internal table. We must check that the internal table is not empty, otherwise the WHERE condition is ignored. Duplicate result rows are removed automatically.

**Syntax:**

```abap
IF lt_keys IS NOT INITIAL.
  SELECT carrid, connid FROM sflight
    FOR ALL ENTRIES IN @lt_keys
    WHERE carrid = @lt_keys-carrid
    INTO TABLE @DATA(lt_flights).
ENDIF.
```

### Q84. What is an SAP LUW? What are COMMIT WORK and ROLLBACK WORK?

An SAP LUW (Logical Unit of Work) groups related changes into one business transaction. `COMMIT WORK` ends the LUW and triggers registered updates, while `ROLLBACK WORK` cancels pending changes. `COMMIT WORK AND WAIT` waits for high-priority updates; committed changes cannot be rolled back this way.

### Q85. What are INSERT, UPDATE, MODIFY and DELETE in ABAP SQL?

ABAP SQL uses `INSERT` to add, `UPDATE` to change, `MODIFY` to insert or update, and `DELETE` to remove database records. For SAP standard business data, I use the appropriate business API rather than directly changing tables.

**Syntax:**

```abap
INSERT zstudent FROM @ls_student.
UPDATE zstudent SET status = @lv_status WHERE id = @lv_id.
MODIFY zstudent FROM @ls_student.
DELETE FROM zstudent WHERE id = @lv_id.
```

These are separate examples for a custom table, not steps to run together.

### Q86. How do you improve ABAP performance?

To improve ABAP performance, I first measure the runtime using ST05 or SAT. I select only required fields and rows, avoid repeated SELECTs inside loops, use suitable joins and choose efficient internal table keys. I also avoid unnecessary data copies.

### Q87. What is debugging? What are breakpoints and watchpoints?

Debugging means checking program execution to find errors. A breakpoint pauses execution at a chosen point; a watchpoint pauses when a value changes or a condition is met. Session and external breakpoints support different execution contexts, and ST22 helps us check dumps.

### Q88. What is AUTHORITY-CHECK? What are message types?

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

---

## Enhancements, Interfaces and Data Migration

[Back to contents](#contents)

### Q89. What are enhancements, user exits, customer exits and BAdIs?

Enhancements add custom logic to SAP standard processes without directly changing standard code. User exits are older application-specific options, customer exits are SAP-provided options (SMOD/CMOD), and BAdIs are object-oriented enhancements (SE18/SE19).

### Q90. What is the difference between RFC and BAPI?

RFC (Remote Function Call) allows us to call remote-enabled function modules. A BAPI (Business Application Programming Interface) provides a defined business operation, such as creating a document. Many BAPIs support RFC, but not every RFC is a BAPI; we follow the BAPI's commit and error-handling rules.

### Q91. What is an IDoc? What are ALE and EDI?

An IDoc (Intermediate Document) is a standard format for exchanging business data, often asynchronously. It contains control, data and status records. ALE distributes data between SAP systems, EDI exchanges documents between organizations, and WE02/WE05 show IDoc status.

### Q92. What is BDC? How is it different from BAPI?

BDC (Batch Data Communication) automates data entry through classical SAP screens, using session processing (SM35) or CALL TRANSACTION. A BAPI uses a business interface instead of screens, so I prefer a suitable supported BAPI when available.

---

## Modern ABAP

[Back to contents](#contents)

### Q93. What is modern ABAP?

Modern ABAP refers to newer ABAP language features, many introduced from release 7.40 onward. It helps us write shorter, clearer code using inline declarations, constructor expressions and table expressions. Availability depends on the release.

### Q94. What is an inline declaration?

An inline declaration defines a variable where we first need it, instead of declaring it separately. ABAP automatically determines its type from the statement.

**Syntax:**

```abap
DATA(lv_name) = 'SAP'.
READ TABLE lt_items INDEX 1 INTO DATA(ls_item).
```

### Q95. What are VALUE, NEW and CONV?

VALUE, NEW and CONV are constructor operators. `VALUE` creates values, structures or tables, `NEW` creates objects or anonymous data and returns references, and `CONV` converts data types. We use `#` when the type can be inferred.

**Syntax:**

```abap
DATA(lt_numbers) = VALUE int4_table( ( 10 ) ( 20 ) ).
DATA(lv_text) = CONV string( 100 ).
```

### Q96. What is a table expression? How is it different from READ TABLE?

A table expression is a short way to access an internal table row by key or index. Unlike READ TABLE, it does not set SY-SUBRC and normally raises an exception if the row is missing. We can use LINE_EXISTS or a suitable fallback.

**Syntax:**

```abap
IF line_exists( lt_items[ id = 10 ] ).
  DATA(ls_item) = lt_items[ id = 10 ].
ENDIF.
```

### Q97. What are COND and SWITCH?

`COND` returns a value based on conditions, like IF/ELSE. `SWITCH` returns a value by matching an input, like CASE. Both make assignments more concise.

**Syntax:**

```abap
DATA(lv_result) = COND string(
  WHEN lv_marks >= 40 THEN 'Pass'
  ELSE 'Fail' ).
```

### Q98. What are FOR, REDUCE and FILTER?

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

### Q99. What is CORRESPONDING?

`CORRESPONDING` copies matching fields between structures or tables into a new result. We use it instead of assigning each field manually. MAPPING handles different field names; MOVE-CORRESPONDING updates an existing target.

**Syntax:**

```abap
ls_target = CORRESPONDING #( ls_source ).
```

### Q100. What is modern ABAP SQL?

Modern ABAP SQL provides features such as inline declarations, expressions, joins and database calculations. The `@` symbol identifies ABAP host variables. We use these features to simplify data access and processing.

**Syntax:**

```abap
SELECT carrid, COUNT( * ) AS flight_count
  FROM sflight
  GROUP BY carrid
  INTO TABLE @DATA(lt_counts).
```

### Q101. How do you handle exceptions in modern ABAP?

Class-based exception handling lets us manage runtime problems using `TRY ... CATCH`. We put the risky statement inside TRY and handle expected exceptions in CATCH so the program can respond appropriately.

**Syntax:**

```abap
TRY.
    DATA(ls_item) = lt_items[ id = 10 ].
  CATCH cx_sy_itab_line_not_found.
    " Handle the missing row
ENDTRY.
```

---

## SAP HANA, CDS and AMDP

[Back to contents](#contents)

### Q102. What is SAP HANA? How is it different from S/4HANA?

SAP HANA is an in-memory database designed for fast data processing and analytics. S/4HANA is the ERP business suite that runs on HANA. HANA stores and processes data, while S/4HANA handles business processes.

### Q103. What is code pushdown?

Code pushdown means moving suitable data processing from the ABAP application server to the database. We let the database handle filtering, joins and calculations, then fetch the required results. ABAP SQL, CDS and AMDP support this approach.

### Q104. What is CDS? How is it different from a classical DDIC view?

CDS (Core Data Services) is used to build reusable data models from tables or other CDS entities. Compared with classical DDIC views, CDS supports annotations, associations and richer expressions. We develop CDS view entities in ADT.

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

This is CDS DDL, written in ADT, not inside a report. The example is for learning; use appropriate authorization settings in real applications.

### Q105. What are CDS annotations and associations?

CDS annotations add information to a data model, such as labels, currency details or UI settings. Associations define relationships between entities, such as a sales order and its items. Consumers can use these relationships to access related data.

### Q106. What is DCL in CDS?

DCL (Data Control Language) defines access rules for CDS data. We use it to restrict which records a user can see based on authorization. DDL defines the data model; DCL controls read access, while other operations may need separate checks.

### Q107. What is AMDP? How is it different from CDS?

AMDP (ABAP Managed Database Procedures) lets us write database-specific logic, such as HANA SQLScript, in an ABAP class method. CDS mainly models data, while AMDP is useful for more complex database-side processing.

---

## RAP, OData, Fiori and ABAP Cloud

[Back to contents](#contents)

### Q108. What is RAP?

RAP (ABAP RESTful Application Programming Model) is SAP's model for building business applications and services in ABAP. It uses CDS for data, behavior definitions for business operations and service bindings to expose services such as OData.

### Q109. What are the main components of RAP?

RAP has five main components:

- **CDS model:** Defines the data and relationships.
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

### Q110. What is the difference between managed and unmanaged RAP?

In managed RAP, the framework handles standard create, update, delete, buffering and saving, so we focus on custom business logic. In unmanaged RAP, we implement the required operations and saving ourselves. Managed suits new applications; unmanaged is useful when reusing existing business logic or APIs.

### Q111. What is managed RAP with unmanaged save?

Managed RAP with unmanaged save combines framework-managed operations and buffering with custom save logic. We use it when standard RAP processing is suitable but saving must go through an existing business API.

### Q112. What is a behavior definition and behavior implementation in RAP?

A behavior definition (BDEF) defines what a RAP business object can do, such as create, update, delete or approve. The behavior implementation contains the ABAP logic for custom operations, validations and actions.

### Q113. What is a root entity and a projection view in RAP?

A root entity is the main entity of a RAP business object, such as a sales order header with child items. A projection view exposes the fields and relationships needed by a particular application or service.

### Q114. What is the difference between service definition and service binding?

A service definition specifies which CDS entities we want to expose. A service binding defines how they are exposed, for example through OData V4. One defines the content, while the other makes it available as a service.

### Q115. What is draft in RAP?

Draft in RAP allows users to save unfinished changes separately from active business data. They can continue editing later and activate the draft when it is ready.

### Q116. What are locking and ETags in RAP?

Locking helps prevent conflicting changes when multiple users edit a record. An ETag checks whether the record has changed since a user last read it. Together, they help avoid overwriting newer data.

### Q117. What are validations, determinations and actions in RAP?

These are ways to add business logic in RAP. A validation checks data, a determination automatically calculates or updates values, and an action performs a specific business operation, such as approving an order.

### Q118. What is EML in RAP?

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

### Q119. What is OData? What is SAP Fiori?

OData (Open Data Protocol) is a standard way to expose and consume data services over HTTP. SAP Fiori is SAP's modern, role-based user experience. Fiori apps can use OData services to read and update business data.

### Q120. What are ADT, ABAP Cloud and Clean Core?

ADT is the Eclipse-based development tool for ABAP, CDS and RAP. ABAP Cloud is a development model that uses released APIs and restricted language versions. Clean Core means avoiding unnecessary changes to standard SAP and using supported extensions.

### Q121. What is ABAP Unit?

ABAP Unit is SAP's automated unit-testing framework for ABAP code. We write test methods with expected results to check our logic and catch errors when the code changes.

---

## ATC Checks and Code Quality

[Back to contents](#contents)

### Q122. What is ATC in SAP ABAP?

ATC (ABAP Test Cockpit) is SAP's tool for checking ABAP code quality. It helps us find possible errors, performance issues, security risks and compatibility problems. We can run it from ADT or supported SAP GUI tools.

### Q123. What types of checks does ATC perform?

ATC checks depend on the selected variant. They can cover programming errors, performance, security, coding standards and outdated statements. Some variants also check S/4HANA compatibility, ABAP Cloud restrictions or run ABAP Unit tests.

### Q124. What is an ATC check variant?

An ATC check variant is a collection of checks that ATC should perform. We choose the variant based on the project's needs, such as general code quality or S/4HANA readiness.

### Q125. How do you run and fix ATC checks?

In ADT, I select the object or package and run ABAP Test Cockpit from the context menu. I review the findings, fix the relevant issues and run ATC again. Supported SAP GUI tools can also run checks.

### Q126. What are ATC priority levels and exemptions?

ATC findings usually have priorities 1, 2 and 3, with 1 being the highest. We fix issues according to the project's release rules. If a finding does not apply or cannot be fixed reasonably, we may request a justified, approved exemption where supported.

### Q127. What is the difference between SCI, ATC and ABAP Unit?

SCI (Code Inspector) checks ABAP code for quality issues. ATC builds on code checks with central finding management and transport checks, and can include SCI checks and ABAP Unit tests. ABAP Unit tests actual program logic; it does not replace functional testing.

### Q128. Why is ATC important in an S/4HANA migration?

ATC helps identify custom code affected by changed or obsolete tables, APIs and statements during an S/4HANA migration. We use the findings to fix and retest the affected programs before moving them.

---

## SAP Fundamentals

[Back to contents](#contents)

### Q129. What is SAP? What is ERP?

SAP provides software for managing business processes. ERP stands for Enterprise Resource Planning. It connects areas like finance, sales, purchasing and production so they can work with shared business data.

### Q130. What is the difference between SAP ECC and SAP S/4HANA?

SAP ECC is the older ERP suite that can run on different supported databases. S/4HANA is the newer ERP suite designed for HANA, with a simpler data model and modern technologies such as Fiori.

### Q131. What are the main SAP functional modules?

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

### Q132. What are functional and technical (non-functional) areas in SAP?

Functional areas support business processes, while technical areas help develop, maintain, secure and integrate SAP systems. Technical areas is a more accurate term than non-functional modules.

| Technical area | Purpose |
|---|---|
| ABAP | Develop reports, interfaces, forms and applications |
| SAP Basis | Install, configure and maintain SAP systems |
| SAP Security / Authorizations | Manage user access and roles |
| SAP Fiori / SAPUI5 | Build modern user interfaces |
| SAP BTP / Integration Suite | Extend applications and connect systems |

### Q133. What is the difference between an SAP functional consultant and an ABAP technical consultant?

A functional consultant understands business requirements and configures SAP processes. An ABAP technical consultant builds the required programs, interfaces or enhancements. For example, the MM consultant defines a purchase order report and the developer builds it.

### Q134. What are functional and non-functional requirements in SAP?

Functional requirements define what an application must do, such as displaying purchase orders. Non-functional requirements define how well it must work, such as performance, security, reliability and usability.

### Q135. What is SAP three-tier architecture?

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

### Q135A. What is an SAP system landscape?

An SAP landscape is a group of systems used for different stages of development.

- **DEV:** Create and change objects.
- **QAS:** Test changes.
- **PRD:** Run live business operations.

We move approved changes through transports instead of directly changing production.

**Transport flow:**

```text
DEV (Develop) → QAS (Test) → PRD (Go Live)
```

### Q135B. What is the difference between SAP three-tier architecture and SAP landscape?

Three-tier architecture explains how one SAP system works internally using presentation, application and database layers. The landscape explains how separate DEV, QAS and PRD systems support development and deployment.

### Q136. What are a client, company code, plant and storage location?

A client separates client-dependent data within a SAP system. A company code is an accounting unit, a plant supports production or logistics, and a storage location identifies where stock is kept within a plant.

### Q137. What is the difference between master data and transaction data?

Master data is reusable business information, such as customer, supplier and material details. Transaction data records business activities, such as purchase orders, sales orders and invoices.

### Q138. What are procure-to-pay and order-to-cash?

Procure-to-pay is the purchasing process from requisition and purchase order through goods receipt, invoice and payment. Order-to-cash is the sales process from sales order through delivery, goods issue, billing and payment receipt.

### Q139. What are some important SAP standard tables?

Common SAP tables include MARA (material), MARC (plant-level material), MAKT (material description), EKKO/EKPO (purchase order header/items), and VBAK/VBAP (sales document header/items). We use them based on the business data needed.

### Q140. What is RICEFW?

RICEFW is a way to classify SAP technical development work. It stands for Reports, Interfaces, Conversions, Enhancements, Forms and Workflows.

### Q141. What is the difference between functional and technical specifications?

A functional specification explains what the business needs and the expected result. A technical specification explains how we will build it, including tables, logic and technical objects.

### Q142. What are unit testing, integration testing and UAT?

Unit testing checks individual development logic. Integration testing checks how it works with other systems or processes. UAT (User Acceptance Testing) lets business users confirm the solution meets their requirements.

### Q143. What is a background job?

A background job runs an ABAP program without requiring the user to keep a screen open. We use it for long-running or scheduled tasks. SM36 schedules jobs and SM37 monitors them.

### Q144. What is SAP BTP?

SAP BTP (Business Technology Platform) provides services for application development, integration, data, analytics and automation. We use it to extend SAP applications and connect systems, including supported cloud ABAP development.

---

## SAP Implementation and S/4HANA Migration

[Back to contents](#contents)

### Q145. What is Greenfield implementation in SAP?

Greenfield is a new SAP implementation that starts from scratch. We redesign business processes and migrate required data instead of carrying over all old custom code and configuration.

### Q146. What is Brownfield implementation in SAP?

Brownfield is the conversion of an existing SAP ERP system to S/4HANA. It retains much of the existing data, configuration and processes. We review and adjust custom ABAP code where needed.

### Q147. What is the difference between Greenfield and Brownfield?

Greenfield starts with a new implementation and allows process redesign. Brownfield converts the existing system and keeps much of its data and configuration. The choice depends on what the business wants to retain or change.

### Q148. What is Selective Data Transition?

Selective Data Transition moves selected data and parts of an existing SAP landscape to S/4HANA. It allows us to retain some history and processes while redesigning others. It is sometimes called a hybrid or bluefield approach.

### Q149. What is SAP Activate methodology?

SAP Activate is SAP's methodology for organizing implementation projects. Its six phases are Discover, Prepare, Explore, Realize, Deploy and Run. They guide the team from planning and design through testing, go-live and support.

### Q150. What is the difference between an implementation, rollout and support project?

An implementation project sets up or converts a SAP solution. A rollout extends an existing solution to another location or business unit. A support project maintains the live system, fixes issues and delivers approved improvements.

### Q151. What is custom code remediation?

Custom code remediation means adapting existing ABAP code for S/4HANA compatibility. We use ATC to identify affected programs, fix incompatible logic and retest them.

### Q152. What is Clean Core and why is it important?

Clean Core means keeping SAP standard code as unchanged as practical. We use released APIs, supported BAdIs and suitable extensions for custom requirements. This makes maintenance and upgrades easier.

### Q153. What is the difference between on-stack and side-by-side extensions?

On-stack extensions run inside the SAP application system using supported extension options. Side-by-side extensions run separately, often on SAP BTP, and connect through APIs or events. We choose based on the requirement and available extension options.

---

## Practical SAP ABAP Interview Questions

[Back to contents](#contents)

### Q154. How would you approach a new ABAP requirement?

I would first understand the business requirement and expected output. Then I would review the specification, develop and test the solution in DEV, run required checks and move it through the approved transport process.

### Q155. How would you handle a production issue?

I would collect the issue details and check logs, dumps, data and authorizations. After reproducing the issue in a test system, I would fix the cause, test the solution and follow the approved transport process.

### Q156. What would you do if a report shows no data?

I would check selection values, client, authorizations and whether the data exists. Then I would debug the SELECT statement and filtering logic to find where records are being lost, without bypassing necessary checks.

### Q157. What would you do if a report is running slowly?

I would measure the runtime with ST05 or SAT and check for repeated database calls, unnecessary data retrieval and slow table searches. After optimizing the cause, I would compare both runtime and output to confirm the fix.

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
| SM12 | Lock entry monitoring |
| SM13 | Update request monitoring |
| SLG1 | Application log display |

---

## Final revision checklist

[Back to contents](#contents)

Practice explaining DDIC, internal tables, modularization, report events, ALV, Smart Forms, PBO/PAI, transports, ABAP SQL and debugging first. Then revise enhancements, BAPI/RFC, modern ABAP, CDS, RAP, ATC checks, SAP functional and technical areas, and Greenfield versus Brownfield implementation. For code, practice the short examples rather than memorizing complete programs.


 [SAP transport release and import process](https://help.sap.com/docs/SAP_NETWEAVER_AS_ABAP_751_IP/4a368c163b08418890a406d413933ba7/0e70a0ed3b6943de93b083496b0f42a0.html)
