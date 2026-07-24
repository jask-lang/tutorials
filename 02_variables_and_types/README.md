# Lesson 2: Variables and Types
In jask, variables are created and changed explicitly using `set`:
```python
set myVar = 5
```
A variable can change its type dynamically during runtime:
```python
set myVar = 5
set myVar = "Hello..."
```
If you want to prevent this, `restrict` your variable:
```python
set myVar = 5
restrict myVar

set myVar = 6 ; <-- this will fail!
```

## Primitive data types
Jask knows the following primitive types of data:
* `string`, like "Hello, World!"
* `number`, like 42 or 3.1415
* `boolean` can be `true` or `false`
* `any` which is a placeholder for any kind of data

If you want to know the type of a variable, use `type()`, which will return the type of the variable as a string:
```python
set myVar = 5
print(type(myVar)) ; <-- this will print 'number'
```

## Structs
A `struct` is a collection of independent variables, usually used to describe an object of the real world:
```python
struct Car
    set brand = ""
    set model = ""
    set hp = 0
endstruct
```
A `struct`s definition must begin with a capital letter.
To instanciate a new struct, initialize a new variable:
```python
set myCar = Car(brand = "Mercedes Benz", model = "R170", ps = 218)
```
Accessing the `struct`s fields (the variables) is done using `->`:
```python
print("I am driving a " + myCar->brand)
```

Updating a field is easy as well:
```python
set myCar = myCar update ps = 340
```

# Run
The interpreter needs the *allow-stdout* permission, because we are using *print* and *printLine* in this example.
```bash
dotnet --allow-stdout --input="main.jask"
```

# Continue...
After mastering basic variable types, have a look at [trust and verify](https://github.com/jask-lang/tutorials/tree/main/03_trust_and_verify)!
