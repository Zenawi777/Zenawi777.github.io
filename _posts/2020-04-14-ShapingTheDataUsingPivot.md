---
title: "Data Wrangling Project"
date: 2020-04-14
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

df = pd.read_csv('customer_data_MissingValuesConsitencyAndCorrectTypeAccuracyChecked.csv')

```


```python
import numpy as np
df1 = df.pivot_table(index = 'customer_id', columns = 'category', values = 'amount', aggfunc = np.sum)

```


```python
df1.to_csv('ReshapedCustomerData.csv')
```
