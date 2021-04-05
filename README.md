# SSIS Exercises

## Variables

This package counts the number of finalists in a text file and displays a message box showing the results.

1. Created a Data Flow Task to count the number of finalists. The Data Flow Task contains a Flat File Data Source and a Row Count transformation. The Flat File Data Source extracts the finalists information from a text file and put into the Row Count transformation. 
2. Created a variable RowNumber to store the number of finalists in the text file.
3. Created a Script Task (using C#)that takes in the RowNumber variable as ReadOnlyVariables and show the number of finalists in a message box.

## Expressions

 This package counts the number of days till New Year's Eve 31st December and displays a message box showing the results and whether today is weekend/weekday.
 
 1. Created several variables to calculate the number of days till New Year's Eve and whether today is weekend/weekday
 2. Created an Expression Task to make the message to be displayed
 3. Created a Script Task (using C#) that takes in the message variable as ReadOnlyVariables and show the number of days till New Year's Eve and whether today is weekend/weekday

## Conditional Split & Derived Columns

This package takes finalists information from a text file, remove all records that has "Tulisa" in Mentor column, change "Cheryl Cole" to "Cheryl Wakerfield" in Mentor column and load the results in tblFinalist1 table in SQL Server

1. Created an Execute SQL Task that delete all data from tblFinalist1 table in SQL Server
2. Created a Data Flow Task that contains a Flat file Data Source, a Conditional Split transformation, Derived Column transformation, Union all transformation and an OLE DB Destination. The Flat File Data Source extracts the finalists data from a text file and put into the conditional split transformation, which direct rows containing Chery Cole to Cheryl Cole output, rows containing Tulisa to Tulisa output and the rest of the rows to Default output. Used Derived Column transformation to change Cheryl Cole to Cheryl Wakerfield in Cheryl Cole Output. Used Union All transformation to union Cheryl Cole output with Default output and used OLEDB Destination to put result in tblFinalist1 table in SQL Server.

## Lookup Transforms

This package takes finalists information from a text file and load into tblFinalist table in SQL server with 2 additional columns displaying the Mentor Id and Notes. If the mentor name in the text file is in the tblMentor table in SQL Server, then the Mentor Id displayed is the Mentor Id for that specific mentor in tblMentor table and Notes displayed is "Imported Ok". Otherwise, Mentor Id desplayed is 9 and Notes displayed is the "specific mentor's name not known"

1. Created a Data Flow Task that loads the mentors into a cache using OLE DB Data Source and Cache Transform transformation.
2. Created an Execute SQL Task that delete all data from tblFinalist table in SQL
3. Created a Data Flow Task that contains  a Flat file Data Source that extract finalists data from a text file and load to Lookup transformation. The Lookup transformation look up the name of the mentor in the finalist file against the mentor names in tblMentor table in SQL Server. For Lookup Match output, use Expression Task to record fact imported ok in Notes column. For Lookup No match output, use Expression Task to set Mentor Id to 9 (Not Known) and record problem in Notes column. Use Union All to combine both output and load into  tblFinalist table in SQL server.

## For Loop Containers

This package contains a loop that counts from 1 to 10.

1. Created a variable i to hold the counter. Set InitExpression @i=1, EvalExpression @i<10, AssignExpression @i+1 in For Loop Container.

## Script Tasks

This package displays a message box that ask if you want to get information from Mentors and Finalists text files or from tblMentors and tblFinalists table in SQL Server. Depending on your choice, a message box will be displayed showing the total number of finalists and mentors either from the text file or SQL Server.

1. Used Script Task to display a message box that has a prompt saying "Use Text?". If chosen yes, return success from the procedure. If chosen no, return failure from the procedure.
2. Created 2 Sequence Containers. One to import data from text - read mentors & finalists information from text file, count the number of mentors & finalist and store the numbers in NumberFinalists & NumberMentors variables. Another to import data from SQL - read mentors & finalists information from tblMentors & tblFinalists table in SQL Server, count the number of mentors & finalist and store the numbers in NumberFinalists & NumberMentors variables.
3. Set import data from text sequence container as success and import data from SQL Server sequence container as Failure
4. Used Script Task to calculate the total number of mentors and finalists and store result in a created variable NumberTotal
5. Used Script Task that takes in variable NumberTotal as ReadOnlyVariables and show the total number of mentors and finalists in a message box.
6. Changed Multiple Constraints to Logical OR in Precedence Constraint Editor.
