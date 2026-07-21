# Lesson 2: Variables and Types
In jask, variables are created and changed explicitly using `set`:
```
set myVar = 5
```
A variable can change its type dynamically during runtime:
```
set myVar = 5
set myVar = "Hello..."
```
If you want to prevent this, `restrict` your variable:
```
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

## Run
The interpreter needs the *allow-stdout* permission, because we are using *print* and *printLine* in this example.
```bash
dotnet --allow-stdout --input="main.jask"
```