# MET Data Analysis in SQL
The _Metropolitan Museum of Art of New York_ is one of the world’s largest and finest art museums. In this project, I will be working with a table named _met_ that contains the museum’s collection of American Decorative Arts and utilize SQL and data analysis techniques to manipulate, organize, and aggregate the data. This data was made publicly available under the Open Access Policy.

## Columns:

id - the id of the art piece

department - the department of the art piece

category - the category of the art piece

title - the title name of the art piece

artist - the name of the artist

date - the date(s) of the art piece

medium - the medium of the art piece

country - the country of the artist

## Let’s get started!

--1. Start by getting a feel for the met table:

    SELECT *
    FROM met
    LIMIT 10;

--2. How many pieces are in the American Decorative Art collection?

    SELECT COUNT(*)
    FROM met;

--3. Count the number of pieces where the category includes ‘celery’.

    SELECT COUNT(*)
    FROM met
    WHERE category LIKE '%celery%';

--4. Find the title and medium of the oldest piece(s) in the collection.

    SELECT MIN(date)
    FROM met;

    SELECT date, title, medium
    FROM met
    WHERE date LIKE '%1600%';

--5. Find the top 10 countries with the most pieces in the collection.

    SELECT country, COUNT(*)
    FROM met
    GROUP BY country
    ORDER BY COUNT(*) DESC
    LIMIT 10;

    SELECT country, COUNT(*)
    FROM met
    WHERE country IS NOT NULL
    GROUP BY 1
    ORDER BY 2 DESC
    LIMIT 10;

--6. Find the categories HAVING more than 100 pieces.

    SELECT category, COUNT(*)
    FROM met
    GROUP BY 1
    HAVING COUNT(*) > 100;

--7. Count the number of pieces where the medium contains ‘gold’ or ‘silver’. And sort in descending order.

    SELECT CASE
       WHEN medium LIKE '%gold%'   THEN 'Gold'
       WHEN medium LIKE '%silver%' THEN 'Silver'
       ELSE NULL
       END AS 'Bling',
    COUNT(*)
    FROM met
    WHERE Bling IS NOT NULL
    GROUP BY 1
    ORDER BY 2 DESC;

## Output:

![MET SQL Output](https://github.com/danial-khawaja/MET-Data-Analysis-SQL/assets/118863662/7e849f6a-0967-44c8-82d5-fb6aefaa4947)
