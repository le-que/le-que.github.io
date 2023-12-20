+++
title = "Database Systems"
date = "2021-08-05"
description = "A brief description of Hugo Shortcodes"
tags = [
    "mySQL","Database"
]
+++
Introduction to designing and implementing modern database systems in large-scale enterprise applications, covering the conceptual representation of data, conversion to specific models like the relational data model, utilization of SQL for defining relations and executing data operations, exploration of relation forms with favorable properties, and a conclusion with advanced topics in database management.
<!--more-->

## Scenario Description
The system, named "Groceries Express! Drone Delivery," is designed to facilitate the delivery of grocery items to customers through a third-party grocery service.

### User Management:

* Users include customers and employees of grocery stores.
* Each user has a distinct username, first name, last name, address, and birthdate.
* Birthdate is stored in "yyyy-mm-dd" format and is used for user authentication and sending birthday greetings.
* Some users may not share their birthdate but must provide their name and address for drone deliveries, tax, and salary purposes.

### Employee Roles:

* Employees can have various roles, such as floor workers or drone pilots.
* Drone pilots are unique and cannot simultaneously be floor workers. They control drones for grocery deliveries.
* Employee roles like financial data analysts or logistical coordinators are not explicitly tracked in the system.

### Store Management:

* Each store has a distinct identifier, a possibly duplicated longer name, and tracks revenue from successful deliveries.
* Stores are supported by various employees, and each store has a floor worker acting as the overall manager.
Each floor worker must be employed by at least one store.

### Drone Management:

* Drones are used for delivering orders and are associated with specific stores.
* Each drone has a unique identifier, limited capacity, and needs maintenance after a certain number of trips.
* A drone must be controlled by one pilot at a time, and each drone pilot must have a valid license.

### Order Management:

* Customers place orders, each assigned to a specific drone for delivery.
* Orders consist of multiple lines, each representing a quantity of a specific item.
* Customers have a rating (1 to 5) based on reliability and a credit balance.
* The system calculates and displays the cost and weight of orders, ensuring the customer's credit covers existing and new orders.
* Each item can appear only once on an order, but the quantity can vary.

### System Constraints:

* Names and identifying attributes are limited to 40 characters (unless specified otherwise).
* Descriptive attributes are limited to 100 characters, and addresses can be up to 500 characters.
* The system must enforce safety measures for drone pilots, such as not allowing them to control multiple drones simultaneously.

## Phase 1
Translate the requirements into an (Enhanced) Entity-Relationship Diagram (EERD).

![static](/img/post/EERD.jpg?width=100px)

### Phase 3
* Implement fifteen (15) stored procedures which allow the system operators to modify the
database state in accordance with the main use case (i.e., taking orders & delivering groceries)
* Implement seven (7) views which provide information to the system operators about the
database state from various "points of view" (i.e., system operator roles)
