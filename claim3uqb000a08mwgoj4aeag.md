# Bash Scripting : 01

## What is Bash 
> The name is an acronym for the  Bourne-Again Shell. Bash is a command-line interface shell program used extensively in Linux and macOS. 

What's a shell?" you ask? A shell is a computer program that allows you to directly control a computer's operating system (OS) with a command-line interface (CLI).
- bash shell comes with .sh extension


### How to create

First, create a file with the extension ```.sh```

```
touch shell.sh
```
then to write something in file 
```
nano shell.sh
```
nano editor will open. write your command inside that file and save it with CTRL + O. for exit press CTRL + x 

Let's write these commands inside the file
```
#!/bin/bash
echo "Welcome $(pwd)"
mkdir name
cd name
```

This line ```#!/bin/bash
``` called  as Shebang

To run the ```
shell.sh
``` file, first give execute permission to file.
```
chmod +x shell.sh
``` 
then type ```
 ./shell.sh
``` to execute the file

### Variables in Bash

Only Letter, number, _ is used for defining variables

**Bash is CASE SENSITIVE**

Types of variables:

- Simple type variable

- Read-only variable

- unset variable

**Don't put space after the (= ) sign.


### IF block in bash

open your editor and write below code in ```demo.sh``` file.

*Ex. 1*
```
#!/bin/bash

read -p "Enter your Number : " number

if [ $number -gt 100 ]
then
        echo "Value is greater than 100 "
fi
```
run your code by ```
./demo.sh
``` Enter your number when prompted.

*Ex. 2*
```
#!/bin/bash

read -p "Enter your Number : " number

if [ $number -gt 100 ]
then
        echo "Value is greater than 100 "
fi

if [ "mylife" == "mylife" ] && [ 13 -gt 10 ]
then
        echo "Conditions are false"

```
*Ex. 3*
```

#!/bin/bash

#if [ 8 -gt 6 ] && [ 10 -eq 10 ]
#then
#echo "this is true"
#fi


if [ $1 -gt 50 ]
then
        echo " Number is greater than 100"

if (( $1 % 2 == 0 ))
then
        echo "and it is even number"
fi
fi

```

### Loops in Bash

```
#!/bin/bash

learn="Hello Nilesh welcome to devops pro course"

for learn in $learn
do

echo $learn
done
echo "loop is completed"
```
### print series of number in arange

```
#!/bin/bash

#learn="Hello Nilesh welcome to devops pro course"

for learn in {1..10}
do

echo $learn
done
echo "loop is completed"
```
### While Loop

```
#!/bin/bash

read -p "Enter starting numbe:r " snum
read -p "Enter ebdibg number: " enum

while [ $snum -le $enum  ]
do
echo $snum
((snum++))
done

echo "THis si hwat"
```
### Until Loop


```
#!/bin/bash

i=1
until [ $i -gt 10 ]
do
echo $i
((i++))
done
```
### Simple password generator

```
#!/bin/bash

echo "Welcome to simple password generator"

echo "Please enter the length of the password"

read PASS_LENGTH

for p in $(seq 1 5);
do
        openssl rand -base64 48 | cut -c1-$PASS_LENGTH
done
```
above code will generate 5 passwords of a given length.

That's it, for now, it is an ongoing learning series. will add more sections as i learn




























