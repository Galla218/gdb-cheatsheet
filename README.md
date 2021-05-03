# gdb-cheatsheet
Useful GDB commands

### Info Functions
```gdb
(gdb) info functions
All defined functions:

Non-debugging symbols:
0x0804830c  malloc@plt
0x0804831c  __libc_start_main@plt
0x0804832c  printf@plt
0x0804833c  exit@plt
0x0804834c  free@plt
0x0804835c  memset@plt
0x0804836c  strcpy@plt
```
The address next to each function is the entry in the Procedure Linkage Table (PLT)

### Back Trace
Gives you layout of the call tree. Useful when binary is stripped and you want to break on a function like `strcpy`, see what the parent function is, and set a break in the parent function.
```gdb
(gdb) bt
#0 0x0804836c in strcpy@plt ()
#1 0x0804850f in ?? ()
#2 0x420158d4 in __libc_start_main () from /opt/libc-2.2.93/libc.so.6
#3 0x0804839d in ?? ()
```
Next you could set a break point at `0x0804850f` and could break in the parent after the call to strcpy.
