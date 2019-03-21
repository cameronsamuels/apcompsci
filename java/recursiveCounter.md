## recursiveCounter.java - Method

```java
// recursiveCounter.java
public static void recursiveCounter(int x) {
  new Scanner(System.in).nextLine();
  System.out.print(x);
  recursiveCounter(x + 1);
}
```

**Purpose**
<br>This method outputs `x` after the user presses the <kbd>enter</kbd> key, then calls itself with the parameter `x + 1`

**Method parameters**
<br>The number to output (the number to start counting at) &mdash; `x` as `int`
