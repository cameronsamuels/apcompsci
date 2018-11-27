## numberPyramid.java - Method

```java
// numberPyramid.java
public static void numberPyramid(int x) {
  for (int i = 1; i <= x; i++) {
    for (int j = 0; j <= x - i; j++)
      System.out.print(" ");
    for (int k = 0; k < i; k++)
      System.out.print(i);
    System.out.println();
  }
}
```

**Method parameters**
<br>Number of rows to produce &mdash; `x` as `int`

**Output**
<br>With parameters `x = 5`
```
    1
   22
  333
 4444
55555
```
