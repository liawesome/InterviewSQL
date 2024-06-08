### Thoughts:

- The question asks to find the count
  - the number of players that logged in for at least two consecutive days starting from their first login date
  - the total number of players
  - only count the non-null value 


```
select count(distinct b.player_id) / count(a.player_id) as fraction from 
(select player_id, min(event_date) as event_date from Activity group by 1) a
left join Activity b
on a.player_id = b.player_id and datediff(a2.event_date, a1.event_date)=1

```
