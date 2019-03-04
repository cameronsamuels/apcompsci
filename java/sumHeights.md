## sumHeights.java - Method

```java
// sumHeights.java
public int sumHeights(int[] heights, int start, int end) {
  int sum = 0;
  for (int i = start; i < end; i++)
    sum += Math.abs(heights[i] - heights[i + 1]);
  return sum;
}
```

**Purpose**
<br>This method is used to determine the sum of the changes (in absolute value) of a subsection in an array of integers

**Method parameters**
<br>The subject array &mdash; `heights` as `int[]`
<br>The start index &mdash; `start` as `int`
<br>The end endex &mdash; `end` as `int`

**Return value**
```java
sumHeights([5, 3, 6, 7, 2], 2, 4) → 6
sumHeights([5, 3, 6, 7, 2], 0, 1) → 2
sumHeights([5, 3, 6, 7, 2], 0, 4) → 11
```
