Great Guide

https://realpython.com/cpython-source-code-guide/#part-2-the-python-interpreter-process

## Part1 Introduction

### compile in Linux

install make, gcc, configure

1 openssl

2 using Makefile to bulid CPython binary

### compile do

compile into:

- low-level machine code , executed by $system$
- intermediary language ,executed by $virtual$  $machine$  -> portable across multiple system

### **runtime**  

FUN: convert python source code and execute it in one step

- convert *python code* into *bytecode* (special low level intermediary language)
  - .byc was in a hidden directory and cached.
- *CPython*  read *bytecode* (.pyc)

Above action lead to python application run faster at second time.

### compiler Types

1. **[Self-hosted compilers](https://en.wikipedia.org/wiki/Self-hosting)** are compilers written in the language they compile, such as the Go compiler.
2. **[Source-to-source compilers](https://en.wikipedia.org/wiki/Source-to-source_compiler)** are compilers written in another language that already have a compiler.

​	high —> low or high, but finally need to be executable



### CPython

API to operate Linux kernels(network,file) are written in pure C

complied version of CPython = . /python.exe

memory management (garbage collector)：

- Allocation of raw memory blocks is done via `PyMem_RawAlloc()`.
- The pointers to Python objects are stored within the `PyArena`.
- `PyArena` also stores a linked-list of allocated memory blocks.

## Part2 Interpret Process

