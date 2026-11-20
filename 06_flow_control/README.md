# Lesson 6: Control Flow

You have already encountered conditionals and loops in previous lessons. This lesson covers control flow in detail, along with the comparison and logical operators that power them.

## Conditionals

The `if...endif` block lets you execute code only when a condition is met:

```jask
set score = 85

if score >= 90
    printLine("Grade: A")
else if score >= 80
    printLine("Grade: B")
else
    printLine("Grade: C or below")
endif
```

You can chain conditions with `else if` and fall back with `else`. Each branch executes only if the previous conditions were false.

## Comparison Operators

| Operator | Description     | Example        | Result  |
|----------|-----------------|---------------|---------|
| `==`     | Equal to        | `5 == 5`      | `true`  |
| `!=`     | Not equal to    | `5 != 3`      | `true`  |
| `<`      | Less than       | `2 < 4`       | `true`  |
| `<=`     | Less or equal   | `4 <= 4`      | `true`  |
| `>`      | Greater than    | `7 > 3`       | `true`  |
| `>=`     | Greater or equal| `6 >= 8`      | `false` |

## Logical Operators

Combine conditions with logical operators:

```jask
set age = 25

; AND - both must be true
if age > 18 and age < 65
    printLine("Working age")
endif

; OR - at least one must be true
set isWeekend = true
set hasDayOff = false
if isWeekend or hasDayOff
    printLine("Time to relax!")
endif

; NOT - negates a boolean
if not (age < 18)
    printLine("Adult")
endif
```

## Loops

### For Loop Over Lists

Iterate over each element in a list:

```jask
set nums = [1, 2, 3, 4, 5]

for item in nums
    printLine(item * 2)
endfor
```

This prints: `2`, `4`, `6`, `8`, `10`.

### While Loop

Repeat while a condition holds:

```jask
set counter = 0

while counter < 5
    printLine("Count: " + counter)
    set counter = counter + 1
endwhile
```

## Run

```bash
dotnet run --allow-stdout --input="main.jask"
```

### Expected Output

```
--- Conditionals ---
Grade: B
It is warm today!

--- Logical Operators ---
Temperature is in comfortable range

--- For Loop ---
Double of 1 is 2
Double of 2 is 4
Double of 3 is 6
Double of 4 is 8
Double of 5 is 10

Sum: 15

--- While Loop ---
Step 0
Step 1
Step 2
Step 3
Step 4

Done!
```

---

## Exercises

1. **Basic:** Write a script that takes a number and prints whether it is positive, negative, or zero using `if...elseif...else`.
2. **Intermediate:** Use a `while` loop to compute the factorial of a number (e.g., 5! = 120). Print each step: `"3 * 2 = 6"` etc.
3. **Challenge:** Write a Fibonacci generator that prints the first N numbers of the sequence using a `while` loop. Use logical operators to validate that N is greater than zero before starting.

---

Continue to [Lesson 7: Try / Catch](../07_try_catch/README.md) to learn how to handle errors gracefully. After that, keep exploring jask by looking at the [jcore modules](https://github.com/jask-lang/jcore) or experimenting with building your own modules.
