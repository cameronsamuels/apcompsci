## countCode.java - Method

```java
// countCode.java
public int countCode(String str) {
  String[] x = str.split("");
  int c = 0;
  for (int i = 0; i < x.length - 3; i++)
    if ((x[i] + x[i + 1]).equals("co") && x[i + 3].equals("e"))
      c++;
  return c;
}
```

**Purpose**
<br>This method is used to determine how many occurences of "co-e" there are in a string (where "-" can be any character)

**Method parameters**
<br>The string to be used as the subject &mdash; `str` as `String`

**Return value**
```java
countCode("aaacodebbb") → 1
countCode("codexxcode") → 2
countCode("cozexxcope") → 2
```
