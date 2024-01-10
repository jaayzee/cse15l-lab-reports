# **cd**
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~/]$
```
> cd with no input brings me back to the root directory
```
[user@sahara ~]$ cd lecturel/
[user@sahara ~/lecture1]$
```
> cd with a path to a folder results in entering the pathway
```
[user@sahara ~/lecture1]$ cd messages/
[user@sahara ~/lecturel/messages]$ cd en-us.txt
bash: cd: en-us.txt: Not a directory
```
> cd with a path to a file results in an error, can't cd into non directories

# **ls**
```
[user@sahara ~]$ ls
lecture1
```
> ls with no input shows me the currently viewable directories or files
```
[user@sahara ~]$ ls lecturel
Hello.class Hello.java messages README
```
> ls with a path to a directory results in viewing the available directories and files when in the path
```
[user@sahara ~]$ ls lecture1/messages/en-us.txt
lecture1/messages/en-us.txt
```
> ls with a path to a file result in the path it is found in

# **cat**
```
[user@sahara ~]$ cat
^C
```
> cat with no input results in a scenario where it begins reading from standard input
```
[user@sahara ~]$ cat lecturel
cat: lecturel: Is a directory
```
> cat with a path to a directory results in an error as it can not concatenate a directory
```
[user@sahara ~]$ cat lecturel/messages/en-us.txt
Hello World!
```
> cat with a path to a file results in reading the file contents and displaying them
