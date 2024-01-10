# **cd**
```
[user@sahara ~/lecture1]$ cd
[user@sahara ~]$ cd lecturel/
[user@sahara ~/lecture1]$ cd messages/
[user@sahara ~/lecturel/messages]$ cd en-us.txt
bash: cd: en-us.txt: Not a directory
```

# **ls**
```
[user@sahara ~]$ ls
lecture1
[user@sahara ~]$ ls lecturel
Hello.class Hello.java messages README
[user@sahara ~]$ ls lecture1/messages/en-us.txt
lecture1/messages/en-us.txt
```

# **cat**
```
[user@sahara ~]$ cat
^C
[user@sahara ~]$ cat lecturel
cat: lecturel: Is a directory
[user@sahara ~]$ cat lecturel/messages/en-us.txt
Hello World!
```
