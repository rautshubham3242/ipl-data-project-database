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
    load data local infile 'home/oem/Desktop/deliveries.csv' into table abc fields terminated by ',' enclosed by '"' lines terminated by '\n' ignore 1 rows;
```

Step 5. Solve the IPL problems
1. Number of matches played per year of all the years in IPL.
```roomsql
    SELECT season, count(season) as Number_of_Matches_Play
    FROM matches
    GROUP BY season;
```

2. Number of matches won of all teams over all the years of IPL.
``````roomsql
    SELECT winner, count(winner) as Number_of_Matches_Won
    FROM matches GROUP BY winner;
``````

3. For the year 2016 get the extra runs conceded per team.
```roomsql
    SELECT bowling_team, sum(extra_runs) as extra_runs_conceded_per_bowler
    FROM deliveries
    WHERE match_id in ( SELECT id FROM matches WHERE season = 2016)
    GROUP BY bowling_team;
```

4. For the year 2015 get the top economical bowlers.
``````roomsql
    SELECT bowler, sum(wide_runs+ noball_runs+batsman_runs)*6/count(all(wide_runs+noball_runs=0)) as Economical_Scrore
    FROM deliveries
    WHERE match_id in (SELECT id FROM matches WHERE season=2015)
    GROUP BY bowler;
``````


