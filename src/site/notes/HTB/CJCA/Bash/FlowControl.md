---
{"dg-publish":true,"permalink":"/htb/cjca/bash/flow-control/","dg-note-properties":{}}
---

There is already a note [here](HTB/CJCA/Bash/Conditional&Operators) where I explained how if-else clauses control the flow of the script, which are also part of flow control.

##### Loops:
Loops are components that can increase efficiency and enable error-free processing. Each control structure is either a `branch` or a `loop`. Logical expressions of Boolean values usually control the execution of a control structure. These control structures include:
- Branches:
    - `If-Else` Conditions
    - `Case` Statements
- Loops:
    - `For` Loops
    - `While` Loops
    - `Until` Loops


##### For loops
The `for` loop is executed on each pass for precisely one parameter, which the shell takes from a list or from another data source. The for loop runs as long as it finds corresponding data. For example, ==for loops are often used when we need to iterate over many values in an array.== This can be used to scan different hosts or ports.

```bash
#!/bin/bash

for variable in 1 2 3 4
do
	echo $variable
done
```

```bash
#!/bin/bash
for variable in file1 file2 file3
do
	echo $variable
done
```

```bash
#!/bin/bash
for ip in "10.10.10.170 10.10.10.174 10.10.10.175"
do
	ping -c 1 $ip
done
```

==We can do the same thing in the shell:==
```shell
sosoBoy@htb[/htb]$ for ip in 10.10.10.170 10.10.10.174; do ping -c 1 $ip;done

PING 10.10.10.170 (10.10.10.170): 56 data bytes
64 bytes from 10.10.10.170: icmp_seq=0 ttl=63 time=42.106 ms

--- 10.10.10.170 ping statistics ---
1 packets transmitted, 1 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 42.106/42.106/42.106/0.000 ms
PING 10.10.10.174 (10.10.10.174): 56 data bytes
64 bytes from 10.10.10.174: icmp_seq=0 ttl=63 time=45.700 ms

--- 10.10.10.174 ping statistics ---
1 packets transmitted, 1 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 45.700/45.700/45.700/0.000 ms
```
(Check [here](HTB/CJCA/Protocols/ICMP) to revisit what #ttl and #hop are) 

---
##### while loops
The `while` loop follows the following principle:
- A statement is executed as long as a condition is fulfilled (`true`).
- A while loop needs some sort of a counter to orientate itself when it has to stop executing the commands it contains.
- we can also use the command "`break`," which interrupts the loop when reaching this command like in the following example:

```bash
#!/bin/bash
count=0

while [ $counter lt 10 ]
do
	#Increase counter by 1
	((counter++))
	echo "Counter: $counter"
	
	if [ $counter == 2 ]
	then
		continue
	elif [ $counter == 5 ]
	then
		break
	fi
done

```
Execution:
```shell
sosoBoy@htb[/htb]$ ./WhileBreaker.sh 
Counter: 1 
Counter: 2 
Counter: 3 
Counter: 4
Counter: 5
```

---

##### until loop
- The code inside a `until` loop is executed as long as the particular condition is `false`.

```bash
#!/bin/bash
count=0

until [ $counter -eq 10 ]
do
	#Increase counter by 1
	((counter++))
	echo "Counter: $counter"
done
```
Execution:
```shell
sosoBoy@htb[/htb]$ ./Until.sh
Counter: 1 
Counter: 2 
Counter: 3 
Counter: 4 
Counter: 5 
Counter: 6 
Counter: 7 
Counter: 8 
Counter: 9 
Counter: 10
```

Do exercise:
