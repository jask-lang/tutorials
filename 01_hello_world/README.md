# Lesson 1: Hello World!
Every programming language should introduce itself with a "Hello World!", and jask is no exception.
In jask, you do not need to import stuff or defining a *main* function.
Just type your code and you are ready to go!

You can use two functions for printing text to the console:
* `print(...)` – Outputs text **without** an automatic newline.
* `printLine(...)` – Outputs text **with** an automatic newline.

These are the two basic functions for stdout.
jask has a very restricted setup per default, the interpreter needs permissions to do certain operations:

* **--allow-stdout** or **-ao** (`print`, `printLine`)
* **--allow-stdin** or **-ai** (`readInput`)
* **--allow-read** or **-ar** (`use` modules, `readFile`)
* **--allow-write** or **-aw** (`writeFile`)
* **--allow-trust** or **-at** (`trust`)
* **--allow-all** combines all permissions in one argument

*read* and *write* permissions can be used with or without paths and multiple times to define exactly the paths and files jask is allowed to read or write. One does not have to use '=', values can be passed as a next argument as well:
```terminal
dotnet run --allow-read
dotnet run --allow-read="sample.jask"
dotnet run --allow-read "a/path/to/a/directory" -aw "a_single_file.txt"
```
Using *allow-read* and *allow-write* without paths enables permissions globally.
Please note, that the interpreter inherits the permissions of the executing user regarding file access and that writing runtime errors to *stderr* is always possible.
For now, you do not need to worry too much on all possible permissions, other tutorials will cover them in more detail.

# Run
The interpreter needs the *allow-stdout* permission, because we are using *print* and *printline*.
```bash
dotnet --allow-stdout --input="main.jask"
```

# Continue...
After mastering *print*, *printLine* and jask permissions system, have a look at [variables and types](https://github.com/jask-lang/tutorials/tree/main/02_variables_and_types)!
