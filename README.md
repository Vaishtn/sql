show databases;
+--------------------+
| Database           |
+--------------------+
| company            |
| emp                |
| information_schema |
| matrimony          |
| movie              |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| trv11              |
| world              |
| xworkz             |
| xworkz1            |
+--------------------+
13 rows in set (0.19 sec)

use company;
Database changed

 show tables;
+-------------------+
| Tables_in_company |
+-------------------+
| dept              |
| emp               |
+-------------------+
2 rows in set (0.14 sec)

desc dept;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| deptno   | int         | NO   | PRI | NULL    |       |
| dname    | varchar(45) | YES  |     | NULL    |       |
| location | varchar(45) | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
3 rows in set (0.13 sec)

insert into company.dept values(11,'Research','India');
Query OK, 1 row affected (0.13 sec)

insert into company.dept values(12,'Sales','Dallas');
Query OK, 1 row affected (0.29 sec)

insert into company.dept values(13,'Operation','USA');
Query OK, 1 row affected (0.11 sec)

insert into company.dept values(14,'Marketing','Chicago');
Query OK, 1 row affected (0.10 sec)

insert into company.dept values(15,'Finance','Bankokok');
Query OK, 1 row affected (0.15 sec)

select * from dept;
+--------+------------+----------+
| deptno | dname      | location |
+--------+------------+----------+
|     10 | accounting | New York |
|     11 | Research   | India    |
|     12 | Sales      | Dallas   |
|     13 | Operation  | USA      |
|     14 | Marketing  | Chicago  |
|     15 | Finance    | Bankokok |
+--------+------------+----------+
6 rows in set (0.00 sec)

create table emp(
    -> empno int not null primary key,
    -> ename varchar(50) not null,
    -> job varchar(50) not null,
    -> mgr int,
    -> hiredate date,
    -> sal decimal(10,2),
    -> comm decimal(10,2),
    -> deptno int not null,
    -> foreign key(deptno) references dept(deptno));
Query OK, 0 rows affected (3.98 sec)


 insert into emp values(7000,'Jhon','Manager',7698,'2020-06-18',2500.00,null,15),
    -> (7001,'Preeth','Manager',7698,'2020-06-18',2500.00,null,15);
Query OK, 2 rows affected (0.25 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> select * from emp;
+-------+-------+---------+------+------------+---------+------+--------+
| empno | ename | job     | mgr  | hiredate   | sal     | comm | deptno |
+-------+-------+---------+------+------------+---------+------+--------+
|  7000 | Jhon  | Manager | 7698 | 2020-06-18 | 2500.00 | NULL |     15|
|  7001 | Preeth| Manager | 7698 | 2020-06-18 | 2500.00 | NULL |     15 |
+-------+-------+---------+------+------------+---------+------+--------+
2 rows in set (0.00 sec)

mysql> insert into emp values(7004,'Ravi','Clerk',7782,'2000-12-12',500.00,null,15),
    -> (7369,'Smith','Clerk',7902,'1993-06-13',800,0.00,12),
    -> (7499,'Allen','Salesman',7698,'1998-08-15',1600,300.00,13),
    -> (7521,'Ward','Salesman',7698,'1996-03-26',1250.00,500.00,13),
    -> (7566,'Jones','Manager',7839,'1995-10-31',2975.00,null,12),
    -> (7654,'Martin','Salesman',7698,'1998-12-05',1250.00,1400.00,13),
    -> (7698,'Blake','Manager',7839,'1992-06-11',2850.00,null,13),
    -> (7782,'Clark','Manager',7839,'1993-05-14',2450.00,null,11),
    -> (7788,'Scott','Analyst',7566,'1996-03-05',3000.00,null,12),
    -> (7839,'King','President',null,'1990-06-09',5000.00,0.00,11),
    -> (7844,'Turner','Salesman',7698,'1995-06-04',1500.00,0.00,13),
    -> (7876,'Adams','Clerk',7788,'1999-06-04',1100,null,12),
    -> (7900,'James','Clerk',7698,'2000-06-23',950.00,null,13),
    -> (7902,'Ford','Analyst',7566,'1997-12-05',3000.00,null,12),
    -> (7934,'Miller','Clerk',7782,'2000-01-21',1300.00,null,11);
Query OK, 15 rows affected (0.10 sec)
Records: 15  Duplicates: 0  Warnings: 0

 select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7000 | Jhon   | Manager   | 7698 | 2020-06-18 | 2500.00 |    NULL |     11 |
|  7001 | Preeth | Manager   | 7698 | 2020-06-18 | 2500.00 |    NULL |     11 |
|  7004 | Ravi   | Clerk     | 7782 | 2020-12-12 |  500.00 |    NULL |     11 |
|  7369 | Smith  | Clerk     | 7902 | 1993-06-13 |  800.00 |    0.00 |     12 |
|  7499 | Allen  | Salesman  | 7698 | 1998-08-15 | 1600.00 |  300.00 |     13 |
|  7521 | Ward   | Salesman  | 7698 | 1996-03-26 | 1250.00 |  500.00 |     13 |
|  7566 | Jones  | Manager   | 7839 | 1995-10-31 | 2975.00 |    NULL |     12 |
|  7654 | Martin | Salesman  | 7698 | 1998-12-05 | 1250.00 | 1400.00 |     13 |
|  7698 | Blake  | Manager   | 7839 | 1992-06-11 | 2850.00 |    NULL |     13 |
|  7782 | Clark  | Manager   | 7839 | 1993-05-14 | 2450.00 |    NULL |     11 |
|  7788 | Scott  | Analyst   | 7566 | 1996-03-05 | 3000.00 |    NULL |     12 |
|  7839 | King   | President | NULL | 1990-06-09 | 5000.00 |    0.00 |     11 |
|  7844 | Turner | Salesman  | 7698 | 1995-06-04 | 1500.00 |    0.00 |     13 |
|  7876 | Adams  | Clerk     | 7788 | 1999-06-04 | 1100.00 |    NULL |     12 |
|  7900 | James  | Clerk     | 7698 | 2000-06-23 |  950.00 |    NULL |     13 |
|  7902 | Ford   | Analyst   | 7566 | 1997-12-05 | 3000.00 |    NULL |     12 |
|  7934 | Miller | Clerk     | 7782 | 2000-01-21 | 1300.00 |    NULL |     11 |
+-------+--------+-----------+------+------------+---------+---------+--------+
17 rows in set (0.00 sec)

 select * from company.emp where ename like 'S%';
+-------+-------+---------+------+------------+---------+------+--------+
| empno | ename | job     | mgr  | hiredate   | sal     | comm | deptno |
+-------+-------+---------+------+------------+---------+------+--------+
|  7369 | Smith | Clerk   | 7902 | 1993-06-13 |  800.00 | 0.00 |     12 |
|  7788 | Scott | Analyst | 7566 | 1996-03-05 | 3000.00 | NULL |     12 |
+-------+-------+---------+------+------------+---------+------+--------+
2 rows in set (0.00 sec)

select * from company.emp where ename like '%E_';
+-------+--------+----------+------+------------+---------+--------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal     | comm   | deptno |
+-------+--------+----------+------+------------+---------+--------+--------+
|  7499 | Allen  | Salesman | 7698 | 1998-08-15 | 1600.00 | 300.00 |     13 |
|  7566 | Jones  | Manager  | 7839 | 1995-10-31 | 2975.00 |   NULL |     12 |
|  7844 | Turner | Salesman | 7698 | 1995-06-04 | 1500.00 |   0.00 |     13 |
|  7900 | James  | Clerk    | 7698 | 2000-06-23 |  950.00 |   NULL |     13 |
|  7934 | Miller | Clerk    | 7782 | 2000-01-21 | 1300.00 |   NULL |     11 |
+-------+--------+----------+------+------------+---------+--------+--------+
5 rows in set (0.00 sec)

select * from company.emp where sal between 2000 AND 3000;
+-------+--------+---------+------+------------+---------+------+--------+
| empno | ename  | job     | mgr  | hiredate   | sal     | comm | deptno |
+-------+--------+---------+------+------------+---------+------+--------+
|  7000 | Jhon   | Manager | 7698 | 2020-06-18 | 2500.00 | NULL |     11 |
|  7001 | Preeth | Manager | 7698 | 2020-06-18 | 2500.00 | NULL |     11 |
|  7566 | Jones  | Manager | 7839 | 1995-10-31 | 2975.00 | NULL |     12 |
|  7698 | Blake  | Manager | 7839 | 1992-06-11 | 2850.00 | NULL |     13 |
|  7782 | Clark  | Manager | 7839 | 1993-05-14 | 2450.00 | NULL |     11 |
|  7788 | Scott  | Analyst | 7566 | 1996-03-05 | 3000.00 | NULL |     12 |
|  7902 | Ford   | Analyst | 7566 | 1997-12-05 | 3000.00 | NULL |     12 |
+-------+--------+---------+------+------------+---------+------+--------+
7 rows in set (0.02 sec)

 select * from company.emp where empno BETWEEN 7000 AND 7500;
+-------+--------+----------+------+------------+---------+--------+--------+
| empno | ename  | job      | mgr  | hiredate   | sal     | comm   | deptno |
+-------+--------+----------+------+------------+---------+--------+--------+
|  7000 | Jhon   | Manager  | 7698 | 2020-06-18 | 2500.00 |   NULL |     11 |
|  7001 | Preeth | Manager  | 7698 | 2020-06-18 | 2500.00 |   NULL |     11 |
|  7004 | Ravi   | Clerk    | 7782 | 2020-12-12 |  500.00 |   NULL |     11 |
|  7369 | Smith  | Clerk    | 7902 | 1993-06-13 |  800.00 |   0.00 |     12 |
|  7499 | Allen  | Salesman | 7698 | 1998-08-15 | 1600.00 | 300.00 |     13 |
+-------+--------+----------+------+------------+---------+--------+--------+
5 rows in set (0.00 sec)

mysql> select ename,comm from company.emp where comm is NULL;
+--------+------+
| ename  | comm |
+--------+------+
| Jhon   | NULL |
| Preeth | NULL |
| Ravi   | NULL |
| Jones  | NULL |
| Blake  | NULL |
| Clark  | NULL |
| Scott  | NULL |
| Adams  | NULL |
| James  | NULL |
| Ford   | NULL |
| Miller | NULL |
+--------+------+
11 rows in set (0.00 sec)

mysql> select * from company.emp where job='salesman' AND deptno=13 AND sal>1500;
+-------+-------+----------+------+------------+---------+--------+--------+
| empno | ename | job      | mgr  | hiredate   | sal     | comm   | deptno |
+-------+-------+----------+------+------------+---------+--------+--------+
|  7499 | Allen | Salesman | 7698 | 1998-08-15 | 1600.00 | 300.00 |     13 |
+-------+-------+----------+------+------------+---------+--------+--------+
1 row in set (0.04 sec)

mysql> select count(comm) from company.emp;
+-------------+
| count(comm) |
+-------------+
|           6 |
+-------------+
1 row in set (0.04 sec)

mysql> select count(empno) from company.emp where deptno=13;
+--------------+
| count(empno) |
+--------------+
|            6 |
+--------------+
1 row in set (0.00 sec)

mysql> select sum(sal) from company.emp where deptno=12;
+----------+
| sum(sal) |
+----------+
| 10875.00 |
+----------+
1 row in set (0.10 sec)

mysql> select count(*),sum(sal),avg(sal) from company.emp where deptno=30;
+----------+----------+----------+
| count(*) | sum(sal) | avg(sal) |
+----------+----------+----------+
|        0 |     NULL |     NULL |
+----------+----------+----------+
1 row in set (0.10 sec)

select sum(sal) from company.emp group by deptno;
+----------+
| sum(sal) |
+----------+
| 14250.00 |
| 10875.00 |
|  9400.00 |
+----------+
3 rows in set (0.03 sec)

select max(sal) from company.emp group by job;
+----------+
| max(sal) |
+----------+
|  2975.00 |
|  1300.00 |
|  1600.00 |
|  3000.00 |
|  5000.00 |
+----------+
5 rows in set (0.12 sec)


