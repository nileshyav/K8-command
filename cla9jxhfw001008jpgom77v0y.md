# Linux Cheat Sheet

## Working With Bash History command
**History command** 

```
history 

```
or you can use 
```
cat .bash_history
```
output will be like this


![MobaXterm screenshot.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667987476835/lYAO0DsDe.png align="left")

The number of commands that can be saved in bash history file is controlled by HISTFILESIZE. this is an env variable. 

```
echo $HISTFILESIZE
``` 

By default, $HISTFILESIZE size limit is 2000. it means 2000 command history can be saved in bash history file. 
BUT when you type history commands only 1000 command will be shown. because 2000 is the max limit of saved command in bash history file but 1000 command shown by history command because of memory limit which is on memory that is control by HISTSIZE.


```
echo $HISTSIZE
``` 

IF i want to run command from history which let's say command number is 17 then

```
!17
``` 
It will execute the last command
```
!!
```
it will execute the last ping command
```
!ping
```
confirm that you are running the correct command

```
!ping:p
```
CTRL + R
for search for command in bash history then select command that you want to execute


to delete command from history


```
history -d lineNumber
```
*Clear commands from entire bash history file*

```
history -c
```

Record the date and time for each command in the bash history file. 

```
HISTTIMEFORMAT="%d/%m/%y %T  "
```
it will looks like this

![MobaXterm screenshot.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1668021496287/UnEzHsTZ2.png align="left")

## Working with users

- **To create new user and change password**

```
sudo useradd one
sudo passwd one
```
- **Switch user** 
```
su one
 ```
```
sudo su : Login as root
```


- Log out from one user Press ```
CTRL + D
``` to exit 
> all users are shown as $ sign but root user is shown as # sign

- **Delete user**

```
sudo userdel userName
```
- **List all user command** ```cat /etc/passwd```


 ## Running the command without leaving trace
 
simply type commands after giving a space. This feature is controlled by ```
$HISTCONTROL
```   environment variable. 
type 
```
echo $HISTCONTROL
``` 
see if the value is ignoreboth but if the value is ignoredups. simply change the value to ignoreboth. ignoredups and ignorespace two option is present here.

```
HISTCONTROL=ignoreboth
```
after enabling ignoreboth, commands written after a space will not be saved in history.  and if you run multiple commands again and again then duplicates will be removed.

if you reboot or log out this setting will again be set to default. we can save this setting in bashrc file to save this setting.
```
echo "HISTCONTROL=ignoreboth" >> .bashrc
```


















