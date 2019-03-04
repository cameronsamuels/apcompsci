## MrPresident.java - Program

```java
import java.util.*;
public class MrPresident {
  public static String[] presidents = new String[]{"George Washington","John Adams","Thomas Jefferson","James Madison",
    "James Monroe","John Quincy Adams","Andrew Jackson","Martin van Buren","William Henry Harrison","John Tyler",
    "James Polk","Zachary Taylor","Millard Fillmore","Franklin Pierce","James Buchanan","Abraham Lincoln","Andrew Johnson",
    "Ulysses S. Grant","Rutherford B. Hayes","James Garfield","Chester Arthur","Grover Cleveland","Benjamin Harrison",
    "Grover Cleveland","William McKinley","Theodore Roosevelt","William Taft","Woodrow Wilson","Warren Harding",
    "Calvin Coolidge","Herbert Hoover","Franklin Delano Roosevelt","Harry S. Truman","Dwight Eisenhower","John F. Kennedy",
    "Lyndon Johnson","Richard Nixon","Gerald Ford","Jimmy Carter","Ronald Reagan","George H.W. Bush","Bill Clinton",
    "George W. Bush","Barack Obama","Not My President"};
  public static String[] dates = new String[]{"1789-1797","1797-1801","1801-1809","1809-1817","1817-1825","1825-1829",
    "1829-1837","1837-1841","1841-1841","1841-1845","1845-1849","1849-1850","1850-1853","1853-1857","1857-1861","1861-1865",
    "1865-1869","1869-1877","1877-1881","1881-1881","1881-1885","1885-1889","1889-1893","1893-1897","1897-1901","1901-1909",
    "1909-1913","1913-1921","1921-1923","1923-1929","1929-1933","1933-1945","1945-1953","1953-1961","1961-1963","1963-1969",
    "1969-1974","1974-1977","1977-1981","1981-1989","1989-1993","1993-2001","2001-2009","2009-2017","2017-Present"};

  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    while (true) {
      System.out.print("Enter a number between 1 and 44: ");
      int i = scanner.nextInt();
      if (i == 0)
        break;
      if (i < 1 || i > 45)
        System.out.println("Invalid choice");
      else
        System.out.println(presidents[i - 1] + "; " + dates[i - 1]);
    }
  }
}
```

**Purpose**
<br>This program prompts for a number and prints out the name and years served of the corresponding POTUS.
