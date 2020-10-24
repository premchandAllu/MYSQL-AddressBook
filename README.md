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
 ### UC-3 Insert Into Table
 ```
INSERT INTO address_book(FirstName,LastName,Address,City,State,Zip,PhoneNumber,Email) VALUES
     ('Premchand','Allu','Tuni','EastGodavari','AndhraPradesh',533401,766008866,'premchandallu@gmail.com'),
     ('Bhanuchand','Allu','MadhuraNagar','Hyderabad','Telangana',500019,916699211,'bhanuchandallu@gmail.com'),
     ('DevaHarsha','Allu','DilsukhNagar','Hyderabad','Telangana',500020,998903355,'devaharsha@gmail.com');
 ```
 #### Show the entries
 ` SELECT * FROM Address_Book;`
