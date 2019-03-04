## sumArray.java - Method

```java
// sumArray.java
public double sumArray(double[] nums) {
  double sum = 0;
  for (double i : nums)
    sum += i;
  return sum;
}
```

**Purpose**
<br>This method returns the sum of the values in a `double[]`

**Method parameters**
<br>Array of doubles to sum &mdash; `nums` as `double[]`

**Return value**
```
sumArray([1.0,2.5,3.2,6.3]) → 13.0
```
