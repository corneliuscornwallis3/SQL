# Problem

Consider *P<sub>1</sub>(a,b)* and *P<sub>2</sub>* to be two points on a 2D plane.

- *a* happens to equal the minimum value in Northern Latitude (LAT_N in ****STATION****).

- *b* happens to equal the minimum value in Western Longitude (LONG_W in **STATION**).

- *c* happens to equal the maximum value in Northern Latitude (LAT_N in **STATION**).

- *d* happens to equal the maximum value in Western Longitude (LONG_W in **STATION**).

Query the Manhattan Distance between points *P<sub>1</sub>* and *P<sub>2</sub>* and round it to a scale of 4 decimal places.

## Input Format

The **STATION** table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/corneliuscornwallis3/SQL/assets/158492493/ee73e1db-cf64-4495-971e-10c297721686)

where LAT_N is the northern latitude and LONG_W is the western longitude. 

# Solution

```
select round((max(lat_n)-min(lat_n))+(max(long_w)-min(long_w)),4) from STATION
```
