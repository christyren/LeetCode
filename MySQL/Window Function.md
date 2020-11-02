184. Department Highest Salary
~~~~sql
select d.Name Department, subquery.Name Employee, subquery.Salary
from 
(select Name, Salary, DepartmentId, 
RANK() over (partition by DepartmentId order by Salary desc) as rk
from Employee) subquery inner join Department d
on subquery.DepartmentId = d.Id
where subquery.rk = 1;
~~~~


