# Join Types

- Mutating joins: Combines data from two tables based on matching observations in both tables.
- Filtering joins: Filter observations from table based on whether or not they match an observation in another table.

## Mutating Joins
### Inner join

Only return rows that have matching value in both tables. 

`df1.merge(df2, on='col1')`: Joining two dataframes on col1 values. df1 columns would appear first in output. Merging can be done based on multiple columns. `on=['col1', 'col2']`

`df1.merge(df2, on='col1', suffixes=('_a', '_b')`: If column names are same in both dataframes by default columns in
dataframe are renamed like col_x, col_y. If we want to edit the names ourselves, we can set it with the suffix parameter. 
(Column names will be col_a, col_b) 

To merge multiple tables use code below. `\` ensures the continuation of the code on the next line.

```
merged_table = table1.merge(table2, on='col1') \
               .merge(table3, on='col2')
```

### Left join

`df1.merge(df2, on='col1', how='left')`: Similar syntax to inner join, difference is how parameter. All rows from df1 appear in the result, only matching ones appear from df2, if match not found returns NaN. 

### Right join

`df1.merge(df2, on='col1', how='right')`: All rows from df2 appear appear in the result, only matching ones appear from df1.

`df1.merge(df2, left_on='df1_col1', right_on='df2_col2', how='right')`: Sometimes **on** column may have different name across tables. 

### Outer join

Outer join is helpful to see which records are not in both tables. 

`df1.merge(df2, on='col1', how='outer')`

### Self join

Common situations:

- Hierarchical relationships
- Sequential relationships: For example if table contains movies and their sequel movie id's by merging this table to itself we can show this relationship in one line.
- Graph data: For example finding customers that are from the same city. 

## Filtering joins
### Semi join

Returns the intersection, similar to an inner join. Unlike inner join only columns from the left table are shown and no duplicate rows returned from the left table. (even if there are one to many relationship)

There is not a direct implementation of semi join in python. Steps are given below.

1. Merge the left and right tables on key column using an inner join.
2. Search if the key column in the left table is in the merged tables using the `.isin()` method creating a Boolean series.
3. Subset the rows of the left table.

### Anti join

Returns the left table, excluding the intersection.

## Concatenation

`.concat()` method can concatenate both vertical and horizontal. `axis=0` is vertical (by default) and `axis=1` is horizontal. 

`pd.concat([january, february, march], ignore_index=False, keys=['jan', 'feb', 'mar'])`: Ignore index should set to False if you want to add keys. Key values help to distinguish between tables before concatination. 

`pd.concat([table1, table2], join='inner')`: Concats two tables but includes only columns which appear in both. 

`.append()`: Simplified version of the concat method. Supports ignore_index and sort. Does not support keys and join. (join always outer)





