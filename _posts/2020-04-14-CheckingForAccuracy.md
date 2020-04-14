---
title: "Data Wrangling Project"
date: 2020-04-13
tags: [data wrangling, data science, messy data]
header:
  image: "/images/perceptron/percept.jpg"
excerpt: "Data Wrangling, Data Science, Messy Data"
mathjax: "true"
---

# Title

Here's some raw text.

And here's some more text.


```python
import pandas as pd

df = pd.read_csv('customer_data_MissingValuesConsitencyCorrectTypeChecked.csv', dtype ={'zip_code': object})

df_accurate = pd.read_csv('AccurateLocationData.csv', dtype = {'Zipcode': object})


ZipCodes = df_accurate.drop_duplicates('Latitude_Longitude').set_index('Latitude_Longitude')['Zipcode']

df['zip_code'] = df['lat_lon'].map(ZipCodes)

df = df.drop(['Unnamed: 0'], axis =1)


df.to_csv('customer_data_MissingValuesConsitencyAndCorrectTypeAccuracyChecked.csv')

```
