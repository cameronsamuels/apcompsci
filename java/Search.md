## Search.java - Program

```java
import java.util.*;
public class Search {
  public static int[] arr;
  public static void main(String[] args) {
    arr = new int[100];
    for (int i = 0; i < arr.length; i++)
      arr[i] = (int)(Math.random() * 50) + 1;
    
    Scanner scanner = new Scanner(System.in);
    System.out.print("Enter a value to search for: ");
    int index = findValue(scanner.nextInt());

    for (int i = 0; i < 10; i++) {
      for (int j = 0; j < 10; j++)
        System.out.print(arr[i * 10 + j] + ", ");
      System.out.println();
    }
    System.out.print("The first position of the number is " + index);
  }
  public static int findValue(int num) {
    for (int i = 0; i < arr.length; i++)
      if (arr[i] == num)
        return i;
    return -1;
  }
}
```

**Purpose**
<br>This program fills an `int[100]` with random numbers between 1 and 50,
then prompts for an `int` to search for, then prints the array and the first occurence of that `int`
