## wordsCount.java - Method

```java
// wordsCount.java
public int wordsCount(String[] arr, int len) {
  int c = 0;
  for (String i : arr)
    if (i.length() == len)
      c++;
  return c;
}
```

**Purpose**
<br>This method is used to count the number of `String` objects in an array are of a specified length.

**Method parameters**
<br>The array to iterate through &mdash; `arr` as `String[]`
<br>The specified length to check for &mdash; `len` as `int`

**Return value**
```java
wordsCount(["a", "bb", "b", "ccc"], 1) → 2
wordsCount(["a", "bb", "b", "ccc"], 3) → 1
wordsCount(["a", "bb", "b", "ccc"], 4) → 0
```
