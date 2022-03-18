# RegexCheatsheet

Regex Cheatsheet for Python 

### Regex Patterns

`\w+`: Matches word

`\d`: Matches digit (if d+ matches multiple digits)

`\s`: Matches space `\S`: Mathces **not** space 

`[a-z]`: Lowercase group

`|`: OR        `()`: Group        `[]`: Ranges

***Example:*** `(\d+|\w+)`: Match digits and words

`[A-Za-z]+`: Upper and lowercase English alphabet

`[0-9]`: Numbers from 0 to 9

`[A-Za-z\-\.]+`: Upper and lowercase English alphabet, - and .

`(a-z)`: a, - and z

`(\s+|,)`: Spaces or a comma

### Regex Functions (from re module)

`split`: Split a string on regex 

***Example:*** re.split('\s+', 'Split on spaces.') 

***Output:*** ['Split, 'on', 'spaces]

`findall`: Find all patterns in a string

`search`: Search for a pattern 

`match`: Mathces only first occurence of string


