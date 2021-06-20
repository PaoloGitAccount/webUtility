# webUtility

Notes about project with User Feedback Utility, Azure Sql Server database, deployed to Azure Cloud from gitHub.

Link to the deployment on Azure:
https://userutilityazurewebapp.azurewebsites.net/

Prepared an architecture following SOLID best practices, Entity Framework, with a code-first approach, created the structure of the User class first.

Deployed the application to Azure Cloud using gitHub.

Link to the project on github:
https://github.com/PaoloGitAccount/webUtility

It's possible to switch easily between two versions of the database, a local SQL Database and the Azure SQL Database (default) on the Azure Cloud.

Used as .NET framework, .NET Core 3.1 , Dependency Injection, using a DbContext, DbSet for the User class.

Installed various NuGet packages:

⦁	Install-Package Microsoft.VisualStudio.Web.CodeGeneration.Design -Version 3.1.0
⦁	Install-Package Microsoft.EntityFrameworkCore.Tools -Version 3.1.0
⦁	Install-Package Microsoft.EntityFrameworkCore.SqlServer -Version 3.1.0

connectionstring to the database in the appsettings.json.

It's possible to add/edit/delete/detail/list each user added in the application.

For the Thanks page and the Calendar, used a Javascript structure.


------------------------------------------
--if required, a script can be used to create the database and the tables:
-- as alternative solution, using instead a database first approach.

USE master
IF NOT EXISTS(SELECT * FROM sys.databases WHERE name = 'UserUtilityDb')
  BEGIN
    CREATE DATABASE [UserUtilityDb]
    END
    GO
       USE [UserUtilityDb]
    GO
GO

USE UserUtilityDb
Create Table Users(
Id Int Identity(1,1) Not null Primary Key,
FirstName Varchar(50) Not null,
LastName Varchar(50) Not null,
DateOfBirth DateTime Not null,
CreatedTime DateTime Default(GetDate()) Not Null)
GO

USE UserUtilityDb
Insert Into Users(FirstName, Lastname, DateOfBirth, CreatedTime) 
Values ('John', 'LastName1', '1945-08-20', GetDate())
GO

--SELECT * FROM Users

 
