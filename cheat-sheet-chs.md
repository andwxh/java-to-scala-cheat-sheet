# Scala cheatsheet
## 变量定义
Java:
```java
int i = 1;
```
Scala:
```scala
var i = 1 // Scala有类型推，一般情况不需要显式声明类型
var i: Int = 1
```


## 只读变量定义
Java:
```java
final int i = 1;
```
Scala:
```scala
val i = 1 // 常用
```


## 判断相等
Java:
```java
int i = 1;
String s = "hey";

i == 1  // true
s.equals("hey")  // true
```
Scala:
```scala
val i = 1
val s = "hey"

i == 1  // true
s == "hey"  // true
```


## 数组操作
Java:
```java
String[] sa = new String[] {"a", "b", "c"};
System.out.println(sa[0]);  // Console output: a
sa[0] = "hello world";
System.out.println(sa[0]);  // Console output: hello world
```
Scala:
```scala
// Scala中的Array不再是特殊语法，而是普通的泛型类型，与List等语法上一致，[]符号留给泛型参数使用，访问数组成员使用()符号
val sa = Array("a", "b", "c")
println(sa(0))  // Console output: a
sa(0) = "hello world"
println(sa(0))  // Console output: hello world
```


## 函数定义
Java:
```java
int count(int l, int r) {
    return l + r
}
```
Scala:
```scala
def count(l: Int, r: Int) = l + r // Scala有类型推断，函数返回值可以不显式声明类型，参数受限于类型系统无法推断仍需要显式声明
```


## 类定义
Java:
```java
class SomeClass {
    int memberVariable;

    final int readonlyMember;

    String memberInitInConstructor;

    SomeClass(int mv, int rm) {
        memberVariable = mv;
        readonlyMember = rm;
        memberInitInConstructor = Integer.toString(mv) + Integer.toString(rm);
    }

    int count(int l, int r) {
        return l + r;
    }
}
```
Scala:
```scala
class SomeClass(memberVariable: Int, val readonlyMember: Int) {
    val memberInitInConstructor = memberVariable.toString + readonlyMember.toString

    def count(l: Int, r: Int) = l + r
}
```


## 接口定义
Java:
```java
interface SomeInterface {
    int getI();

    default int getIPlus() {
        return getI() + 1;
    }
}
```
Scala:
```scala
trait SomeTrait {
    def i: Int
    def getIPlus = i + 1
}
```


## 包含static成员的类定义
Java:
```java
class SomeClassWithStaticMember {
    public static int i = 1;
    public static int getIPuls() {
        return i + 1;
    }
}
```
Scala:
```scala
// Scala中没有static成员，应该使用单例对象
object SomeObject {
    val i = 1
    def getIPlus = i + 1
}
```


## 类继承
Java:
```java
class SomeClass extends BaseClass implement SomeInterface1, SomeInterface2 {
    ...
}
```
Scala:
```scala
class SomeClass extends BaseClass with SomeInterface1 with SomeInterface2 {
    ...
}
```


## getter / setter
Java:
```java
class SomeClass {
    private String si = "0";

    public int getI() {
        return Integer.parseInt(si);
    }

    public void setI(int i) {
        si = Integer.toString(i);
    }
}

SomeClass o = new SomeClass();
o.setI(123);
System.out.println(o.getI());  // console output: 123
```
Scala:
```scala
class SomeClass {
    private var si = "0"

    def i: Int = si.toInt

    def i_=(i: Int) = si = i.toString
}

val o = new SomeClass
o.i = 123
println(o.i)  // console output: 123
```


## 枚举类型
Java:
```java
enum EnumType {
    A(1), B(2), C(4);

    public final int i;
    EnumType(int i) {
        this.i = i;
    }
}
```
Scala:
```scala
trait SomeType {
    def i: Int
}

object A extends SomeType { val i = 1 }
object B extends SomeType { val i = 2 }
object C extends SomeType { val i = 4 }
```


## if语句
Java:
```java
if (条件) {
    语句
} else {
    语句
}
```
Scala:
```scala
// 没有变化
if (条件) {
    语句
} else {
    语句
}
```


## 三元布尔表达式
Java:
```java
(条件) ? 表达式 : 表达式
```
Scala:
```scala
// Scala的if语句本身带有返回值，因此可以直接替代三元布尔表达式使用
if (条件) 表达式 else 表达式
```


## while循环
Java:
```java
while(条件) {
    循环体
}
```
Scala:
```scala
// 没有变化
while(条件) {
    循环体
}
```


## for循环
Java:
```java
for(int i=0; i < 10; i++) {
    循环体
}
```
Scala:
```scala
// Scala中没有这种for循环，需要使用这种循环的情况会非常非常少见
var i = 0
while(i < 10) {
    循环体
    i++
}
```


## for each语法
Java:
```java
List<String> ls = Arrays.asList(new String[]{"abc"});
for(String s : ls) {
    循环体
}
```
Scala:
```scala
val ls = List("abc")
for(s <- ls) {
    循环体
}
```
