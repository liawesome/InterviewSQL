### Thoughts: 

- The question asks to find the rows that contain the median salary of each company. (Use row_number() to sort)
- To find the median, we split into even/odd cases. For example, if we have 6 salary records, we need to choose 3 and 4. If we have 5, we should choose 3.
- Thus it is between n/2 and n/2+1


### Answers: 
```
with cte as (select id, company, 
      row_number() over(partition by company order by salary) as rnk, 
      count(id) over(partition by company) as n 
from Employee )

select id, company, salary from cte
where rnk>=n/2 and rnk <=n/2+1

```
