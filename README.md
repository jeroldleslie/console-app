console-app
===========
# ASCII SPREADSHEET 123

Background
==========
Your task is to build a spreadsheet from scratch in Java. Please document your steps as you go as we may ask you to justify your implementation after you turned in your work. Do comment your code. Unit tests are not required but highly recommended. Please tell us how to compile and run your code upon submission. A tarball submission will suffice.

You might also want to finish reading all the sections first before embarking on the actual implementation.

## Task 0
Print out to the screen a 4x3 spreadsheet with empty cells. Each cell should have exactly 5 spaces in it. The following is exactly what you should print out to the screen.
1. Adjacent cells in the same row are separated by a pipe character (|).
2. Columns are label by English Alphabet (A, B, C, etc.). Don't worry about running out of letters if you have to insert a lot more columns later.
3. Rows are label by integers starting from 1.
4. Keep in mind that you'll have to update a cell's value. Choose your data structure wisely.

       A     B     C     D
    *-----------------------*
    |     |     |     |     | 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |     |     |     |     | 3
    *-----------------------*

## Task 1
Add a command prompt at the end of the spreadsheet that can read in user input. Once the user presses enter, your program should consume, parse, and execute the command. Then, print out the resulting spreadsheet again to stdout. For now, just make sure you can read in user's input.

       A     B     C     D
    *-----------------------*
    |     |     |     |     | 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |     |     |     |     | 3
    *-----------------------*

    Your command?>

## Task 2
Add the capability of assigning a float value to any given cell. The command needs to take the following lisp-like format.
    (define A1 3.14)

Example:

       A     B     C     D
    *-----------------------*
    |     |     |     |     | 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |     |     |     |     | 3
    *-----------------------*

    Your command?> (define A1 3.14)

[enter]

       A     B     C     D
    *-----------------------*
    | 3.14|     |     |     | 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |     |     |     |     | 3
    *-----------------------*

    Your command?>

If the length of the float number is larger than the default 5 space cell width, truncate the number and make the last character to be '>' to denote truncated values.

Example:

       A     B     C     D
    *-----------------------*
    | 3.14|     |     |     | 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |     |     |     |     | 3
    *-----------------------*

    Your command?> (define A1 3.1415926)

[enter]

       A     B     C     D
    *-----------------------*
    |3.14>|     |     |     | 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |     |     |     |     | 3
    *-----------------------*

    Your command?>


Example

       A     B     C     D
    *-----------------------*
    |3.14>|     |     |     | 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |     |     |     |     | 3
    *-----------------------*

    Your command?> (define A1 12345.123)

[enter]

       A     B     C     D
    *-----------------------*
    |1234>|     |     |     | 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |     |     |     |     | 3
    *-----------------------*

    Your command?> (define A1 12345.123)

What potential erroneous inputs will you have to watch out for?

## Task 3
Add the capability of inserting a new column. The user needs to be able to insert a column between existing columns.

    (col_insert_after B)    # insert a new column after Column B
    (col_insert_before A)   # insert a new column before Column A
    (col_insert_after)      # insert a new column at the very end.
    (col_insert_before)     # insert a new column in the very beginning.

Example:

       A     B     C     D
    *-----------------------*
    |    1|    2|   11|   22| 1
    *-----------------------*
    |    1|    2|   11|   22| 2
    *-----------------------*
    |    1|    2|   11|   22| 3
    *-----------------------*

    Your command? > (col_insert_before B)

       A     B     C     D     E
    *-----------------------------*
    |    1|     |    2|   11|   22| 1
    *-----------------------------*
    |    1|     |    2|   11|   22| 2
    *-----------------------------*
    |    1|     |    2|   11|   22| 3
    *-----------------------------*

    Your command? >

Notice that the column label got shifted.


Example:

       A     B     C     D
    *-----------------------*
    |    1|    2|   11|   22| 1
    *-----------------------*
    |    1|    2|   11|   22| 2
    *-----------------------*
    |    1|    2|   11|   22| 3
    *-----------------------*

    Your command? > (col_insert_after B)

       A     B     C     D     E
    *-----------------------------*
    |    1|    2|     |   11|   22| 1
    *-----------------------------*
    |    1|    2|     |   11|   22| 2
    *-----------------------------*
    |    1|    2|     |   11|   22| 3
    *-----------------------------*

    Your command? >


## Task 4
Add the capability of inserting a new row. The user needs to be able to insert a row between existing rows.

    (row_insert_after 1)    # insert a new row after row 1
    (row_insert_before 1)   # insert a new row before row 1
    (row_insert_after)      # insert a new row at the very end
    (row_insert_before)     # insert a new row in the very beginning

Example:

       A     B     C     D
    *-----------------------*
    |    1|    2|   11|   22| 1
    *-----------------------*
    |    1|    2|   11|   22| 2
    *-----------------------*
    |    1|    2|   11|   22| 3
    *-----------------------*

    Your command? > (row_insert_after 1)

[enter]

       A     B     C     D
    *-----------------------*
    |    1|    2|   11|   22| 1
    *-----------------------*
    |     |     |     |     | 2
    *-----------------------*
    |    1|    2|   11|   22| 3
    *-----------------------*
    |    1|    2|   11|   22| 4
    *-----------------------*

    Your command? >


Example:

       A     B     C     D
    *-----------------------*
    |    1|    2|   11|   22| 1
    *-----------------------*
    |    1|    2|   11|   22| 2
    *-----------------------*
    |    1|    2|   11|   22| 3
    *-----------------------*

    Your command? > (row_insert_before 1)

[enter]

       A     B     C     D
    *-----------------------*
    |     |     |     |     | 1
    *-----------------------*
    |    1|    2|   11|   22| 2
    *-----------------------*
    |    1|    2|   11|   22| 3
    *-----------------------*
    |    1|    2|   11|   22| 4
    *-----------------------*

    Your command? >


## Task 5
Add the capability of summing up across the values in a row or column range.
    (+ A1:D1)     # Calculate the sum of row 2 and write out the result to the end of row 1.
                    # If there's isn't an available cell at the end of row 1, handle it
                    # resonably.

    (+ A1:A4)     # Calculate the sum of column A and write out the result to the end of col A.
                    # Likewise, if there isn't an extra blank cell at the end of column A, come up with
                    # a reasonable way to handle this case.

    (define B5 (+ A1:A4)) # Calculate the sum of column A and write out the result to cell B5.


## Task 5
Add a command line argument (-csv) to take in a csv file. Display the content of the csv file inside your ASCII spreadsheet program.

## Task 6
Add the capability to resize cell's width.

    (resize_column A 10) # Resize it to 10 characters

## Task 7 (Optional)
Add the ability to format numbers with 1000 separators. For example, 1000 can be displayed as 1,000.
    (num_separator A2)       # format only one cell
    (num_separator A1:A4)    # format the whole column

Note: your sum function should still work, regardless of the numbering format.

## Task 8 (Optional)
Complex formula.
   (define A3 (/ (+ A1:D1) D4))
