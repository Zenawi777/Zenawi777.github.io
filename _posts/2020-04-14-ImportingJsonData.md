---
title: "Data Wrangling Project"
date: 2020-04-10
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
import json 
from pandas.io.json import json_normalize


with open('customer_data.json') as f_in:
    customer_data = json.load(f_in)


customer_data = json_normalize(customer_data)

customer_data.to_csv('customer_data_new.csv')

```
