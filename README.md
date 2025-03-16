# EDB-ID-1518
script and compile directions for EDB-1518 - used to exploit Proving Grounds - Pebbles

### Compile with gcc
```bash
gcc -g -c raptor_exploit.c
````
- Makes a `raptor_exploit.o` file in the current directory
---
#### Then:
```bash
gcc -g -shared -Wl,-soname,raptor_exploit.so -o raptor_exploit.so raptor_exploit.o -lc
```
- Makes a `raptor_exploit.so` file in the current directory
---
### commands explained
`-g` adds dbug symbols into the compiled object file

`-c` instructs to compile only which produces an object file `.o`
this is run on the source file `raptor_exploit.c`

`-shared` generates a shared object dynamic library

`-Wl` arguments passed directly to linker

`-soname,raptor_exploit.so` sets the shared object name (soname)
- Match the output file name
- shared objects (`.so` files) are dynamically-loaded libraries/plugins like user defined functions in databases or extensible systems - hence its use in exploiting the mysql perms

`-o` designates the output file `raptor_exploit.so` compiled shared object
- `raptor_exploit.o` is the input file

`-lc` explicitly links library agaists standard C library `libc`

---
### Target mysql:



