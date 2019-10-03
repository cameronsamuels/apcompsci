## OddsAndEvens.java - Class

```java
import java.util.TreeSet;

public class OddsAndEvens {
	
	private TreeSet<Integer> odds;
	private TreeSet<Integer> evens;
	private TreeSet<Integer> perfect;
	
	public OddsAndEvens(TreeSet<Integer> set) {
		
		odds = new TreeSet<Integer>();
		evens = new TreeSet<Integer>();
		perfect = new TreeSet<Integer>();
		
		// Separate odds and evens
		for (int i : set)
			if (i % 2 == 0) evens.add(i);
			else odds.add(i);
		
		// Determine perfect numbers
		for (int i : set) {
			TreeSet<Integer> divisors = new TreeSet<Integer>();
			
			for (int j = 1; j < i; j++)
				if (i % j == 0)
					divisors.add(j);
			
			int sum = 0;
			for (int j : divisors)
				sum += j;
			
			if (i == sum)
				perfect.add(i);
		}
			
	}
	
	public TreeSet<Integer> getOdds() { return odds; }
	public TreeSet<Integer> getEvens() { return evens; }
	public TreeSet<Integer> getPerfect() { return perfect; }
	
}
```

**Purpose**
<br>Each instance of `OddsAndEvens` stores three `TreeSet` references of a single `TreeSet` separated into odds and even numbers, and perfect numbers.
