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

#### `P1.class` javap output
```
Compiled from "P1.java"
public class nsu.fit.javaperf.lab2.P1 {
  public nsu.fit.javaperf.lab2.P1();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: ldc           #2                  // String
       2: astore_1
       3: iconst_0
       4: istore_2
       5: iload_2
       6: sipush        10000
       9: if_icmpge     29
      12: aload_1
      13: iload_2
      14: invokestatic  #3                  // Method java/lang/String.valueOf:(I)Ljava/lang/String;
      17: invokedynamic #4,  0              // InvokeDynamic #0:makeConcatWithConstants:(Ljava/lang/String;Ljava/lang/String;)Ljava/lang/String;
      22: astore_1
      23: iinc          2, 1
      26: goto          5
      29: getstatic     #5                  // Field java/lang/System.out:Ljava/io/PrintStream;
      32: aload_1
      33: invokevirtual #6                  // Method java/lang/String.length:()I
      36: invokevirtual #7                  // Method java/io/PrintStream.println:(I)V
      39: return
}
```
#### `P2.class` javap output
```
Compiled from "P2.java"
public class nsu.fit.javaperf.lab2.P2 {
  public nsu.fit.javaperf.lab2.P2();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: new           #2                  // class java/lang/StringBuilder
       3: dup
       4: invokespecial #3                  // Method java/lang/StringBuilder."<init>":()V
       7: astore_1
       8: iconst_0
       9: istore_2
      10: iload_2
      11: sipush        10000
      14: if_icmpge     37
      17: aload_1
      18: ldc           #4                  // String
      20: invokevirtual #5                  // Method java/lang/StringBuilder.append:(Ljava/lang/String;)Ljava/lang/StringBuilder;
      23: iload_2
      24: invokestatic  #6                  // Method java/lang/String.valueOf:(I)Ljava/lang/String;
      27: invokevirtual #5                  // Method java/lang/StringBuilder.append:(Ljava/lang/String;)Ljava/lang/StringBuilder;
      30: pop
      31: iinc          2, 1
      34: goto          10
      37: getstatic     #7                  // Field java/lang/System.out:Ljava/io/PrintStream;
      40: aload_1
      41: invokevirtual #8                  // Method java/lang/StringBuilder.length:()I
      44: invokevirtual #9                  // Method java/io/PrintStream.println:(I)V
      47: return
}
```
