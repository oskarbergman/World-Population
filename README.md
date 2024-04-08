# World-Population

1) Analys av Befolkningstäthet: Vilka länder har högst befolkningstäthet?


SELECT country, 
       ROUND(last_year_population / country_land_area, 0) AS population_density

FROM world_data_flatten

ORDER BY population_density DESC

LIMIT 5;
![Skärmavbild 2024-04-07 kl  17 32 02](https://github.com/oskarbergman/World-Population/assets/105347124/a929c61e-9d4a-4464-b722-16a7005e13b0)



2) Analys av Befolkningstäthet: Vilka länder har lägst befolkningstäthet?

SELECT country, 
       last_year_population / country_land_area AS population_density

FROM world_data_flatten

ORDER BY population_density

LIMIT 5;
![Skärmavbild 2024-04-08 kl  14 43 39](https://github.com/oskarbergman/World-Population/assets/105347124/f76675e3-ca34-4dca-9a76-2af217eff8ae)

3.) Jämförelse av Befolkningens Storlekar: Hur jämför sig befolkningarna i de tio mest folkrika länderna med varandra i förhållande till landsyta?
SELECT country,
       last_year_population,
       country_land_area * 100
       
FROM world_data_flatten

ORDER BY last_year_population DESC

LIMIT 5;
![Skärmavbild 2024-04-08 kl  14 47 15](https://github.com/oskarbergman/World-Population/assets/105347124/ddacef62-b777-47c6-8bba-2bebe2cb74c5)

4.) Jämförelse av Befolkningens Storlekar: Hur jämför sig befolkningarna i de tio minst folkrika länderna med varandra i förhållande till landsyta?
SELECT country,
       last_year_population,
       country_land_area * 100
       
FROM world_data_flatten

ORDER BY last_year_population

LIMIT 5;
![Skärmavbild 2024-04-08 kl  14 52 18](https://github.com/oskarbergman/World-Population/assets/105347124/ff42a37d-7995-4c0f-a69d-cd30eb363042)


5.) FN-medlemskap jämfört med Befolkningens Storlek: Finns det en korrelation mellan ett lands medlemskap i Förenta Nationerna och dess befolkningsstorlek? Är det vanligt att större populationer är representerade i FN?

SELECT is_un_member,
       ROUND(AVG(last_year_population), 0)
       AS average_population

FROM world_data_flatten

GROUP BY is_un_member
![Skärmavbild 2024-04-08 kl  14 58 08](https://github.com/oskarbergman/World-Population/assets/105347124/838347f2-1523-423f-adc0-7ef402571053)

6.) FN-medlemskap jämfört med Befolkningens Storlek: Finns det en korrelation mellan ett lands medlemskap i Förenta Nationerna och dess befolkningsstorlek? Är det vanligt att större populationer är representerade i FN? (ta bort de fem största populationerna (Kina, Indien, USA, Indonesien, Pakistan))
SELECT is_un_member,
ROUND(AVG(last_year_population), 0) AS average_population

FROM (
    SELECT *
    FROM world_data_flatten
    WHERE country NOT IN ('China', 'India', 'United States', 'Indonesia', 'Pakistan')
) AS filtered_data

GROUP BY is_un_member;
![Skärmavbild 2024-04-08 kl  15 14 55](https://github.com/oskarbergman/World-Population/assets/105347124/3e83b281-4954-44f5-b78f-5b5e0d8e9cf6)







    
