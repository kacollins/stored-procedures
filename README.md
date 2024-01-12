# Stored Procedures

## What is a stored procedure?
  A collection of SQL statements that are stored on the database server for later execution
* Can have input and output parameters
* SQL statement(s) that select or modify data

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
    * Can use one or more SQL statements to select data
    * Can have input and output parameters
    * EXECUTE GetEmployeeDetails 123
* View:
    * Represents a virtual table based on a predefined query
    * Cannot have parameters or multiple statements
    * SELECT * FROM EmployeeSummary WHERE EmployeeID = 123

## Stored Procedures vs Functions
* Stored Procedure: 
    * Execute a series of SQL statements, such as modifying data or running * complex queries
    * EXECUTE GetEmployeesByDepartment 123
* Function: 
    * Return a value or a table result that can be used in SQL
    * SELECT GETDATE()
    * SELECT Value FROM STRING_SPLIT('1,2,3', ',');

## Stored Procedures vs Application Code
* Set of multiple SQL statements
    * Single SP call - reduce network traffic
    * Transaction - ensure that the entire set succeeds or fails as a single unit
* Aggregations (SUM, AVG, COUNT, etc.)
* Batch processing - updating large sets of data in a single operation
* Performance improvements
    * Query plan caching
    * Indexes
