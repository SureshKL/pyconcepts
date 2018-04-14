
# List Operations



## Split the list into given no. of chunks

**Note:** Extra values in list are ignored

### List of values to be split


```python
print(*range(1, 13))
```

    1 2 3 4 5 6 7 8 9 10 11 12



```python
def chunkify(seq, size):
    """Return list of chunks """
    start = 0
    end = size
    chunks = []
    for _ in range(len(seq) // size):
        chunks.append(seq[start:end])
        start = end
        end = end + size
    return chunks

for chunk in chunkify(range(1, 13), 4):
    print(*chunk)
```

    1 2 3 4
    5 6 7 8
    9 10 11 12


## Combining multiple lists into one


```python
list1 = [1, 2, 3]
list2 = [1, 2, 3]
list3 = [1, 2, 3]

print(list1 + list2 + list3)  # Creates a new refrence for list
```

    [1, 2, 3, 1, 2, 3, 1, 2, 3]


## Find difference between two lists by occurrence of item in list


```python
fruits = ['Apple', 'Apple', 'Apple', 'Mango', 'Mango', 'Grapes', 'Banana', 'Banana']
sold = ['Apple', 'Banana', 'Banana']

from collections import Counter

f = Counter(fruits)
s = Counter(sold)

print(f'Fruits in total : {f}')
print(f'Fruits sold out : {s}')
print(f'Fruits In-Stock : {f-s}')

```

    Fruits in total : Counter({'Apple': 3, 'Mango': 2, 'Banana': 2, 'Grapes': 1})
    Fruits sold out : Counter({'Banana': 2, 'Apple': 1})
    Fruits In-Stock : Counter({'Apple': 2, 'Mango': 2, 'Grapes': 1})


## Find difference between two lists by value

zip() function stops for the shortest list. Therefore using the zip_longest() from itertools we can get the additonal values from the longest list.


```python
import itertools

list1 = [1, 2, 3]
list2 = [4, 5, 6, 9, 10]

for i, j in itertools.zip_longest(list1, list2):
    if isinstance(i, int) and isinstance(j, int):
        print(j-i)
        continue
    value = i if i else j
    print(value)

```

    3
    3
    3
    9
    10

