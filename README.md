# SSIS Exercises

## Variables

This package reads Finalists information from a text file, counts number of records and displays a message box showing the results.

1. Created a Data Flow Task to count the number of records in Finalists text file. The Data Flow Task contains a Flat File Data Source and a Row Count transformation. The Flat File Data Source extracts the Finalists information from a text file and put into the Row Count transformation
2. Created a variable RowNumber to store the number of records in the Finalists text file
3. Created a Script Task (using C#) that takes in the RowNumber variable as ReadOnlyVariables and show the results in a message box

## Expressions

 This package counts the number of days till New Year's Eve 31st December and displays a message box showing the results and whether today is weekend/weekday.
 
 1. Created several variables to calculate the number of days till New Year's Eve and whether today is weekend/weekday
 2. Created an Expression Task to make the message to be displayed
 3. Created a Script Task (using C#) that takes in the message variable as ReadOnlyVariables and show the number of days till New Year's Eve and whether today is weekend/weekday

## Conditional Split & Derived Columns

This package takes Finalists information from a text file, removes all records that contain "Tulisa" in Mentor column, changes "Cheryl Cole" to "Cheryl Wakerfield" in Mentor column and load the results in tblFinalist1 table in SQL Server.

1. Created an Execute SQL Task that deletes all data from tblFinalist1 table in SQL Server
2. Created a Data Flow Task that contains a Flat file Data Source, a Conditional Split transformation, Derived Column transformation, Union all transformation and an OLE DB Destination. The Flat File Data Source extracts the Finalists data from a text file and put into the conditional split transformation, which direct rows containing "Chery Cole" to Cheryl Cole output, rows containing "Tulisa" to Tulisa output and the rest of the rows to Default output. Used Derived Column transformation to change "Cheryl Cole" to "Cheryl Wakerfield" in Cheryl Cole Output. Used Union All transformation to union Cheryl Cole output with Default output and used OLEDB Destination to put result in tblFinalist1 table in SQL Server

## Lookup Transforms

This package takes Finalists information from a text file and loads into tblFinalist table in SQL server with 2 additional columns displaying Mentor Id and Notes. If the Mentor Name in the text file is in the tblMentor table in SQL Server, then tblFinalist table will display the corresponding Mentor Id from tblMentor table and Notes "Imported Ok". Otherwise, tblFinalist table will display Mentor Id 9 and Notes "Specific Mentor not known".

1. Created a Data Flow Task that loads the Mentors into a cache using OLE DB Data Source and Cache Transform transformation
2. Created an Execute SQL Task that delete all data from tblFinalist table in SQL Server
3. Created a Data Flow Task that contains a Flat file Data Source that extract Finalists information from a text file and load to Lookup transformation. The Lookup transformation look up for corresponding Mentor names in tblMentor table in SQL Server. For Lookup Match output, used Expression Task to set Mentor Id column to corresponding Mentor Id in tblMentor table and Notes column to "Imported Ok". For Lookup No match output, used Expression Task to set Mentor Id column to 9 (Not Known) and Notes column to "Specific Mentor not known". Use Union All to combine both output and load into tblFinalist table in SQL server

## For Loop Containers

This package contains a loop that counts from 1 to 10.

1. Created a variable i to hold the counter. Set InitExpression @i=1, EvalExpression @i<10, AssignExpression @i+1 in For Loop Container

## Script Tasks (using C#)

This package displays a message box that asks if you want to get information from Mentors and Finalists text files or from tblMentors and tblFinalists tables in SQL Server. Depending on your choice, a message box will be displayed showing the total number of Finalists and Mentors either from the text file or SQL Server.

1. Used Script Task to display a message box that has a prompt saying "Use Text?". If chosen yes, return success from the procedure. If chosen no, return failure from the procedure
2. Created 2 Sequence Containers. One to import data from text - read Mentors & Finalists information from text file, count the number of Mentors & finalist and store the numbers in NumberFinalists & NumberMentors variables. Another to import data from SQL - read Mentors & Finalists information from tblMentors & tblFinalists tables in SQL Server, count the number of Mentors & Finalists and store the numbers in NumberFinalists & NumberMentors variables
3. Set import data from text sequence container as success and import data from SQL Server sequence container as Failure
4. Used Script Task to calculate the total number of Mentors and Finalists and store result in NumberTotal variable
5. Used Script Task that takes in variable NumberTotal as ReadOnlyVariables and show the total number of Mentors and Finalists in a message box
6. Changed Multiple Constraints to Logical OR in Precedence Constraint Editor
