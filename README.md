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
### UC-10 Count of Persons by type
``` SELECT type,COUNT(type) FROM Address_Book GROUP BY type;```
### UC-11 Add Person to Friend and Family
```INSERT INTO address_book(FirstName,LastName,Address,City,State,Zip,PhoneNumber,Email,Type,AddressBookName) VALUES
    -> ('Chaitanya','Rangu','Tadepalligudem','WestGodavari','AndhraPradesh',531106,901417141,'chaitanyarangu@gmail.com','Friends','Personal'),
    -> ('Suryanarayana','Allu','Tuni','EastGodavari','AndhraPradesh',533401,949361331,'suryam_allu@gmail.com','Family','Personal');
```
#### Show Updated Table
``` SELECT * FROM Address_Book;```
### UC-13 Ensure Working of Retrieve Queries
#### Drop table address_book
```DROP TABLE address_book;```

#### Creating table Address_Book_Dictionary
```CREATE TABLE Address_Book_Dictionary
    -> (
    -> Address_Book_Name VARCHAR(200) NOT NULL PRIMARY KEY,
    -> Address_Book_Type VARCHAR(150) NOT NULL
    -> );
 ```
#### Creating table Contacts
```CREATE TABLE contacts
    -> (
    -> firstName    varchar(150) NOT NULL,
    -> lastName     varchar(150) NOT NULL,
    -> Address_Book_Name VARCHAR(200) NOT NULL,
    -> FOREIGN KEY (Address_Book_Name) REFERENCES Address_Book_Dictionary (Address_Book_Name),
    -> Address      varchar(200) NOT NULL,
    -> City         varchar(200) NOT NULL,
    -> State        varchar(200) NOT NULL,
    -> Zip          int(10)      NOT NULL,
    -> Phone_Number int(15)      NOT NULL,
    -> Email        varchar(300) NOT NULL,
    -> PRIMARY KEY  (firstName,lastName)
    -> );
 ```
#### Inserting records into Address_Book_Dictionary table
```INSERT INTO Address_Book_Dictionary VALUES
    -> ('Personal','Family'),
    -> ('Corporate','Professional'),
    -> ('Casual','Friends');
```
#### Inserting records into Contacts
```INSERT INTO contacts VALUES
    -> ('M S','Dhoni','Casual','Balaji nagar','Chennai','Tamil Nadu',500001,9440293758,'msdhoni@gmail.com'),
    -> ('Virat','Kohli','Personal','Shanthi nagar','Bangalore','Karnataka',500050,9494118273,'vkohli@gmail.com'),
    -> ('Rohit','Sharma','Corporate','Anderi','Mumbai','Maharashtra',500010,7207020464,'rohit@gmail.com');
```    
#### Ability to Retrieve Person belonging to a City or State
```SELECT * FROM contacts WHERE City='Bangalore';
SELECT * FROM contacts WHERE State='Maharashtra';
Ability to understand the size of address book by City and State
SELECT city,COUNT(city) FROM contacts GROUP BY city;
SELECT state,COUNT(state) FROM contacts GROUP BY state;
Ability to retrieve entries sorted alphabetically by Person’s name for a given city
SELECT * FROM contacts WHERE city='Chennai' ORDER BY firstName;
Ability to get number of contact persons(count by type)
SELECT a.Address_Book_Type,COUNT(a.Address_Book_Type) FROM Address_Book_Dictionary a LEFT JOIN contacts c ON c.Address_Book_Name=a.Address_Book_Name GROUP BY a.Address_Book_Type;
```
