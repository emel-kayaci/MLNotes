## DataFrameMethods

`df.info()`: Displays the names of columns, the data types they contain and whether they have any missing values.

`df.describe()`: Some summary statistics for numerical columns. 

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
