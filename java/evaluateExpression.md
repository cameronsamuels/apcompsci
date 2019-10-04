## evaluateExpression.java - Method

```java
public static double evaluateExpression(String x) {

  String[] arr = x.split(" ");
  ArrayList<String> list = new ArrayList<String>();
  for (String i : arr)
    list.add(i);
  
  for (int i = 0; i < 2; i++) {
    for (int j = 0; j < list.size(); j++) {
      String k = list.get(j);
      if (k.equals(i == 0 ? "*" : "+") || k.equals(i == 0 ? "/" : "-")) {
        double a = Double.parseDouble(list.get(j - 1));
        double b = Double.parseDouble(list.get(j + 1));
        if (i == 0) list.set(j, "" + (k.equals("*") ? a * b : a / b));
        else list.set(j, "" + (k.equals("+") ? a + b : a - b));
        list.remove(j + 1);
        list.remove(j - 1);
        j = 0;
      }
    }
  }

  return Double.parseDouble(list.get(0));
  
}
```

**Purpose**
<br>This method is used to evaluate a mathematical expression and return a `double` value.

**Method parameters**
<br>The expression to solve — `x` as `String`

**Return value**
```java
evaluateExpression("5 + 9") → 14.0
evaluateExpression("2 - 8") → -6.0
evaluateExpression("12 * -4") → -36.0
evaluateExpression("10 / 4") → 2.5
```
