## JumpToIt.java - Program

```java
import java.util.*;

public class JumpToIt {
  public static char[][] mat;
  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    System.out.print("Enter the number of rows: ");
    int x = scanner.nextInt();
    System.out.print("Enter the number of columns: ");
    int y = scanner.nextInt();
    mat = createMatrix(x, y);

    for (int i = 0; i < 10; i++)
      moveTo(mat);
  }
  public static char[][] createMatrix(int x, int y) {
    return new char[x][y];
  }
  public static void moveTo(char[][] mat) {
    for (int i = 0; i < mat.length; i++)
      for (int j = 0; j < mat[i].length; j++)
        mat[i][j] = '\u0000';

    int x = (int)(Math.random() * mat.length);
    int y = (int)(Math.random() * mat[x].length);

    mat[x][y] = '@';
    display();
  }
  public static void display() {
    for (char[] i : mat) {
      for (char j : i) {
        if (j == '\u0000')
          System.out.printf("%3s", "-");
        else
          System.out.printf("%3s", j);
      }
      System.out.println();
    }
    System.out.println();
  }
}
```

**Purpose**
<br>This program prints 10 instances of a `char[][]` with an `'@'` in a random position every time.
