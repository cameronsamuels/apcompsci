## UnionDiffInter.java - Class

```java
import java.util.TreeSet;

public class UnionDiffInter {
	
	private TreeSet<Integer> x1;
	private TreeSet<Integer> x2;
	
	public UnionDiffInter(TreeSet<Integer> one, TreeSet<Integer> two) {
		x1 = one;
		x2 = two;
	}
	
	public TreeSet<Integer> union() {
		TreeSet<Integer> y = new TreeSet<Integer>();
		y.addAll(x1);
		y.addAll(x2);
		return y;
	}
	
	public TreeSet<Integer> intersection() {
		TreeSet<Integer> y = new TreeSet<Integer>();
		y.addAll(x1);
		y.retainAll(x2);
		return y;
	}
	
	public TreeSet<Integer> differenceAB() {
		TreeSet<Integer> y = new TreeSet<Integer>();
		y.addAll(x1);
		y.removeAll(x2);
		return y;
	}
	
	public TreeSet<Integer> differenceBA() {
		TreeSet<Integer> y = new TreeSet<Integer>();
		y.addAll(x2);
		y.removeAll(x1);
		return y;
	}
	
	public TreeSet<Integer> symmetricDifference() {
		TreeSet<Integer> y = new TreeSet<Integer>();
		y.addAll(x1);
		y.removeAll(x2);
		TreeSet<Integer> z = new TreeSet<Integer>();
		z.addAll(x2);
		z.removeAll(x1);
		y.addAll(z);
		return y;
	}
	
}
```

**Purpose**
<br>Each instance of `UnionDiffInter` stores two `TreeSet` references and allows for union, intersection, and difference operations to be performed upon them.
