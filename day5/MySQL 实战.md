# MySQL 实战
## 项目七: 各部门工资最高的员工（难度：中等）
创建Employee 表，包含所有员工信息，每个员工有其对应的 Id, salary 和 department Id。
+----+-------+--------+--------------+
| Id | Name  | Salary | DepartmentId |
+----+-------+--------+--------------+
| 1  | Joe   | 70000  | 1            |
| 2  | Henry | 80000  | 2            |
| 3  | Sam   | 60000  | 2            |
| 4  | Max   | 90000  | 1            |
+----+-------+--------+--------------+
创建Department 表，包含公司所有部门的信息。
+----+----------+
| Id | Name     |
+----+----------+
| 1  | IT       |
| 2  | Sales    |
+----+----------+
编写一个 SQL 查询，找出每个部门工资最高的员工。例如，根据上述给定的表格，Max 在 IT 部门有最高工资，Henry 在 Sales 部门有最高工资。
+------------+----------+--------+
| Department | Employee | Salary |
+------------+----------+--------+
| IT         | Max      | 90000  |
| Sales      | Henry    | 80000  |
+------------+----------+--------

代码：
```
CREATE TABLE Department (Id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(10));

CREATE TABLE Employee (Id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
Name VARCHAR(10), Salary BIGINT, DepartmentId INT NOT NULL);

INSERT INTO Employee (Id, Name, Salary, DepartmentId) VALUES
 (1, "Joe", 70000, 1),
 (2, "Henry", 80000, 2),
 (3, "Sam", 60000, 2),
 (4, "Max", 90000, 1);

INSERT INTO Department (Id, Name) VALUES
 (1, "IT"),
 (2, "Sales");

 SELECT d.Name Department, e.Name Employee,  Salary
 FROM Employee e, Department d
 WHERE e.DepartmentId = d.Id
 AND Salary IN (SELECT MAX(Salary)
 FROM Employee, Department
 WHERE DepartmentId = Department.Id
 GROUP BY Department.Id);
 ```
 
 ## 项目八: 换座位（难度：中等）
小美是一所中学的信息科技老师，她有一张 seat 座位表，平时用来储存学生名字和与他们相对应的座位 id。
其中纵列的 id 是连续递增的
小美想改变相邻俩学生的座位。
你能不能帮她写一个 SQL query 来输出小美想要的结果呢？
 请创建如下所示seat表：
示例：
+---------+---------+
|    id   | student |
+---------+---------+
|    1    | Abbot   |
|    2    | Doris   |
|    3    | Emerson |
|    4    | Green   |
|    5    | Jeames  |
+---------+---------+
假如数据输入的是上表，则输出结果如下：
+---------+---------+
|    id   | student |
+---------+---------+
|    1    | Doris   |
|    2    | Abbot   |
|    3    | Green   |
|    4    | Emerson |
|    5    | Jeames  |
+---------+---------+
注意：
如果学生人数是奇数，则不需要改变最后一个同学的座位。

代码：
```
--创建表
 CREATE TABLE seat (id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
     student VARCHAR(20));

--插入数据
INSERT INTO seat (id, student) VALUES
    (1, "Abbot"),
    (2, "Doris"),
    (3, "Emerson"),
    (4, "Green"),
    (5, "Jeames");
    
SELECT (CASE 
        WHEN id % 2 != 0 AND id != counts THEN id+1
        WHEN id % 2 != 0 AND id = counts THEN id
        ELSE id-1 
        END) AS id, student
FROM seat, 
(SELECT COUNT(*) counts FROM seat) as seat_count
ORDER BY id;
```

## 项目九:  分数排名（难度：中等）
编写一个 SQL 查询来实现分数排名。如果两个分数相同，则两个分数排名（Rank）相同。请注意，平分后的下一个名次应该是下一个连续的整数值。换句话说，名次之间不应该有“间隔”。
创建以下score表：
+----+-------+
| Id | Score |
+----+-------+
| 1  | 3.50  |
| 2  | 3.65  |
| 3  | 4.00  |
| 4  | 3.85  |
| 5  | 4.00  |
| 6  | 3.65  |
+----+-------+
例如，根据上述给定的 Scores 表，你的查询应该返回（按分数从高到低排列）：
+-------+------+
| Score | Rank |
+-------+------+
| 4.00  | 1    |
| 4.00  | 1    |
| 3.85  | 2    |
| 3.65  | 3    |
| 3.65  | 3    |
| 3.50  | 4    |
+-------+------+

代码：
```
--创建表
CREATE TABLE score (Id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
Score DOUBLE);

--插入数据    
INSERT INTO score (Id, Score) VALUES
(1, 3.50),
(2, 3.65),
(3, 4.00),
(4, 3.85),
(5, 4.00),
(6, 3.65);

SELECT Score,
(SELECT COUNT(DISTINCT Score) 
FROM score WHERE Score >= s.Score) 
AS Rank 
FROM score s 
ORDER BY Score DESC;
```
## 参考 
- [MYSQL实战](https://www.zxpblog.cn/2019/03/03/Excel%E6%96%87%E4%BB%B6%E5%AF%BC%E5%85%A5%E5%AF%BC%E5%87%BA%E5%92%8C%E7%BB%83%E4%B9%A0%E9%A2%98/#more)
