# Lesson 3: Trust and verify

# Verify
All external input in jask is per default `untrusted` and cannot be used.
An `untrusted` variable must be safely transfered into `verified` state using `verify`.
Have a look at the following example:
```python
set rawInput = readInput("Please enter your name: ")
set name = verify(untrusted = rawInput, pattern = "string")
```
This transfers the `untrusted` raw input from `readInput`, which reads a line from `stdin`, to a `Result` struct containing the verifications result:
```python
if name.type == "OK"
    print("Your name is " + name.value)
else
    print("Error reading from stdin: " + name.error)
endif
```

Jask has a number of different patterns to choose from:
* `string` - verifies that an untrusted variable contains a string
* `number` - verifies that an untrusted variable contains a number
* `boolean` - verifies that an untrusted variable contains either true or false

This allows external input to be elegantly converted into usable types during runtime.
The interpreter is constantly updated to support new patterns to make `verify` even more useful, e.g. it is planned to support safe URL matching in the future.

A variable can be marked `untrust`ed even at runtime, which is useful when working with functions from external or unknown modules and you want to check their return values:
```python
use "an_unknown_module.jask" as unknown

set untrustedValue to untrust(unknown::someFunction())
set value = verify(untrustedValue, "number")
```

# Trust
In truly rare cases, if a developer is certain that an expected external value is safe, they can use `trust` to use the variable directly without verifying it first:
```python
set age = trust(readInput("Enter only a number and nothing else please!"))
```
Note, that `trust` returns the string representation or throws a runtime error in case of failures.
In order to use `trust`, the interpreter needs the corresponding permission `--allow-trust`.

# Run
The interpreter needs the *allow-stdout* as well as *allow-stdin* and *allow-trust* permissions, because we are using *print*, *printLine*, *readInput* and *trust* in this example.
```bash
dotnet --allow-stdout --allow-stdin --allow-trust --input="main.jask"
```
# Continue...
After mastering *trust* and *verify*, have a look at [functions and modules](https://github.com/jask-lang/tutorials/tree/main/04_functions_and_modules)!