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
<br>With parameters `nums = new double[]{3.0,4.0,4.5,5.0}`
```
4.125
```
