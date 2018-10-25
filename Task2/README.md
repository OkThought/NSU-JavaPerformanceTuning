# Task 2
## Bytecode analysis
### Analize bytecode of following programs

##### `P1.java`
```java
package nsu.fit.javaperf.lab2;

public class P1 {
    public static void main(String[] args) {
        String s = "";
        for (int i = 0; i < 10000; ++i) {
            s += " " + String.valueOf(i);
        }
        System.out.println(s.length());
    }
}

```

##### `P2.java`
```java
package nsu.fit.javaperf.lab2;

public class P2 {
    public static void main(String[] args) {
        StringBuilder s = new StringBuilder();
        for (int i = 0; i < 10000; ++i) {
            s.append(" ").append(String.valueOf(i));
        }
        System.out.println(s.length());
    }
}
```

##### bytecode analysis of `P1`:

```java
package nsu.fit.javaperf.lab2;

public class P1 {
    public static void main(String[] args) {
        
        // 0: ldc           #2
        // 2: astore_1
        String s = "";
        
        // 3: iconst_0
        // 4: istore_2
        // 5: iload_2
        // 6: sipush        10000
        // 9: if_icmpge     29
        for (int i = 0; i < 10000; ++i) {
            
            // 12: aload_1
            // 13: iload_2
            // 14: invokestatic  #3
            // 17: invokedynamic #4,  0
            // 22: astore_1
            s += " " + String.valueOf(i);
            
            // 23: iinc          2, 1
            // 26: goto          5
        }
        // 29: getstatic     #5
        // 32: aload_1
        // 33: invokevirtual #6
        // 36: invokevirtual #7
        System.out.println(s.length());
        
        // 39: return
    }
}
```
##### bytecode analysis of `P2`:
```java
package nsu.fit.javaperf.lab2;

public class P2 {
    public static void main(String[] args) {
        // 0: new           #2
        // 3: dup
        // 4: invokespecial #3
        // 7: astore_1
        StringBuilder s = new StringBuilder();
        
        for (
                // 9: istore_2
                int i = 
                // 8: iconst_0
                0; 
                // 10: iload_2
                i 
                // 14: if_icmpge     37
                < 
                // 11: sipush        10000
                10000; 
                // 31: iinc          2, 1
                ++i
        ) {
            // 17: aload_1
            s
            // 20: invokevirtual #5
            .append(
                // 18: ldc           #4
                " "
            // 27: invokevirtual #5
            ).append(
                //24: invokestatic  #6
                String.valueOf(
                    // 23: iload_2
                    i
                )
            );
            // 30: pop
            // 34: goto          10
        }
        // 37: getstatic     #7
        System.out
        // 44: invokevirtual #9
        .println(
                // 40: aload_1
                s
                // 41: invokevirtual #8
                .length()
        );
    }
}
```
