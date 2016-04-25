/*Exercise 1

Connect to the MySQL instance within your Workspace using your Cloud9 username
*/
--start MySQL server: mysql-ctl start
--connect to MySQL server: mysql -u [username]

/*
Exercise 2

Create a database named decodemtl_test within MySQL

Create a database named decodemtl_addressbook within MySQL
*/

DROP DATABASE IF EXISTS `decodemtl_test`;
CREATE DATABASE `decodemtl_test`;

DROP DATABASE IF EXISTS `decodemtl_addressbook`;
CREATE DATABASE `decodemtl_addressbook`;
/*

Exercise 3

Remove database named decodemtl_test from MySQL
*/

DROP DATABASE `decodemtl_test`;

/*
Exercise 4

Return the list of databases within MySQL
*/

show databases;



--Exercise 5
--Create table Account for database decodemtl_addressbook

USE decodemtl_addressbook;
DROP TABLE IF EXISTS `Account`;
CREATE TABLE `Account`
(
    id int not null auto_increment,
    email varchar(255),
    password varchar(40),
    createdOn datetime,
    modifiedOn datetime,
    PRIMARY KEY(id)
);


--Create table AddressBook for database decodemtl_addressbook
USE decodemtl_addressbook;
DROP TABLE IF EXISTS `AddressBook`;
CREATE TABLE `AddressBook`
(
    id int not null auto_increment primary key,
    accountid int,
    name varchar(255),
    createdOn datetime,
    modifiedOn datetime,
    FOREIGN KEY(accountid) REFERENCES Account(id)
);




--Create table Entry for database decodemtl_addressbook
USE decodemtl_addressbook;
DROP TABLE IF EXISTS `Entry`;
CREATE TABLE `Entry`
(
    id int not null auto_increment primary key,
    addressBookId int,
    firstName varchar(255),
    lastName varchar(255),
    birthay datetime,
    type enum (home,work,other),
    subtype enum(phone,address,email),
    contentLineOne varchar(255),
    contentLineTwo varchar(255),
    contentLineThree varchar(255),
    contentLineFour varchar(255),
    contentLineFive varchar(255)
);
--Create table Test for database decodemtl_addressbook
USE decodemtl_addressbook;
DROP TABLE IF EXISTS `Test`;
CREATE TABLE `Test`
(

);






--Exercise 6
--Remove table Test for database decodemtl_addressbook
DROP TABLE IF EXISTS `Test`;


--Exercise 7
--Return list of tables within database decodemtl_addressbook
USE decodemtl_addressbook;
show tables;


--Exercise 8

--Reflect the data model shown in schema/addressbook_denormalized.png within database decodemtl_addressbook
/*
Account.id is a primary auto-increment key

AddressBook.id is a primary auto-increment key

Entry.id is a primary auto-increment key

Entry.type is an ENUM column permitting home, work and other

Entry.subtype is an ENUM column permitting phone, address and email
*/

/*
Exercise 9			
			
Create a data model representing a Barn with Chickens :hatching_chick:			
			
This model should provide answers to the following questions:			
			
How many rooster, hen and chicks existed in the Barn on a specific date			
			
How many chicks will come to age on a specific date			
			
			
			
			
table: Chickens			
chickenId	int	not null	PK, auto increment
name	varchar(75)	null	
birthDate	datetime	not null	
deceasedDate	datetime	null	
sex	enum(male,female)	not null	
			
			
			
			
			
Exercise 10 (Workshop Challenge)			
			
Create a data model representing a Hotel with Floors and Rooms :hotel:			
			
This model should provide answers to the following questions:			
			
The list of Rooms available for rent on a specific date			
			
The list of Rooms which can be occupied by at least 3 people on a specific date			
			
The amount of unrentable Rooms (janitor closets, public laundry room, gym, etc.)			
			
The amount of Rooms having a private Kitchen			
			
The average amount of windows per Floor			
			
The amount of Floors having Rooms with carpets			
			
			
table: Floors			
floorId	int	not null	PK, auto increment
floorNumber	varchar(10)	not null	
			
			
table: Rooms			
roomId	int	not null 	PK, auto increment
doorNumber	varchar(25)		
phoneExt	varchar(25)		
capacity	int		
windows	int		
withKitchen	enum(Y,N)		
floorId	int		FK
roomTypeId	int		FK
floroMaterialId	int		FK
			
			
			
table: floorMaterials			
floorMaterialId	int	not null	PK, auto increment
name	varchar(75)	not null	
			
			
table: RoomTypes			
roomTypeId	int	not null	PK, auto increment
name	varchar(75)		
description	varchar(255)		
rentable	enum(Y,N)		
			
table: ReservationLog			
reservationId	int	not null	PK, auto increment
startDate	datetime		
endDate	datetime		
roomId	int		FK
customerId*	int		FK
employeeId*	int		FK
logDate	datetime		
			
table: RoomTransLog			
roomTransLogId	int	not null	PK, auto increment
roomId	int	not null	FK
roomTransTypeId	int	not null	FK
logDate	datetime		
customerId*	int		FK
employeeId*	int		FK
			
table: RoomTransType			
roomTransTypeId	int	not null	PK, auto increment
name	varchar(75)	not null	
			
			
*Fields from tables assumed to exist, but not explicitly shown in this diagram			

*/