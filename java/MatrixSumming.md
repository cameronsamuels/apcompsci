## MatrixSumming.java - Class

```java
public class MatrixSumming {

    int[][] mat;

    public MatrixSumming(int[][] x) {
      mat = x;
    }

    public int sum(int x, int y) {
      int s = 0;
      s += mat[x][y];
      
      if (x > 0) // north
        s += mat[x - 1][y];
      if (x < mat.length - 1) // south
        s += mat[x + 1][y];
      if (y > 0) // west
        s += mat[x][y - 1];
      if (y < mat[x].length - 1) // east
        s += mat[x][y + 1];
      if (x > 0 && y > 0) // northwest
        s += mat[x - 1][y - 1];
      if (x > 0 && y < mat.length - 1) // northeast
        s += mat[x - 1][y + 1];
      if (x < mat.length - 1 && y > 0) // southwest
        s += mat[x + 1][y - 1];
      if (x < mat.length - 1 && y < mat.length - 1) // southeast
        s += mat[x + 1][y + 1];
        
      return s;
    }
    
}
```

**Purpose**
<br>Each instance of `MatrixSumming` stores an `int[][]` reference of a matrix. `public int sum()` returns the sum of the `(x, y)` value and its surrounding values.
