---
layout: post
title: Playing with MySQL stored procedures
---

This is kind of a self note to myself in case I forget how to define Stored Procedures.
I am originally from a MongoDB background so switching to the SQL territory is quite overwhelming lol.

So lets learn about defining SP(stored procedures) in MySQL

## MySQL CREATE PROCEDURE statement

This query returns all products in the products table from the sample database.

`SELECT * FROM pokemons;`

The following statement creates a new stored procedure that wraps the query:

```sql
DELIMITER //
 
CREATE PROCEDURE GetAllPokemons()
BEGIN
    SELECT *  FROM pokemons;
END //
 
DELIMITER ;
```

Congratulation! you have successfully created the first stored procedure in MySQL.

## Syntax

The first and last DELIMITER commands are not a part of the stored procedure. The first DELIMITER command changes the default delimiter to // and the last DELIMITER command changes the delimiter back to the default one which is semicolon (;).

To create a new stored procedure, you use the CREATE PROCEDURE statement.

Here is the basic syntax of the CREATE PROCEDURE statement:

```sql
CREATE PROCEDURE procedure_name(parameter_list)
BEGIN
   statements;
END //
```

In this syntax

* First, specify the name of the stored procedure that you want to create after the CREATE PROCEDURE keywords.

* Second, specify a list of comma-separated parameters for the stored procedure in parentheses after the procedure name.

* Third, write the code between the BEGIN END block. The above example just has a simple SELECT statement. After the END keyword, you place the delimiter character to end the procedure statement.

## Calling a procedure

To execute a stored procedure, we can use the `CALL` statement:

```sql
CALL stored_procedure_name(argument_list);
```

## Passing arguments INTO the procedure

A good procedure takes arguments! We can pass arguments `INTO` the procedure using the `IN` Statement inside the `(` and `)`

```sql
CREATE PROCEDURE getPokemons(
 IN PokemonName NVARCHAR(128)
)
BEGIN
  SELECT * FROM Pokemon where name = PokemonName;
END //
```

Now, lets learn about passing arguments for using OUTSIDE the procedure.

## Passing output OUTSIDE the procedure

To recieve a type-safe output from the procedure, you can simply add a `OUT` statement in the parameter listings.

```
```sql
CREATE PROCEDURE getPokemonID(
 IN PokemonName NVARCHAR(128),
 OUT INT(8)
)
BEGIN
  statements_here;
END //
```

## Yayy, we are good readers.

So finally we have now understood how to use stored procedures. I hope this will be helpful for people on the internet. Good bye :smile:

