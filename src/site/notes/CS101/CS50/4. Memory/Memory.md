---
{"dg-publish":true,"permalink":"/cs-101/cs-50/4-memory/memory/","dg-note-properties":{}}
---

==From this lecture onwards the `cs50.h` library is not going to be used anymore!==

Binary system : `0` & `1` 

Hexa system: `0123456789ABCDEF` (numbers 0-15)
- 16^0 = 0
- 16^1 = 16

Snippet of memory:
![Attachments/Pasted image 20260615190639.png](/img/user/CS101/CS50/4.%20Memory/Attachments/Pasted%20image%2020260615190639.png)
IN computer the memory location are referred in Hexadecimal. ==So per convention, any number using Hexadecimal notation has a `0x`.== 

###### Code starting from `addresses.c`
- integer tends to be 4 bytes (32bits)

```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	int n = 50;
	printf("%i\n",n);
}
```

New terminology:
- `&` If we prefix a variable with `&n` it gives the address in memory where the variable is stores 
- `%p` percent p to print an address of something in the computer's memory

```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	int n = 50;
	printf("%p\n",&n);
}
```

###### Pointers:
==Core topic in C!== A *pointer* is a variable that can store in address