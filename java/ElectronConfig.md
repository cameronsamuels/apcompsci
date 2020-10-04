## ElectronConfig.java - Class

```java
public class ElectronConfig {

    public static final String[] ORBITALS = {
        "1s","2s","2p","3s","3p","4s","3d","4p",
        "5s","4d","5p","6s","4f","5d","6p","7s","5f","6d","7p"
    };
    
    private int numElectrons;

    public ElectronConfig(int num) {
        setNumElectrons(num);
    }

    public int getNumElectrons() {
        return numElectrons;
    }

    public void setNumElectrons(int num) {
        numElectrons = num;
    }

    public String getConfiguration() {
        String config = "";
        int remaining = numElectrons;
        for (int i = 0; i < ORBITALS.length; i++) {
            String orb = ORBITALS[i];
            char subshell = orb.charAt(1);
            int max = subshell == 's' ? 2 : subshell == 'p' ? 6 : subshell == 'd' ? 10 : 14;
            if (remaining >= max) {
                config += orb + "(" + max + ") ";
                remaining -= max;
            }
            else if (remaining > 0) {
                config += orb + "(" + remaining + ") ";
                remaining = 0;
            }
            else break;
        }
        return config.trim();
    }

    public String toString() {
        return getConfiguration();
    }

}
```

# Electron Configuration

**Program Name: ElectronConfig.java**

**Input File: ElectronConfig.dat**

In Chemistry, the electron configuration of an atom or ion is written to describe how many electrons are present and in which orbitals. The configuration includes subshells denoted by a letter (s, p, d, f) in which the orbitals for each of these contain a maximum of 2, 6, 10, and 14 electrons respectively. For example, Neon has an electron configuration of "1s(2) 2s(2) 2p(6)" as it completely fills these orbitals and does not occupy other orbitals.

Given an array of the order of orbitals, complete the `ElectronConfig` class that receives an `int numElectrons` in the constructor and contains a method that returns the `String electronConfiguration`. Due to formatting restrictions, the superscript can be written in parentheses (e.g. "1s(2)").

**Input:** a list of `numElectrons` on individual lines.

**Output:** the electron configurations of each of these atoms on individual lines.

**Sample input:**
```
2
3
4
7
9
13
25
60
118
```

**Sample output:**
```
1s(2)
1s(2) 2s(1)
1s(2) 2s(2)
1s(2) 2s(2) 2p(3)
1s(2) 2s(2) 2p(5)
1s(2) 2s(2) 2p(6) 3s(2) 3p(1)
1s(2) 2s(2) 2p(6) 3s(2) 3p(6) 4s(2) 3d(5)
1s(2) 2s(2) 2p(6) 3s(2) 3p(6) 4s(2) 3d(10) 4p(6) 5s(2) 4d(10) 5p(6) 6s(2) 4f(4)
1s(2) 2s(2) 2p(6) 3s(2) 3p(6) 4s(2) 3d(10) 4p(6) 5s(2) 4d(10) 5p(6) 6s(2) 4f(14) 5d(10) 6p(6) 7s(2) 5f(14) 6d(10) 7p(6)
```
