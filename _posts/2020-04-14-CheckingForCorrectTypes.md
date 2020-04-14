# Title

Here's some raw text.

And here's some more text.


```python
import pandas as pd 

df = pd.read_csv('customer_data_replacedMissingValuesCityConsitencyChecked.csv')

```


```python
bad_characters = ['?','_','%','\\', '^', '$', '&']

cnt = 0
for x in df['category']:
    for bad_character in bad_characters:
        x = x.replace(bad_character, '')
    df.loc[cnt, 'category'] = x
    cnt+=1
```


```python
incomplete_words = {'house': 'household', 'elec': 'electronics', 'electronic': 'electronics'}

cnt = 0

for word in df['category']:
    if word in incomplete_words:
        df.loc[cnt, 'category'] = incomplete_words[word]
    cnt+=1
```


```python
b_words = {'lawn_mower': 'lawnmower', 'cell_phone': 'cell phone', 'lawn mower': 'lawnmower', 'cell': 'cell phone'}

cnt = 0
for w in df['purchase']:
    if w in b_words:
        df.loc[cnt, 'purchase'] = b_words[w]
    cnt+=1
```


```python
p_words = {'t shirt': 't-shirts', 'teeshirts': 't-shirts', 'T': 't-shirts', 't_shirts': 't-shirts', 't-shirt': 't-shirts', 'dvd_player': 'dvd player'}

cnt = 0

for p in df['frequently_bought_together']:
    if p in p_words:
        df.loc[cnt, 'frequently_bought_together'] = p_words[p]
    cnt+=1
```


```python

b_characters = ['?','%','/', '^', '$', '&', '#']

cnt = 0

for word in df['frequently_bought_together']:
    for char in b_characters:
        word = word.replace(char,'')
        df.loc[cnt, 'frequently_bought_together'] = word
    cnt+=1
```


```python
cnt = 0

messy_data = {}

for r in df['amount']:
    try:
        float(r)
        pass
    except ValueError:
        messy_data[cnt] = r
    cnt+=1
```


```python
m_characters = ['_', '$', ' ']

for mon in messy_data:
    for m in m_characters:
        if m in messy_data[mon]:
            messy_data[mon] = messy_data[mon].replace(m,'')
```


```python
for mon in messy_data:
    df.loc[mon, 'amount'] = messy_data[mon]
```


```python
df.to_csv('customer_data_MissingValuesConsitencyAndCorrectTypeChecked.csv')

```
