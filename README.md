# SSIS Exercises

## Variables Exercise

This package counts the number of finalists in a text file and outputs the results.

1. Created a Data Flow Task to count the number of finalists. The Data Flow Task contains a Flat File Data Source and a Row Count Transformation. 
The Flat File Data Source extracts the finalists information from a text file and put into the Row Count Transformation. A variable RowNumber was
created to store the number of finalists in the text file.

2. Created a Script Task that takes in the RowNumber variable as ReadOnlyVariables and show the number of finalists in a message box.
