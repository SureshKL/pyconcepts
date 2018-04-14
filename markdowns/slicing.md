
# Slicing
------------------

Square bracket notation
\[StartIndex : EndIndex : Stride]
- **StartIndex** : Value at StartIndex position is "*included*"
- **EndIndex**   : Value at EndIndex position is "*not included*"

Default the elements are considered from Left => Right

| 0  | 1  | 2  | 3  | 4  | 5  |
|----|----|----|----|----|----|
| P  | Y  | T  | H  | O  | N  |
| -6 | -5 | -4 | -3 | -2 | -1 |

> When StartIndex is not specified, default consume from first element

> When EndIndex is not specified, default consume till last element


```python
name = 'PYTHON'
print(name)
```

    PYTHON


### Get all elements


```python
print(name[:])   # Without StartIndex & EndIndex
print(name[::])  # Without StartIndex, EndIndex & Stride
print(name[0:])  # Include StartIndex value, since EndIndex is not given default considers even the last element
```

    PYTHON
    PYTHON
    PYTHON


### Get first two elements


```python
print(f'{name} -> , {name[0:2]}')
```

    PYTHON -> , PY


### Get last element


```python
print(f'{name} -> {name[-1]}')
```

    PYTHON -> N


## Slicing with Stride in place
----------------------------------------

### Get elements in even position


```python
print(f'{name} -> {name[::2]}')  # Stride is 2, get elements incrementing index by 2 
```

    PYTHON -> PTO


### Reverse the string


```python
print(f'{name} -> {name[::-1]}')  # - Elements are retrieved from R to L, since Stride is negative
```

    PYTHON -> NOHTYP



```python
print(f'{name} -> {name[3:0:-1]}' )  # StartIndex should be higher than EndIndex when Stride is negative
```

    PYTHON -> HTY


### Get last 3 elements


```python
name[-3: ]
```




    'HON'


