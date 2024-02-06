# Problem
You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!
The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of 0 from your result.

## Input Format

The following tables contain contest data:

  -  Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.
  -  
![1458522826-a9ddd28469-ScreenShot2016-03-21at6 40 27AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/425c0d30-93ee-4a61-a27f-82563f904a79)

  -  Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge for which the submission belongs to, and score is the score of the submission.

![1458523022-771511df90-ScreenShot2016-03-21at6 40 37AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/3b64a394-68e9-4166-b1a7-c501b36f2c50)

## Sample Input
![1458523374-7ecc39010f-ScreenShot2016-03-21at6 51 56AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/6cbd68a7-65d5-4c30-a8d2-237bf8502c63)

Hackers Table:

![1458523374-7ecc39010f-ScreenShot2016-03-21at6 51 56AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/6c48f548-98e7-452c-b3c1-794005e0561f)

Submissions Table:

![1458523388-0896218137-ScreenShot2016-03-21at6 51 45AM](https://github.com/corneliuscornwallis3/SQL/assets/158492493/a9db5d2d-e1c0-40a8-a10e-e75bebd38a28)

## Sample Output
```
4071 Rose 191
74842 Lisa 174
84072 Bonnie 100
4806 Angela 89
26071 Frank 85
80305 Kimberly 67
49438 Patrick 43
```
## Explanation

Hacker 4071 submitted solutions for challenges 19797 and 49593, so the total score = 95 + max(43,96) = 191. 

Hacker 74842 submitted solutions for challenges 19797 and 63132, so the total score = max(98,5) + 76 = 174. 

Hacker 84072 submitted solutions for challenges 49593 and 63132, so the total score = 100 + 0 = 100.

The total scores for hackers 4806, 26071, 80305, and 49438 can be similarly calculated.

# Solution

```
/*
total score = sum of max scores for all challenges
*/
select s.hacker_id, h.name, sum(score) as tscore from (
select hacker_id, challenge_id, max(score) as score from
    submissions group by hacker_id, challenge_id
) as s
join hackers as h on s.hacker_id = h.hacker_id
group by s.hacker_id, h.name having tscore > 0
order by tscore desc, s.hacker_id
```
