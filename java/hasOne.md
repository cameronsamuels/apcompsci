## hasOne.java - Method

```java
// hasOne.java
public boolean hasOne(int n) {
  String s = Integer.toString(n);
  return s.contains("1");
}
```

**Purpose**
<br>This method is used to determine if an `int` has a "1" digit.

**Method parameters**
<br>The integer for the subject &mdash; `n` as `int`

**Return value**
```java
hasOne(10) → true
hasOne(22) → false
hasOne(220) → false
```
