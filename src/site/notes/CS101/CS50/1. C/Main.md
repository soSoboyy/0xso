---
{"dg-publish":true,"permalink":"/cs-101/cs-50/1-c/main/","dg-note-properties":{}}
---

In C **the main function is called automatically whenever code is running.**
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	
}
```
###### (void)
- ==It means that the program is not taking any command line input as an argument==
- (except make)

Programs that take command like arguments:
```c
#include <stdio.h>
#include <cs50.h>

int main(void)
{
	string s = get_string("What's your name? ");
	printf("%s\n Hello, " , s);	
}
```

But there are *keywords* such as `argc` and `argv` that can go inside the main function:
- `argc` (argument count ) is an integer , contains the total count of arguments in the prompt
- `argv` (argument vector) is an array of strings and defines how many variables the program can take 

```c
#include <stdio.h>
#include <cs50.h>
int main(int argc, string argv[]){
// This program takes the input from the command line
	printf("Hello, %s\n", argv[1] );
	
```
- If inside the `argv` variable is assigned 0, the print statement will print the program's name. <mark style="background: #BBFABBA6;">This is because the 0 location, automatically will contain the program-s name. (Useful for self-referencing)</mark>
- Same for `argc` , it contains the total number of argument in the prompt, ==but the first is always the programs name.==


==The value that the main function returns , is called an*exit status*.==
```c
#include <stdio.h>
#include <cs50.h>
int main(int argc, string argv[]){
	if (argc != 2)
	{
		printf("Missing CL argument\n");
		return 1;
	}
	printf("Hello, %s\n", argv[1]);
	return 0;
}
```

We can check secretly the return value of a program by digiting: `echo $?`
In C when a program returns the a value, the execution stops.