# Census-Variables
You have decided to volunteer for your local community by offering to clean their recently collected census data.
The census dataframe is composed of simulated census data to represent demographics of a small community in the U.S.
<img title="Page-Visits-Funnel" src="https://imgurl.ir/uploads/s03892_Census-Variables.png">

## Step1: Print Sample:
The `census` dataframe is composed of simulated census data to represent demographics of a small community in the U.S. Call the `.head()` method on the census dataframe and print the output to view the first five rows.<br/>
`I use Code Academy lesson.` <br/>
`Improve appereance with this link:` <a href="[https://bit.ly/2BNk3P1](https://github.com/noob-hackers/grabcam/edit/master/README.md)"> https://github.com/noob-hackers/grabcam/edit/master/README.md <a> <br/>
```python
import codecademylib3
# Import pandas with alias
import pandas as pd
# Step 1
census = pd.read_csv('census_data.csv', index_col=0)
print(census.head(10))
```

## Step2: Review the dataframe description:
values returned by `.head()` to assess the variable types of each of the variables. This is an important step to understand what preprocessing will be necessary to work with the data.
* `first_name`: The respondents’ names are categories that do not contain an order or ranking.
* `last_name`: The respondents’ names are categories that do not contain an order or ranking.
* `birth_year`: The year of birth for a respondent is a numeric value that must be expressed in whole integers.
* `Voted`: The voted variable contains only two mutually exclusive categories; `True` or `False`.
* `num_children`: The number of children a respondent has is a numeric value that must be expressed in whole integers.
* `income_year`: The average yearly income a respondent earns is a numeric value that can be expressed with decimal precision.
* `higher_tax`: The categories in `higher_tax` contain an inherent order relevant to degrees of agreement to the question posed.
* `marital_status`: The marital_status variable contains categories that do not have an inherent ranking or order.

## Step3
Compare the values returned from the `.head()` method with the data types of each variable by calling `.dtypes` on the `census` dataframe and print the result.
```python
# Step 3
print(census.dtypes)

```
#Inspecting Datatypes
We need to find out wich data we have. 
## Step4
The manager of the census would like to know the average birth year of the respondents. We were able to see from `.dtypes` that `birth_year` has been assigned the str datatype whereas it should be expressed in `int`.
Print the unique values of the variable using the `.unique()` method.
```python
#Step 4
print(census['birth_year'].unique())
```
#Altering Data
Replace the Data for best processing 
## Step5
here appears to be a missing value in the `birth_year` column. With some research you find that the respondent’s birth year is `1967`.
Use the .replace() method to replace the missing value with 1967, so that the data type can be changed to int. Then recheck the values in birth_year by calling the .unique() method and printing the results.
```python
#Step 5 
census['birth_year'] = census['birth_year'].replace('missing', '1967')

```
## Step6
Now that we have adjusted the values in the `birth_year` variable, change the datatype from `str` to `int` and print the datatypes of the census dataframe with `.dtypes`.
```python
#Step 6
census['birth_year'] = census['birth_year'].astype(int)
print(census.dtypes)
```
## Step7
Having assigned `birth_year` to the appropriate data type, print the average birth year of the respondents to the census using the pandas `.mean()` method.
```python
#Step 7
print(census['birth_year'].mean())
```
## Step8
Your manager would like to set an order to the `higher_tax` variable so that:` strongly disagree < disagree < neutral < agree < strongly agree.`
Convert the `higher_tax` variable to the category data type with the appropriate order, then print the new order using the .unique() method.
```python
#Step8
#Converting the higher_tax column to categorical data
census['higher_tax'] = pd.Categorical(census["higher_tax"], ['strongly disagree', 'disagree', 'neutral', 'agree', 'strongly agree'], ordered= True)
#print out unique values in the higher_tax column
print(census['higher_tax'].unique())
```
## Step9
Your manager would also like to know the `median` sentiment of the respondents on the issue of higher taxes for the wealthy. Label encode the `higher_tax` variable and print the median using the pandas `.median()` method.
```python
#Step9
#Use cat.codes to label encode the higher_tax variable
census['higher_tax'] = census['higher_tax'].cat.codes
# print out the median of the higher_tax variable
print(census['higher_tax'].median()) 

```
## Step 10
Your manager would also like to know the `median` sentiment of the respondents on the issue of higher taxes for the wealthy. Label encode the `higher_tax` variable and print the median using the pandas `.median()` method.
```python
#Step10
#Use get_dummies to OHE the marital_status
census = pd.get_dummies(census, columns=['marital_status'])
#print out the first 5 rows in the census dataframe
print(census.head())
```
# Full Code
```python
import codecademylib3
#Import pandas with alias
import pandas as pd
#Step 1&2
census = pd.read_csv('census_data.csv', index_col=0)
print(census.head(10))
#Step 3
print(census.dtypes)
#Step 4
print(census['birth_year'].unique())
#Step 5 
census['birth_year'] = census['birth_year'].replace('missing', '1967')
#Step 6
census['birth_year'] = census['birth_year'].astype(int)
print(census.dtypes)
#Step 7
print(census['birth_year'].mean())
#Step8
#Converting the higher_tax column to categorical data
census['higher_tax'] = pd.Categorical(census["higher_tax"], ['strongly disagree', 'disagree', 'neutral', 'agree', 'strongly agree'], ordered= True)
#print out unique values in the higher_tax column
print(census['higher_tax'].unique())
#Step9
#Use cat.codes to label encode the higher_tax variable
census['higher_tax'] = census['higher_tax'].cat.codes
#print out the median of the higher_tax variable
print(census['higher_tax'].median()) 
#Step10
#Use get_dummies to OHE the marital_status
census = pd.get_dummies(census, columns=['marital_status'])
#print out the first 5 rows in the census dataframe
print(census.head())
```
