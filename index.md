<h1>Lab Report 3</h1>
<h2>Part 1 Bugs</h2>
<h3>A failure-inducing input:</h3>
<br/>
```java
  @Test
  public void testReversed() {
    int[] input1 = {1,2,3,4,5};
    assertArrayEquals(new int[]{5,4,3,2,1}, ArrayExamples.reversed(input1));
  }
```
<p>The result is:</p>
![Image](failure_result.png)
<h3>An input that doesn't induce a failure:</h3>
```java
 @Test
  public void testReversed() {
    int[] input1 = {};
    assertArrayEquals(new int[]{}, ArrayExamples.reversed(input1));
  }
```
<p>The result is:</p>
![Image](failure_result.png)
<p>The symptom is:</p>
![Image](test_symptom.png)

<p>Code with bug:</p>
```java

  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  
```
<p>The code fix with switching newArray and arr, also the return changes to newArray:</p>

```java

  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length-1-i];
    }
    return newArray;
  }

```
<p>Success Test:</p>
![Image](test_success.png)
<h3>Describe why the fix addresses the issue:</h3>
The code before fix, inside the `for loop` the array `arr` is the one who changes. `newArray` is new created and it is empty. For every `i` the array `arr` is setting the value to `newArray` which are all 0s. After fixing the problem by switching their position, now `newArray` will store the integers in `arr` in a reverse order. At the end, I changed the `return arr` to `return newArray` to return the correct array result.
