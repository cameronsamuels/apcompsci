## replaceInMatrix.java - Method

```java
// replaceInMatrix.java
public static int[][] replaceInMatrix(int[][] matrix, int a, int b) {
  for (int i = 0; i < matrix.length; i++)
    for (int j = 0; j < matrix[i].length; j++)
      if (matrix[i][j] == a) matrix[i][j] = b;
  return matrix;
}
```

**Purpose**
<br>This method returns a given matrix after replacing the occurences of a given value with another given value.

**Method parameters**
<br>The matrix &mdash; `matrix` as `int[][]`
<br>The value to replace &mdash; `a` as `int`
<br>The value that the replaced values will be &mdash; `b` as `int`

**Return value**
```
replaceInMatrix([[5,4,4,5], [3,4,6,8], [4,4,6,4]]) → [[5,0,0,5], [3,0,6,8], [0,0,6,0]]
```
