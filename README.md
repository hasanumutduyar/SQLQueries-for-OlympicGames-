# SQL Queries for Olympic Data Analysis

This repository contains SQL queries that analyze Olympic Games data to extract insights about medal counts, host country participation, and winter games performance. The queries are written to provide detailed comparisons based on specific criteria such as years, medal types, and game types.

## Queries Overview

- Medal Rates of Countries in The 2016-2022 Olympic Games

![Medal Rates of Countries in The 2016-2022 Olympic Games](https://github.com/user-attachments/assets/d1735954-aef9-4d69-86da-1dd328c3802e)

```
SELECT 
     country,
     SUM(CAST(gold AS INT)) AS total_gold,
     SUM(CAST(silver AS INT)) AS total_silver,
     SUM(CAST(bronze AS INT)) AS total_bronze
FROM 
     olympic_games
WHERE 
     year >= 2016
GROUP BY 
     country
ORDER BY 
     total_gold DESC;
```

- T984-2022 Total Number of Athletes for Each Host Country

![1984-2022 Total Number of Athletes for Each Host Country](https://github.com/user-attachments/assets/a3f53484-52a6-4cc8-a6b0-f3e52c62fcc0)

```
SELECT 
    host_country,
    SUM(CAST(athletes AS INT)) AS total_athletes
FROM 
    olympic_games
GROUP BY 
    host_country
ORDER BY 
    total_athletes DESC;
```

- Gold Medal Ranking for The Winter Olympics in 2016-2022

![Gold Medal Ranking for The Winter Olympics in 2016-2022](https://github.com/user-attachments/assets/0a250355-e93f-4d96-996b-7a1889588ab4)

```
SELECT 
    country,
    SUM(CAST(gold AS INT)) AS total_gold
FROM 
    olympic_games
WHERE 
    year >= 2016
    AND games_type = 'Winter'
GROUP BY 
    country
HAVING 
    SUM(CAST(gold AS INT)) > 0
ORDER BY 
    total_gold DESC;
```

## How to Use
1. Download the `olympic_games.cvs` SQL file:
Make sure you have a table structure that resembles the following columns (from the CSV data used)
  - year (INT): The year of the Olympic Games.
  - games_type (VARCHAR): The type of Olympic Games (Summer/Winter).
  - host_country (VARCHAR): The country that hosted the Olympics.
  - country (VARCHAR): The country competing.
  - gold, silver, bronze (VARCHAR or INT): Number of medals won by the country.
- athletes (VARCHAR or INT): Number of athletes competing.

2. Run the queries on your database to extract insights from Olympic data.

## Contact
If you have any questions or suggestions, feel free to open an issue or contact me via e-mail [Linked in](https://www.linkedin.com/in/hasanumut-duyar/)
