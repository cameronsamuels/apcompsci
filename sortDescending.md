## sortDescending.java - Method

```java
// sortDescending.java
public static String[] sortDescending(String[] array) {
  Arrays.sort(array);
  String[] desc = new String[array.length];
  for (int i = 0; i < array.length; i++)
    desc[i] = array[array.length - i - 1];
  return desc;
}
```

**Method parameters**
<br>Array to sort &mdash; `array` as `String[]`

**Return value**
<br>With parameters `array = new String[]{"Hello","World","!!","hello","world"}`
```
{"world","hello","World","Hello","!!"}
```
