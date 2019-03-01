## mixStart.java - Method

```java
// mixStart.java
public boolean mixStart(String str) {
  if (str.length() < 3) return false;
  return str.substring(1, 3).equals("ix");
}
```

**Purpose**
<br>This method is used to determine if a `String` contains "ix" directly after the first character.

**Method parameters**
<br>The string to use as the subject &mdash; `str` as `String`

**Return value**
```java
mixStart("mix snacks") → true
mixStart("pix snacks") → true
mixStart("piz snacks") → false
```
