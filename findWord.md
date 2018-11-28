## findWord.java - Method

```java
// findWord.java
public static int findWord(String[] words, String word) {
  for (int i = 0; i < words.length; i++)
    if (words[i].equals(word)) return i;
  return -1;
}
```

**Method parameters**
<br>The words to look through &mdash; `words` as `String[]`
<br>The word to look for &mdash; `word` as `String`

**Return value**
<br>With parameters `words = new String[]{"Hello","World","!!"}; word = "World"`
```
1
```
