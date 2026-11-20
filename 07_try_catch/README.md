# Lesson 7: Try / Catch

No matter how carefully you write code, things can still go wrong at runtime: a key is missing from a map, you divide by zero, or a function receives unexpected input. This lesson covers jask's error handling with the `try / catch / endtry` construct.

## The Basics

A `try` block guards a section of code that *might* raise an error. If an error is raised anywhere inside the `try` block, the rest of the `try` block is skipped and execution jumps to the `catch` block. If no error is raised, the `catch` block is skipped entirely.

```jask
try
    ; code that might raise an error
catch e
    ; code that runs only if an error occurred
endtry
```

Like the other blocks you have learned, the body is defined by indentation and closed with the `endtry` keyword.

## The Error Variable

The identifier after `catch` (here `e`) is the **error variable**. It is **optional** — if you do not need the error details you can write a bare `catch` with no variable.

When an error is caught, the error variable holds a value with three fields you can read with dot access:

| Field       | Type     | Description                                              |
|-------------|----------|----------------------------------------------------------|
| `e.message` | `string` | A description of what went wrong.                        |
| `e.line`    | `number` | The line number where the error occurred.                |
| `e.file`    | `string` | The path of the file the error came from (`nil` in the REPL). |

```jask
set config = { "host" = "localhost" }

try
    set port = config["port"]
catch e
    printLine("Missing port on line " + e.line + ": " + e.message)
endtry
```

## Common Errors

Any jask-level failure raises an error that `try / catch` can handle, for example:

- Reading a key that is not present in a map (`config["port"]`).
- Dividing by zero (`10 / 0`).
- Indexing a list out of bounds (`[1, 2][5]`).
- Calling a function that is not defined.

## Errors Propagate

An error raised inside a function is not swallowed by the function — it propagates up to the `try` block of the caller. This means you can keep functions simple and let the caller decide how to recover.

```jask
function divide(a: number, b: number)
    return a / b
endfunction

try
    set result = divide(100, 0)
    printLine("Result: " + result)
catch e
    printLine("Caught: " + e.message)
endtry
```

Here the "Division by zero" error is raised inside `divide` but caught by the caller's `try` block. Note that `e.line` points to the line inside `divide` where the error actually happened, not the line of the call.

## Run

```bash
dotnet run --allow-stdout --input="main.jask"
```

### Expected Output

(`[<path>:<line>]` in the output is the absolute path to `main.jask`, so it differs per machine. It is part of `e.message`.)

```
--- 1. Successful try ---
Connected to localhost

--- 2. Caught error ---
An error occurred on line 29
The error said: [<path>:29] Map does not contain key 'database'

--- 3. Bare catch ---
Recovered. recovered = true

--- 4. Error from a function ---
100 / 4 = 25
divide() by zero caught: [<path>:55] Division by zero

All errors were handled - the program kept running.
```

---

## Exercises

1. **Basic:** Wrap the statement `set age = people["age"]` (where `people` is a map without an `"age"` key) in a `try / catch`. In the `catch` block, print `e.message`.
2. **Intermediate:** Write a function `safeDivide(a: number, b: number)` that returns `a / b`. Call it inside a `try / catch` with `b = 0` and print a friendly message using the error variable instead of letting the program crash.
3. **Challenge:** Given a map of nested user data, use `try / catch` to safely read a deeply nested value. If any key is missing, fall back to a default value and print which line the lookup failed on using `e.line`.

---

Congratulations on completing the tutorial series! Continue exploring jask by looking at the [jcore modules](https://github.com/jask-lang/jcore) or experimenting with building your own modules.
