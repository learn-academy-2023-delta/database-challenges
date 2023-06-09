What is the population of the US? (HINT: 278357000)

SELECT name, population FROM country
WHERE name = 'United States'


What is the area of the US? (HINT: 9.36352e+06)

SELECT surfacearea FROM country
WHERE name = 'United States'


Which countries gained their independence before 1963?
 121 of em
SELECT name, indepyear FROM country
WHERE indepyear <1963


List the countries in Africa that have a population smaller than 30,000,000 and a life expectancy of more than 45? (HINT: 37 entries)

SELECT * FROM country
WHERE continent = 'Africa' AND
population < 30000000 AND
lifeexpectancy >45;

Which countries are something like a republic? (HINT: Are there 122 or 143?)
Well you tricksy tricksters, there are 21 countries that are republic subsets(federal, islamic, etc), and there are 122 straight republics.
SELECT * FROM country
WHERE governmentform
LIKE '%epublic' AND governmentform NOT LIKE 'Republic';



Which countries are some kind of republic and achieved independence after 1945? (HINT: 92 entries)

SELECT * FROM country
WHERE governmentform
LIKE '%epub%' AND indepyear >1945


Which countries achieved independence after 1945 and are not some kind of republic? (HINT: 27 entries)

SELECT * FROM country
WHERE governmentform
NOT LIKE '%epub%' AND indepyear >1945



Which fifteen countries have the lowest life expectancy? (HINT: starts with Zambia, ends with Sierra Leonne)
SELECT * FROM country
ORDER BY lifeexpectancy ASC
LIMIT 15

Which fifteen countries have the highest life expectancy? (HINT: starts with Andorra, ends with Spain)

SELECT * FROM country
WHERE lifeexpectancy IS NOT NULL
ORDER BY lifeexpectancy DESC 
LIMIT 15

Which five countries have the lowest population density (density = population / surfacearea)? (HINT: starts with Greenland)

SELECT name, population, surfacearea, (population / surfacearea) AS density FROM country
WHERE population IS NOT NULL AND 
NOT population = '0' 
ORDER BY density ASC 

Which countries have the highest population density?(HINT: starts with Macao)

SELECT name, population, surfacearea, (population / surfacearea) AS density FROM country
WHERE population IS NOT NULL AND 
NOT population = '0' 
ORDER BY density DESC 

Which is the smallest country by area? (HINT: .4)

SELECT name, population, surfacearea, (population / surfacearea) AS density FROM country
WHERE population IS NOT NULL AND 
NOT population = '0' 
ORDER BY surfacearea ASC

Which is the smallest country by population? (HINT: 50)?

SELECT name, population, surfacearea, (population / surfacearea) AS density FROM country
WHERE population IS NOT NULL AND 
NOT population = '0' 
ORDER BY population ASC 

Which is the biggest country by area? (HINT: 1.70754e+07)

SELECT name, population, surfacearea, (population / surfacearea) AS density FROM country
WHERE population IS NOT NULL AND 
NOT population = '0' 
ORDER BY surfacearea DESC 

Which is the biggest country by population? (HINT: 1277558000)

SELECT name, population, surfacearea, (population / surfacearea) AS density FROM country
WHERE population IS NOT NULL AND 
NOT population = '0' 
ORDER BY population DESC 

Who is the most influential head of state measured by population? (HINT: Jiang Zemin)


SELECT name, population, surfacearea, headofstate, (population / surfacearea) AS density FROM country
WHERE population IS NOT NULL AND 
NOT population = '0' 
ORDER BY population DESC 


-------SUB QUERIES WITH-----------


Of the countries with the top 10 gnp, which has the smallest population? (HINT: Canada)

WITH populated_countries AS (
	SELECT name, population, gnp
	FROM country
	ORDER BY gnp desc
	limit 10

	)
SELECT name, population, gnp
FROM populated_countries
ORDER BY population asc;



Of the 10 least populated countries with permament residents (a non-zero population), which has the largest surfacearea? (HINT: Svalbard and Jan Mayen)

WITH populated_countries AS (
	SELECT name, population, gnp, surfacearea
	FROM country
	WHERE population > 0
	ORDER BY population ASC
	limit 10

	)
SELECT name, population, gnp, surfacearea
FROM populated_countries
ORDER BY surfacearea DESC;


-------SUB QUERIES GROUP BY-----------



Which region has the highest average gnp? (HINT: North America)

SELECT  region, AVG(gnp)
FROM country 
GROUP BY region
ORDER BY avg DESC
LIMIT 1;

Who is the most influential head of state measured by surface area? (HINT: Elisabeth II)


What is the average life expectancy for all continents?


What are the most common forms of government? (HINT: use count(*))


How many countries are in North America?


What is the total population of all continents?