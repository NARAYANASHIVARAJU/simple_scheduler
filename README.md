# simple_scheduler
This project implements a simple ELF loader in C. It demonstrates how an operating system or runtime environment might load and execute an ELF (Executable and Linkable Format) binary.
# ELF Loader in C

This project implements a **basic ELF loader** in C that can read, validate, and execute a 32-bit ELF executable.  
It mimics how an operating system loads binaries into memory and transfers control to their entry point.

---

1. Features
- Reads the **ELF header** (`Elf32_Ehdr`) from the input file.
- Parses **program headers** (`Elf32_Phdr`) to locate loadable segments (`PT_LOAD`).
- Uses **mmap** to load ELF segments into memory at the correct virtual addresses.
- Transfers execution to the ELF **entry point (`e_entry`)**.
- Cleans up allocated resources and file descriptors after execution.

---

2. How It Works
1. Open the ELF file from command-line input.  
2. Read and validate the ELF header.  
3. Iterate over program headers to find loadable segments.  
4. If the entry point lies within a segment, load it into memory.  
5. Execute the program starting from its `_start` entry point.  
6. Print the return value from the ELF’s entry function.  

---

3. File Structure
- `loader.c` → Core ELF loader implementation.  
- `loader.h` → Header declarations (structures, prototypes, constants).  

---

## ⚙️ Build Instructions
Compile the loader with:
```bash
gcc -m32 -o loader loader.c -Wall
