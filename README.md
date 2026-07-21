# 🚀 Welcome to the jask tutorial!
Welcome to **jask** – a highly readable and safe interpreted language.
This tutorial will guide you step-by-step through the language using practical, runnable examples.

## 🛠️ Prerequisites
Make sure you clone the interpreter repository and that it is ready to run:
```bash
dotnet run --version
```

## 🏃 Running the tutorial files
In each tutorial, we cover a specific aspect of jask.
Every tutorial comes with a README with some explanations and a jask script ready for you to try out!
We assume, that you have cloned the interpreter repository next to the tutorials, so you only have to point the interpreter to the desired tutorial directory.
```
├── interpreter/
└── tutorials/
    └── 01_hello_world/
        ├── main.jask
```
For example, run tutorial 01 from your *interpreter* directory:
```bash
dotnet run --allow-stdout --input="../tutorials/01_hello_world/main.jask"
```
Have fun scripting jask!