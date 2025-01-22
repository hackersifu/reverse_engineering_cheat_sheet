# Reverse Engineering Cheat Sheet
This is a collection of reverse engineering notes, code snippets, and resources.

## ELF (Executable and Linkable Format) Section List
-	.init – contains executable code that performs initialization tasks, and runs before any other code in the binary
-	.fini – runs after the main program completes, acting as the destructor of the program
-	.text – where the main code of the program resides
-	.bss – reserves spaces for uninitialized variables
-	.data – storage for initialized variables
-	.rodata – stands for “read-only” data, dedicated to storing constant variables. 
-	.plt – Procedure Linkage Table (PLT), and this is the code section that contains executable code
-	.got.plt – data section of the PLT
-	.rel.* - Contains relocation entries for the .text section
-	.init_array – holds pointers to functions that are executed before the main function is called
-	.fini_array - holds pointers to functions that are executed after the main function is called
-	.got – Global Offset Table (GOT), used for dynamic symbol resolution during runtime
-	.dynsym – stores the dynamic symbol table, used for dynamic linking
-	.dynstr – stores strings associated with dynamic symbols in the .dynsym table
-	.dynamic – contains information about dynamic linking, such as library dependencies and symbol resolution
-	.symtab – holds the symbol table used for linking and debugging
-	.strtab – stores strings for the names of symbols and sections referenced in .symtab
-	.debug – contains debugging information, such as line numbers and variable names (optional in production binaries)
-	.note – stores metadata, such as build information or identification notes
-	.tls – Thread Local Storage (TLS), used for variables that are unique to each thread

## File Headers to file type
- ELF - Executable and Linkable Format (Linux)
- PE - Portable Executable (Windows)
- Mach-O - Mach Object (macOS)
- MZ - DOS Executable (Windows)
- PK... - ZIP Archive
- Rar! - RAR Archive
- X.S.BB` - Mac Disk image file
- %PDF - PDF file
- MSCF - CAB file
