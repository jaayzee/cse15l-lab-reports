
# **`LAB 5`**
* I have chosen the LinkedListExample.java Bug
# **`Failure Inducing Test`**
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

# **`Non-Failure Inducing Test`**
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


# **`The Symptom`**
---
* Failure Test
  ![Image](/images/Failure.png)
* Non-Failure Test
* ![Image](/images/NonFailure.png)


# **`The Bug`**
