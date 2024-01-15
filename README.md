# Stored Procedures
* Kimberly Collins
* SQL Server database developer for 17 years

## What is a stored procedure?
A collection of SQL statements that is stored on the database server for later execution
* Can have input and output parameters
* SQL statement(s) that select or modify data
* Often abbreviated `SP` or `SPROC`

## Structure
    CREATE PROCEDURE ProcedureName
        @Parameter1 DataType,
        @Parameter2 DataType
    AS
    BEGIN
        --SQL statement(s) defining the logic of the stored procedure
    END

## Example
    CREATE PROCEDURE GetEmployeeDetails
        @EmployeeID INT
    AS
    BEGIN
        SELECT * 
        FROM Employees 
        WHERE EmployeeID = @EmployeeID
    END

## Stored Procedures vs Views
* Stored Procedure:
    * Can use variables and one or more SQL statements to select data
    * Can have input and output parameters
    * `EXECUTE GetEmployeeDetails 123`
* View:
    * Represents a virtual table based on a predefined query
    * Cannot have variables, multiple statements, or parameters
    * `SELECT * FROM EmployeeSummary WHERE EmployeeID = 123`

## Stored Procedures vs Functions
* Stored Procedure: 
    * Executes a series of SQL statements, such as modifying data or running * complex queries
    * `EXECUTE GetEmployeesByDepartment 123`
* Function: 
    * Returns a value or a table result that can be used in SQL
    * `SELECT GETDATE()`
    * `SELECT Value FROM STRING_SPLIT('1,2,3', ',')`

## Why use Stored Procedures?

### Aggregating data (SUM, AVG, COUNT, etc.)

### Batch processing - updating large sets of data in a single operation

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
  * As needed, usually along with an ORM

## Questions?
* `#databases` channel
* `@KimberlyCollins`
