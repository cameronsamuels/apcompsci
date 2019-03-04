## arrayIncreasing.java - Method

```java
// arrayIncreasing.java
public boolean arrayIncreasing(int[] array) {
  for (int i = 1; i < array.length; i++)
    if (array[i] >= array[i-1]) continue;
    else return false;
  return true;
}
```

**Purpose**
<br>This method is used to determine if the values in an `int[]` array are increasing each index.

**Method parameters**
<br>The array to iterate through &mdash; `array` as `int[]`

**Return value**
```java
arrayIncreasing([1, 3, 4]) → true
arrayIncreasing([1, 3, 2]) → false
arrayIncreasing([1, 1, 4]) → true
```
