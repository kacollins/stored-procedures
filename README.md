# [Stored Procedures in SQL Server](https://simpleslides.dev/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2thY29sbGlucy9zdG9yZWQtcHJvY2VkdXJlcy9tYWluL1JFQURNRS5tZA==)
* Kimberly Collins
* SQL Server database developer for 17 years
* [github.com/kacollins/stored-procedures](https://github.com/kacollins/stored-procedures)

## What is a stored procedure?
A collection of SQL statements stored on the database server for later execution
* Can have input and output parameters
* SQL statement(s) to select or modify data
* Often abbreviated `SP` or `SPROC`

## Structure of a Stored Procedure
    CREATE PROCEDURE ProcedureName
        @Parameter1 DataType,
        @Parameter2 DataType
    AS
    BEGIN
        --SQL statement(s) defining the logic of the stored procedure
    END

## Example of a Stored Procedure
    CREATE PROCEDURE GetEmployeeDetails
        @EmployeeID INT
    AS
    BEGIN
        SELECT * 
        FROM Employees
        --Probably join to some other tables
        WHERE EmployeeID = @EmployeeID
    END

| View | Stored Procedure |
| ---- | ---------------- |
| * Represents a virtual table based on a predefined query | * Can use variables and one or more SQL statements to select or modify data |
| * Can't have variables, multiple statements, or parameters | * Can have input and output parameters |
| `SELECT *`<br>`FROM EmployeeSummary`<br>`WHERE EmployeeID = 123`|  `EXEC GetEmployeeDetails 123` |

| Function | Stored Procedure |
| -------- | ---------------- |
| * Returns a single value or a table that can be used in SQL | *  Can have multiple output parameters but doesn't necessarily return data |
| * Not intended to modify data | * Can be used to modify data |
| `SELECT GETDATE()`<br>`SELECT Value`<br>`FROM STRING_SPLIT('1,2,3', ',')`|  `EXEC GetEmployeeDetails 123` |

## Why use Stored Procedures?

### Aggregating data
SUM, AVG, COUNT, etc.

### Batch processing
Updating large sets of data in a single operation

### Complicated [joins](https://www.youtube.com/watch?v=2IGQFucnGR4)

### Set of multiple SQL statements
* Single stored procedure call reduces network traffic
* Transaction ensures that the entire set succeeds or fails as a single unit

### Performance improvements
* Query plan caching
* Indexes

## Typical Uses of Stored Procedures
* Reports
* Called from back end
  * Never - some teams want all business logic in the application code
  * Always - some teams use stored procedures for all data access
  * As needed, usually along with an [ORM](https://www.youtube.com/watch?v=UY7PKt-p6Uk)

## Questions?
* Techlahoma's Slack
  * `#databases` channel
  * `@KimberlyCollins`
* [github.com/kacollins/stored-procedures](https://github.com/kacollins/stored-procedures)
