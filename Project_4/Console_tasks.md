## Console

### Task 1
  
The developers have assigned a task to determine which requests were sent from an IP address. 
I needed the addresses that start with "233.201.".
The logs were located on a remote server at the address logs/2019/12. The day when the error was occurred is unknown.
My task was to find out which requests were sent.

<br> The queries I used to get this logs:
<br> cd logs/2019/12 
grep -R "^233.201."

Logs:
233.201.188.154 - - [18/12/2019:21:46:01 +0000] "DELETE /events HTTP/1.1" 403 3971
233.201.182.9 - - [21/12/2019:21:56:20 +0000] "PATCH /users HTTP/1.1" 400 4118
<br><br>
### Task 2

A bug has been identified in the system. It occurred on December 30, 2019, and December 31, 2019, from 21:30:00 to 21:39:59. 
<br>During this time, errors with numbers 400 and 500 were logged. 
<br>My task was to save the logs recorded during this period to a separate file. 
<br> What I've done to get this logs:

In the home directory on the remote server, I created a directory named "bug1."

Placed all requests that occurred during the specified period into a file named "main.txt" in the "bug1" directory.

Inside the "bug1" directory, created a subdirectory named "events."

Inside the "events" directory, created two files (400.txt and 500.txt) for errors with numbers 400 and 500 and extracted the logs corresponding to the respective error numbers from the "main.txt" file.

So the queries:
<br>mkdir bug1
<br>mkdir bug1/events
<br>grep -R "3./12/2019:21:3.:.." ~/logs/2019/12/ > bug1/main.txt
<br>grep " 400 " bug1/main.txt > bug1/events/400.txt
<br>grep " 500 " bug1/main.txt > bug1/events/500.txt

<br>I've got data in 400.txt


|cnt|logs|
|:-:|:-:|
1|80.57.170.51 - - [30/12/2019:21:35:12 +0000] "DELETE /users HTTP/1.1" 400 3623|
2|204.235.176.118 - - [30/12/2019:21:35:13 +0000] "POST /users HTTP/1.1" 400 4704|
3|82.95.203.67 - - [30/12/2019:21:35:19 +0000] "DELETE /lists HTTP/1.1" 400 3737|
4|155.242.215.46 - - [30/12/2019:21:35:38 +0000] "POST /playbooks HTTP/1.1" 400 4450|
5|189.176.85.0 - - [30/12/2019:21:35:39 +0000] "PATCH /alerts HTTP/1.1" 400 2732|
6|13.108.71.71 - - [30/12/2019:21:35:43 +0000] "PATCH /events HTTP/1.1" 400 3410|
7|195.213.133.182 - - [30/12/2019:21:35:46 +0000] "PUT /customers HTTP/1.1" 400 3085|
8|235.243.133.78 - - [30/12/2019:21:35:47 +0000] "PATCH /customers HTTP/1.1" 400 3264|
9|192.57.115.49 - - [30/12/2019:21:35:55 +0000] "POST /parsers HTTP/1.1" 400 2457|
10|71.0.49.244 - - [30/12/2019:21:35:55 +0000] "PUT /collectors HTTP/1.1" 400 2785|
11|224.159.206.126 - - [30/12/2019:21:36:02 +0000] "DELETE /customers HTTP/1.1" 400 4569|
12|131.35.106.246 - - [30/12/2019:21:36:04 +0000] "DELETE /lists HTTP/1.1" 400 2578|
13|216.24.42.208 - - [30/12/2019:21:36:06 +0000] "GET /parsers HTTP/1.1" 400 4597|
14|123.53.150.160 - - [30/12/2019:21:37:19 +0000] "PATCH /events HTTP/1.1" 400 4379|
15|61.129.127.103 - - [30/12/2019:21:37:32 +0000] "GET /lists HTTP/1.1" 400 2575|
16|90.216.4.78 - - [30/12/2019:21:37:34 +0000] "PATCH /lists HTTP/1.1" 400 3899|
17|204.250.214.208 - - [30/12/2019:21:37:36 +0000] "PATCH /parsers HTTP/1.1" 400 4742|
18|79.214.240.98 - - [30/12/2019:21:37:37 +0000] "POST /fieldsets HTTP/1.1" 400 4441|
19|65.47.42.12 - - [30/12/2019:21:37:39 +0000] "PATCH /customers HTTP/1.1" 400 2500|
20|251.118.141.34 - - [30/12/2019:21:37:41 +0000] "POST /customers HTTP/1.1" 400 3519|
21|205.20.166.196 - - [30/12/2019:21:37:51 +0000] "POST /users HTTP/1.1" 400 4032|
22|156.217.3.46 - - [30/12/2019:21:37:52 +0000] "PATCH /parsers HTTP/1.1" 400 2020|
23|48.240.198.167 - - [30/12/2019:21:37:57 +0000] "PATCH /playbooks HTTP/1.1" 400 4100|
24|101.255.159.211 - - [30/12/2019:21:37:59 +0000] "GET /auth HTTP/1.1" 400 2324|
25|80.76.98.203 - - [30/12/2019:21:38:00 +0000] "POST /playbooks HTTP/1.1" 400 3045|
26|85.64.63.255 - - [30/12/2019:21:38:13 +0000] "PATCH /collectors HTTP/1.1" 400 2291|
27|184.79.247.161 - - [30/12/2019:21:38:13 +0000] "PUT /alerts HTTP/1.1" 400 3557|
28|93.2.134.22 - - [30/12/2019:21:39:39 +0000] "DELETE /alerts HTTP/1.1" 400 3701|
29|86.34.86.182 - - [31/12/2019:21:35:10 +0000] "POST /auth HTTP/1.1" 400 3626|
30|167.37.16.117 - - [31/12/2019:21:35:17 +0000] "PATCH /customers HTTP/1.1" 400 3294|
31|199.128.92.19 - - [31/12/2019:21:35:43 +0000] "PUT /users HTTP/1.1" 400 4180|
32|162.152.99.143 - - [31/12/2019:21:35:59 +0000] "PUT /users HTTP/1.1" 400 4606|
33|83.115.59.224 - - [31/12/2019:21:37:26 +0000] "GET /alerts HTTP/1.1" 400 3489|
34|194.10.97.226 - - [31/12/2019:21:37:31 +0000] "DELETE /lists HTTP/1.1" 400 2447|
35|180.99.214.40 - - [31/12/2019:21:37:44 +0000] "DELETE /alerts HTTP/1.1" 400 2077|
36|154.152.205.4 - - [31/12/2019:21:37:50 +0000] "GET /playbooks HTTP/1.1" 400 3324|
37|197.82.125.54 - - [31/12/2019:21:37:52 +0000] "PUT /fieldsets HTTP/1.1" 400 4365|
38|115.89.87.219 - - [31/12/2019:21:38:06 +0000] "PUT /playbooks HTTP/1.1" 400 2589|
39|100.77.15.14 - - [31/12/2019:21:38:07 +0000] "GET /fieldsets HTTP/1.1" 400 4911|
40|22.33.159.242 - - [31/12/2019:21:38:07 +0000] "GET /playbooks HTTP/1.1" 400 3955|
41|149.148.229.11 - - [31/12/2019:21:39:16 +0000] "GET /users HTTP/1.1" 400 2071|
42|236.107.64.192 - - [31/12/2019:21:39:17 +0000] "PATCH /users HTTP/1.1" 400 2791|
43|24.156.105.39 - - [31/12/2019:21:39:23 +0000] "GET /lists HTTP/1.1" 400 2902|
44|193.50.164.254 - - [31/12/2019:21:39:23 +0000] "PUT /playbooks HTTP/1.1" 400 3296|
45|18.123.104.91 - - [31/12/2019:21:39:52 +0000] "GET /collectors HTTP/1.1" 400 4372|
46|234.218.148.4 - - [31/12/2019:21:39:54 +0000] "PUT /users HTTP/1.1" 400 2509|
(46 rows)

<br><br>
And data in 500.txt
|cnt|logs|
|:-:|:-:|
1|64.250.112.189 - - [30/12/2019:21:35:13 +0000] "PUT /parsers HTTP/1.1" 500 4639
2|193.253.101.180 - - [30/12/2019:21:35:31 +0000] "PATCH /alerts HTTP/1.1" 500 2944
3|197.106.117.194 - - [30/12/2019:21:35:31 +0000] "PATCH /parsers HTTP/1.1" 500 3519
4|247.124.71.67 - - [30/12/2019:21:35:45 +0000] "PUT /alerts HTTP/1.1" 500 2746
5|62.88.204.119 - - [30/12/2019:21:35:51 +0000] "PUT /auth HTTP/1.1" 500 2666
6|125.156.142.26 - - [30/12/2019:21:36:01 +0000] "PATCH /events HTTP/1.1" 500 3460
7|144.170.212.70 - - [30/12/2019:21:36:04 +0000] "DELETE /parsers HTTP/1.1" 500 2599
8|59.39.200.252 - - [30/12/2019:21:36:05 +0000] "GET /alerts HTTP/1.1" 500 2650
9|150.136.200.100 - - [30/12/2019:21:37:24 +0000] "POST /lists HTTP/1.1" 500 2684
10|84.81.25.45 - - [30/12/2019:21:37:25 +0000] "POST /auth HTTP/1.1" 500 2052
11|30.222.160.141 - - [30/12/2019:21:37:30 +0000] "PATCH /parsers HTTP/1.1" 500 2017
12|117.87.158.36 - - [30/12/2019:21:37:34 +0000] "POST /fieldsets HTTP/1.1" 500 4056
13|212.153.128.212 - - [30/12/2019:21:37:42 +0000] "PUT /fieldsets HTTP/1.1" 500 3259
14|58.188.83.217 - - [30/12/2019:21:37:46 +0000] "POST /playbooks HTTP/1.1" 500 3947
15|193.123.131.146 - - [30/12/2019:21:37:47 +0000] "PUT /lists HTTP/1.1" 500 3902
16|182.7.179.91 - - [30/12/2019:21:37:48 +0000] "GET /users HTTP/1.1" 500 2950
17|10.25.168.164 - - [30/12/2019:21:38:05 +0000] "PATCH /playbooks HTTP/1.1" 500 3858
18|215.201.210.173 - - [30/12/2019:21:38:11 +0000] "PATCH /customers HTTP/1.1" 500 3277
19|179.241.103.167 - - [30/12/2019:21:39:23 +0000] "POST /lists HTTP/1.1" 500 3669
20|147.188.170.252 - - [30/12/2019:21:39:33 +0000] "POST /fieldsets HTTP/1.1" 500 3313
21|1.249.123.189 - - [30/12/2019:21:39:36 +0000] "PATCH /alerts HTTP/1.1" 500 4734
22|124.114.135.105 - - [30/12/2019:21:39:41 +0000] "PATCH /customers HTTP/1.1" 500 3348
23|35.215.100.202 - - [30/12/2019:21:39:43 +0000] "PUT /alerts HTTP/1.1" 500 4345
24|86.222.23.128 - - [30/12/2019:21:39:44 +0000] "PATCH /alerts HTTP/1.1" 500 2230
25|20.161.75.95 - - [30/12/2019:21:39:48 +0000] "DELETE /users HTTP/1.1" 500 2412
26|196.18.151.117 - - [30/12/2019:21:39:55 +0000] "PUT /events HTTP/1.1" 500 4439
27|77.101.138.151 - - [30/12/2019:21:39:57 +0000] "PUT /lists HTTP/1.1" 500 2194
28|208.205.133.127 - - [31/12/2019:21:35:17 +0000] "DELETE /alerts HTTP/1.1" 500 4561
29|20.145.255.91 - - [31/12/2019:21:35:30 +0000] "GET /parsers HTTP/1.1" 500 3051
30|91.66.134.13 - - [31/12/2019:21:35:53 +0000] "POST /lists HTTP/1.1" 500 3319
31|31.88.211.206 - - [31/12/2019:21:35:57 +0000] "DELETE /events HTTP/1.1" 500 2325
32|171.37.114.114 - - [31/12/2019:21:37:39 +0000] "DELETE /fieldsets HTTP/1.1" 500 3253
33|223.157.242.167 - - [31/12/2019:21:37:59 +0000] "POST /users HTTP/1.1" 500 2283
34|98.181.102.34 - - [31/12/2019:21:38:06 +0000] "PATCH /fieldsets HTTP/1.1" 500 4672
35|254.74.22.79 - - [31/12/2019:21:38:06 +0000] "PUT /lists HTTP/1.1" 500 2259
36|103.46.238.3 - - [31/12/2019:21:38:09 +0000] "PUT /lists HTTP/1.1" 500 3992
37|41.62.205.107 - - [31/12/2019:21:39:20 +0000] "PATCH /alerts HTTP/1.1" 500 3631
38|22.53.105.197 - - [31/12/2019:21:39:31 +0000] "DELETE /collectors HTTP/1.1" 500 4202
39|178.22.133.42 - - [31/12/2019:21:39:43 +0000] "PUT /alerts HTTP/1.1" 500 4648
40|102.247.13.50 - - [31/12/2019:21:39:55 +0000] "PATCH /auth HTTP/1.1" 500 3736
(40 rows)
