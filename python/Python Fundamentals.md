# Python Fundamentals

**Types**
`bool`, `int`, `float`, `string`, `NoneType`

Any operation executed where at least one element is a `float` will return a `float `

`x/y`, however, will always return a `float`
`x//y`, will return an `int`, rounding down (Python always rounds down when `typecasting`

`string`s are immutable. Must be redefined entirely. 

**Logic Operators**
`and`, `or`, `not`

Booleans are `True` and `False` (capitalized)

**Basic Functions**
`round(x)` returns an `int` where values less than or equal to .5 round down and greater than .5 round up

`input("text: ")` prints the string and waits for the users input. The input is always treated as a string, so it may need to be casted. 

`range(start, stop. step)`

**Indexing**
`a:b:c` makes use of extended slices. Where the 3 argument is an optional `step`. 

```python
a = [0,1,2,3,4,5,6]
a[::2]
# 0, 2, 4, 6
```

