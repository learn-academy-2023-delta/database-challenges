Challenges.

1. What is the population of the US? (HINT: 278357000)

        SELECT *
        FROM country
        WHERE continent = 'North America'
        AND name = 'United States';

What is the area of the US? (HINT: 9.36352e+06)

        SELECT *
        FROM country
        WHERE continent = 'North America'
        AND surfacearea > 9e5
        AND name = 'United States';

Which countries gained their independence before 1963?

        SELECT name, region, indepyear
        FROM country
        WHERE indepyear < 1963;

List the countries in Africa that have a population smaller than 30,000,000 and a life expectancy of more than 45? (HINT: 37 entries)

        SELECT name, continent, population, lifeexpectancy
        FROM country
        WHERE continent = 'Africa'
        AND population >= 3e7
        AND lifeexpectancy > 45;



Which countries are something like a republic? (HINT: Are there 122 or 143?)

        SELECT *
        FROM country
        WHERE governmentform = 'Republic';

        There's 122


Which countries are some kind of republic and achieved independence after 1945? (HINT: 92 entries)

        SELECT *
        FROM country
        WHERE governmentform LIKE 'Republic'
        AND indepyear > 1945;


Which countries achieved independence after 1945 and are not some kind of republic? (HINT: 27 entries)

        SELECT *
        FROM country
        WHERE
        NOT(governmentform LIKE '%Republic')
        AND indepyear > 1945;

Which fifteen countries have the lowest life expectancy? (HINT: starts with Zambia, ends with Sierra Leonne)


SELECT * 
FROM country
WHERE lifeexpectancy != 0 
ORDER BY lifeexpectancy
LIMIT 15;


Which fifteen countries have the highest life expectancy? (HINT: starts with Andorra, ends with Spain)


SELECT * 
FROM country
WHERE lifeexpectancy != 0 
ORDER BY lifeexpectancy DESC
LIMIT 15;


Which five countries have the lowest population density (density = population / surfacearea)? (HINT: starts with Greenland)


SELECT name, surfacearea, population, population/surfacearea AS population_density
FROM country
WHERE population !=0  
ORDER BY population_density 
LIMIT 5;


Which countries have the highest population density?(HINT: starts with Macao)


SELECT name, surfacearea, population, population/surfacearea AS population_density
FROM country
WHERE population !=0  
ORDER BY population_density DESC
LIMIT 5;


Which is the smallest country by area? (HINT: .4)


SELECT name, surfacearea
FROM country
ORDER BY surfacearea
LIMIT 1;


Which is the smallest country by population? (HINT: 50)?


SELECT name, population
FROM country
WHERE population !=0
ORDER BY population
LIMIT 1;


Which is the biggest country by area? (HINT: 1.70754e+07)


SELECT name, surfacearea
FROM country
ORDER BY surfacearea DESC
LIMIT 1;



Which is the biggest country by population? (HINT: 1277558000)

SELECT name, population
FROM country
ORDER BY population DESC
LIMIT 1;


Who is the most influential head of state measured by population? (HINT: Jiang Zemin)