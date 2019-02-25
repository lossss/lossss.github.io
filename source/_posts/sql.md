---
title: sql
date: 2019-02-23 02:56:56
categories: sql
tags: sql
---
必要的sql 备注
<!--more-->
## oracle
### 查询表结构
```sql
desc tablename;
```

### 打开编辑窗口 编辑完后/执行
```sql
ed
```
### || 连接字符串
```sql
select last_name||'`s job is '||job_id from employees
```

### <> 不等于
``` sql 
select *
from employees
where job_id <> 'IT_PROG'
```

### 去重 distinct
```sql
select distinct job_id from employees
```

### where
```sql
select * from employees where department_id = 90
```
### 范围
```sql
select last_name
from employees 
where salary>=4000 and salary<=7000
```
### in
```sql
select last_name
from employees
where department_id in (80,90);
```
### between 包含边界
```sql
select last_name
from employees
where salary between 3000 and 5000
```

### like
```sql
select last_name
from employees
where last_name like '%a%' -- 名字中含有a

where last_name like '%a' -- 以a结尾
where last_name like '_a%' -- 第二个字符是a
where last_name like '#_%' escape '#' -- 名字中带有_

```

### is null
```sql
select last_name
from employees
where commission_pct is null
```

### order by
```sql
select last_name
from employees
where department_id =80
order by salary desc,last_name asc -- 多层排序

order by salary asc

--按照别名排序
select last_name, 12*salary annual_sal
from employees
order by annual_sal desc
```
### 函数
#### 单行函数
```sql
select * 
from employees
where upper(last_name) = 'KING'
where lower(last_name) = 'king'

```
#### 字符控制函数
```sql
select CONCAT('Hello', 'World') from dual
select SUBSTR('HelloWorld',1,5) from dual -- 第一位下标1 截取5个数
select LENGTH('HelloWorld') from dual
select INSTR('HelloWorld', 'W') from dual
select LPAD(salary,10,'*') from dual
select RPAD(salary, 10, '*') from dual
select TRIM('H' FROM 'HelloWorld') from dual
select REPLACE(‘abcd’,’b’,’m’) from dual -- 替换所有匹配到的

```
#### 数字函数
```sql
select ROUND(45.926, 2) from dual -- 四舍五入

select TRUNC(45.926, 2) from dual -- 截断

select MOD(1600, 300) from dual -- 求余数

```
#### 日期函数
```sql
-- 日期相减 表示相差天数
select last_name,trunc(sysdate-hire_date)
from employees

-- 两个日期相差的月数
MONTHS_BETWEEN

-- 向指定日期中加上若干月数
ADD_MONTHS

-- 指定日期的下一个星期 * 对应的日期
NEXT_DAY

-- 本月的最后一天
LAST_DAY

-- 日期四舍五入
ROUND(SYSDATE,'MONTH')

-- 日期截断
TRUNC(SYSDATE ,'MONTH')
```
| 符号 | 含义 |
|------|------|
| yyyy | 年   |
| mm   | 月   |
| dd   | 日   |
| day  | 星期 |
| hh   | 小时 |
| mi   | 分钟 |
| ss   | 秒   |


### 转换函数
#### to_char
```sql
select employee_id,hire_date
from employees
where to_char(hire_date,'yyyy-mm-dd')='1994-06-07'

select to_char(12345678.9, '999,999,999.99') from dual-- 12,345,678.90

select to_char(12345678.9, '000,999,999.99') from dual--  012,345,678.90

select to_char(12345678.9, '$000,999,999.99') from dual

select to_char(12345678.9, 'L000,999,999.99') from dual -- 当地货币符号
```
#### to_number
```sql
select to_number('￥012,345,678.90','L000,999,999.99') from dual
```
#### to_date
```sql
select * from employees
where hire_date = to_date('1994-06-07','yyyy-mm-dd')
```

### 通用函数
#### nvl
```sql
-- 为空则用0代替
select employee_id,last_name,salary*12*(1+nvl(commission_pct,0)) from employees
```
#### nvl2
```sql
-- 不为空+0.015 为空则返回0.01
select last_name,commission_pct,nvl2(commission_pct,commission_pct+0.015,0.01)
from employees
```
#### case
```sql
select employee_id,last_name,department_id,case department_id when 10 then salary*1.1
                                                              when 20 then salary*1.2
                                                              else salary*1.3end new_sal
from employees
where department_id in (10,20,30)
```
#### decode
```sql
select employee_id,last_name,department_id,decode(department_id,10,salary*1.1,
                                                                20,salary*1.2,
                                                                salary) new_sal
from employees
where department_id in (10,20,30)
```

### 多表查询
#### 内连接
```sql
-- 等值连接
select e.employee_id,e.department_id,d.department_name
from employees e,departments d
where e.department_id=d.department_id

-- 非等值连接
select e.employee_id,e.department_id,j.grade_level
from employees e,job_grades j
where e.salary between j.lowest_sal and j.highest_sal
```

#### 外连接
```sql
-- 左外连接
-- 有些员工没有部门
select e.employee_id,e.department_id,d.department_name
from employees e,departments d
where e.department_id=d.department_id(+)

select last_name,e.department_id,department_name
from employees e
join departments d
on e.department_id = d.department_id

-- left join
select last_name,e.department_id,department_name
from employees e
left join departments d
on e.department_id = d.department_id

-- right join
select last_name,e.department_id,department_name
from employees e
right join departments d
on e.department_id = d.department_id
hello
-- full join
select last_name,e.department_id,department_name
from employees e
full join departments d
on e.department_id = d.department_id

-- 自连接
select emp.last_name,emp.department_id,d.department_name,manager.last_name
from employees emp
join employees manager
on emp.manager_id = manager.employee_id
join departments d
on emp.department_id = d.department_id
```

### 分组函数
```sql
-- avg 会忽略空值 如果不想忽略则改为  avg(nvl(commission_pct,0))
select avg(salary), max(salary),min(salary), sum(salary)
from   employees
where  job_id like '%REP%'

-- count 会忽略空值 不想忽略则count(nvl(department_id))
select count(department_id)
from employees

-- 非空且不重复的记录总数
select count(distinct department_id)
from   employees

--gourp by
select department_id,job_id,avg(salary)
from employees
group by department_id,job_id

-- having where 里面不能出现分组函数 此时替换为having即可
select department_id,job_id,avg(salary)
from employees
group by department_id,job_id

```
### 子查询
#### 单行子查询
```sql
select last_name
from   employees
where  salary >
               (select salary
                from   employees
                where  last_name = 'abel');

```
#### 多行子查询

| 操作符 | 含义                       |
|--------|----------------------------|
| IN     | 等于列表中的任意一个       |
| ANY    | 和子查询返回的某一个值比较 |
| ALL    | 和子查询返回的所有值比较   |

```sql
-- any
select employee_id, last_name, job_id, salary
from   employees
where  salary < any
                    (select salary
                     from   employees
                     where  job_id = 'IT_PROG')
and    job_id <> 'IT_PROG';

-- all
select employee_id, last_name, job_id, salary
from   employees
where  salary < all
                    (select salary
                     from   employees
                     where  job_id = 'IT_PROG')
and    job_id <> 'IT_PROG';

```
### 
```sql

```
### 
```sql

```
### 
```sql

```
### 
```sql

```
## mysql 知识复习
### 数据类型 

| 类型    | 长度    | 格式                     | 其他                           |
|---------|---------|--------------------------|--------------------------------|
| double  | 8       | 双精度浮点数             |                                |
| enum    | --      |                          | 单选,比如性别	enum('a','b','c') |
| set     | --      | 多选	set('1','2','3')     |                                |
| date    | 3       | 日期	yyyy-mm-dd           |                                |
| time    | 3       | 时间点或持续时间	hh:mm:ss |                                |
| year    | 1       | 年份值	yyyy               |                                |
| char    | 0~255   | 定长字符串               |                                |
| varchar | 0~255   | 变长字符串               |                                |
| text    | 0~65535 | 长文本数据               |                                |

注:
1. 整数除了 int 外，还有 tinyint、smallint、mediumint、bigint。

2. char 和 varchar 的区别: char 的长度是固定的，而 varchar 的长度是可以变化的，比如，存储字符串 “abc"，对于 char(10)，表示存储的字符将占 10 个字节(包括 7 个空字符)，而同样的 varchar(12) 则只占用4个字节的长度，增加一个额外字节来存储字符串本身的长度，12 只是最大值，当你存储的字符小于 12 时，按实际长度存储。

enum和set的区别: enum 类型的数据的值，必须是定义时枚举的值的其中之一，即单选，而 set 类型的值则可以多选。