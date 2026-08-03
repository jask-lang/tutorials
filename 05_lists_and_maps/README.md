# Lesson 5: Lists and maps

# Lists
A `list` is a data type storing elements ordered in a row:
```python
set myList = list(1, 2, 3)
```

It is not required that the list contains the same type of data, a `list` can story any type simultaneously:
```python
set myList = list(1, "Two", true, list())
```

Elements are being accessed using the index in the list, starting with 0:
```python
set myList = list(1, 2, 3)
printLine(listGet(list = myList, index = 0)) ; will access the number element '1'
```

Adding new elements is easy as well:
```python
set myList = list(1, 2, 3)
set myList = listAdd(list = myList, element = 4)
```
The element `4` will be added at the end of `myList` while `listAdd` returns a copy of the list.
In jask, variables cannot be altered in place, every manipulating functions always returns a copy of the original variable!

There are several more functions for manipulating `list`s, there are more examples shipped with this tutorials main.jask!

# Maps
A `map` is a data type mapping keys to values. Like a list but with own defined keys as indexes.
The following example maps ages to peoples names:
```python
set myKeys = list("Jules", "Ann", "Peter")
set myVals = list("31", "24", "69")

set ages = map(keys = myKeys, values = myVals)
```
Now we can access the age numbers based on the names of the people:
```python
set jules = "Jules"
printLine(jules + " is " + mapGet(map = ages, key = jules) + " years old!")
```

Adding a person is easy:
```python
set ages = mapSet(map = ages, key = "Lucia", value = 31)
```

Oh! We made a mistake. We have added Lucias age as a number while the other ages are strings.
We can fix this with a simple `for...in`:
```python
for kvp in ages
    if type(kvp.value == "string")
        set ages = mapSet(ages, kvp.key, toNumber(kvp.value))
    endif
endfor
```
When iterating over a `map`, ever iteration receives a `struct` containing the `key` and corresponding `value`, therefore we are calling it a key-value-pair.

There are several more functions for manipulating `map`s. Explore the main.jask from this tutorial and happy coding!

# Run
The interpreter needs the *allow-stdout* permission, because we are using *print* and *printLine* in this example.
```bash
dotnet --allow-stdout --input="main.jask"
```
