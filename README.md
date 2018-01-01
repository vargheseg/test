##### Project Structure:

```
       +--------+
    +->+main.cpp+<-+
    |  +--------+  |
    |              |
    |              |
    |              |
  +----+        +----+
  |ModA|        |ModB|
  +----+        +----+
    ^              ^
    |              |
    |    +----+    |
    +----+ModC+----+
         +----+

ModA <- ModC: Module A
   depends on ModC
```
