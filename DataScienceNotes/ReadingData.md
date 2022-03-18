# Reading Data in Python

Sometimes the size of the data can be so large that it is impossible to keep all of it in memory. In this case, we can read the data as chunks. If this data is in csv file format, we can use the code block below.

```
def read_data(csv_file, c_size, colname):

    # Iterate over the file chunk by chunk
    for chunk in pd.read_csv(csv_file, chunksize=c_size):

        # Iterate over the any column you want in DataFrame
        for entry in chunk[colname]:
```
### Generators vs. List Comprehensions

Generators are useful when we want to go over very large list. Because they use lazy evaluation this means that evaluation of the expression is delayed until its value is needed. 
```
result = [num for num in range(10**100000000)]
```
The list below would first create the list then if we want to go over it we need additional for loops. but the number of elements in the list is so large that our computer or server cannot even create such a large list.

The generator version is below. To iterate over generators we can use for loops as well. 

```
result = (num for num in range(3))

print(next(result)) #0
print(next(result)) #1
..
```
### Generator functions

These are the functions that produce generator objects. Instead of using return to returning values these functions uses keyword yield.  

The difference between yield and return is that yield returns a value and pauses the execution while maintaining the internal states, whereas the return statement returns a value and terminates the execution of the function.
