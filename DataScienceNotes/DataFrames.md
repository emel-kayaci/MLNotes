## General DataFrame Methods

`df.info()`: Displays the names of columns, the data types they contain and whether they have any missing values.

`df.describe()`: Some summary statistics for numerical columns. 

`df.drop_duplicates(subset='col1')`: Drops non-unique rows from the column col1. subset also could be list of columns like `subset=['col1', 'col2']`

`df.set_index('col1')`: Changes the index from default 0, 1, 2, .. to col1 values. To undo the change use `df.reset_index()`, if you want to reset and get rid of col1 then you can `df.reset_index(drop=True)`

`df.set_index(['col1', 'col2'])`: Multi-level (hierarchical) indexes. They are useful when we have hierarchical columns like country, city, etc.

`df.loc[('col1_value1', 'col2_value1'), ('col1_value2', 'col2_value2')]`: Subset inner levels with a list of tuples. 

## General DataFrame Attributes

`df.shape`: Returns a tuple that contains number of rows and columns. 

`df.values`: Data values in a 2-dimensional numpy array.

`df.columns`: Column names. 

`df.index`: Row numbers or row names. 

## Sorting and Subsetting

`df.sort_values('col_name')`: Change the order of the rows by sorting them according to column values. 

`df.sort_values(['col1', 'col2'])`: Sorting by muliple variables. First sorting by col1 then by col2. 

`df.sort_values(['col1', 'col2'], ascending=[True, True])`: Changing direction of sorting. 

`df.sort_index()`: Sorts by index.

`df[['col1', 'col2']]`: Getting only col1 and col2 values. 

`df[df['col_name'] > 10]`: Subsetting rows based on one condition.

`df[(df['col1'] > 10) & (df['col2'] == 'example')]`: Subsetting rows based on multiple conditions.

`df[df['col_name'].isin(['Blue', 'Red'])]`: Subsetting using isin(), getting rows which contain Blue and Red values in column col_name.

`df.loc[['Blue', 'Red']]`: Same output as above but shorter and common way.

### Slicing and subsetting with loc and iloc

**Important**: You can only slice an index if the index is sorted. 

`df.loc['starting_val':'ending_val']`: Gets rows from starting_val to ending_val including both values. (if these values are in index column)

`df.loc[:, 'starting_col':'ending_col']`: Gets all rows but columns that are starting with starting_col, ending with ending_col. 

`df.iloc[1:2, 3:6]`: Slicing with row and column numbers. Last indexes (2 and 6) are not included.

## Cumulative Statistics

With agg method we can see cumulative statistics for one or more columns. In code block below iqr method is defined and passed to agg method. 

```
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)

print(df[["col1", "col2", "col3"]].agg([iqr, np.median]))
```
## Summary Statistics

`df['col1'].value_counts(sort=True)`: Counts number of same values then sorts them in descending order. (with `normalize=True` proportions can be achieved) 

### Summaries by group

```
df[df['color'] == 'Black']['price'].mean()
df[df['color'] == 'Red']['price'].mean()
...
```
We know that we find the average of the prices according to the colors in the code snippet given above, but when we have too much color data, using such a structure causes code duplication.

`df.groupby('color')['price'].mean()`: With the group by method, we can reduce this to a single line. 

`df.groupby(['color', 'type'])['price'].mean()`: By giving list instead of just one column in group by we can also group by multiple columns. 

`df.groupby(['color', 'type'])['price', 'revenue'].mean()`: You can also aggregate by multiple columns. 

`df.groupby('color')['price'].agg([min, max, sum])`: We can use the agg method to get multiple statistics. 

### Pivot tables

Second method for groupby is to use pivot tables. 

`df.pivot_table(values='price', index='color')` and `df.groupby('color')['price'].mean()` is gives us the same result. 

In pivot tables we did not specify the statistics because default one is `mean`. But if we want to display another statistics we can do it like `df.pivot_table(values='price', index='color', aggfunc=np.median)` this. If we want multiple summary statistics we can pass a list of functions to the aggfunc argument. 

`df.pivot_table(values='price', index='color', columns='type'`: In group by we could also group by multiple columns. In pivot tables we can also achieve same result like this. The difference that pivot table would also include NaN values. Instead of NaN's with `fill_value=0` we can replace this values with 0's. With `margins=True` last column would include mean values for each row (not including NaN values). 

`df.mean(axis='index')` or `df.mean()`: Calculates mean for each column. 

`df.mean(axis='columns')`: Calculates mean for each row. 


