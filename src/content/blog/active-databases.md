---
author: Helios
pubDatetime: 2023-05-07T15:57:52.737Z
title: Transistor Transistor Logic
postSlug: ttl-logic
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - CASE-STUDY
description: nothing and everything 
---

Active databases and triggers are two important concepts in the field of database management systems.

## What are Active Databases?

Active databases are database systems that can actively monitor and respond to events in real-time. These systems can detect changes in the database and automatically trigger actions or workflows based on predefined rules or conditions. In other words, active databases are capable of reacting to events or stimuli in real-time and can take actions to maintain data consistency and integrity.

![image](https://user-images.githubusercontent.com/103866475/236673946-f8073f54-7d87-4afe-9111-c6111f8a460c.png)


Triggers, a class of stored procedures that are executed automatically when a specified event takes place, are how active databases function. Triggers are defined using SQL commands and are attached to database tables, views, or other database objects. When a predefined event occurs, the trigger is executed, and it can perform a variety of actions, such as modifying data in the database, executing other procedures, or sending notifications.

## Features of Active Database:

    It is equipped with all the features found in a typical database, including query language capabilities and data modeling tools.
    It provides all of the typical database functions, including data definition, data manipulation, storage management, etc.
    ECA rules can be defined and managed with its assistance.
    It finds the occurrence of events.
    It must have the capacity to assess situations and carry out actions.
    It follows that rule execution must be put into practise.

## Benefits of Active Databases:

Active databases offer several benefits, such as real-time monitoring, automated response, improved data integrity, and reduced workload for database administrators. Active databases can assist in ensuring that the database always remains consistent and up-to-date by automating repetitive processes and enforcing business standards.

## Triggers

Triggers are used to automate tasks such as enforcing data integrity constraints, updating related tables when data is inserted, updated or deleted, and generating notifications or alerts based on certain conditions.

Triggers are used extensively in active databases to implement various functionalities. There are four types of triggers that can be used in active databases:

- **Data manipulation language (DML) triggers** — These triggers execute when an INSERT, UPDATE, or DELETE statement is executed on a table.
- **Data definition language (DDL) triggers** — These triggers execute when a DDL statement is executed, such as creating or modifying a table.The acronym DDL stands for Data Definition Language, which includes statements like CREATE, ALTER, and DROP.
- **Logon triggers** — These triggers execute when a user logs on to the database.
- **Logoff triggers** — These triggers execute when a user logs off from the database.

There are numerous uses for triggers, including auditing, logging, preserving data integrity, and enforcing business rules. A trigger can be used, for instance, to send an email message when a certain condition is satisfied or to automatically update the inventory whenever a new product is added to the database.

![image](https://user-images.githubusercontent.com/103866475/236673986-e6a8e2e1-a796-48a0-83b6-79688bb452af.png)

Triggers can also be used to implement complex data processing and analysis tasks, such as data mining and predictive analytics. By automatically executing predefined code in response to specific events or conditions, triggers can enable an active database to analyse patterns and trends in the data, and to make intelligent decisions and recommendations based on that analysis.

![image](https://user-images.githubusercontent.com/103866475/236673996-5354b46b-0d91-4473-9439-dc8ca10ce22c.png)
Source: Oracle

trigger is a special type of stored procedure that is automatically executed in response to certain events, such as INSERT, UPDATE, or DELETE statements being executed on a table.

Trigger Operations:

    Insert Trigger
    Delete Trigger
    Update Trigger

### Insert Trigger

Firstly we have to create a table named “product”, next we will insert some records into this table and then execute the select statement to see the table. Again we will create a new table named “product_backup”, next we will use the create trigger statement to create an insert trigger on the table product. The trigger is fired following an insert operation on the table. If the trigger is created successfully, we will get the output by running select statements on “product_backup” table. We can see that on inserting values into the product table, the product_backup table will automatically fill the records by invoking a trigger.

![image](https://user-images.githubusercontent.com/103866475/236674020-0200d367-66fb-46e3-a3e4-1038bf8be3f7.png)

![image](https://user-images.githubusercontent.com/103866475/236674031-e11fd731-d576-400b-b0f4-1264130d6c17.png)


### 2. Delete Trigger

In this trigger we perform the delete operation. The process remains the same as the above trigger till the creation of the trigger. After that we have to use the delete trigger statement to perform the delete trigger operation. After executing the select statement on the product_table we can see that whichever value we want to delete is deleted from the table as shown below.

![image](https://user-images.githubusercontent.com/103866475/236674038-107d9831-20dd-4abb-b41f-6efe6542625b.png)


3. Update Trigger

In this trigger we perform an update trigger operation. Same as above triggers firstly we have to create a table and use select statements to display the table and we also create another table and insert the values in that table. For performing an update trigger operation we have to use the update trigger statement as shown in below screenshot. So in this trigger we update the values in the table for below example we update the product id. The old product id was 105 so we have updated it from 105 to the new product id as 106. After executing the statements we can see that product id is updated in the table.

![image](https://user-images.githubusercontent.com/103866475/236674050-a625d364-6625-46aa-83d4-e04ebe0cccf0.png)


This trigger is defined on the “product_backup” table and is triggered after any insert, update or delete operation is performed on the table.

Active databases and triggers are powerful tools for managing and analyzing large volumes of data in real-time, and they are widely used in a variety of industries and applications, including finance, healthcare, logistics, and more.

Active databases and triggers are an essential part of modern database management systems. They enable real-time monitoring and automated responses to events, helping to maintain data integrity and consistency. By using triggers, active databases can execute predefined actions or workflows automatically, reducing the workload for database administrators and improving the overall efficiency of the database system.

## References:

    Paton, Norman W., and Oscar Diaz. “Active database systems.” ACM Computing Surveys (CSUR) 31.1 (1999): 63–103.
    Dayal, Umeshwar. “Ten years of activity in active database systems: What have we accomplished?.” Active and Real-Time Database Systems (ARTDB-95) Proceedings of the First International Workshop on Active and Real-Time Database Systems, Skövde, Sweden, 9–11 June 1995. Springer London, 1996.
    Sistla, A. Prasad, and Ouri Wolfson. “Temporal triggers in active databases.” IEEE Transactions on Knowledge and Data Engineering 7.3 (1995): 471–486.
    Widom, Jennifer, and Stefano Ceri, eds. Active database systems: Triggers and rules for advanced database processing. Morgan Kaufmann, 1995.
    Halse, Gambhir, and Malakappa Shirdhonkar. “An Overview of Active Database: Model, Architecture and Challenges.”
    Active Database Systems: Triggers and Rules for Advanced Database Processing (The Morgan Kaufmann Series in Data Management Systems) Hardcover — Import, 4 October 1995 by Jennifer Widom (Editor), Stefano Ceri (Editor).
