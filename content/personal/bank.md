+++
title = "Creating a Bank Bankend with Spring Boot"
date = "2023-12-30"
tags = [
    "java",
    "work-in-progress",
    "sql",
    "database",
]
+++
This project focuses on creating a bank backend using Spring Boot. It utilizes Spring Data JPA to interact with a postgres database. It also implements a REST API to perform CRUD operations on the database.
<!--more-->
**[code](https://github.com/le-que/bank)**

Here is the EER diagram for the database:

![static](/img/image.png)

Here is an example for the bank table using Postman to visualize (the example below is shown in raw format, while the rest will be shown in pretty format):
![static](/img/bankGet.png)

### Adding a new bank:

Here is an example where the new bank has the same id as an existing bank:

![static](/img/bankD.png)

While this one has a unique id:

![static](/img/bankPost.png)
![static](/img/bankAPost.png)

### Deleting a bank:

![static](/img/bankDel.png)
![static](/img/bankDelA.png)