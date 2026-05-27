---
{"dg-publish":true,"permalink":"/0x/cs-101/cs-50/2-arrays/c-lecture-2/","created":"2026-05-15T18:06:17.703+01:00","dg-note-properties":{}}
---

#### Debugging
Whenever you want to find logical flows in the code, use always `printf` as a debugging tool to check how the code behaves.
#### Compiling
`make` is a command that compiles the source code into machine code, but *make is not the compiler.*
The actual compiler is called `clang`, so instead of using `make hello` , we use:
```c
#include <stdio.h>

int main(void)
{
	printf('hello')
}
```
and run:
```bash
cs50/c/lec2/ $ clang name.c
cs50/c/lec2/ $ ls
a.out*  name*  name.c
```
This outputs a assembly.output file

with `#include <cs50.h>` library **clang will return error:**
```bash
cs50/c/lec2/ $ clang name.c
/usr/bin/ld: /tmp/name-3c3e1b.o: in function `main':
name.c:(.text+0x16): undefined reference to `get_string'
clang: error: linker command failed with exit code 1 (use -v to see invocation)
```
This is mainly because we think clang knows where to find the CS50 library , but that's not a standard library frequently used. It's being used for the time being , because we are fairly new to C.

###### When source code get processed into machine code, it goes though:
- preprocessing : header file function added to the main function
- compiling : source code to assembly code
- assembling : conversion to binary + combine header file codes 
- linking : all the converted binary code are linked together

#### C data types:
- bool - 1 byte
- int - 4 byte (4 billions)
- long - 8 byte
- float - 4 byte (real numbers with decimal points)
- double - 8 byte
- char - 1 byte
- string - Depends on the lenght of the string 

When we store value in memory all we are doing is memory in the hardware like this:
![Attachments/Pasted image 20260515164311.png](/img/user/0x/CS101/CS50/2.%20Arrays/Attachments/Pasted%20image%2020260515164311.png)
so for the code :
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	int score1 = 72;
	int score2 = 73;
	int score3 = 33;
}
```
we would use 4 byte of each integer , so 12 bytes in total:
![Attachments/Pasted image 20260515170103.png](/img/user/0x/CS101/CS50/2.%20Arrays/Attachments/Pasted%20image%2020260515170103.png)

---
#### Arrays
<mark style="background: #FF5582A6;">We can use arrays, which are a chuck of contiguous memory. </mark>
![Attachments/Pasted image 20260515170613.png](/img/user/0x/CS101/CS50/2.%20Arrays/Attachments/Pasted%20image%2020260515170613.png)

