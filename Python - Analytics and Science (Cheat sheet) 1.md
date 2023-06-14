https://elitedatascience.com/python-cheat-sheet

# Importing Data

pd.read_csv(filename) # From a CSV file
pd.read_table(filename) # From a delimited text file (like TSV)
pd.read_excel(filename) # From an Excel file
pd.read_sql(query, connection_object) # Reads from a SQL table/database
pd.read_json(json_string) # Reads from a JSON formatted string, URL or file.
pd.read_html(url) # Parses an html URL, string or file and extracts tables to a list of dataframes
pd.read_clipboard() # Takes the contents of your clipboard and passes it to read_table()
pd.DataFrame(dict) # From a dict, keys for columns names, values for data as lists

-----------------------------------------------------------------------------------

# Exploring Data
  
1. **df.shape()** # Prints number of rows and columns in dataframe 
2. **df.head(n)** # Prints first n rows of the DataFrame
3. **df.tail(n)** # Prints last n rows of the DataFrame 
4. **df.info**() # Index, Datatype and Memory information 
5. **df.describe**() # Summary statistics for numerical columns 
6. **s.value_counts(dropna=False)** # Views unique values and counts 
7. **df.apply(pd.Series.value_counts)** # Unique values and counts for all columns 
8. **df.describe()** # Summary statistics for numerical columns 
9. **df.mean()** # Returns the mean of all columns 
10. **df.corr()** # Returns the correlation between columns in a DataFrame 
11. **df.count()** # Returns the number of non-null values in each DataFrame columns 
12. **df.max()** # Returns the highest value in each columns 
13. **df.min()** # Returns the lowest value in each columns 
14. **df.median()** # Returns the median of each column 
15. **df.std()** # Returns the standard deviation of each column|
--------------------------------------------------------------------------------------------

# Selection

1. **df[col]** # Returns column with label col as Series 
2. **df[  col1, col2 ]**  # Returns Columns as a new DataFrame 
3. **s.iloc[0]** # Selection by position (selects first element) 
4. **s.loc[0]** # Selection by index (selects element at index 0)
5. **df.loc[column name >= condition]** # First  - label based data selecting method
	ex : df.loc[df['genre'] == 'Action']
6. **df.iloc[0,0]** # First element of first column  - index based data selecting method
	ex: df.iloc[[1,2,3,] ]
	ex: df.iloc[1:][df['genre'] == 'Action ']
--------------------------------------------------------------------------------------

# Data cleaning
Contains Renaming ,checking for null values, dropping null values, filling null values, conversion of datatypes, setting index.

#Null_values
1. **pd.isnull()** # Checks for null Values, Returns Boolean Array
2. **pd.notnull()** # Opposite of s.isnull()
3. **df.dropna()** # Drops all rows that contain null values
4. **df.dropna(axis=1)** # Drops all columns that contain null values
5. **df.dropna(axis=1,thresh=n)** # Drops all rows have have less than n non null values
6. **df.fillna(x)** # Replaces all null values with x
7. **s.fillna(s.mean())** # Replaces all null values with the mean (mean can be replaced with almost any function from the statistics section)
#datatype_conversiom
8. **s.astype(float)** # Converts the datatype of the series to float
#renaming
9. **df.columns** = ['a','b','c'] # Renames columns
10. **df.rename(columns=lambda x: x + 1)** # Mass renaming of columns
11. **df.rename(columns={'old_name': 'new_ name'})** # Selective renaming
12. **df.rename(index=lambda x: x + 1)** # Mass renaming of index 
#replace
13. **s.replace(1,'one')** # Replaces all values equal to 1 with 'one'
14. **s.replace([1,3],['one','three'])** # Replaces all 1 with 'one' and 3 with 'three'
#setting_index
15. **df.set_index('column_one')** # Changes the index
----------------------------------------------------------------------------------------

# Filter, Sort and Grouping

#Filter
1. **df[df[col] > 0.5]** # Rows where the col column is greater than 0.5
2. **df[(df[col] > 0.5) & (df[col] < 0.7)]** # Rows where 0.5 < col < 0.7
#Sort
3. **df.sort_values(col1)** # Sorts values by col1 in ascending order
4. **df.sort_values(col2,ascending=False)** # Sorts values by col2 in descending order
5. **df.sort_values([col1,col2], ascending=[True,False])** # Sorts values by col1 in ascending order then col2 in descending order
#Group-by
6. **df.groupby(col)** # Returns a groupby object for values from one column
7. **df.groupby([col1,col2])** # Returns a groupby object values from multiple columns
8. **df.groupby(col1)[col2].mean()** # Returns the mean of the values in col2, grouped by the values in col1 (mean can be replaced with almost any function from the statistics section)
9. **df.pivot_table(index=col1, values= col2,col3], aggfunc=mean)** # Creates a pivot table that groups by col1 and calculates the mean of col2 and col3
10. **df.groupby(col1).agg(np.mean)** # Finds the average across all columns for every unique column 1 group
#Applying
11. **df.apply(np.mean)** # Applies a function across each column
12. **df.apply(np.max, axis=1)** # Applies a function across each row