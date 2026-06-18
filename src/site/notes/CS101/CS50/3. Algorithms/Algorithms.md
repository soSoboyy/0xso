---
{"dg-publish":true,"permalink":"/cs-101/cs-50/3-algorithms/algorithms/","dg-note-properties":{}}
---

*A code is a representation of an algorithm.*
Exercises in the CS50 codespace, folder lec3algo
![Attachments/Pasted image 20260512135447.png](/img/user/CS101/CS50/3.%20Algorithms/Attachments/Pasted%20image%2020260512135447.png)
X-axis = Problem size
Y-axis = Time to computer
###### Time complexity:
- Usually for time-complexity analysis in algorithm performance , the upper bound of is denoted with big O
- The lower bound denoted by omega symbol
![Attachments/Pasted image 20260613135339.png](/img/user/CS101/CS50/3.%20Algorithms/Attachments/Pasted%20image%2020260613135339.png)
Big O notation (Big O of something)
Time main concept here is to understand how much time a program consumes while it grows:
- O(n)
	- Linear search algorithm: The steps taken depends of the size of N 
	- Best case scenario , it takes only 1 step 
- O(log n)
	- Binary search : As N gets large, binary search is much faster. ==Assuming the numbers are sorted, It divides N by half over and over again.== (Because the logic is based on searching for greater than OR lower than)
	- Still best case scenario it takes only one step, after dividing
- O(n^2)
- O(1)
-  



---
###### Linear Search:
Searching from left to right OR from right to left in an array.

Example of linear search implementation with numbers:
`linearSearch.c`

```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	// Create an array of numbers
	
	int numbers[] = {1,20,30,6,50,10,230,100,500,25};
	int n = get_int("Number: ");
	
	for (int i = 0; i < 10; i++)
	{
	if (n == numbers[i])
	{	
		printf("number found\n");
		return 0;
	}
	
	}
	printf("not found\n");
	return 1;
}
```

Example of linear search implementation with strings:
- Using string compare function `strcmp`
- strcmp takes 2 arguments
- t returns 0 if found
- returns positive or negative number if not found

`betterLinearSearch.`

```c
#include <stdio.h>
#include <cs50.h>
int main(void)
{
	// Create an array of strings
    string strings[] ={"cat","dog","penguin","iron","cannon","boot"};
    string s = get_string("What are you looking for? \n");

    for (int i = 0; i < 6; i++){
        // Using string compare from the string library
        // strcmp takes 2 arguments
        // it returns 0 if found
        // returns positive or negative number if not found
        if (strcmp(strings[i],s) == 0)
        {
            printf("Found!\n");
            return 1;
        }
    }
    printf("not found...\n");
}
```

###### Data types:
==Define a new data type that is a data structure with keywords== : `typedef struct`
- Define inside the curly brackets the data types to link
- define outside the curly brackets the structure name
```c
typedef struct
{
	string name;
	string age;
}
person;
```
- Then create a new array with a defined length that will  have two data types *under the person structure*:
```c
#include <stdio.h>
#include <cs50.h>
typedef struct
{
	string name;
	string age;
}
person;

int main(void)
{
	person people[3]
}
```
We define an array of people with the relative name and numbers:
```c
#include <stdio.h>
#include <cs50.h>
typedef struct
{
	string name;
	string age;
}
person;

int main(void)
{
	person people[3]
	
	people[0].name = "David";
	people[0].number = "20";
	
	people[1].name = "Luca";
	people[1].number = "22";
	
	people[2].name = "Sara";
	people[2].number = "18";
}
```
Implement the search algorithm:
- include `string.h` library
- compare `people[i].names` to `name`
- Return the relative age from `people[i].age`

```c
#include <stdio.h>
#include <cs50.h>
#inlcude <string.h>

typedef struct
{
	string names;
	string age;
}
person;

int main(void)
{
	person people[3]
	
	people[0].names = "David";
	people[0].number = "20";
	
	people[1].names = "Luca";
	people[1].number = "22";
	
	people[2].names = "Sara";
	people[2].number = "18";
	
	string name = get_string("Name: ");
	
    for (int i = 0; i < 3; i++)
    {
        if (strcmp(people[i].names, name) == 0)
        {
            printf("%s\n", people[i].age);
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```

---
###### Binary Search: 
Binary search is a highly efficient algorithm used to find a specific item in a **sorted list** by repeatedly dividing the search space in half.

- Binary search requires sorted data:
	- selection sort
	- bubble sort
- At the beginning we start by sorting the array of numbers

![Attachments/Pasted image 20260614113659.png](/img/user/CS101/CS50/3.%20Algorithms/Attachments/Pasted%20image%2020260614113659.png)

<mark style="background: #FF5582A6;">Check sorting algorithms visually</mark> [here](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html)

<mark style="background: #BBFABBA6;">pseudocode for a selection sort</mark>
O(n^2)
```
For i from n to n-1 
	find smallest number between numbers[i] and numbers[n-1]
	swap smallest number with numbers[i]
```

<mark style="background: #BBFABBA6;">pseudocode for a bubble sort</mark>
O(n^2)
```
reperat n times
	for i from 0 to n-2
		if numbers[i] and numbers[i+1] out of order
			swap them
	if no swaps
	quit
```
- it's comparing to n-2 because there is an operation that checks numbers[i+1]
- *If it was n-1 as before* , when checking the last element n-1 , the operation [i+1] won't have anything to compare it to.
- Visual explanation [here](https://www.youtube.com/watch?v=Q7yOw50KNpI)



---
###### Recursion:
It's a function that call's itself
- Uses base cases that responds to a simple conditional *yes* or *no*
- code in codespace called `iterationRecursion.c`
- **When a function is called, that function call is put on a specific area of memory called a stack using a stack frame. Every time you call that same function new stack frame is created and they stack on top of each other, meaning these function calls are independent. Once the function returns a value, or it executes it's every line, it "returns" back to where it was called and its stack frame gets popped out of the stack. You don't need to know the specifics but realize that same function call if called multiple times, gets their own stack frame.**

- The 5 steps to implement recursion:
	1. Find the simplest case (base case)
	2. Play around with examples and visualize. 
	3. Relate the harder cases to the simpler cases. 
	4. Generalize pattern. 
	5. Combine recursive pattern with base case using code.

- Visual explanation [here](https://www.youtube.com/watch?v=DUC1qg7ZaRg)

```c
#include <stdio.h>
#include <cs50.h>

//declare function prototype
void draw(int n);

int main(void)
{
    int h = get_int("Height: ");
    draw(h) ;
}

/*
Recursion implementation
*/
void draw(int n)
{
    //Base case
    if(n <= 0)
    {
        return;
    }
    draw(n-1);
    for (int i = 0; i < n; i++)
    {
        printf("#");
    }
    printf("\n");
}
```

Similar to: ![Attachments/Pasted image 20260614210705.png](/img/user/CS101/CS50/3.%20Algorithms/Attachments/Pasted%20image%2020260614210705.png)

--- 
###### Merge sort:
Faster than selection sort and bubble sort. Psuedocode:
```text
if only one number
	quit
else
	sort left half of the numbers
	sort right half of the numbers
	merge the sorted halves
```

step 1:sort the left half
[6,3,4,1,5,2,7,0]
![Attachments/Pasted image 20260615184013.png](/img/user/CS101/CS50/3.%20Algorithms/Attachments/Pasted%20image%2020260615184013.png)
step merge them:
![Attachments/Pasted image 20260615184522.png](/img/user/CS101/CS50/3.%20Algorithms/Attachments/Pasted%20image%2020260615184522.png)
