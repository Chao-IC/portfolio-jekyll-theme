---
layout: post
title: "Example Project"
---
```python
import pandas as pd
```


```python
sales = pd.read_csv('Auto_Sales_data.csv', index_col = 0)
```


```python
sales_modified = sales.drop(['ORDERLINENUMBER','CUSTOMERNAME','PHONE','ADDRESSLINE1','POSTALCODE','CONTACTLASTNAME','CONTACTFIRSTNAME'], axis=1)
```


```python
sales_modified.head()
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
      <th>QUANTITYORDERED</th>
      <th>PRICEEACH</th>
      <th>SALES</th>
      <th>ORDERDATE</th>
      <th>DAYS_SINCE_LASTORDER</th>
      <th>STATUS</th>
      <th>PRODUCTLINE</th>
      <th>MSRP</th>
      <th>PRODUCTCODE</th>
      <th>CITY</th>
      <th>COUNTRY</th>
      <th>DEALSIZE</th>
    </tr>
    <tr>
      <th>ORDERNUMBER</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10107</th>
      <td>30</td>
      <td>95.70</td>
      <td>2871.00</td>
      <td>24/02/2018</td>
      <td>828</td>
      <td>Shipped</td>
      <td>Motorcycles</td>
      <td>95</td>
      <td>S10_1678</td>
      <td>NYC</td>
      <td>USA</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>10121</th>
      <td>34</td>
      <td>81.35</td>
      <td>2765.90</td>
      <td>07/05/2018</td>
      <td>757</td>
      <td>Shipped</td>
      <td>Motorcycles</td>
      <td>95</td>
      <td>S10_1678</td>
      <td>Reims</td>
      <td>France</td>
      <td>Small</td>
    </tr>
    <tr>
      <th>10134</th>
      <td>41</td>
      <td>94.74</td>
      <td>3884.34</td>
      <td>01/07/2018</td>
      <td>703</td>
      <td>Shipped</td>
      <td>Motorcycles</td>
      <td>95</td>
      <td>S10_1678</td>
      <td>Paris</td>
      <td>France</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>10145</th>
      <td>45</td>
      <td>83.26</td>
      <td>3746.70</td>
      <td>25/08/2018</td>
      <td>649</td>
      <td>Shipped</td>
      <td>Motorcycles</td>
      <td>95</td>
      <td>S10_1678</td>
      <td>Pasadena</td>
      <td>USA</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>10168</th>
      <td>36</td>
      <td>96.66</td>
      <td>3479.76</td>
      <td>28/10/2018</td>
      <td>586</td>
      <td>Shipped</td>
      <td>Motorcycles</td>
      <td>95</td>
      <td>S10_1678</td>
      <td>Burlingame</td>
      <td>USA</td>
      <td>Medium</td>
    </tr>
  </tbody>
</table>
</div>




```python
print(sales_modified.notnull().sum())
```

    QUANTITYORDERED         2747
    PRICEEACH               2747
    SALES                   2747
    ORDERDATE               2747
    DAYS_SINCE_LASTORDER    2747
    STATUS                  2747
    PRODUCTLINE             2747
    MSRP                    2747
    PRODUCTCODE             2747
    CITY                    2747
    COUNTRY                 2747
    DEALSIZE                2747
    dtype: int64



```python
print(sales_modified.columns.tolist())
```

    ['QUANTITYORDERED', 'PRICEEACH', 'SALES', 'ORDERDATE', 'DAYS_SINCE_LASTORDER', 'STATUS', 'PRODUCTLINE', 'MSRP', 'PRODUCTCODE', 'CITY', 'COUNTRY', 'DEALSIZE']



```python
indicater = pd.read_csv('e22f2293-f590-46c3-91df-5eea2aeed022_Data.csv', index_col = 0)
```


```python
indicater.head()
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
      <th>Country Code</th>
      <th>Series Name</th>
      <th>Series Code</th>
      <th>2018 [YR2018]</th>
      <th>2019 [YR2019]</th>
      <th>2020 [YR2020]</th>
    </tr>
    <tr>
      <th>Country Name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan</th>
      <td>AFG</td>
      <td>Access to clean fuels and technologies for coo...</td>
      <td>EG.CFT.ACCS.ZS</td>
      <td>31.4</td>
      <td>32.6</td>
      <td>33.8</td>
    </tr>
    <tr>
      <th>Afghanistan</th>
      <td>AFG</td>
      <td>Access to clean fuels and technologies for coo...</td>
      <td>EG.CFT.ACCS.RU.ZS</td>
      <td>14.5</td>
      <td>15.6</td>
      <td>16.4</td>
    </tr>
    <tr>
      <th>Afghanistan</th>
      <td>AFG</td>
      <td>Access to clean fuels and technologies for coo...</td>
      <td>EG.CFT.ACCS.UR.ZS</td>
      <td>82.6</td>
      <td>83.2</td>
      <td>83.8</td>
    </tr>
    <tr>
      <th>Afghanistan</th>
      <td>AFG</td>
      <td>Access to electricity (% of population)</td>
      <td>EG.ELC.ACCS.ZS</td>
      <td>93.4</td>
      <td>97.7</td>
      <td>97.7</td>
    </tr>
    <tr>
      <th>Afghanistan</th>
      <td>AFG</td>
      <td>Access to electricity, rural (% of rural popul...</td>
      <td>EG.ELC.ACCS.RU.ZS</td>
      <td>91.6</td>
      <td>97.1</td>
      <td>97.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
indicater.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Index: 401399 entries, Afghanistan to Last Updated: 04/15/2025
    Data columns (total 6 columns):
     #   Column         Non-Null Count   Dtype 
    ---  ------         --------------   ----- 
     0   Country Code   401394 non-null  object
     1   Series Name    401394 non-null  object
     2   Series Code    401394 non-null  object
     3   2018 [YR2018]  401394 non-null  object
     4   2019 [YR2019]  401394 non-null  object
     5   2020 [YR2020]  401394 non-null  object
    dtypes: object(6)
    memory usage: 21.4+ MB



```python
print(indicater.columns.tolist())
```

    ['Country Code', 'Series Name', 'Series Code', '2018 [YR2018]', '2019 [YR2019]', '2020 [YR2020]']



```python

```
