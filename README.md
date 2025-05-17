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

## Basic Data Units and Types
- Boolean: A binary data type that can only store two possible values: true or false. 
- Integer: This stores whole numbers. The size varies. In some cases, it can be specified as a suffix defining the number of bits (int16, int32, and so on). 
Unsigned: All bits are dedicated to storing the numeric value. 
- Signed: The most significant bit (the top left) is dedicated to storing the sign, 0 for plus and 1 for minus. So 0xFFFFFFFF = -1. 
- Short and long: These data types are integers that are smaller or bigger than the standard integer, respectively. The size is 2 bytes for short and 4 or 8 bytes for long. 
Float and double: These data types are designed to store floating-point numbers (values that can have fractions). They are pretty much never used in malware. 
- Char: Generally used to store characters of strings, each value has a size of 1 byte. 
- String: A group of bytes that defines human-readable strings. It can utilize one or multiple bytes per character, depending on the encoding. 
- ASCII: Defines the mappings between characters (letters, numbers, punctuation signs, and so on) and the byte values. It uses 7 bits per character.
- UTF-8: A variable-length encoding scheme that can use 1 to 4 bytes per character. It is backward compatible with ASCII, meaning that the first 128 characters are the same as in ASCII.
- UTF-16: A fixed-length encoding scheme that uses 2 bytes per character. It can also use 4 bytes for some characters.
- Little-endian: The least significant byte is stored first, followed by the more significant bytes.
- Big-endian: The most significant byte is stored first, followed by the less significant bytes.

## Bitwise Operations
- AND (&): The result is 1 if both bits are 1, otherwise it is 0.
- OR (|): The result is 1 if at least one of the bits is 1, otherwise it is 0.
- XOR (^): The result is 1 if the bits are different, otherwise it is 0.
- NOT (~): The result is the inverse of the bit, 0 becomes 1 and 1 becomes 0.
- Logical Shift left (<<): Moves the bits to the left, filling the rightmost bits with 0. This is equivalent to multiplying by 2.
- Logical Shift right (>>): Moves the bits to the right, filling the leftmost bits with 0. This is equivalent to dividing by 2.

## Packers
Commonly used executable packers are UPX, MPRESS, and ExeStealth. Popular features include the ability to encrypt files to avoid detection, file compression, decreased start time, and built-in anti-debugging mechanisms. Packers allow malware authors to add an additional layer for analysts to crawl through, as analysts must undo the work performed by the packer. This requires understanding on how a packer operates, specifically in the context of how the malware was packed.
#### Tools to check for Packers
- PeiD


 

## Resources
- Process Creation Flags (from Microsoft) - https://learn.microsoft.com/en-us/windows/win32/procthread/process-creation-flags