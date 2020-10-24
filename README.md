## MYSQL-AddressBook
### UC-1 Create DataBase for AddressBook Service
`CREATE DATABASE Address_Book_Service;`
#### Use the Created DataBase
`USE Address_Book_Service;`
### UC-2 Create Address_Book Table
```
 CREATE TABLE Address_Book
    ->   (    FirstName    varchar(150) NOT NULL,
    ->        LastName     varchar(150) NOT NULL,
    ->        Address      varchar(200) NOT NULL,
    ->        City         varchar(200) NOT NULL,
    ->        State        varchar(200) NOT NULL,
    ->        Zip          int(6)       NOT NULL,
    ->        PhoneNumber  int(10)      NOT NULL,
    ->        Email        varchar(300) NOT NULL,
    ->       PRIMARY KEY  (FirstName)
    ->     );
 ```
 #### Show Address_Book Table
 ` DESCRIBE Address_Book;`
