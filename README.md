# postgres-powershell
a DB module to access a Postgres DB from Powershell

## Motivation
This Powershell module simplifies the use of psql to access a Postgres database from Powershell.

All interactions with Postgres are done with the Powershell function InvokePgSqlCmd.

## Authentication to Postgres
We are using the paramters -Server, -Port and -Database to specify the Postgres database.
The connecting UserID is specified with parameter -User.

No password is handed over to Postgres. Therefore it has to be set externally.

One method would be to supply the environment variable PGPASSWORD. 
Another method is to supply the file .pgpass in the users home directory.

## Function InvokePgSqlCmd
The function InvokePgSqlCmd uses these parameters:
* -InputFile - the input file containing the SQL statements to be executed, terminated by ;
* -Query - a string containing the SQL statements to be executed, terminated by ;
* -Server - the server of the postgres database
* -Port - the port on the server of the postgres database
* -Database - the database to connect with
* -User - the database user that connects to the database
* -Variable - an array of variable-to-value mappings in the form "<variable>=<value>". Each occurence of $(<variable>) in the SQL statement will be replaced by the corresponding <value>.

If the parameter -Query is not specified, the -InputFile is read.

