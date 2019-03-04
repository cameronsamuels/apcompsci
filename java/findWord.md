## findWord.java - Method

```java
// findWord.java
public static int findWord(String[] words, String word) {
  for (int i = 0; i < words.length; i++)
    if (words[i].equals(word)) return i;
  return -1;
}
```

**Purpose**
<br>This method returns the index of a given word in a given array, or -1 if the word is not found

**Method parameters**
<br>The words to look through &mdash; `words` as `String[]`
<br>The word to look for &mdash; `word` as `String`

**Return value**
```
findWord(["Hello", "World", "!!"], "World") → 1
```
