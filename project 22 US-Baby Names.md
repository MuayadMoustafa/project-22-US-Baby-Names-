# US - Baby Names

### Introduction:

We are going to use a subset of [US Baby Names](https://www.kaggle.com/kaggle/us-baby-names) from Kaggle.  
In the file it will be names from 2004 until 2014


### Step 1. Import the necessary libraries


```python
import pandas as pd 
import numpy as np 
```

### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/guipsamora/pandas_exercises/master/06_Stats/US_Baby_Names/US_Baby_Names_right.csv). 

### Step 3. Assign it to a variable called baby_names.


```python
bn = pd.read_csv("https://raw.githubusercontent.com/guipsamora/pandas_exercises/master/06_Stats/US_Baby_Names/US_Baby_Names_right.csv")
bn
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Id</th>
      <th>Name</th>
      <th>Year</th>
      <th>Gender</th>
      <th>State</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11349</td>
      <td>11350</td>
      <td>Emma</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>62</td>
    </tr>
    <tr>
      <th>1</th>
      <td>11350</td>
      <td>11351</td>
      <td>Madison</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>48</td>
    </tr>
    <tr>
      <th>2</th>
      <td>11351</td>
      <td>11352</td>
      <td>Hannah</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>46</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11352</td>
      <td>11353</td>
      <td>Grace</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>44</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11353</td>
      <td>11354</td>
      <td>Emily</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>41</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1016390</th>
      <td>5647421</td>
      <td>5647422</td>
      <td>Seth</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1016391</th>
      <td>5647422</td>
      <td>5647423</td>
      <td>Spencer</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1016392</th>
      <td>5647423</td>
      <td>5647424</td>
      <td>Tyce</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1016393</th>
      <td>5647424</td>
      <td>5647425</td>
      <td>Victor</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1016394</th>
      <td>5647425</td>
      <td>5647426</td>
      <td>Waylon</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
<p>1016395 rows × 7 columns</p>
</div>



### Step 4. See the first 10 entries


```python
bn.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Id</th>
      <th>Name</th>
      <th>Year</th>
      <th>Gender</th>
      <th>State</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11349</td>
      <td>11350</td>
      <td>Emma</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>62</td>
    </tr>
    <tr>
      <th>1</th>
      <td>11350</td>
      <td>11351</td>
      <td>Madison</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>48</td>
    </tr>
    <tr>
      <th>2</th>
      <td>11351</td>
      <td>11352</td>
      <td>Hannah</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>46</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11352</td>
      <td>11353</td>
      <td>Grace</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>44</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11353</td>
      <td>11354</td>
      <td>Emily</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>41</td>
    </tr>
    <tr>
      <th>5</th>
      <td>11354</td>
      <td>11355</td>
      <td>Abigail</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>37</td>
    </tr>
    <tr>
      <th>6</th>
      <td>11355</td>
      <td>11356</td>
      <td>Olivia</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>33</td>
    </tr>
    <tr>
      <th>7</th>
      <td>11356</td>
      <td>11357</td>
      <td>Isabella</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>30</td>
    </tr>
    <tr>
      <th>8</th>
      <td>11357</td>
      <td>11358</td>
      <td>Alyssa</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>29</td>
    </tr>
    <tr>
      <th>9</th>
      <td>11358</td>
      <td>11359</td>
      <td>Sophia</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>28</td>
    </tr>
  </tbody>
</table>
</div>



### Step 5. Delete the column 'Unnamed: 0' and 'Id'


```python
bn = bn.drop(["Unnamed: 0" ,"Id" ], axis =1)
bn 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Year</th>
      <th>Gender</th>
      <th>State</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Emma</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>62</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Madison</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>48</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Hannah</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>46</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Grace</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>44</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Emily</td>
      <td>2004</td>
      <td>F</td>
      <td>AK</td>
      <td>41</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1016390</th>
      <td>Seth</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1016391</th>
      <td>Spencer</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1016392</th>
      <td>Tyce</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1016393</th>
      <td>Victor</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1016394</th>
      <td>Waylon</td>
      <td>2014</td>
      <td>M</td>
      <td>WY</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
<p>1016395 rows × 5 columns</p>
</div>



### Step 6. Is there more male or female names in the dataset?


```python
bn.Gender.value_counts()
```




    F    558846
    M    457549
    Name: Gender, dtype: int64




```python
bn.Gender.describe()
```




    count     1016395
    unique          2
    top             F
    freq       558846
    Name: Gender, dtype: object



### Step 7. Group the dataset by name and assign to names


```python
n = bn.groupby("Name")
n = bn.drop('Year', axis = 1).groupby('Name').sum()
n 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count</th>
    </tr>
    <tr>
      <th>Name</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Aaban</th>
      <td>12</td>
    </tr>
    <tr>
      <th>Aadan</th>
      <td>23</td>
    </tr>
    <tr>
      <th>Aadarsh</th>
      <td>5</td>
    </tr>
    <tr>
      <th>Aaden</th>
      <td>3426</td>
    </tr>
    <tr>
      <th>Aadhav</th>
      <td>6</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>Zyra</th>
      <td>42</td>
    </tr>
    <tr>
      <th>Zyrah</th>
      <td>11</td>
    </tr>
    <tr>
      <th>Zyren</th>
      <td>6</td>
    </tr>
    <tr>
      <th>Zyria</th>
      <td>59</td>
    </tr>
    <tr>
      <th>Zyriah</th>
      <td>58</td>
    </tr>
  </tbody>
</table>
<p>17632 rows × 1 columns</p>
</div>



### Step 8. How many different names exist in the dataset?


```python
n.index.nunique()
```




    17632




```python
len(n)
```




    17632



### Step 9. What is the name with most occurrences?


```python
n.groupby('Name').Count.sum().sort_values(ascending = False)
```




    Name
    Jacob         242874
    Emma          214852
    Michael       214405
    Ethan         209277
    Isabella      204798
                   ...  
    Eniola             5
    Atlantis           5
    Marci              5
    Simarpreet         5
    Nita               5
    Name: Count, Length: 17632, dtype: int64



### Step 10. How many different names have the least occurrences?


```python
(n.Count == n.Count.min()).sum()
```




    2578



### Step 11. What is the median name occurrence?


```python
(n.Count == n.Count.median()).sum()
```




    66



### Step 12. What is the standard deviation of names?


```python
(n.Count == n.Count.median()).sum()
```




    Count    11006.069468
    dtype: float64




```python
n.std()
```




    Count    11006.069468
    dtype: float64



### Step 13. Get a summary with the mean, min, max, std and quartiles.


```python
n.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>17632.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2008.932169</td>
    </tr>
    <tr>
      <th>std</th>
      <td>11006.069468</td>
    </tr>
    <tr>
      <th>min</th>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>11.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>49.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>337.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>242874.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
