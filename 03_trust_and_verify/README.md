# Lesson 3: Trust and verify

# Verify
All external input in jask is per default `untrusted` and cannot be used.
An `untrusted` variable must be safely transfered into `verified` state using `verify`.
Have a look at the following example:
```python
set rawInput = readInput("Please enter your name: ")
set name = verify(untrusted = rawInput, pattern = "string")
```
This transfers the `untrusted` raw input from `readInput`, which reads a line from `stdin`, to a `verified string`using the corresponding pattern.

Jask has a number of different patterns to choose from:
* `string` - verifies that an untrusted variable contains a string
* `number` - verifies that an untrusted variable contains a number
* `boolean` - verifies that an untrusted variable contains either true or false

This allows external input to be elegantly converted into usable types during runtime.
The interpreter is constantly updated to support new patterns to make `verify` even more useful, e.g. it is planned to support safe URL matching in the future.
Note, that the interpreter currently throws a runtime error and aborts the execution ff a transfer failed because of a pattern not matching.

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
Note, that `trust` always returns the string representation of the raw value.

## Run
The interpreter needs the *allow-stdout* as well as *allow-stdin* and *allow-trust* permissions, because we are using *print*, *printLine*, *readInput* and *trust* in this example.
```bash
dotnet --allow-stdout --allow-stdin --allow-trust --input="main.jask"
```
