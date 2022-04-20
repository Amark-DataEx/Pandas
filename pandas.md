# PANDAS HANDBOOK
### We will learn everything about pandas here.
* Pandas is a Python library.
* Pandas are used to analyze large data sets.
* Pandas are used to analyze big data and make conclusions based on statistical theories.
* Pandas are used to clean messy data sets and make them relevant data.
__ __
There are two fundamental data structures.

* Series—Pandas Series are like columns in a table. They’re 1D arrays holding data of any type.
* Data Frame—Pandas DataFrames are like Tables. They’re 2D arrays holding data of any type, such as rows and columns.
## Series
``` python
#creating Series out of List.
import pandas as pd
a=[1,2,3,'amar',34.90]

mySeries=pd.Series(a)  # index(Axis lables) + data
print(mySeries)

# If no index is specified while creating Series then indexes 0 and 1 o is given default.

>>> 0    1
    1    7
    2    2
    dtype: int64
    
# to return any thing form Series
mySeries[0]
or
print(mySeries[0])
```
Creating Series and its labels out of Lists.
```python
import pandas as pd
a=[1,2,3,4]
labels=['egg','fry','noodules','double'] # Here length of index should be equal to number of values.

mySeries= pd.Series(a,index=labels)
print(mySeries)

>>> egg    1
fry        2
noodules   3
double     4
dtype: int64

# To access the data 
print(myseries['egg'])
>>> 1
```
Creating Series out of Dictionary(key/Value objects)
```python
import pandas as pd

a={"day1":200,"day2":300,"day3":400}

mySeries = pd.Series(a)  # Here the key of dictionaries become index of Series.
print(a) 
>>>
day1    200
day2    300
day3    400
dtype: int64

# we can also create Series using only few key: value pair.

mySeries= pd.Series(a,index=['day1','day2'])
print(mySeries)

>>> day1 200
day2 300
int64
```
## DataFrames
* These are like tables with rows and columns. These are 2D arrays.
* These are the most commonly used Pandas objects.
* To create these we need:  index(row labels) + data + column(column labels)

```python
# creating simple DataFrame using lists.
import pandas as pd

row1=[420,320]
row2=[320,440]
row3=[50,60]
data=[row1,row2,row3]
index=['day1','day2','day3']
column=['cal','dur']

myDataFrame = pd.DataFrame(index=index,data,columns=column)

# Creating simple DataFrame using key/value pair
import pandas as pd

data={'cal':[200,300,400],'dur':[300,400,500]} # keys become column names.
index=['day1','day2','day3']
myD = pd.DataFrame(data,index=index)
print(myD)


# We can also turn Series into DataFrame.(example if we have two Series named 'mySeries')
myD=pd.DataFrame({'first':mySeries,'second':mySeries*3})
print(myD)
>>>
```
Use the named index in the loc attribute to return the specified row(s)
```python
print(myD.loc['day2'])
>>>cal    320
  dur     440
  Name: day2, dtype: int64
```
## Importing Data - Loading Data
Importing data from external sources is the first step in data analysis.

Pandas allow us to load external files like CSV, Excel, SQL, and many more.

1. Reading CSV file.
```python
# Reading CSV files
import pandas as pd

hero_powers=pd.read_csv('file_name.csv') #or
hero_powers=pd.read_csv('D:\\dataengi\\super_powers')

# we can also use
# hero_powers = pd.read_csv('file_name',sep=';',usecols=['col1',col2],norows=10,compression='zip')

```
2. Reading Excel Files.
```python
# reading excel file(xlsx)
import pandas as pd

hero_dc = pd.read_excel('file_name.xlsx',sheet_name='Dc Comics')
hero_marvel = pd.read_excel('file_name.xlsx',sheet_name='Marvel Comics')
```

## Previewing the Data
After loading the CSV and Excel files we can view them using the below methods.
1. Just using print( variable_name)
```python
import pandas as pd

print(hero_powers) ##This will print first 5 rows and last 5 rows of DataFrame.
# this happens when the DataFrame exceeds 'max_rows'
# we can find this max_rows by looking at 'pd.options.display.max_rows'
# we can also change this setting.
```
2. using print(variable_name.to_string())
```python
# this will display entiry DataFrame
print(hero_powers.to_string())
```
3. Analyzing data using methods in pandas - head()
```python
# we use some methods to get quick over view of DataFrame
import pandas as pd

df = pd.read_csv('file_name.csv')

print(df.head(10))
# here head(10) prints starting 10 rows of the DataFrame.if no number then staring 5 rows.
```
4. Tail()
```python
print(df.tail()) 
# prints last 5 rows of the DataFrame.
```
5. info of the DataFrame
```python
print(df.info())
# it prints the total information of DataFrame.

# Note: If a DataFrame have more then 100 columns the info() method won't  give total info
# so we force it to print total info by adding verbose= True
print(df.info(verbose=True))
```
### Here we use DataFrame attributes to print DataFrame values.
* These three are the main attributes of creating a DataFrame.
1. columns
```python
import pandas as pd

df = pd.read_csv ('file_name.csv')

print(df.columns) 
```
2. Shape
3. index
4. dtypes