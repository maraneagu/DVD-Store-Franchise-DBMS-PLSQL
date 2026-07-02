# DVD Store Franchise DBMS — SQL & PL/SQL

A database management systems project for modeling and managing a fictional DVD store franchise named **The Velvet Stage**.

The project was developed for the **Database Management Systems** course and focuses on relational database design, SQL implementation, PL/SQL programming, triggers, and reusable database packages.

The database supports the management of multiple DVD stores, employees, films, inventory, customers, orders, rentals, categories, languages, actors, directors, and business rules related to sales and rentals.

---

## Project Overview

This project models a chain of DVD stores where customers can either buy or rent DVDs directly from physical store locations.

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

The database was designed to support both operational management and analytical queries across the franchise.

---

## Database Design

The project includes both an **Entity-Relationship Diagram** and a **conceptual database model**.

The database models relationships such as:

- A store has multiple employees
- An employee may work in multiple stores
- A store contains multiple films in its inventory
- A film belongs to one category
- A film has one director
- A film can have multiple actors
- A film can be translated into multiple languages
- A customer can place orders and rent films
- Orders and rentals may contain multiple films

---

## Main Entities

The main database entities include:

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

The schema includes primary keys, foreign keys, unique constraints, cascading delete rules, and relationship tables for many-to-many associations.

---

## Business Rules

The database was designed around several business rules, including:

- Each store must have at least one film in its inventory.
- Each store must have at least one employee.
- Employees can process both orders and rentals.
- Orders and rentals are completed in-store.
- Rental and purchase prices are stored separately.
- Rental return dates are calculated based on the rental date.
- Films belong to one category.
- Film ratings are constrained between 1 and 10.
- Films may have translations in several languages.

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

The database is populated with sample data for multiple franchise locations and a large collection of films, actors, directors, customers, employees, orders, rentals, and inventories.

---

## PL/SQL Procedures and Functions

The project includes several independent stored program units.

### Procedure using collections

A procedure that displays actors who appear in at least one comedy film, using different PL/SQL collection types.

### Procedure using cursors

A procedure that lists, for each franchise store, the employees who processed at least one order in a given year.

### Function using multiple tables

A function that determines the number of directors associated with films in a selected store whose rating is above a specified value.

### Procedure using multi-table queries

A procedure that displays the films rented by a customer that are translated into a selected language.

These program units include SQL joins, PL/SQL collections, cursors, exception handling, and business-rule validation.

---

## Triggers

The project includes multiple trigger types.

### Statement-level DML triggers

Triggers restrict updates to order and rental tables outside the allowed working schedule.

### Row-level DML triggers

Triggers automatically update order and rental prices when films are inserted, updated, or deleted from order/rental composition tables.

### DDL trigger

A schema-level trigger restricts structural database changes to a specific authorized user.

---

## PL/SQL Packages

The project organizes stored logic into reusable PL/SQL packages.

### General package

A package containing the main stored procedures and functions developed throughout the project.

### Integrated business-flow package

A second package includes more complex operations, such as:

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
- **Concepts:** Relational database design, ERD, normalization, constraints, triggers, stored procedures, functions, cursors, collections, packages, exception handling

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

## Repository

This repository contains the SQL and PL/SQL implementation of a DVD store franchise database management system, including schema creation, sample data, stored procedures, functions, triggers, and packages.
