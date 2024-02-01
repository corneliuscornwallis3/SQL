# Problem

A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from **STATION** and round your answer to 4 decimal places.

## Input Format

The **STATION** table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/corneliuscornwallis3/SQL/assets/158492493/ecdd8efd-c48a-4db3-a20c-02b190515264)

where LAT_N is the northern latitude and LONG_W is the western longitude.

# Solution

```
SELECT ROUND(s1.LAT_N, 4) from 
(select row_number() over(order by lat_n) as row_num, lat_n from station) as s1 where row_num =
(select ceil(count(*)/2) from station)
```


