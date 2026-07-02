# DVD Store Franchise DBMS — SQL & PL/SQL

A database management systems project for modeling and managing a fictional DVD store franchise named **The Velvet Stage**.

The project was developed for the **Database Management Systems** course and focuses on relational database design, SQL implementation, PL/SQL programming, triggers, stored procedures, functions, and reusable database packages.

The database supports the management of multiple DVD stores, employees, films, store inventories, customers, orders, rentals, categories, languages, actors, directors, and business rules related to DVD sales and rentals.

---

## Overview

This project models a chain of DVD stores where customers can either **buy** or **rent** DVDs directly from physical franchise locations.

The system supports:

- Multiple franchise stores
- Store employees
- Film inventory per store
- Film categories and directors
- Actors and film casts
- Film translation languages
- Customers
- DVD orders
- DVD rentals
- Rental return dates
- Pricing logic for orders and rentals
- Business-rule validation using PL/SQL triggers and procedures

The goal of the project was to design and implement a complete database system starting from business requirements and ending with SQL schema creation, populated data, stored program units, triggers, and PL/SQL packages.

---

## Database Design

The project includes both an **Entity-Relationship Diagram** and a **conceptual database model**.

The database models relationships such as:

- A store has multiple employees.
- An employee may work in multiple stores.
- A store contains multiple films in its inventory.
- A film belongs to one category.
- A film has one director.
- A film can have multiple actors.
- A film can be translated into multiple languages.
- A customer can place orders and rent films.
- Orders and rentals can contain multiple films.

### Entity-Relationship Diagram

<img width="1597" height="737" alt="Screenshot 2026-07-02 171948" src="https://github.com/user-attachments/assets/d98b734a-9c76-48bb-a558-eb404f5d16ae" />

### Conceptual Database Model

<img width="1598" height="736" alt="Screenshot 2026-07-02 172002" src="https://github.com/user-attachments/assets/56e9cab1-71e0-447d-8c0b-54243b55cfb4" />

---

## Main Entities

The database schema includes the following main entities and relationship tables:

- `store_mng`
- `employee_mng`
- `works_in`
- `category_mng`
- `director_mng`
- `film_mng`
- `store_inventory`
- `actor_mng`
- `acts_in`
- `language_mng`
- `translated_to`
- `customer_mng`
- `rental_mng`
- `rental_consists_of`
- `order_mng`
- `order_consists_of`

The schema includes primary keys, foreign keys, unique constraints, cascading delete rules, and many-to-many relationship tables.

---

## Business Rules

The database was designed around several business rules:

- Each store must have at least one film in its inventory.
- Each store must have at least one employee.
- Employees can process both orders and rentals.
- Orders and rentals are completed in-store.
- Rental and purchase prices are stored separately.
- A rental return deadline is associated with each rental.
- Films belong to one category.
- Films are directed by one director.
- Films may have translations in several languages.
- Film ratings are constrained between 1 and 10.
- Orders and rentals may include multiple films.

---

## SQL Implementation

The project includes SQL scripts for:

- Creating sequences
- Defining relational tables
- Adding primary and foreign keys
- Implementing constraints
- Creating many-to-many relationship tables
- Inserting coherent sample data
- Modeling stores, films, employees, customers, orders, and rentals

### Table Definition and Constraints

Example table definition for the film entity, including primary key, required attributes, prices, rating, and foreign key references to directors and categories.

<img width="1560" height="540" alt="Screenshot 2026-07-02 172016" src="https://github.com/user-attachments/assets/af4d318f-3f07-45c3-9062-842dc94ef40d" />

---

## Sample Data

The database was populated with coherent sample data for multiple franchise locations, employees, films, categories, languages, customers, rentals, orders, and inventory relationships.

### Populated Employee Table
<img width="1698" height="731" alt="Screenshot 2026-07-02 172037" src="https://github.com/user-attachments/assets/de35be2d-b688-4970-bd4b-0fe2075fabeb" />

---

## PL/SQL Procedures and Functions

The project includes several independent PL/SQL stored program units.

### Procedure Using Collections

A stored procedure retrieves the list of actors who appear in at least one comedy film. The implementation uses different PL/SQL collection types, including a `VARRAY` and an indexed table, together with `BULK COLLECT`.

<img width="1585" height="731" alt="Screenshot 2026-07-02 172050" src="https://github.com/user-attachments/assets/1cdc7816-f6df-4a9f-a4ef-13e30259d9b4" />

### Procedure Using Cursors

A procedure lists, for each store in the franchise, the employees who processed at least one order in a selected year. This demonstrates cursor usage and iteration over store-specific results.

<img width="1698" height="836" alt="image" src="https://github.com/user-attachments/assets/4eb3de9f-20d2-40b9-87ca-4cc386918678" />

### Function Using Multiple Tables

A function determines the number of directors associated with films in a selected store whose rating is above a specified value. It includes validation logic and exception handling for invalid store names and invalid rating values.

<img width="1699" height="835" alt="image" src="https://github.com/user-attachments/assets/27ab3fda-fa31-4aa0-9341-1a1ebc1303e3" />

### Procedure Using Multi-Table Queries

A procedure displays the films rented by a selected customer that are translated into a selected language. This uses joins across customers, rentals, films, and translation tables.

<img width="1695" height="833" alt="image" src="https://github.com/user-attachments/assets/8aca016c-56a0-4330-a1d3-615940a25aa3" />

---

## Triggers

The project includes several trigger types used to enforce business rules and automate database behavior.

### Statement-Level DML Triggers

Statement-level triggers restrict updates to order and rental tables outside the allowed working schedule.

<img width="1091" height="508" alt="image" src="https://github.com/user-attachments/assets/c5ede435-5793-4d60-9740-501e33d5670f" />
<img width="1253" height="692" alt="image" src="https://github.com/user-attachments/assets/b0493bb5-8ac2-4714-89a2-e0e896ec4dd0" />

### Row-Level DML Triggers

Row-level triggers automatically update order and rental prices when films are inserted, updated, or deleted from order/rental composition tables.

These triggers help keep the total order and rental prices synchronized with the films included in each transaction.

<img width="1659" height="748" alt="image" src="https://github.com/user-attachments/assets/aa1f6aa3-c7e5-4ee5-bf50-1a22ba311e0f" />

### DDL Trigger

A schema-level DDL trigger restricts structural database changes to a specific authorized user.

<img width="1253" height="427" alt="image" src="https://github.com/user-attachments/assets/6c753c84-a17a-4388-9e93-10e77880fc5a" />

---

## PL/SQL Packages

The project organizes stored logic into reusable PL/SQL packages.

### General Package

The first package groups the main stored procedures and functions developed throughout the project, including procedures for actors in comedy films, employees processing orders, director counts by rating, and rented films by translation language.

### Package Specification

<img width="1253" height="522" alt="image" src="https://github.com/user-attachments/assets/cac87c7b-b7d8-44ee-adfa-cbad0ebfcab5" />

### Package Body

<img width="1253" height="586" alt="image" src="https://github.com/user-attachments/assets/cc1606b5-ec85-4a64-a227-41ac4d0113a7" />

### Integrated Business-Flow Package

A second package includes more complex database operations, such as:

- Calculating average spring sales profit for a store
- Updating DVD purchase prices when profit is below a threshold
- Returning the employee of the month for a given store and period
- Displaying the top 5 most sold and rented films for a store
- Calculating average annual profit for a film category

---

## Tech Stack

- **Database:** Oracle Database
- **Languages:** SQL, PL/SQL
- **Tools:** Oracle SQL Developer / SQL environment
- **Concepts:** Relational database design, ERD, conceptual modeling, constraints, triggers, stored procedures, functions, cursors, collections, packages, exception handling

---

## Project Focus

This project focuses on applying database management concepts to a realistic business scenario.

The main learning goals included:

- Designing a relational database from business requirements
- Creating an ERD and conceptual schema
- Implementing SQL tables and constraints
- Populating a relational database with coherent sample data
- Writing PL/SQL stored procedures and functions
- Using collections, cursors, exceptions, and multi-table queries
- Implementing triggers for business logic and database protection
- Structuring reusable database logic through packages

---

## Repository Structure

The repository contains the SQL and PL/SQL implementation of the DVD store franchise database management system, including schema creation, sample data, stored procedures, functions, triggers, and packages.

Suggested structure:

```text
DVDStore-DBMS/
│
├── schema/
│   └── create_tables.sql
│
├── data/
│   └── insert_data.sql
│
├── plsql/
│   ├── procedures.sql
│   ├── functions.sql
│   ├── triggers.sql
│   └── packages.sql
│
└── README.md![Uploading Screenshot 2026-07-02 171948.png…]()
