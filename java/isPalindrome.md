## isPalindrome.java - Method

```java
// isPalindrome.java
public boolean isPalindrome(ArrayList<String> list) {

  Queue<String> queue = new LinkedList<String>(list);
  Stack<String> stack = new Stack<String>();
  stack.addAll(list);

  while (queue.size() > 0)
    if (!stack.pop().equals(queue.remove()))
      return false;
  return true;

}
```

**Purpose**
<br>This method returns whether or not the given list is symmetrical.

**Return value**
```java
isPalindrome([1, 2, 2, 1]) → true
isPalindrome([2, 2, 4, 4]) → false
```
