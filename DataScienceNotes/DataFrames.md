## DataFrameMethods

`df.info()`: Displays the names of columns, the data types they contain and whether they have any missing values.

`df.describe()`: Some summary statistics for numerical columns. 

`df.drop_duplicates(subset='col1')`: Drops non-unique rows from the column col1. subset also could be list of columns like `subset=['col1', 'col2']`

`df['col1'].value_counts(sort=True)`: Counts number of same values then sorts them in descending order. (with normalize=True proportions can be achieved) 

## DataFrameAttributes

`df.shape`: Returns a tuple that contains number of rows and columns. 

`df.values`: Data values in a 2-dimensional numpy array.

`df.columns`: Column names. 

`df.index`: Row numbers or row names. 

## Sorting and subsetting

`df.sort_values('col_name')`: Change the order of the rows by sorting them according to column values. 

`df.sort_values(['col1', 'col2'])`: Sorting by muliple variables. First sorting by col1 then by col2. 

`df.sort_values(['col1', 'col2'], ascending=[True, True])`: Changing direction of sorting. 

`df[['col1', 'col2']]`: Getting only col1 and col2 values. 

`df[df['col_name'] > 10]`: Subsetting rows based on one condition.

`df[(df['col1'] > 10) & (df['col2'] == 'example')]`: Subsetting rows based on multiple conditions.

`df[df['col_name'].isin(['Blue', 'Red'])]`: Subsetting using isin()

## Cumulative Statistics

With agg method we can see cumulative statistics for one or more columns. In code block below iqr method is defined and passed to agg method. 

```
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)

print(df[["col1", "col2", "col3"]].agg([iqr, np.median]))
```
