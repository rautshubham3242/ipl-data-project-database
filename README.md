Step 1. First I have created user by using following Sql Queries,
`````` roomsql
   CREATE USER shubham WITH PASSWORD "1234";
``````

Step 2. Created Database By following queries,
`````` roomsql
    CREATE DATABASE student WITH OWNER shubham ENCODING='UTF8' LC_COLLATE='en_US.UTF-8' LC_CTYPE='en_US.UTF-8';
``````

Step 3. Removed Database By following queries,
``````roomsql
    DROP DATABASE student;
``````

Step 4. Converted CSV file into table
```roomsql
    load data local infile 'home/oem/Desktop/matches.csv' into table abc fields terminated by ',' enclosed by '"' lines terminated by '\n' ignore 1 rows;
```

Step 5. Solve the IPL problems
1. 


