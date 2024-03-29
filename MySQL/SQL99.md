# 连接查询 SQL99

- SQL99 标准下的连接查询是如何操作的？
- SQL99 与 SQL92 的区别是什么？
- 在不同的 DBMS 中，使用连接需要注意什么？



如之前的表结构；

### 交叉连接

交叉连接实际上就是 SQL92 中的笛卡尔乘积，只是这里我们采用的是 CROSS JOIN。我们可以通过下面这行代码得到 player 和 team 这两张表的笛卡尔积的结果：

`SQL: SELECT * FROM player CROSS JOIN team`

如果多张表进行交叉连接，比如表 t1，表 t2，表 t3 进行交叉连接，可以写成下面这样：

`SQL: SELECT * FROM t1 CROSS JOIN t2 CROSS JOIN t3`



### 自然连接



你可以把自然连接理解为 SQL92 中的等值连接。它会帮你自动查询两张连接表中所有相同的字段，然后进行等值连接。

如果我们想把 player 表和 team 表进行等值连接，相同的字段是 team_id。还记得在 SQL92 标准中，是如何编写的么？

`SELECT player_id, a.team_id, player_name, height, team_name FROM player as a, team as b WHERE a.team_id = b.team_id`

在 SQL99 中你可以写成：

`SELECT player_id, team_id, player_name, height, team_name FROM player NATURAL JOIN team `

实际上，在 SQL99 中用 NATURAL JOIN 替代了 WHERE player.team_id = team.team_id



### ON 连接

ON 连接用来指定我们想要的连接条件，针对上面的例子，它同样可以帮助我们实现自然连接的功能：

`SELECT player_id, player.team_id, player_name, height, team_name `

`FROM player JOIN team ON player.team_id = team.team_id`

这里我们指定了连接条件是ON player.team_id = team.team_id，相当于是用 ON 进行了 team_id 字段的等值连接。



当然你也可以 ON 连接进行非等值连接，比如我们想要查询球员的身高等级，需要用 player 和 height_grades 两张表：

`SQL99：SELECT p.player_name, p.height, h.height_level
FROM player as p JOIN height_grades as h
ON height BETWEEN h.height_lowest AND h.height_highest`

这个语句的运行结果和我们之前采用 SQL92 标准的查询结果一样。

`SQL92：SELECT p.player_name, p.height, h.height_level
FROM player AS p, height_grades AS h
WHERE p.height BETWEEN h.height_lowest AND h.height_highest`

一般来说在 SQL99 中，我们需要连接的表会采用 JOIN 进行连接，ON 指定了连接条件，后面可以是等值连接，也可以采用非等值连接。



### USING 连接



当我们进行连接的时候，可以用 USING 指定数据表里的同名字段进行等值连接。比如：

`SELECT player_id, team_id, player_name, height, team_name FROM player `

`JOIN team USING(team_id)`

你能看出与自然连接 NATURAL JOIN 不同的是，USING 指定了具体的相同的字段名称，你需要在 USING 的括号 () 中填入要指定的同名字段。同时使用 JOIN USING 可以简化 JOIN ON 的等值连接，它与下面的 SQL 查询结果是相同的：

`SELECT player_id, player.team_id, player_name, height, team_name FROM player `

`JOIN team `  `ON player.team_id = team.team_id`



你能看出与自然连接 NATURAL JOIN 不同的是，USING 指定了具体的相同的字段名称，你需要在 USING 的括号 () 中填入要指定的同名字段。同时使用 JOIN USING 可以简化 JOIN ON 的等值连接，它与下面的 SQL 查询结果是相同的：

`SELECT player_id, player.team_id, player_name, height, team_name FROM player `

`JOIN team ` `ON player.team_id = team.team_id`



### 外连接

SQL99 的外连接包括了三种形式：

​	左外连接：LEFT JOIN 或 LEFT OUTER JOIN

​	右外连接：RIGHT JOIN 或 RIGHT OUTER JOIN

​	全外连接：FULL JOIN 或 FULL OUTER JOIN



我们在 SQL92 中讲解了左外连接、右外连接，在 SQL99 中还有全外连接。全外连接实际上就是左外连接和右外连接的结合。在这三种外连接中，我们一般省略 OUTER 不写。

1. 左外连接

   SQL92

   ​		`SELECT * FROM player, team where player.team_id = team.team_id(+)`

   SQL99

   ​		`		SELECT * FROM player LEFT JOIN team ON player.team_id = team.team_id`



2. 右外连接

   SQL92

   ​	`SELECT * FROM player, team where player.team_id(+) = team.team_id`

   SQL99

   ​	`SELECT * FROM player RIGHT JOIN team ON player.team_id = team.team_id`



3. 全外连接

   SQL99

   ​	`SELECT * FROM player FULL JOIN team ON player.team_id = team.team_id`

​	

需要注意的是 MySQL 不支持全外连接，否则的话全外连接会返回左表和右表中的所有行。当表之间有匹配的行，会显示内连接的结果。当某行在另一个表中没有匹配时，那么会把另一个表中选择的列显示为空值。

也就是说，全外连接的结果 = 左右表匹配的数据 + 左表没有匹配到的数据 + 右表没有匹配到的数据。



### 自连接

自连接的原理在 SQL92 和 SQL99 中都是一样的，只是表述方式不同。

比如我们想要查看比布雷克·格里芬身高高的球员都有哪些，在两个 SQL 标准下的查询如下。

SQL92

​	`SELECT b.player_name, b.height FROM player as a , player as b WHERE a.player_name = '布雷克 - 格里芬' and a.height < b.height`

SQL99

​	`SELECT b.player_name, b.height FROM player as a JOIN player as b ON a.player_name = '布雷克 - 格里芬' and a.height < b.height`





### SQL99 和 SQL92 的区别

至此我们讲解完了 SQL92 和 SQL99 标准下的连接查询，它们都对连接进行了定义，只是操作的方式略有不同。我们再来回顾下，这些连接操作基本上可以分成三种情况：

- 内连接：将多个表之间满足连接条件的数据行查询出来。它包括了等值连接、非等值连接和自连接。
- 外连接：会返回一个表中的所有记录，以及另一个表中匹配的行。它包括了左外连接、右外连接和全连接。
- 交叉连接：也称为笛卡尔积，返回左表中每一行与右表中每一行的组合。在 SQL99 中使用的 CROSS JOIN。



不过 SQL92 在这三种连接操作中，和 SQL99 还存在着明显的区别。

首先我们看下 SQL92 中的 WHERE 和 SQL99 中的 JOIN。

你能看出在 SQL92 中进行查询时，会把所有需要连接的表都放到 FROM 之后，然后在 WHERE 中写明连接的条件。而 SQL99 在这方面更灵活，它不需要一次性把所有需要连接的表都放到 FROM 之后，而是采用 JOIN 的方式，每次连接一张表，可以多次使用 JOIN 进行连接。



另外，我建议多表连接使用 SQL99 标准，因为层次性更强，可读性更强，比如：



`SELECT ...
FROM table1
    JOIN table2 ON table1 和 table2 的连接条件
        JOIN table3 ON table2 和 table3 的连接条件`

 

它的嵌套逻辑类似我们使用的 FOR 循环：

`for t1 in table1:
    for t2 in table2:
       if condition1:
           for t3 in table3:
              if condition2:
                  output t1 + t2 + t3`

SQL99 采用的这种嵌套结构非常清爽，即使再多的表进行连接也都清晰可见。如果你采用 SQL92，可读性就会大打折扣。

最后一点就是，SQL99 在 SQL92 的基础上提供了一些特殊语法，比如 NATURAL JOIN 和 JOIN USING。它们在实际中是比较常用的，省略了 ON 后面的等值条件判断，让 SQL 语句更加简洁。





### 不同 DBMS 中使用连接需要注意的地方

SQL 连接具有通用性，但是不同的 DBMS 在使用规范上会存在差异，在标准支持上也存在不同。在实际工作中，你需要参考你正在使用的 DBMS 文档，这里我整理了一些需要注意的常见的问题。

1. 不是所有的 DBMS 都支持全外连接

   虽然 SQL99 标准提供了全外连接，但不是所有的 DBMS 都支持。不仅 MySQL 不支持，Access、SQLite、MariaDB 等数据库软件也不支持。不过在 Oracle、DB2、SQL Server 中是支持的。

2. Oracle 没有表别名 AS

   为了让 SQL 查询语句更简洁，我们经常会使用表别名 AS，不过在 Oracle 中是不存在 AS 的，使用表别名的时候，直接在表名后面写上表别名即可，比如 player p，而不是 player AS p。

3. SQLite 的外连接只有左连接

   SQLite 是一款轻量级的数据库软件，在外连接上只支持左连接，不支持右连接，不过如果你想使用右连接的方式，比如table1 RIGHT JOIN table2 ，在 SQLite 你可以写成 table2 LEFT JOIN table1，这样就可以得到相同的效果。

   

   

   

   除了一些常见的语法问题，还有一些关于连接的性能问题需要你注意：

   

   

   