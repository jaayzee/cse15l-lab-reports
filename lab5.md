
# **`LAB 5`**
# **`PART 1`**
* I have chosen the LinkedListExample.java Bug
# **Failure Inducing Test**
---
```Java
@Test 
public void testAppend() {
      list.append(3);
      list.append(2);
      list.append(1);
      list.append(0);
      assertEquals(list.root.value, 3);
      assertEquals(list.root.next.next.next.value, 0);
}
```
* This test prevents the completion of the entire test file, therefore something must be causing it to loop indefinitely.

# **Non-Failure Inducing Test**
---
```Java
@Test 
public void testAppend() {
  list.append(3);
  list.append(2);
  assertEquals(list.root.value, 3);
  assertEquals(list.root.next.value, 2);
}
```
* This test completes the test file, as well as passes with zero complications.


# **The Symptom**
---
* Failure Test  
![Image](/images/Failure.png)
* This showcases that the test is prevented from completing, as something within the `@Test` is looping to no end  
* Non-Failure Test  
![Image](/images/NonFailure.png)


# **The Bug**
---
`BEFORE`
```Java
public void append(int value) {
  if(this.root == null) {
      this.root = new Node(value, null);
      return;
  }
  // If it's just one element, add if after that one
  Node n = this.root;
  if(n.next == null) {
      n.next = new Node(value, null);
      return;
  }
  // Otherwise, loop until the end and add at the end with a null
  while(n.next != null) {
      n = n.next;
      n.next = new Node(value, null);
  }
}
```
`AFTER`
```Java
public void append(int value) {
  if(this.root == null) {
      this.root = new Node(value, null);
      return;
  }
  // If it's just one element, add if after that one
  Node n = this.root;
  if(n.next == null) {
      n.next = new Node(value, null);
      return;
  }
  // Otherwise, loop until the end and add at the end with a null
  while(n.next != null) {
      // EDITTED SECTION
      n = n.next;
  }
  n.next = new Node(value, null);
}
```
* Moving the `n.next = new Node(value, null);` fixes the never ending loop, as the while loop NOW looks for the first instance of a Node being null, rather than what it was doing before;
incrementing over each node after the root and assigning the next node to be null, which would self-fulfill the next loop of the while loop, thus looping forever. The Non-Failure test was that way because in the case of only 2 Nodes, it does it properly, but with the usage of the while loop, the function breaks.

# **`PART 2`**
`find -type`
```
jozo2@zhou MINGW64 ~/docsearch (main)
$ find technical/ -type d
technical/
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos
```
* -type d is a commandline option that changes the listing of every file and directory in `technical/` to just directories in `technical/`. This is useful in the event that I am searching for a specific nested folder within folders.
```
jozo2@zhou MINGW64 ~/docsearch (main)
$ find technical/ -type f | less
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-2.txt
technical/911report/chapter-3.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-8.txt
technical/911report/chapter-9.txt
technical/911report/preface.txt
technical/biomed/1468-6708-3-1.txt
technical/biomed/1468-6708-3-10.txt
technical/biomed/1468-6708-3-3.txt
technical/biomed/1468-6708-3-4.txt
technical/biomed/1468-6708-3-7.txt
technical/biomed/1471-2091-2-10.txt
technical/biomed/1471-2091-2-11.txt
technical/biomed/1471-2091-2-12.txt
technical/biomed/1471-2091-2-13.txt
technical/biomed/1471-2091-2-16.txt
technical/biomed/1471-2091-2-5.txt
technical/biomed/1471-2091-2-7.txt
technical/biomed/1471-2091-2-9.txt
technical/biomed/1471-2091-3-13.txt
technical/biomed/1471-2091-3-14.txt
technical/biomed/1471-2091-3-15.txt
technical/biomed/1471-2091-3-16.txt
technical/biomed/1471-2091-3-17.txt
technical/biomed/1471-2091-3-18.txt
technical/biomed/1471-2091-3-22.txt
technical/biomed/1471-2091-3-23.txt
:
```
* -type f is a commandline option that changes the listing of every file and directory in `technical/` to just files in `technical/`. This is useful in the event that I am searching for a specific nested file within folders. I used ` | less` as the total output of the number of files is humongous, and I didn't want to overtake my whole page, so this small snippet is only a TASTE.

`find -user`
```
jozo2@zhou MINGW64 ~/docsearch (main)
$ find technical/ -user jozo2 | less
technical/
technical/911report
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-2.txt
technical/911report/chapter-3.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-8.txt
technical/911report/chapter-9.txt
technical/911report/preface.txt
technical/biomed
technical/biomed/1468-6708-3-1.txt
technical/biomed/1468-6708-3-10.txt
technical/biomed/1468-6708-3-3.txt
technical/biomed/1468-6708-3-4.txt
technical/biomed/1468-6708-3-7.txt
technical/biomed/1471-2091-2-10.txt
technical/biomed/1471-2091-2-11.txt
technical/biomed/1471-2091-2-12.txt
technical/biomed/1471-2091-2-13.txt
technical/biomed/1471-2091-2-16.txt
technical/biomed/1471-2091-2-5.txt
technical/biomed/1471-2091-2-7.txt
technical/biomed/1471-2091-2-9.txt
technical/biomed/1471-2091-3-13.txt
technical/biomed/1471-2091-3-14.txt
technical/biomed/1471-2091-3-15.txt
technical/biomed/1471-2091-3-16.txt
technical/biomed/1471-2091-3-17.txt
```
* -user is a commandline option that changes the listing of every file and directory in `technical/` to files and directories owned by "user", in this case `jozo2` in `technical/`. This is useful in the event that I am searching a computer used by different users, and I want only the files/directories I worked on. I used ` | less` as the total output of the number of files is humongous, and I didn't want to overtake my whole page, so this small snippet is only a TASTE.
```
jozo2@zhou MINGW64 ~/docsearch (main)
$ find technical/911report/ -user jozo2
technical/911report/
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-2.txt
technical/911report/chapter-3.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-8.txt
technical/911report/chapter-9.txt
technical/911report/preface.txt
```
* Similarly to what I did above, this occurrence scours the `911report/` directory within `technical/` for directories and files owned by jozo2. This is again useful for differentiating my files and directories from another users. Had I assigned a different user (say `benie`)to `-user`, it would spit out `find: ‘benie’ is not the name of a known user`, as this computer has no other users.

`find -used`
```
$ find technical/911report/ -used -1
technical/911report/
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-2.txt
technical/911report/chapter-3.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-8.txt
technical/911report/chapter-9.txt
technical/911report/preface.txt
```
* -used is a commandline option that changes the listing of every file and directory in `technical/911report/` to files and directories accessed within the time frame specified, in this case `-1` would mean accessed less than a day ago. `+` would denote "more than", and no sign would denote "exactly". This is useful in the event that I am searching for files that were recently worked on, so that I may review them.  


```
jozo2@zhou MINGW64 ~/docsearch (main)
$ find technical/911report/ -used +3

```
  
* In this case, the `-used` commandline option would return nothing, as there are no files last accessed more than 3 days ago (`+3`), as I am making this markdown report the day I `git clone`d the repo.
  

`find -size`
  
```
$ find technical/ -size 117k
technical/911report/chapter-1.txt
```
  
* -size is a commandline option that changes the listing of every file and directory in `technical/` to files within a certain size, in this case `117k` would mean sized exactly at 117 kibibytes. `+` would denote "more than" `-` denotes "less than", and no sign would denote "exactly". This is useful if I know the size of certain files that I am searching for. In this case using the "exactly" version of the search.
  
```
jozo2@zhou MINGW64 ~/docsearch (main)
$ find technical/ -size +117k
technical/911report/chapter-12.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-3.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/biomed/1471-2105-3-2.txt
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/State_Planning_Report.txt
technical/government/Env_Prot_Agen/bill.txt
technical/government/Env_Prot_Agen/ctm4-10.txt
technical/government/Env_Prot_Agen/multi102902.txt
technical/government/Env_Prot_Agen/tech_adden.txt
technical/government/Gen_Account_Office/d01376g.txt
technical/government/Gen_Account_Office/d01591sp.txt
technical/government/Gen_Account_Office/d0269g.txt
technical/government/Gen_Account_Office/d02701.txt
technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
technical/government/Gen_Account_Office/im814.txt
technical/government/Gen_Account_Office/pe1019.txt
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
```
  
* In this case, I am searching for files sized above 117 kibibytes within the `technical/` directory. This is useful in the event that I am searching for files that are above a certain size, and causing my device's storage to be overly impacted.

# **`SOURCE`**
[Man7 Linux Find Options](https://man7.org/linux/man-pages/man1/find.1.html)
