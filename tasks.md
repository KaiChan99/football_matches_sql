# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE season = '2017';

```

2) Find all the matches featuring Barcelona.


```sql
<!-- Copy solution here -->
SELECT * FROM matches WHERE (hometeam = 'Barcelona') OR (awayteam = 'Barcelona');

```

3) What are the names of the Scottish divisions included?

```sql
<!-- Copy solution here -->

SELECT name FROM divisions WHERE country = 'Scotland';


```

4) Find the division code for the Bundesliga. Use that code to find out how many matches Freiburg have played in the Bundesliga since the data started being collected.

```sql
<!-- Copy solution here -->
SELECT code FROM divisions WHERE name = 'Bundesliga';
SELECT COUNT(*) FROM matches WHERE (division_code = 'D1') and (hometeam = 'Freiburg') OR (awayteam = 'Freiburg');


```

5) Find the unique names of the teams which include the word "City" in their name (as entered in the database)

```sql
<!-- Copy solution here -->
-- SELECT DISTINCT (hometeam,awayteam) FROM matches WHERE (LOWER(hometeam) LIKE LOWER('%City%')) OR (LOWER(awayteam) LIKE LOWER('%City%'))
-- Wrong code That I wanna keep

SELECT DISTINCT (hometeam) FROM matches WHERE (LOWER(hometeam) LIKE LOWER('%City%'))
```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- Copy solution here -->
SELECT code FROM divisions WHERE country = 'France'; -- > returns F1 and F2 -->


SELECT DISTINCT hometeam FROM matches WHERE (division_code = 'F1') OR (division_code = 'F2')

-- Found 61 rows but don't know how to display using COUNT
```

7) Have Huddersfield played Swansea in the period covered?

```sql
<!-- Copy solution here -->
SELECT COUNT (*) FROM matches WHERE (hometeam,awayteam) = ('Huddersfield','Swansea') OR ((hometeam,awayteam) = ('Swansea','Huddersfield'))


```

8) How many draws were there in the Eredivisie between 2010 and 2015?

```sql
<!-- Copy solution here -->
SELECT COUNT (*) FROM matches WHERE (division_code = 'N1') AND (season BETWEEN 2010 AND 2015) AND (ftr = 'D')


```

9) Select the matches played in the Premier League in order of total goals scored from highest to lowest. Where there is a tie the match with more home goals should come first.

```sql
<!-- Copy solution here -->


SELECT (hometeam,awayteam,fthg, ftag) FROM matches WHERE (division_code = 'E0') ORDER BY (fthg+ftag) DESC, fthg DESC;

```

10) In which division and which season were the most goals scored?

```sql
<!-- Copy solution here -->


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)