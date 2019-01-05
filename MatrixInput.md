## MatrixInput.java - Program

```java
import java.util.*;
public class MatrixInput
{
  public static void main(String[] args)
  {
    Scanner scanner = new Scanner(System.in);
    System.out.print("Enter the row size: ");
    int r = scanner.nextInt();
    System.out.print("Enter the column size: ");
    int[][] mat = new int[r][scanner.nextInt()];
    
    for (int i = 0; i < mat.length; i++)
      for (int j = 1; j <= mat[i].length; j++)
        mat[i][j - 1] = i * mat[i].length + j;
        
    for (int i = 0; i < mat.length; i++)
    {
      for (int j = 0; j < mat[i].length; j++)
        System.out.print(mat[i][j] + " ");
      System.out.println();
    }
  }
}
```

**Purpose**
<br>This program asks for dimensions to create an `int[][]` and fills it with numbers starting at 1.
