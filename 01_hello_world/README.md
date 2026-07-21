# Lesson 1: Hello World!
Every programming language should introduce itself with a "Hello World!", and jask is no exception.
In jask, you do not need to import stuff or defining a *main* function.
Just type your code and you are ready to go!

You can use two functions for printing text to the console:
* `print(...)` – Outputs text **without** an automatic newline.
* `printLine(...)` – Outputs text **with** an automatic newline.

These are the two basic functions for stdout.

## Run
The interpreter needs the *allow-stdout* permission, because we are using *print* and *printline*.
```bash
dotnet --allow-stdout --input="main.jask"
```