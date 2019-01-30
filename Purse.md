## Purse.java - Class

```java
public class Purse {
  
  private int nickels, dimes, quarters;
  
  public Purse() {
    nickels = 0;
    dimes = 0;
    quarters = 0;
  }
  
  public Purse(int n, int d, int q) {
    nickels = n;
    dimes = d;
    quarters = q;
  }
  
  public void addNickels(int a) { nickels += a; }
  public void addDimes(int a) { dimes += a; }
  public void addQuarters(int a) { quarters += a; }
  
  public int getNickels() { return nickels; }
  public int getDimes() { return dimes; }
  public int getQuarters() { return quarters; }
  
  public double getTotal() {
    double total = (nickels * .05) + (dimes * .1) + (quarters * .25);
    return total;
  }
  
}
```

**Purpose**
<br>The `Purse` object is meant to resemble a purse or wallet.
Each instance of a `Purse` can store nickels, dimes, and quarters, and allows calculatation of the value of the coins.
