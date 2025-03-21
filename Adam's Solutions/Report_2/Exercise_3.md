# Exercise 3. - GroupBy

### Introduction:

GroupBy can be summarized as Split-Apply-Combine.

Special thanks to: https://github.com/justmarkham for sharing the dataset and materials.

Check out this [Diagram](http://i.imgur.com/yjNkiwL.png)  

Check out [Alcohol Consumption Exercises Video Tutorial](https://youtu.be/az67CMdmS6s) to watch a data scientist go through the exercises


### Step 1. Import the necessary libraries


```python
import pandas as pd
```

### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/justmarkham/DAT8/master/data/drinks.csv). 

### Step 3. Assign it to a variable called drinks.


```python
url = 'https://raw.githubusercontent.com/justmarkham/DAT8/master/data/drinks.csv'
drinks = pd.read_csv(url, sep=',')
drinks
```

### Step 4. Which continent drinks more beer on average?


```python
avg_beer_consumed = drinks['beer_servings'].mean()
avg_beer_consumed_by_continent = drinks.groupby('continent')['beer_servings'].mean() 
avg_beer_consumed_by_continent[avg_beer_consumed_by_continent > avg_beer_consumed]
```

### Step 5. For each continent print the statistics for wine consumption.


```python
drinks.groupby('continent')['wine_servings'].describe() 
```

### Step 6. Print the mean alcohol consumption per continent for every column


```python
drinks.groupby('continent').mean(numeric_only=True)
```

### Step 7. Print the median alcohol consumption per continent for every column


```python
drinks.groupby('continent').median(numeric_only=True)
```

### Step 8. Print the mean, min and max values for spirit consumption.
#### This time output a DataFrame


```python
summary = pd.DataFrame({
    "Mean": [drinks["spirit_servings"].mean()],
    "Min": [drinks["spirit_servings"].min()],
    "Max": [drinks["spirit_servings"].max()]
}, index=["spirit_servings"])
summary
```
