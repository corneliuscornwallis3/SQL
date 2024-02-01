# Problem

Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.

Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.

## Input Format

The following tables contain data on the wands in Ollivander's inventory:

   - Wands: The id is the id of the wand, code is the code of the wand, coins_needed is the total number of gold galleons needed to buy the wand, and power denotes the quality of the wand (the higher the power, the better the wand is).

      ![1458538092-b2a8163a74-ScreenShot2016-03-08at12 13 39AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/1724d934-1313-4fd7-8de1-256d8300c756)

   - Wands_Property: The code is the code of the wand, age is the age of the wand, and is_evil denotes whether the wand is good for the dark arts. If the value of is_evil is 0, it means that the wand is not evil. The mapping between code and age is one-one, meaning that if there are two pairs, *(code<sub>1</sub>,age<sub>1</sub>)* and *(code<sub>2</sub>,age<sub>2/sub>)*
then *code<sub>1</sub> != code<sub>2</sub>* and *age<sub>1</sub> != age<sub>2</sub>*
      ![1458538221-18c4092b7d-ScreenShot2016-03-08at12 13 53AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/412b42ed-a20a-403e-b7fc-2d2eca3f22ee)

## Sample Input

Wands Table:

![1458538559-51bf29644e-ScreenShot2016-03-21at10 34 41AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/2d47387d-4281-4e49-a208-355495e66dc9)

Wands_Property Table:

![1458538583-fd514566f9-ScreenShot2016-03-21at10 34 28AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/be5a4558-91e9-484c-8003-45889592b20e)

## Sample Output
```
9 45 1647 10
12 17 9897 10
1 20 3688 8
15 40 6018 7
19 20 7651 6
11 40 7587 5
10 20 504 5
18 40 3312 3
```
# Solution

```
select w.id, wp.age, w.coins_needed, w.power from wands as w
join wands_property as wp on w.code = wp.code
where w.coins_needed = 
(select min(w2.coins_needed) from wands as w2
 join wands_property as wp2 on w2.code = wp2.code
 where wp2.is_evil = 0 and wp2.age = wp.age and w2.power = w.power   
)
order by w.power desc, wp.age desc
```
