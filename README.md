# Census-Variables
You have decided to volunteer for your local community by offering to clean their recently collected census data.
The census dataframe is composed of simulated census data to represent demographics of a small community in the U.S.
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

