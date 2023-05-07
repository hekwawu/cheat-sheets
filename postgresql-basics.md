### Table of Contents
[Selections](#selections)</br>
[Filtering](#filtering) </br>
[Sorting](#sorting) </br>
[Aggregate Functions](#aggregate-functions) </br>
[GROUP BY FUNCTIONS](#group-by-functions)


### Selections 
```sql
SELECT col1, col2 etc
FROM table
```
- Columns can be aliased with different names using `AS`

### Filtering
```sql
WHERE col [expression]
```
- Where statements can be stacked using AND/OR/NOT statements, do not have to act on the same columns
```sql
WHERE col [expression]
  AND col2 [expression]
```
> Note: Alias and aggregations can NOT be used in WHERE statements

- Filtering based on text data
```sql
WHERE col = 'string'
WHERE col IN/ NOT IN ('text1','text2' etc)
WHERE col LIKE/NOT LIKE (regular expression)
```
- Simple subqueries can be called using `IN/NOT IN`
```sql
WHERE
  col IN/NOT IN (
    SELECT col
    from table) 
```

### Sorting
```sql
  ORDER BY col1, col2 etc       ## Orders data ascending
  ORDER BY col1, col2 ETC DESC  ## Orders data by descending
```
- Columns are sorted independently (ie when can be asc, one can be desc)

### Aggregate Functions
- Any time data is being calculated based on column values, we have to use a `GROUP BY` function
```sql
SELECT
  COUNT(*)
FROM table
GROUP BY col
```
- Can group on multiple columns, grouping goes in order of listing
  - Visualize a pivot table and how data aggregates 
- Aggregate functions requiring `GROUP BY`
```sql
SELECT
  COUNT(*)              # Returns number of rows
  COUNT(col)            # Returns number of non-NULL values in a column
  COUNT (DISTINCT col)  # Returns number of distinct values in column
  
  SUM(column)           # Adds integer values in a column
  MIN(col)              # Returns minimum value of a column
  MAX(col)              # Returns maximum value of a column
  AVG(col)              # Returns average value of a column
```

#### GROUP BY FUNCTIONS
- `WHERE` statements can come before grouping, however better approach is to use `HAVING`
```sql
GROUP BY col
  HAVING col [expression]
```
  - Similar AND/OR/NOT rules apply, however `HAVING` **CAN** use aggreggations
- `GROUP BY ROLLUP` provides a summary statistic for every combination of values run through it
  - Again, think of a pivot table and the levels of subtotals
```sql
GROUP BY col1, col2 etc
  WITH ROLLUP col1, col2 etc
```
