# **`cd`**
---
* `cd` with no input from the directory `/home/lecture1` brings me back to the `home` directory
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~/]$
```
* `cd` with a path to a folder from the `home` directory results in entering the pathway specified, in this case into `/home/lecture1`
```
[user@sahara ~]$ cd lecturel/
[user@sahara ~/lecture1]$
```
* `cd` with a path to a file from the `/home/lecture1/messages` directory results in an error, as you can't cd into non directories
```
[user@sahara ~/lecture1]$ cd messages/
[user@sahara ~/lecturel/messages]$ cd en-us.txt
bash: cd: en-us.txt: Not a directory
```

# **`ls`**
---
* `ls` from the `/home` directory with no input shows me the currently viewable directories or files, in this case `lecture1` is available
```
[user@sahara ~]$ ls
lecture1
```
* `ls` from the `/home` directory with a path to a directory results in viewing the available directories and files within the path, in this case, the files and directories within `/home/lecture1`
```
[user@sahara ~]$ ls lecturel
Hello.class Hello.java messages README
```
* `ls` from the `/home` directory with a path to a file result in the path it is found in; in this case, the `en-us.txt` file has the path `/lecture1/messages/en-us.txt` from `/home`
```
[user@sahara ~]$ ls lecture1/messages/en-us.txt
lecture1/messages/en-us.txt
```

# **`cat`**
---
* `cat` from the `/home` directory with no input results in a scenario where it begins reading from standard input, and outputs the result of concatenating, which is just the same text back
```
[user@sahara ~]$ cat
ben
ben
^C
```
* `cat` from the `/home` directory with a path to a directory results in an error as it can not concatenate a directory, in this case it attempts to concatenate `/lecture1`, which it can't do as there is no concatenatable data provided
```
[user@sahara ~]$ cat lecturel
cat: lecturel: Is a directory
```
* `cat` from the `/home` directory with a path to a file results in reading the file contents and displaying them
```
[user@sahara ~]$ cat lecturel/messages/en-us.txt
Hello World!
```
