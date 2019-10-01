## SpiralMatrix.java - Class

```java
public class SpiralMatrix {
  
  int[][] mat;
  
  public SpiralMatrix(int num) {
    mat = new int[num][num];
    int r = 0, c = 0, z = num - 1; //row, column, depth
    char d = 'D'; //direction
    
    for (int i = 1; i <= num * num; i++) {
      mat[r][c] = i;
      
      if (d == 'D') {
        if (++r == z) d = 'R';
      }
      else if (d == 'R') {
        if (++c == z) d = 'U';
      }
      else if (d == 'U') {
        if (--r == num - z - 1) {
          d = 'L';
          z--;
        }
      }
      else if (d == 'L') {
        if (--c == num - z - 1) d = 'D';
      }
    }
  }
  
  public int[][] getMatrix() {
    return mat;
  }
  
}
```

**Purpose**
<br>Each instance of `SpiralMatrix` stores a matrix reference with incremental values starting from 1 arranged in a counterclockwise spiral.
