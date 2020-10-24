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
 ### UC-4 Ability to Edit Contact Using Person Name
 ```
 UPDATE Address_Book SET PhoneNumber=949478262 WHERE FirstName='Premchand';
 ```
 ####  Show Updated Contact
 ```SELECT * FROM Address_Book Where FirstName='Premchand';```
### UC-5 Delete Contact Using Person Name
``` DELETE FROM Address_Book Where FirstName='Premchand';```
#### View AddressBook
``` SELECT * FROM Address_Book;```
### UC-6 Retrieve Persons By State or City
#### By City
``` SELECT * FROM Address_Book Where city = 'Hyderabad';```
#### By State
``` SELECT * FROM Address_Book Where State='Telangana';```
### UC-7 Count By State or City
#### COUNT By City
```SELECT COUNT(City) From Address_Book;```
#### COUNT By State
``` SELECT COUNT(State) From Address_Book;```

### UC-8 Retrieve Entries Sorted Alphabetically
` SELECT * FROM address_book WHERE city='Hyderabad' ORDER BY firstName;`

### UC-9 Ability to Identify AddressBook With name and type

#### Alter Table
```
ALTER table address_book add AddressBookName varchar(200) AFTER Email;
ALTER table address_book add Type varchar(200) AFTER Email;
UPDATE address_book set type='Family' where firstName='Premchand';
UPDATE address_book set type='Friends' where firstName='BhanuChand';
UPDATE address_book set type='Professional' where firstName='DevaHarsha';
UPDATE address_book set AddressBookName='Casual' where firstName='DevaHarsha';
UPDATE address_book set AddressBookName='Personal' where firstName='Premchand' or firstName='Bhanuchand';
```
#### View address book
```SELECT * FROM address_book;```

