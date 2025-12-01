# hot-code-reloading

See NOTES below
+
In progress, see https://github.com/FlavorlessQuark/ELF_Parser

/* Hot code reloading (library ?)

Expected features:

- Program should compile as usually with the addition of the lib;
- Reload functions at runtime
- As little user input as possible (i.e, doesn't need user to call and setup a billion functions)
- Migrate data on reload if needed
- Usable with multiple .so
- Rollback in case of error

----------------------------------

The common approach :

"Host" program gets init and sets up various variables to keep track of .dll/.so, functions and data to be reloaded
            |
            V
Tracks specificed libs and then runs specified "main guest" function
            |
            V
Watch libs and reload them
            |
            V
Replace old func ptrs & data with new ones


READ :

https://slembcke.github.io/HotLoadC (very simple impl, good to understand how it broadly works)
https://fungos.github.io/cr-simple-c-hot-reload/ (implementation : https://github.com/fungos/cr/blob/master/cr.h)
https://thenumb.at/Hot-Reloading-in-Exile/

------

Approach I want to take (if possible):


Don't like being forced to compile the whole application as a .so or dll.
Better if it was possible to reload symbols from object files directly

// Using reflection like in the Exile example could be a viable alternaive. It would still require to re-compile the entire program but at least we can just tag the functions we want
// to reload

READ :
    About ELF files:
        - https://linux-audit.com/elf-binaries-on-linux-understanding-and-analysis/
        - https://unix.stackexchange.com/questions/476165/what-is-the-difference-between-shared-object-file-and-relocatable-file
        - (ELF format) https://docs.oracle.com/cd/E19683-01/817-3677/chapter6-46512/index.html
        - SysV (Linux basically) ABI https://www.sco.com/developers/devspecs/gabi41.pdf
        - https://en.wikipedia.org/wiki/Executable_and_Linkable_Format
    About Object linking:
        - https://carsontang.github.io/unix/2013/06/01/guide-to-object-file-linking/
        - https://blog.cloudflare.com/how-to-execute-an-object-file-part-1

- [X] Make ELF parser to better understand file format.
- [ ] Simple program, change one function
- [ ] // // // // //, change main
- [ ] Can we tag things whose data we want to keep loade (e.g value persists after hcr)

<!-- How to :

- Find and parse the .strtab and shstrab section for use when going over symtab
-  -->

*/
(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)(≧ω≦)
