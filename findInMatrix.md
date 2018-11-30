## findInMatrix.java - Method

```java
// findInMatrix.java
public static int findInMatrix(String[][] matrix, String str) {
  int count = 0;
  for (String[] i : matrix)
    for (String j : i)
      if (j.equals(str)) count++;
  return count;
}
```

**Purpose**
<br>This method returns the number of occurences of a string in a `String[]` matrix.

**Method parameters**
<br>The matrix to search through &mdash; `matrix` as `String[][]`
<br>The string to search for &mdash; `str` as `String`

**Return value**
<br>With parameters `matrix = {{"Hello","World"},{"Hello","Earth"},{"Hello","World"}}; str = "World"`
```
2
```
