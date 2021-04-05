# SSIS Exercises

## Variables Exercise

This package counts the number of finalists in a text file and displays a message box showing the results.

1. Created a Data Flow Task to count the number of finalists. The Data Flow Task contains a Flat File Data Source and a Row Count transformation. The Flat File Data Source extracts the finalists information from a text file and put into the Row Count Transformation. 
2. Created a variable RowNumber to store the number of finalists in the text file.
3. Created a Script Task that takes in the RowNumber variable as ReadOnlyVariables and show the number of finalists in a message box.

## Expressions Exercise

 This package counts the number of days till New Year's Eve 31st December and displays a message box showing the results and whether today is weekend/weekday.
 
 1. Created several variables to calculate the number of days till New Year's Eve and whether today is weekend/weekday
 2. Created an Expression Task to make the message to be displayed
 3. Created a Script Task that takes in the message variable as ReadOnlyVariables and show the number of days till New Year's Eve and whether today is weekend/weekday

## Conditional Split & Derived Columns

This package takes finalists information from a text file, remove all records that has "Tulisa" in Mentor column, change "Cheryl Cole" to "Cheryl Wakerfield" in Mentor column and load the results in tblFinalist1 table in SQL

1. Created an Execute SQL Task that delete all data from tblFinalist1 table in SQL
2. Created a Data Flow Task that contains a Flat file Data Source, a Conditional Split transformation, Derived Column transformation, Union all transformation and an OLE DB Destination. The Flat File Data Source extracts the finalists data from a text file and put into the conditional split transformation, which direct rows containing Chery Cole to Cheryl Cole output, rows containing Tulisa to Tulisa output and the rest of the rows to Default output. Used Derived Column transformation to change Cheryl Cole to Cheryl Wakerfield in Cheryl Cole Output. Used Union All transformation to union Cheryl Cole output with Default output and used OLEDB Destination to put result in tblFinalist1 table in SQL Server.
