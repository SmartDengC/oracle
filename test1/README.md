# test1.md

# 任务一：
## 对两个sql语句进行对比优化
查询一
```sql
set autotrace on

SELECT d.department_name,count(e.job_id)as "部门总人数",
avg(e.salary)as "平均工资"
from hr.departments d,hr.employees e
where d.department_id = e.department_id
and d.department_name in ('IT','Sales')
GROUP BY d.department_name;
```

# 处理结果

![](./picture/sent_pic_1.png)