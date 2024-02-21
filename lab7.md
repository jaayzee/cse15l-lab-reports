# **`LAB 7`**
# **Step 4**
I typed out `ssh jozhou@ieng6-201.ucsd.edu` in the terminal to access my remote machine  
![Image](/images/step4.png)  
# **Step 5**
I then ran `git clone` on my forked repository, which has an SSH created through the lab: `git clone git@github.com:jaayzee/lab7.git`.  
![Image](/images/step5.png)  
# **Step 6**
To access the files within the cloned repo, I used `cd lab7`  
To run the initial tests on the initial files, I used their built in `bash test.sh`, which I know contains the necessary two lines:  
"javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java"  
and  
"java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests".  
This initial implementation fails.  
![Image](/images/step6.png)  
# **Step 7**
I first used `vim ListExamples.java` to enter into the text editor for the file `ListExamples.java`  
![Image](/images/step7.1.png)  
My inputs are then:  
`?i`  
`<Enter>`  
Where `/` searches from the beginning of a file, `?` searches from the end, and knowing that it is the last "input1" that needs to be changed to "input2", I located it using `<Enter>`. Had it not been the very first item in the search, I would press `n` until I have found the correct one.  
![Image](/images/step7.2.png)  
Then, my inputs are:  
`e`  
`r2`  
`:wq`  
Where `e` brings us to the last character of a the word we are standing by in, we can then do `r` to replace the character being selected, and `2` to turn "input1" into "input2". With this necessary change, I can then `:wq` to save my changes to the file.  
![Image](/images/step7.3.png)  
# **Step 8**
I then run `bash test.sh` afterwards to test the new `ListExamples.java` file, to which the implementation passes.  
![Image](/images/step8.png)  
# **Step 9**
To add all my changes, whether it be adding new files or editting existing files, the parameter `.` in `git add` adds them all to the current commit  
`git add .`  
Then, to commit the work to the forked repository, I run `git commit` and then `-m` to specify the commit message, to which I set to "Update"  
`git commit -m "Update"`  
Once all commits are nice and tidy, I `git push` my changes to `origin`, or the main/master branch of the forked lab7 repository.  
git push origin  
![Image](/images/step9.png)
