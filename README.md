# Record

**Record** is an early .NET relational object mapper (ORM), originally developed in **2006**. It was created to reduce the repetitive ADO.NET code involved in mapping database rows to objects and performing common data-access operations.

## Why it was built

In the mid-2000s, .NET developers often wrote data access by hand with ADO.NET commands, readers, and `DataSet`/`DataTable` code. Record was an attempt to put a lightweight object-oriented layer over that work: describe a database record as a .NET type, then let the library handle much of the routine mapping and SQL command execution.

This is a piece of software history, not a modern ORM recommendation. The project dates from an era before Entity Framework and today's established .NET data-access ecosystem; that does not mean no ORM tools existed, but the available conventions and choices were very different from those developers have now.

## What the library did

The source code shows support for:

- **Attribute-based mapping** between record types and database tables. Attributes describe table, catalog and schema names, map properties to columns, and mark primary keys and identity fields.
- **Basic record operations**: load a record by identity or conditions, insert new records, update existing ones, and delete records. Insert operations can retrieve the generated identity value.
- **Query conditions and parameters**, including comparisons such as equality, ranges, `LIKE`, `IN`, and null checks.
- **ADO.NET provider factories** (`DbProviderFactory`) for creating connections, commands, and parameters, with provider options represented for SQL Server, ODBC, OleDb, Oracle and SQL Server Compact. Provider-specific SQL behavior means this should not be assumed to work unchanged with every database.
- **Transactions**, including a helper that runs work in a transaction and commits or rolls it back on failure.
- **Stored procedures and direct commands** for non-query, reader, and scalar operations; stored-procedure results can also be mapped to `Record` types.
- **Record state tracking** to distinguish new records from loaded records and detect changes against the original column values.
- **Extension hooks and command/status events** around loading, saving, and deleting, allowing application code to participate in those operations.

The intent was to make ordinary data access less repetitive, not to provide the broad capabilities expected of a current full-featured ORM.

## Status

Record is a **legacy, historical project** and is not actively maintained. Its APIs, target frameworks, and database behavior reflect the time in which it was written. It is mainly of interest to people studying early .NET data-access approaches or maintaining an existing application that depends on it. Compatibility with current .NET versions and database providers is not guaranteed.

Before using it in a new project, consider a currently maintained data-access library and verify your requirements against its documentation and tests.
