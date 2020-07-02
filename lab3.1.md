# Lab:Importing RDBMS Data into HDFS

## step1: Create a Table in MySQL

**img** :![Screenshot (46)](https://user-images.githubusercontent.com/31212980/86351355-c7f8dd00-bc81-11ea-8f77-2ba39c823900.png)

## step2: View the Table

**img** :![Screenshot (52)](https://user-images.githubusercontent.com/31212980/86351389-d47d3580-bc81-11ea-8351-6b108748c171.png)

## step3: Import the Table into HDFS

# a. Enter the following Sqoop command (all on a single line), which imports the
salaries table in the test database into HDFS:

**cmd1** : sqoop import --connect jdbc:mysql://sandbox/test?user=root --table salaries

**ex** : sqoop import  --connect jdbc:mysql://sqoopdb1.cc6obx24apkz.us-east-1.rds.amazonaws.com/test --username root --password Coconuttree123  --table salaries

**img** :

## step4: Verify the Import

**img** :

## step5 : Specify Columns to Import
# a. Using the ‐‐columns argument, write a Sqoop command that imports the salary
  and age columns (in that order) of the salaries table into a directory in HDFS
  named salaries2. In addition, set the ‐m argument to 1 so that the result is a single
  file.
# Solution: The command you enter in the command line will look like this in the
  terminal window:

**cmd2** : sqoop import --connect jdbc:mysql://sandbox/test?user=root --
          table salaries--columns salary,age -m 1 --target-dir salaries2
          
**ex** :sqoop import --connect jdbc:mysql://sqoopdb1.cc6obx24apkz.us-east-1.rds.amazonaws.com/test --username root --password Coconuttree123  --table salaries --columns                    salary,age -m 1 --target-dir salaries2

**img** :

# step6 :) Importing from a Query
#   Write a Sqoop import command that imports the rows from salaries in MySQL whose
    salary column is greater than 90,000.00.
    
##    a. Use gender as the --split-by value, specify only two mappers, and import the
    data into the salaries3 folder in HDFS.
##    Tip
    The Sqoop command will look similar to the ones you have been using throughout
    this lab, except you will use --query instead of --table. Recall that when you use
##    a --query command you must also define a --split-by column, or define -m to be 1.
    Also, do not forget to add $CONDITIONS to the WHERE clause of your query, as
    demonstrated earlier in this unit.

**cmd3**

**ex** :.apache.sqoop.splitter.allow_text_splitter=true" --connect jdbc:mysql://sqoopdb1.cc6obx24apkz.us-east-1.rds.amazonaws.com/test --username root --password Coconuttree123            --query "select * from salaries where salary>90000.00 AND \$CONDITIONS" --split-by salaries.gender -m 2 --target-dir salaries3

**img** :
          
          
          
          
          
