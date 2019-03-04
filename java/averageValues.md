## averageValues.java - Method

```java
// averageValues.java
public static double averageValues(double[] nums) {
  double sum = 0;
  for (double i : nums) sum += i;
  return sum / nums.length;
}
```

**Purpose**
<br>This method returns the average of the doubles given

**Method parameters**
<br>Numbers to find the average of &mdash; `nums` as `double[]`

**Return value**
```java
averageValues([2, 2, 4, 4]) → 3
averageValues([1, 2, 3]) → 2
averageValues([2, 5, 5, 8]) → 5
```
