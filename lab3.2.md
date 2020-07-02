## Lab: Exporting HDFS Data to an RDBMS

## step1:  Put the Data into HDFS

## a. If not already done, open a Terminal in your VM and type "ssh sandbox".
## b. Change directories to /root/devph/labs/Lab3.2:
## c. Create a new directory in HDFS named salarydata.

**cmd** : # hdfs dfs -mkdir salarydata

## d. Put salarydata.txt into the salarydata directory in HDFS.

**cmd** : # hdfs dfs –put salarydata.txt salarydata

**img** : ![cmd_1](https://user-images.githubusercontent.com/31212980/86354654-0c3aac00-bc87-11ea-8763-451f2fcbeaf9.jpg)


## step2 : 2 ) Create a Table in the Database

# a. There is a script in the Exporting HDFS Data to an RDBMS lab folder that creates a table in MySQL that matches the records in salarydata.txt. View the SQL script:

**img** :


## step3 :  Export the Data

# a. Run a Sqoop command that exports the salarydata folder in HDFS into the
  salaries2 table in MySQL. At the end of the MapReduce output, you should see a
  log event stating that 10,000 records were exported.

**cmd** : # sqoop export \--connect jdbc:mysql://sandbox/test?user=root \--table salaries2 \--export-dir salarydata \--input-fields-terminated-by ","

**ex** : sqoop export --connect jdbc:mysql://sqoopdb1.cc6obx24apkz.us-east-1.rds.amazonaws.com/test --username root --password Coconuttree123  --table salaries2 --export-dir salarydata --input-fields-terminated-by ","

**img** : ![cmd_2](https://user-images.githubusercontent.com/31212980/86354659-0e9d0600-bc87-11ea-93a5-329695af1fce.jpg)
          
          ![cmd_2 2](https://user-images.githubusercontent.com/31212980/86354657-0e046f80-bc87-11ea-96cc-f2adfb83c1b1.jpg)
        

# b. Verify it worked by viewing the table’s contents from the mysql prompt. The output should look like the following:

**img** :![Screenshot (83)](https://user-images.githubusercontent.com/31212980/86354625-01801700-bc87-11ea-9487-0df7698fe650.png)
