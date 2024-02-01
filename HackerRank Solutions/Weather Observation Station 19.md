# Problem

Consider *P<sub>1</sub>(a,c)* and *P<sub>2</sub>(b,d)* to be two points on a 2D plane where *(a,b)* are the respective minimum and maximum values of Northern Latitude (LAT_N) and *(c,d)* 
are the respective minimum and maximum values of Western Longitude (LONG_W) in **STATION**.

Query the Euclidean Distance between points *P<sub>1</sub>* and *P<sub>2</sub>* and format your answer to display decimal digits.

## Input Format
The **STATION** table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/corneliuscornwallis3/SQL/assets/158492493/564a96d8-4fa9-434e-908d-63f0c741dfab)

where LAT_N is the northern latitude and LONG_W is the western longitude. 

# Solution

`select truncate(sqrt(power(max(lat_n)-min(lat_n),2) + power(max(long_w)-min(long_w),2)),4) from station`
