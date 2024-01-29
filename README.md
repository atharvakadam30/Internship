# sql tasks of stored procedure
```SQL
Create database EmployeeDB;
CREATE DATABASE EmployeeDb;
USE EmployeeDb;


ALTER TABLE MasterDesignation(
ID INT PRIMARY KEY IDENTITY(1,1),
DesignationName VARCHAR(30),
);

INSERT INTO MasterDesignation (DesignationName) VALUES ('Manager');
INSERT INTO MasterDesignation (DesignationName) VALUES ('Developer'); 
INSERT INTO MasterDesignation (DesignationName) VALUES ('Analyst');


CREATE TABLE Employee(
ID INT PRIMARY KEY IDENTITY(1,1), EmpName VARCHAR(50),
Birthdate DATE,
DesignationID INT FOREIGN KEY REFERENCES MasterDesignation(ID), Gender INT,
EmailID VARCHAR(50), MobNO VARCHAR(20),
);

select * from MasterDesignation;
GO
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
ALTER PROCEDURE Usp_InsertNewRecord
@EmpName VARCHAR(50),
@Birthdate DATE,
@DesignationID INT,
@Gender INT,
@EmailID VARCHAR(50), 
@MobNO VARCHAR(20)
AS
BEGIN
	INSERT INTO Employee(EmpName, Birthdate, DesignationID, Gender, EmailID, MobNO)
	VALUES(@EmpName, @Birthdate, @DesignationID, @Gender, @EmailID, @MobNO);
 END

EXEC Usp_InsertNewRecord @EmpName='Atharva', @Birthdate='2001-12-30', @DesignationID=1, @Gender=1, @EmailID='atharva@gmail.com', @MobNo='2748731798';
EXEC Usp_InsertNewRecord @EmpName='Amit', @Birthdate='2002-1-3', @DesignationID=1, @Gender=1, @EmailID='amit@gmail.com', @MobNo='2748735778';
EXEC Usp_InsertNewRecord @EmpName='Rohit', @Birthdate='2002-11-23', @DesignationID=1, @Gender=1, @EmailID='rohit@gmail.com', @MobNo='1234567898';

use EmployeeDb;
SELECT * FROM Employee;


--- update query-------
GO
ALTER PROCEDURE Usp_UpdateEmployeeList 
@EmployeeID INT,
@NewEmpName VARCHAR(50),
@NewBirthdate DATE,
@NewDesignationID INT,
@NewGender INT,
@NewEmailID VARCHAR(50),
@NewMobNO VARCHAR(20)
AS BEGIN
UPDATE Employee
SET EmpName=@NewEmpName,
Birthdate=@NewBirthdate,
DesignationID=@NewDesignationID,  
EmailID=@NewEmailID,
MobNO=@NewMobNO
WHERE ID=@EmployeeID;
END;

EXEC Usp_UpdateEmployeeList @EmployeeID=3, @NewEmpName='Aman',@NewBirthdate ='1-1-2001',@NewDesignationID=2,@NewEmailID='aman@gmail.com',@NewMobNO='2345678901'



---Update query----
GO
ALTER PROCEDURE Usp_DeleteEmployeeDetails
@EmployeeID INT
AS BEGIN

DELETE FROM Employee WHERE ID=@EmployeeID;

END;

EXEC Usp_DeleteEmployeeDetails @EmployeeID=5;


GO
CREATE PROCEDURE Usp_GetEmployeeDetails
@EmployeeID INT,
@NewEmpName VARCHAR(50),
@NewBirthdate DATE,
@NewDesignationID INT,
@NewGender INT,
@NewEmailID VARCHAR(50),
@NewMobNO VARCHAR(20)
AS BEGIN
select*from Employee;
END;

----Get procedre Query------
CREATE PROCEDURE Usp_Getdetails
AS
BEGIN
select * from Employee;
END

EXEC Usp_details

----Drop Down-----
CREATE PROCEDURE Usp_MasterDesignation
AS
BEGIN
select * from MasterDesignation;
END
EXEC Usp_MasterDesignation

```
