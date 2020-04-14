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
import pandas as pd
import xml.etree.ElementTree as ET

tree = ET.parse('location_data.xml')
root = tree.getroot()

fieldTitle = ['City', 'Zipcode', 'Latitude_Longitude']

dfLocation = pd.DataFrame(columns = fieldTitle)

for x in root:
    record = x.attrib.get('record')
    City = x.find('City').text
    Zipcode = x.find('Zipcode').text
    Latitude_Longitude = x.find('Latitude_Longitude').text
    dfLocation = dfLocation.append(pd.Series([City,Zipcode,Latitude_Longitude],index = fieldTitle), ignore_index = True)

    
dfLocation.to_csv('AccurateLocationData.csv')

```
