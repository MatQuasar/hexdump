# Hexdump for Windows, Linux, and DOS
Three separate programs

## Intro

Your hexdump for the command lines. Those are source code I wrote in the early days of my Assembly programming.
They are not perfect, but I keep it as is. 

> [!NOTE]
> Windows version of hexdump only runs in Command Prompt, because there is command line parsing error in PowerShell.

## Build 

Compile with flat assembler.

## Comparison of API calls

The main code in each of these programs is the same Assembly code, except library calls to OS kernel are different.

| Linux             | Win32 API                       | DOS                           |
|-------------------|---------------------------------|-------------------------------|
| Call stack        | GetCommandLineA (Win32 API)     | Program Segment Prefix (DOS)  |
| syscall 2         | CreateFileA                     | DOS Interrupt AH=3dh          |
| syscall 0         | ReadFile                        | DOS Interrupt AH=3fh          |
| syscall 1         | WriteFile                       | DOS Interrupt AH=2 & AH=9     |
| syscall 3         | CloseHandle                     | DOS Interrupt AH=3eh          |
| syscall 60        | ExitProcess                     | DOS Interrupt AH=4ch          |


## License

MIT

## Similar programs

Some fasm users had published similar hexdump program:

* https://github.com/chastitywhiterose/chastehex (see `asm` folder)

* https://github.com/vlabsc/file_in_hex

 
