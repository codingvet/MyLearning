# 内部类

##  静态内部类static inner class 

1. also called nested class

2. 权限修饰符static修饰的内部类

    ```java
    public class Outer{
        private static int a = 4;
        // 静态内部类
        public static class Inner{
            public void test(){
                // 静态内部类可以访问外部类的静态成员
                // 并且它只能访问静态的
                System.out.println(a);
            }
        }
    }
    ```

3. 静态代码中不能够使用this操作，所以在静态内部类中只可以访问外部类的静态变量和静态方法，包括了私有的静态成员和方法

4. 生成静态内部类对象的方法：

    -   Outer.Inner inner = new Outer.Inner();

5. 可以在静态内部类的方法中，亦只允许访问外部类的静态成员，不允许访问外部类的实例变量以及实例方法。

##  成员内部类member inner class

1.  定义在另一个类中，但不用static修饰

    -   可用的修饰符有：final、abstract、public、private、protected、strictfp

    ```java
    class Outer {
        class Inner{
    
        }
    }
    ```

2. 成员内部类依赖于外部类的实例存在

    -   在外部类中创建内部类的实例
        -   this.new Inner()
        -   Inner inner = new Inner
    -   在外部类之外创建内部类实例
        -   (new Outer()).new Inner()
        -   Inner inner = new Outer().new Inner()
        -   Outer outer = new Outer(); Inner inner = outer.new Inner()


3.  成员内部类可以访问它的外部类的所有成员变量和方法，不管是静态的还是非静态的都可以
    -   内部类引用外部类当前的对象
        -   outer.this*.method()*
4.  内部类对象中不能有静态成员
    -   内部类的实例对象是外部类实例对象的一个成员，若没有外部类对象，内部类就不会存在，何谈静态成员    

##  局部内部类local inner class

1.  方法内部类，定义在方法中，比方法的范围还小，是内部类中最少用到的一种类型
2.  像局部变量一样，不能被public, protected, private和static修饰
3.  只能在方法中使用，即只能在方法当中生成局部内部类的实例并且调用其方法

    -   一定是要先声明后使用，否则编译器会说找不到
4.  方法内部类的修饰符：只有final和abstract
5.  注意事项：
    -   方法内部类只能在定义该内部类的方法内实例化，不可以在此方法外对其实例化
    -   方法内部类对象不能使用该内部类所在方法的非final局部变量

```java
class Outer {
    public void doSomething(){
        class Inner{
            public void seeOuter(){
                System.out.println("inner class");
            }
        }

        Inner inner = new Inner();
        inner.seeOuter();
    }

    public static void main(String ... args){
        new  Outer().doSomething();
    }
}
```



##  匿名内部类anonymous inner class

1.  没有名字的局部内部类，不使用关键字class, extends, implements, 没有构造方法
2.  匿名内部类隐式地继承了一个父类或者实现了一个接口，通常是作为一个方法参数
    -   继承式的匿名内部类
    -   接口式的匿名内部类
    -   参数式的匿名内部类

##  小结

1.  共性：
    -   内部类仍然是一个独立的类，在编译之后会内部类会被编译成独立的.class文件，但是前面冠以外部类的类命和$符号
    -   内部类不能用普通的方式访问。内部类是外部类的一个成员，因此内部类可以自由地访问外部类的成员变量，无论是否是private的（静态内部类只能访问外部类的静态成员变量和方法）。
2.   java中为什么要引入内部类
    -   单继承的一种补充解决方案 inner classes能有效实际地允许“多重实现继承（multiple implementation）"
        -   每个inner class都能够各自继承某一实现类（implementation）
    -   针对具体的问题提供具体的解决方案，同时又能对外隐藏实现细节

