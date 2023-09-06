## PostgreSQL

### Task 1
  
Database of taxi trips. 
<br>According to the plan, there were supposed to be 10,550 vehicles in service, which should have met user demand. 
<br>However, the team received numerous complaints that there weren't enough available taxis. 
<br>I need to determine how many taxis were actually in service.
<br><br>The query I used to solve this:
<br>\c spb_taxi
<br>SELECT COUNT (DISTINCT vehicle_id) AS vehicle_id FROM cabs
<br>So the actual vehicles number was <b>5500</b>

### Task 2
Then we decided to count the number of vehicles in each company.
<br>The team suspects that some companies did not deploy enough vehicles on the line. 
<br>I had to find companies with fewer than 100 vehicles.
<br><br>Query I used:
<br>\c spb_taxi
<br>SELECT company_name AS company_name, COUNT (DISTINCT vehicle_id) AS cnt FROM cabs GROUP BY company_name HAVING COUNT (DISTINCT vehicle_id) < 100 ORDER BY COUNT (DISTINCT vehicle_id) DESC;

<br> List of companies with fewer than 100 vehicles:
|vehicles cnt|company_name|
|:-:|:-:|
97 | Nova Taxi Affiliation Llc |
89 | Patriot Taxi Dba Peace Taxi Associat |
85 | Blue Diamond |
81 | Checker Taxi Affiliation |
80 | SPb Medallion Management |
69 | SPb Independents |
67 | 24 Seven Taxi |
60 | Checker Taxi |
55 | SPb United |
53 | SPb Medallion Leasing INC |
49 | Top Cab Affiliation |
48 | SPb Taxi Association |
38 | SPb Taxicab |
34 | Nevsky Cab |
20 | Gold Bridge Taxi |
20 | Metro Group |
18 | Service Taxi Association |
14 | 5 Star Taxi |
8 | Russia United Taxi Affiliation |
8 | Metro Jet Taxi A |
7 | Setare Inc |
1 | 5997 - 65283 AW Services Inc. |
1 | 2092 - 61288 Sbeih company |
1 | 1469 - 64126 Omar Jada |
1 | 2733 - 74600 Benny Jona |
1 | 2192 - 73487 Zeymane Corp |
1 | 5006 - 39261 Salifu Bawa | 
1 | 3556 - 36214 RC Andrews Cab |
1 | 3721 - SPb Express, Ivan Santa |
1 | 2809 - 95474 C & D Cab Co Inc. |
1 | 2241 - 44667 - Felman Corp, Manuel Alonso |
1 | 3620 - 52292 David K. Cab Corp. |
1 | 2823 - 73307 Lee Express Inc |
1 | 6057 - 24657 Evgeniy Addo |
1 | 6742 - 83735 Tasha ride inc |
1 | 1085 - 72312 N and W Cab Co |
1 | 3591 - 63480 Chuks Cab |
1 | 0118 - 42111 Godfrey S.Awir |
1 | 6574 - Babylon Express Inc. |
1 | 3094 - 24059 G.L.B. Cab Co |
1 | 5874 - 73628 Sergey Cab Corp. |
1 | 6743 - 78771 Luhak Corp |
1 | 5074 - 54002 Ahzmi Inc |
1 | 3623 - 72222 Arrington Enterprises |
1 | 4053 - 40193 Adwar H. Nikola |
1 | Chicago Star Taxicab |
1 | 3011 - 66308 JBL Cab Inc. |
(51 rows) 

### Task 3
In the taxi application, a fare coefficient is calculated for each trip. 
<br>If the weather is good, the coefficient is set to 1. If it's raining or there's a storm, the coefficient is increased to 2. 
<br>The team suspects there might be an error in the coefficient calculation. 
<br>To verify the calculation, they need a dataset. The developer can compare the coefficient with the data in the logs and fix any bugs. 
<br>My task was to obtain this dataset for dates between 2022-11-05 00:00 to 2022-11-06 00:00.

<br><br>Query I used:
<br>\c spb_taxi
<br>SELECT ts, CASE WHEN description LIKE '%rain%’ OR description LIKE '%storm%' THEN ‘Bad’ ELSE ‘Good’ END AS weather_conditions FROM weather_records WHERE ts BETWEEN '2022-11-05 00:00:00' AND '2022-11-06 00:00:00';
<br>
<br>The data I've got
|        ts          | weather_conditions|
|:-:|:-:|
| 2022-11-05 00:00:00 | Good |
| 2022-11-05 01:00:00 | Bad |
| 2022-11-05 02:00:00 | Good |
| 2022-11-05 03:00:00 | Good |
| 2022-11-05 04:00:00 | Bad |
| 2022-11-05 05:00:00 | Bad |
| 2022-11-05 06:00:00 | Good |
| 2022-11-05 07:00:00 | Good |
| 2022-11-05 08:00:00 | Good |
| 2022-11-05 09:00:00 | Good |
| 2022-11-05 10:00:00 | Good |
| 2022-11-05 11:00:00 | Good |
| 2022-11-05 12:00:00 | Good |
| 2022-11-05 13:00:00 | Good |
| 2022-11-05 14:00:00 | Bad |
| 2022-11-05 15:00:00 | Good |
| 2022-11-05 16:00:00 | Bad |
| 2022-11-05 17:00:00 | Good |
| 2022-11-05 18:00:00 | Bad |
| 2022-11-05 19:00:00 | Bad |
| 2022-11-05 20:00:00 | Bad |
| 2022-11-05 21:00:00 | Good |
| 2022-11-05 22:00:00 | Good |
| 2022-11-05 23:00:00 | Good |
| 2022-11-06 00:00:00 | Good |
(25 rows)

### Task 4
After a software update, taxi fleets started reporting discrepancies between the profits they were receiving and the data provided by the application. 
<br>The development team suspected that the issue may be related to trip count data. 
<br>To determine if there is a bug, they needed to obtain a dataset with the number of trips for each taxi fleet on November 15th and 16th, 2022.
<br><br>Query I used:
<br>\c spb_taxi
<br>SELECT cabs.company_name as company_name, COUNT(trips.trip_id) as trips_amount FROM trips INNER JOIN cabs ON cabs.cab_id = trips.cab_id WHERE trips.start_ts>='2022-11-15 00:00:00' AND trips.start_ts <'2022-11-17 00:00:00' GROUP BY cabs.company_name ORDER BY trips_amount DESC;
<br>
<br>The data I've got
|company_name | trips_amount |
|:-:|:-:|
 Choice Taxi Association                      |         5015 |
 Globe Taxi                                   |         4383 |
 Dispatch Taxi Affiliation                    |         3355 |
 Nova Taxi Affiliation Llc                    |         3175 |
 Patriot Taxi Dba Peace Taxi Associat         |         2235 |
 Checker Taxi Affiliation                     |         2216 |
 Blue Diamond                                 |         2070 |
 spb Medallion Management                 |         1955 |
 24 Seven Taxi                                |         1775 |
 spb Medallion Leasing INC                |         1607 |
 Checker Taxi                                 |         1486 |
Russian United                              |         1404 |
 spb Independents                         |         1296 |
 spb Taxi Association                        |         1259 |
 spb Taxicab                              |         1014 |
 Top Cab Affiliation                          |          978 |
 Gold Bridge Taxi                              |          428 |
 Service Taxi Association                     |          402 |
 5 Star Taxi                                  |          310 |
 303 Taxi                                     |          250 |
 Setare Inc                                   |          230 |
 Russia United Taxi Affiliation             |          210 |
 Leo Cab Co                               |          147 |
 6574 - Babylon Express Inc.                  |           31 |
 spb Star Taxicab                         |           29 |
 1085 - 72312 N and W Cab Co                  |           29 |
 2809 - 95474 C & D Cab Co Inc.               |           29 |
 2092 - 61288 Sbeih company                   |           27 |
 3011 - 66308 JBL Cab Inc.                    |           25 |
 3620 - 52292 David K. Cab Corp.              |           21 |
 4615 - 83503 Tyrone Henderson                |           21 |
 3623 - 72222 Arrington Enterprises           |           20 |
 5074 - 54002 Ahzmi Inc                       |           16 |
 2823 - 73307 Lee Express Inc                 |           15 |
 4623 - 27290 Jay Kim                         |           15 |
 3721 - spb Express, Alvaro Santamaria |           14 |
 5006 - 39261 Salifu Bawa                     |           14 |
2192 - 73487 Zeymane Corp                    |           14 |
 6057 - 24657 Evgeniy Addo                    |           13 |
 5997 - 65283 AW Services Inc.                |           12 |
 Metro Group                                  |           11 |
 5062 - 34841 Sam Mestas                      |            8 |
 4053 - 40193 Adwar H. Nikola                 |            7 |
 2733 - 74600 Benny Jona                      |            7 |
 5874 - 73628 Sergey Cab Corp.                |            5 |
 2241 - 44667 - Felman Corp, Manuel Alonso    |            3 |
 3556 - 36214 RC Andrews Cab                  |            2 |
(64 rows)
