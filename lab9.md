
# **`LAB 9`**
# **`Part 1`**
# **PseudoStudent Issue**
"Hi, I'm having some difficulty with my code. It looks like my JUnit is not running, and I'm getting '..'. I keep using control+c to exit out of it but I'm not sure what is causing the issue. I attached my code and tests below. I think something in my code is causing it to loop forever but I'm unable to find where."  
![Image](/images/Lab9FailedCode.png) 
![Image](/images/Lab9FailedTester.png) 
# **PseudoTA Response**
"Hey, if you let the '..' run, it will give you an OutOfMemoryError. You are correct about the code looping forever, as that is one of the ways to cause such an error. I suggest you set a "(timeout = 500)" next to @Test so it doesn't run forever. As for the issues with your code, is there a way you could get the iterators to show up every loops so that you could diagnose what condition isn't being met?" It may be easier to diagnose issues occurring in your code if you can see what is happening each iteration."
# **PsuedoStudent Result**
Information after Implementation:
![Image](/images/Lab9FixingCode.png) 
![Image](/images/Lab9FixTester.png) 
The bug is caused by the index1 at the last while loop, as it isn't iterating index2, so the last while loop, if triggered, would never meet a condition where it ends. This causes the OutOfMemoryError, and is clearly seen in the print statements, as we see index1 is iterated to absurd numbers in the index2 while loop.
![Image](/images/Lab9Solution.png) 
# **Information Needed:**
*The tree at the time of the issue looks like this:*  
LAB7  
--lib  
----hamcrest-core-1.3.jar  
----junit-4.13.2.jar  
--.gitignore  
--ListExamples.class  
--ListExamples.java  
--ListExamplesTests.class  
--ListExamplesTests.java  
--StringChecker.class  
--test.sh  
  
*.class files can be obtained from running `bash test.sh`
*Content of Pre-fix ListExamples.java*
```java
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
	    if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }
}
```
*Content of Pre-fix ListExamplesTest.java*
```java
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
	@Test
	public void testMerge1() {
    	List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
		assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
	}
	
	@Test
        public void testMerge2() {
		List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
		assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
        }
}
```
*Content of Pre and Post-fix test.sh
```sh
javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ListExamplesTests
```
* Commands ran to trigger the bug:  
`bash test.sh`
* What to edit to fix the bug:  
Line 43 of `ListExamples.java` contains the wrong `index1`, which should be `index2`. Changing this fixes the bug.


# **`Part 2`**
I actually didn't know jdb was a thing. I assumed all debugging took place on javac for java. Knowing that jdb is an available tool makes my debugging more versatile, and I will enjoy knowing more about a bug and where it occurs. Javac sort of doesn't give many explicit indicators of what is going wrong, but knowing what inputs and variable values are during the time of a bug or issue is really helpful to me.
