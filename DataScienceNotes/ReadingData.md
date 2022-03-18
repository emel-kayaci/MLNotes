# Reading Data in Python

Sometimes the size of the data can be so large that it is impossible to keep all of it in memory. In this case, we can read the data as chunks. If this data is in csv file format, we can use the code block below.

```
def read_data(csv_file, c_size, colname):

    # Iterate over the file chunk by chunk
    for chunk in pd.read_csv(csv_file, chunksize=c_size):

        # Iterate over the any column you want in DataFrame
        for entry in chunk[colname]:
```
