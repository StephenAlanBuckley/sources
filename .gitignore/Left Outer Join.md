> Programming in SQL is a humbling experience. I thought I knew just what this would return:
>
> create table a (a1 int primary key, a2 int)
> create table b (b1 int primary key, a1 int)
>
> insert a values (1, 10)
> insert a values (2, 20)
> insert b values (2, 2)
>
> select * 
> from a 
> left join b 
> on a.a1 = b.a1 
> and a.a1 = 1
>
>
> Here's the results:
> a1 a2 b1 a1
> 1 10 NULL NULL
> 2 20 NULL NULL
>
> Can someone explain to me why the second row is there? Obviously, moving the line a.a1 = 1 into a WHERE clause will eliminate the row, but I'd like a technical explanation as to why SQL null-extends the second row and includes it in the result set. I'd understand this action if the ON clause referenced a b column and a constant, but I thought that the inner table to constant conditions in an ON clause behaved identically to that condition in a WHERE clause.
>
> My understanding of LEFT JOIN was: return NULLS for all columns of null-extended table (b, in this case) where criteria involving that table is not met. However, here is what BOL says on outer joins:
>
>
> Inner joins eliminate the rows that do not match with a row from the other table. Outer joins, however, return all rows from at least one of the tables or views mentioned in the FROM clause, as long as those rows meet any WHERE or HAVING search conditions. All rows are retrieved from the left table referenced with a left outer join, and all rows from the right table referenced in a right outer join. All rows from both tables are returned in a full outer join
>
>
> Wow, that's just not the way I've viewed outer joins for the last 10 years of daily programming. Does this surprise anyone else?
>
> Vince 

[Source](https://www.sqlservercentral.com/Forums/Topic449462-338-1.aspx)
