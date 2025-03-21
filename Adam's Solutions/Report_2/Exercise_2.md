# Exercise 2. - Filtering and Sorting Data

Check out [Euro 12 Exercises Video Tutorial](https://youtu.be/iqk5d48Qisg) to watch a data scientist go through the exercises

This time we are going to pull data directly from the internet.

### Step 1. Import the necessary libraries


```python
import pandas as pd
```

### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/kflisikowsky/pandas_exercises/refs/heads/main/Euro_2012_stats_TEAM.csv). 

### Step 3. Assign it to a variable called euro12.


```python
url = 'https://raw.githubusercontent.com/kflisikowsky/pandas_exercises/refs/heads/main/Euro_2012_stats_TEAM.csv'
euro12 = pd.read_csv(url, sep=',')
```

### Step 4. Select only the Goal column.


```python
euro12['Goals']
```

### Step 5. How many team participated in the Euro2012?


```python
euro12['Team'].nunique()

```

### Step 6. What is the number of columns in the dataset?


```python
euro12.shape[1]
```

### Step 7. View only the columns Team, Yellow Cards and Red Cards and assign them to a dataframe called discipline


```python
discipline = euro12[['Team','Yellow Cards', 'Red Cards']]
discipline

```

### Step 8. Sort the teams by Red Cards, then to Yellow Cards


```python
discipline.sort_values(by=['Red Cards', 'Yellow Cards'], ascending=False)
```

### Step 9. Calculate the mean Yellow Cards given per Team


```python
discipline['Yellow Cards'].mean()
```

### Step 10. Filter teams that scored more than 6 goals


```python
euro12[euro12['Goals']>6]
```

### Step 11. Select the teams that start with G


```python
euro12[euro12['Team'].str.startswith('G')]
```

### Step 12. Select the first 7 columns


```python
euro12.iloc[:, :7]
```

### Step 13. Select all columns except the last 3.


```python
euro12.iloc[:, :-3]
```

### Step 14. Present only the Shooting Accuracy from England, Italy and Russia


```python
euro12[euro12['Team'].isin(['England', 'Italy', 'Russia'])][['Team', 'Shooting Accuracy']]
```
