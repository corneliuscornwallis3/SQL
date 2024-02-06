# Problem

[Problem Link](https://www.hackerrank.com/challenges/interviews/problem?isFullScreen=true)

# Solution

```
select cn1.contest_id, cn.hacker_id, cn.name, sum(sg.total_submissions), sum(sg.total_accepted_submissions), sum(vg.total_views), sum(vg.total_unique_views) from (
    contests as cn join colleges as cn1 using(contest_id)
    join challenges as ch on cn1.college_id = ch.college_id
    left join (select vw.challenge_id, sum(vw.total_views) as total_views, sum(vw.total_unique_views) as total_unique_views from view_stats as vw group by vw.challenge_id) as vg on ch.challenge_id = vg.challenge_id
    left join (select ss.challenge_id, sum(ss.total_submissions) as total_submissions, sum(ss.total_accepted_submissions) as total_accepted_submissions from Submission_stats as ss group by ss.challenge_id) as sg on ch.challenge_id = sg.challenge_id
)
group by cn1.contest_id, cn.hacker_id, cn.name having sum(sg.total_submissions) > 0 or sum(sg.total_accepted_submissions) > 0 or sum(vg.total_views) > 0 or sum(vg.total_unique_views) > 0
order by cn1.contest_id
```
