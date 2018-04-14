
# Patterns


```python
n = 5  # The size of the shape (technically - it is the no. of rows)
char = '*'  # The character used to draw the shape
fillchar = ' '  # The char to be filled in the gap (Default: Space char)
```

## Staircase pattern towards left with all characters in steps are same


```python
def staircase_left(n):    
    for i in range(1, n + 1):        
        chars = char * i
        print(chars.ljust(n, fillchar))
        
staircase_left(n)
```

    *    
    **   
    ***  
    **** 
    *****


## Staircase pattern towards right with all characters in steps are same


```python
def staircase_right(n):    
    for i in range(1, n + 1):        
        chars = char * i
        print(chars.rjust(n, fillchar))

staircase_right(n)
```

        *
       **
      ***
     ****
    *****


## Staircase pattern inverted towards left with all characters in steps are same


```python
def staircase_inverted_left(n):    
    for i in range(n, 0, -1):        
        chars = char * i
        print(chars.ljust(n, fillchar))
        
staircase_inverted_left(n)
```

    *****
    **** 
    ***  
    **   
    *    


## Staircase pattern towards right with all characters in steps are same


```python
def staircase_inverted_right(n):    
    for i in range(n, 0, -1):        
        chars = char * i
        print(chars.rjust(n, fillchar))
        
staircase_inverted_right(n)
```

    *****
     ****
      ***
       **
        *



```python
## Solid Square with all chars same
```


```python
def square_solid(n):
    if n < 4:
        raise ValueError('Size cannot be < 4')

    for _ in range(n):
        print(f'{char}{fillchar}' * n)

square_solid(n)
```

    * * * * * 
    * * * * * 
    * * * * * 
    * * * * * 
    * * * * * 


## Hollow square with all chars same


```python
def square_hollow(n):
    if n < 4:
        raise ValueError('Size cannot be < 4')

    first_or_last_row = f'{char}{fillchar}' * n    
    print(first_or_last_row)  # First row

    # Rows in between
    for _ in range(1, n-1):
        print(char + ' ' * (n*2-3) + char)  
        # minus -3 for two chars at left and right end + a space char at R.H.S
    
    print(first_or_last_row)  # Last row

        
square_hollow(n)
```

    * * * * * 
    *       *
    *       *
    *       *
    * * * * * 



```python
## Solid triangle with all chars same
```


```python
def triangle_solid(n):
    if n < 2:
        raise ValueError('Size cannot be < 2')

    width = n * 2  
    # With extra space char included, width should be doubled
    
    for i in range(1, n+1):
        chars = f'{char}{fillchar}' * i
        print(str(chars).center(width, fillchar))

triangle_solid(n)
```

        *     
       * *    
      * * *   
     * * * *  
    * * * * * 


## Hollow triangle with all chars same


```python
def triangle_hollow(n):
    if n < 2:
        raise ValueError('Size cannot be < 2')

    counter = 1  
    # Counter to fill hollow space inside triangle
    width = n*2  
    # Need twice the space to print the shape as it is, since we cannot have a char in b/w two chars below row

    print(char.center(width, fillchar))
    # First row
    
    # Rows in between
    for _ in range(1, n-1):
        c = char + fillchar * counter + char
        print(c.center(width, fillchar))
        counter += 2  # Space inside triangle gets widened twice per iteration
    
    print(f'{char}{fillchar}' * n)
    # Last row

triangle_hollow(n)
```

        *     
       * *    
      *   *   
     *     *  
    * * * * * 


## Staircase pattern towards left with each step representing the step number


```python
def staircase_left_with_same_numbers():
    for i in range(1, n+1):
        print(str(i) * i)

staircase_left_with_same_numbers()

```

    1
    22
    333
    4444
    55555


## Staircase pattern towards left with each char in step with increasing number


```python
def staircase_left_with_nums_increasing():
    num = 1
    for row in range(1, n+1):      
        for col in range(row):
            print(num, end=" ")
            num += 1
        print()
        
staircase_left_with_nums_increasing()
    
```

    1 
    2 3 
    4 5 6 
    7 8 9 10 
    11 12 13 14 15 

