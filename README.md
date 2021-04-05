# SSIS Exercises

## Variables Exercise

This package counts the number of finalists in a text file and displays a message box showing the results.

1. Created a Data Flow Task to count the number of finalists. The Data Flow Task contains a Flat File Data Source and a Row Count Transformation. 
The Flat File Data Source extracts the finalists information from a text file and put into the Row Count Transformation. 
2. Created a variable RowNumber to store the number of finalists in the text file.
3. Created a Script Task that takes in the RowNumber variable as ReadOnlyVariables and show the number of finalists in a message box.

## Expressions Exercise

 This package counts the number of days till New Year's Eve 31st December and displays a message box showing the results and whether today is weekend/weekday.
 
 1. Created several variables to calculate the number of days till New Year's Eve and whether today is weekend/weekday
 2. Created an Expression Task to make the message to be displayed
 3. Created a Script Task that takes in the message variable as ReadOnlyVariables and show the number of days till New Year's Eve and whether today is weekend/weekday
