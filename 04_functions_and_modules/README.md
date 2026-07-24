# Lesson 4: Functions and modules

# Functions
Defining a function requires a _name_ and a list of _parameters_:
```python
function myFunction(param1: string, param2: number, param3: any)
    [...]
end
```

Functions should be defined using _lowerCamelCase_ notation.
A parameter must have a type and can be optionally followed by a default value:
```python
function round(num: number, digits: number = 0)
    [...]
end

; will result in 3
round(num = 3.1415)

; will result in 3.14
round(num = 3.1415, digits = 2) 
```

Naming parameters is not mandatory:
```python
; will result in 2.718
round(2.71828, 3)
```

# Modules
Modules are jask scripts in separated files which are providing functionalities for other scripts, like a library or framework.
For example, write a file `my_math_functions.jask`:
```python
function calculateDiscount(price: number, percent: number = 10)
    return price - (price * (percent / 100))
end
```

This file can be imported via `use` where using `.jask` at the end of the file is optional:
```python
use "my_math_functions" as math

printLine("Your discount is " + math::calculateDiscount(price = 200.123, percent = 20))
```

# Run
The interpreter needs the *allow-stdout* permission, because we are using *print* and *printLine* in this example.
```bash
dotnet --allow-stdout --input="main.jask"
```