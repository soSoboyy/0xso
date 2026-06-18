---
{"dg-publish":true,"permalink":"/cs-101/cs-50/1-c/welcome-to-c/","dg-note-properties":{}}
---

#C
The exercises are in `VScode/Learning/`
The code that human writes, is called source code.
A computer that takes source code and translates it in machine code, is called a compiler.

- When writing a program in c, the extension is `hello.c`
- To run the program, we need to run the `make` command that compiles the source code into machine code.
- Then we run the program with`./` which indicates the current file in the current folder.
![Attachments/Pasted image 20260512153707.png](/img/user/CS101%20/CS50/1.%20C/Attachments/Pasted%20image%2020260512153707.png)
Write your first program:
```c
#include <stdio.h>
int main(void)
{
printf("Hello \n World!");
}
```

---
###### `printf`

Print format statement in C is `printf('')` , in Python is `print('')`

###### Escape sequences:
- `\n`  = New line
- `\r`  = Goes all the way to the write
- `\'` = Tell the problem *to print only* the quote character 
- `\''` = Or double quote character

--- 
###### Header file `.h`
C header files end with the extension`.h`  , which are  C libraries.
*So any time we want to use specific pieces of code, even `printf`  we need  to import the header files.*
##### `#include <stdio.h>`

==The `printf` function is contained in the Standard I/O header file.==

==Documentation for C [libraries](https://manual.cs50.io/) from CS50==

At the beginning I'm using the `<cs50.h>` library which probably includes all the libraries. ==(Only cloud based vscode version)==

---
###### User input
Whenever printing something, we need to define the type of data we are taking as input.
```c
#include <stdio.h>
#include <cs50.h>

int main()
{
printf("Hello!\n");
string answer = get_string("What is your name?\n"); 
#input function = get_string
printf("hello, %s\n" , answer); 
# placeholder  %s to define string type
# /n prints a new line, moving cursor to a new line
}
``` 

For the moment I'm using the *CS50* library that includes all the input functions such as:
- `get_string`
- `get_int`

Whenever we want to print a specific data type, we need to **define the format specifier in C, which is used to tell the compiler about the type of data to be printed or scanned in input and output operations.**

- A format specifier always starts with a percentage sign `%`, followed by a letter.
![Attachments/Pasted image 20260515154336.png](/img/user/CS101%20/CS50/1.%20C/Attachments/Pasted%20image%2020260515154336.png)

---
###### Variables:
Create a variable: 
```c
counter = 1;
# or
counter = counter = 1;
# or
counter += 1;
# or
counter++;
```

###### Comparisons
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
int x = get_int("what is x? ");
int y = get_int("what is y? ");

if (x > y)
{
printf("x is bigger than y\n");
}

}
```

###### Comparing singe characters
- ==In C when you want to compare single characters, use `''` single quotes.== 
- When is a string, with multiple characters, *use `""` double quotes*
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	char c = get_char("Do you agree? ");
	# declare char type variable
	if (c == 'y')
	{
	printf("agreed.\n");
	}
	else
	{
	printf("Not agreed\n")
	}
}
```
The function `get_char` enforce only single character, because we declared the variable `char`.

<mark style="background: #BBFABBA6;">Same code but with logical operator `OR`</mark>
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	char c = get_char("Do you agree? ");
	# declare char type variable
	if (c == 'y' || c == 'Y')
	{
	printf("agreed.\n");
	}
	else
	{
	printf("Not agreed\n")
	}
}
```

---
###### Conditionals : While
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	int i = 0;
	while (i < 5)
	{
	printf("I'm increasing..%i\n", i);
	i++;
	}
}
```
![Attachments/Pasted image 20260512180750.png](/img/user/CS101%20/CS50/1.%20C/Attachments/Pasted%20image%2020260512180750.png)
==NOTICE==
- *i'm using the formatter `%i` to print the int value as well.*
- Careful that the loop has an exit code, otherwise it can become an infinite loop.
	- In case `ctrl + c` interrupts the program.

###### For
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	for (int i = 0; i < 3; i++)
	{
	printf("I'm a cat\n");
	}
}
```
- Initialize the variable
- Check the condition
- and execute the counter

###### Combination of while-for loop
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	int n; 
	while (true)
	{
		n = get_int("How many times should the cat meow? \n");
		if (n < 0)
		{
			continue;
		}
		else
		{
			break;
		}
		
		for (int i = 0; i < n; i++)
		{
		printf("meow\n");
		}
	}
}
```
==In **line 5** i'm declaring the variable outside the scope of the loops so it can be used in both loops==

---
# One of the best practice is that in C, the **main** function contains the entire code so it should be at the top, always.
###### Functions:
When a function has void, it takes no input.
```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	meow();
}

void meow(void)
	{
		printf('meow');
	}
```
==Note that because the function is below and outside the main function, it won't be called or it will return error, like this:==
```bash
CS50/C/ $ make cowFuncWithInput 
cowFuncWithInput.c:9:5: error: call to undeclared function 'meow'; ISO C99 and later do not support implicit function declarations [-Wimplicit-function-declaration]
    5 |     meow();
      |     ^
fatal error: too many errors emitted, stopping now [-ferror-limit=]
2 errors generated.
make: *** [<builtin>: cowFuncWithInput] Error 1
CS50/C/ $ ^C
CS50/C/ $ 
```
##### <mark style="background: #FF5582A6;">It's mandatory that the code is inside the main function</mark>
###### Prototype for functions
==A prototype is a declaration to the compiler that at some point, there will be a function.==
```c
#include <stdio.h>
#include <cs50.h>

//Signature
void bark(void)

int main(void)
{
	for (int i = 0; i < 5; i++)
	{
		bark();
	}
}

void bark(void)
	{
		printf('woof');
	}

```
So I declare the function *before the main func.* , and can define it after the main func.
###### functions taking input:
```c
#include <stdio.h>
#include <cs50.h>

// Signature moo function
void moo(int n);

int main()
{
	int n = get_int("How many times?\n")
	// Pass the user input as function argument
	moo(n);
}

void moo(int n)
{
	for (int i = 0; i < n; i++)
	{
		printf("moooo!\n");
	}
}
```

**Notice** that in *line 9* there is an input variable :
- The input is used as argument for the function
- We also need to declare inside of the function above in *line 5* and below in *line 14* the input.
- ==We can change the argument name on both line 5 and 14 and the code will work the same.
 ==
<mark style="background: #BBFABBA6;">Same as:</mark>
```c
#include <stdio.h>
#include <cs50.h>

// Signature moo function
void moo(int mooTimes);

int main()
{
	int n = get_int("How many times?\n")
	// Pass the user input as function argument
	moo(n);
}

void moo(int mooTimes)
{
	for (int i = 0; i < mooTimes; i++)
	{
		printf("moooo!\n");
	}
}
```
###### Printing out a row of bricks : 2D matrix

```c
#include <stdio.h>
#include <cs50.h>

//Create a 3x3 block of hashes
//Creating two loops
int main(void)
{
	//Outer loop - for each row
	for (int i = 0; i < 3; i++)
	{
	//inner loop - for each column
		for (int j = 0; j < 3; j++)
		{
		printf("#");
		}
	printf("\n");
	}
}
```

###### How to improve better code design?
- Use a **constant** for a value that you know won-t change.
- Do not use hard coded numbers like 3

```c
#include <stdio.h>
#include <cs50.h>

//Create a 3x3 block of hashes
//Creating two loops
int main(void)
{
	//Define a constant value
	const int n = 3
	//Outer loop - for each row
	for (int i = 0; i < n; i++)
	{
	//inner loop - for each column
		for (int j = 0; j < n; j++)
		{
		printf("#");
		}
	printf("\n");
	}
}
```
- line 9 defines constant
	- line 11 and 14 use constant

---
###### Integer overflow:
It's a situation where a variable type has a specific memory size (bit allocation) and it exceeds its allocation ,which is called  **overflow**.

*Exercise* : Make a calculator in C
 