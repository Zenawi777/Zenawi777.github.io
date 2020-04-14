---
title: "Data Wrangling Project"
date: 2020-04-12
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

df = pd.read_csv('customer_data_replacedMissingValues.csv')


```


```python
city_names = {'SD': 'San Diego', 'Chi': 'Chicago', 'Hou': 'Houston', 'LA': 'Los Angeles'}

cnt = 0

for city in df['city']:
    if city in city_names:
        df.loc[cnt, 'city'] = city_names[city]
    cnt +=1

```


```python
df.to_csv('customer_data_replacedMissingValuesCityConsitencyChecked.csv')

```
