---

---

# JAVA基础

##  选择语句

###  if-else

###  switch

- 语法格式

    ```java
    switch (label){
        case case1:
            do-something;
            break;
        case case2:
            do-something;
            break;
        case case3:
            do-something;
            break;
            ...
        default:
            do-something;
            break;
    }
    ```

- 注意事项：

    - 匹配哪一个case就从哪一个位置开始向下执行，直到遇到break语句或整体结束

    - 多个case后面的数值不可以重复
    - label只能是:
        - 基础数据类型：byte/short/char/int
        - 引用类型：String/enum
    - case语句包括default语句顺序可以颠倒
    - break语句可以省略，但可能会导致穿透现象



##  循环语句

- 循环结构的基本组成部分，一般可以分为四个部分：
    1. 初始化语句
    2. 判断条件语句
    3. 循环体
    4. 步进表达式

###   for循环

- 语法：

    ``` JAVA
    for(初始化表达式; 条件表达式; 步进表达式){
        循环体;
    }
    ```

###   while循环

- 语法

    ```java
    初始化表达式;
    while(条件判断){
        循环体;
        步进表达式；
    }
    ```

###   do-while循环

- 语法：

    ```java
    初始化表达式;
    do {
        循环体;
        步进表达式；
    }while(条件判断);
    ```

- do-while语句无条件执行第一次循环

- **注意**：while后面有分号

###   三种循环的区别

- 如果条件判断从来没被满足过，for、while循环将执行0次，do-while循环会执行至少一次
- for循环的变量在小括号中定义，只有循环内部可以使用；while和do-while循环初始化语句在循环外面，在循环外仍然可以使用
- 循环次数确定使用for循环，否则使用while循环

###   循环控制语句

- break：  打断整个循环；
- continue：  跳过当前次循环剩余内容，马上开始下一次循环；

###   死循环

- 永远停不下来的循环

    ```java
    while(true){
        
    }
    ```

###   循环的嵌套

- 语法：

    ```java
    for(初始化表达式1; 条件表达式1; 步进表达式1){
        for(初始化表达式2; 条件表达式2; 步进表达式2){
            执行语句;
        }
    }
    ```

- 练习：使用嵌套循环，打印5*8的矩形  

    ```java
    public static void main(String[] args) {
        //5*8的矩形，打印5行*号，每行8个
        //外循环5次，内循环8次
        for(int i = 0; i < 5; i++){
    		for(int j = 0; j < 8; j++){
    			//不换行打印星号
    			System.out.print("*");
    		} //内循环打印8个星号后，需要一次换行
    		System.out.println();
    	}
    }
    ```

##   集成开发环境（Intellj IDEA）

- 项目结构：

    <img src="D:\MyLearning\img\02-IDEA的项目结构.png"/>

- 新建项目

- 新建模块

- 新建包，一般用域名反写

###   快捷键

1. 批量更改变量名，shift+ F6
2. 格式化代码，ctrl+shift+L
3. 上下移动代码，alt+shift+up/down
4. 方法重写， ctrl+O
5. 方法重写（接口）， ctrl+I





##   方法

### 定义方法

```java
修饰符 返回值类型 方法名（参数列表）{
    方法体
    return 结果;
}        
```

- 修饰符： public static 固定写法  

- 返回值类型： 表示方法运行的结果的数据类型，方法执行后将结果返回到调用者

- 参数列表：方法在运算过程中的未知数据，调用者调用方法时  

- return：将方法执行后的结果带给调用者，方法执行到 return ，整体方法运行结束  

- **注意：**return 结果; 这里的"结果"在开发中，我们正确的叫法成为方法的返回值。不能在 return 后面写代码， return 意味着方法结束，所有后面的代码永远不会执行，属于无效代码。    

    

    练习：

    需求：定义方法实现两个整数的求和计算  ：

    ```java
    public static int add(int a, int b) {
            int result = a + b;
            return result;
    }
    ```

### 方法的调用

- 打印调用：在输出语句中调用方法， System.out.println(方法名()) 。  
- 单独调用：直接写方法名调用  
- 赋值调用：调用方法，在方法前面定义变量，接收方法返回值  
- **注意：**对于没有返回值的方法，只能单独调用，不能打印或赋值

###   方法的注意事项

- 方法应该定义在类中，方法不能定义在方法当中
- 方法定义的先后顺序无所谓
- 方法定义后不会执行，如果希望执行，一定要调用
- 如果方法有返回值，必须有人return语句
- return后面的返回值数据必须和方法的返回值类型对应起来
- 一个方法中可以有多个return语句，但必须保证同时只能有一个会被执行

###   方法的重载

- 方法重载：指在同一个类中，允许存在一个以上的同名方法，只要它们的参数列表不同即可，与修饰符和返回值类型无关。
- 参数列表：个数不同，数据类型不同，顺序不同。
- 重载方法调用：JVM通过方法的参数列表，调用不同的方法。  
- 方法的重载与下列因素无关：
    - 参数的名称
    - 返回值类型

##  数组

###   数组概念

- 数组就是存储数据长度固定的容器，保证多个数据的数据类型要一致。  
- 数组的特点：
    - 数组是一种引用数据类型
    - 数组当中的多个数据，类型必须统一
    - 数组的长度在程序运行期间不可改变

###   数组的初始化

- 常见的初始化方式

    - 动态初始化（指定长度）

        - 数据类型[] 数组名称 = new 数据类型[数组长度];

        - **注意：**左右两边的数据类型必须一致，数组长度为int

    - 静态初始化（指定内容）

        - 数据类型[] 数组名称 = new 数据类型[] {元素1，元素2，...};
        - 数据类型[] 数组名称 = {元素1，元素2，...};

- **注意事项：**

    - 静态初始化可以拆分为两个步骤

        数据类型[] 数组名称 ;

        数组名称 = new 数据类型[] {元素1，元素2，...};

    - 动态初始化可以拆分为两个步骤

        数据类型[] 数组名称;

        数组名称 = new 数据类型[数组长度];

    - 静态初始化的省略格式不能拆分为两个步骤

    - 使用建议：不确定数组的具体内容，用动态初始化；否则，用静态初始化。

###   数组的访问  

- **索引：** 每一个存储到数组的元素，都会自动的拥有一个编号，从0开始，到数组长度-1，这个自动编号称为数组索引**(index)**，可以通过数组的索引访问到数组中的元素。
- 格式：
    - 数组名[索引] = 数值；赋值
    - 变量名 = 数组名[索引]; 获取
- 默认值
    - 动态初始化的数组有默认值，
    - 静态初始化的数组默认值会被替换成赋值的内容

###   数组的内存原理

- Java内存划分：

    | 区域名称   | 作用                                                       |
    | ---------- | ---------------------------------------------------------- |
    | 寄存器     | 给CPU使用，和我们开发无关。                                |
    | 本地方法栈 | JVM在使用操作系统功能的时候使用，和我们开发无关。          |
    | 方法区     | 存储可以运行的class文件。                                  |
    | 堆内存     | 存储对象或者数组，new来创建的，都存储在堆内存。            |
    | 方法栈     | 方法运行时使用的内存，比如main方法运行，进入方法栈中执行。 |

<img src="D:\MyLearning\img\image-20200529201829245.png" alt="image-20200529201829245"  />

- 注意：
    1. 凡是new出来的东西都在堆中；
    2. 数组的元素在堆内存中，地址值存储在栈中；
    3. int[] arr2 = arr; 表示将arr的地址值赋值给arr2，并没有在堆中新建一个数组。此时，更改arr2中的元素同样也更改arr中元素，反之亦然。

###   数组的常见操作  

1. 异常：

    - 数组越界异常ArrayIndexOutOfBoundsException：访问数组元素时，索引编号并不存在

    - 数组空指针异常NullPointerException ：数组必须进行new初始化，才能使用其中的元素，如果只是赋值null（arr = null;  ）将发生空指针异常

2. 获取数组的长度：

    ```java
    arr.length;
    ```

    - **注意：**数组一旦创建（堆中，不是地址值），长度不可改变

3. 遍历数组：

    ```java
    for (int i = 0; i < arr.length; i++){
        System.out.println(arr[i])
    }
    ```

4. 获取数组中最大值元素：

    ```java
    int[] arr = { 5, 15, 2000, 10000, 100, 4000 };
    int max = arr[0];
    for (int i = 1; i < arr.length; i++){
        if (arr[i] > max){
            max = arr[i]
        }
    }
    System.out.println("数组最大值是： " + max);
    ```

5. 数组元素反转：要求不适用新数组

    ```java
    int i = 0;
    int j = arr.length - 1;
    while(i < j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        i++;
        j--;
    }
    ```

###   数组作为方法参数和返回值

- 数组作为方法参数传递，传递的参数是数组内存的地址  
- 数组作为方法的返回值，返回的是数组的内存地址  
- 方法的参数为基本类型时，传递的是数据值； 方法的参数为引用类型时，传递的是地址值  

##  面向对象

​        Java语言是一种面向对象的程序设计语言，而面向对象思想是一种程序设计思想，我们在面向对象思想的指引下，使用Java语言去设计、开发计算机程序。 这里的**对象**泛指现实中一切事物，每种事物都具备自己的**属性**和**行为**。面向对象思想就是在计算机程序设计过程中，参照现实中事物，将事物的属性特征、行为特征抽象出来，描述成计算机事件的设计思想。 它区别于面向过程思想，强调的是通过调用对象的行为来实现功能，而不是自己一步一步的去操作实现。  

- **区别:**
    - 面向过程：强调步骤。
    - 面向对象：强调对象。  
- **特点：**
    - 面向对象思想是一种更符合我们思考习惯的思想，它可以将复杂的事情简单化，并将我们从执行者变成了指挥者。
    - 面向对象的语言中，包含了三大基本特征，即**封装、继承和多态**。  

###   类和对象

- 什么是类 ：
    - 类：是一组相关属性和行为的集合。可以看成是一类事物的模板，使用事物的属性特征和行为特征来描述该类事物。  
    - 属性：就是该事物的状态信息。  
    - 行为：就是该事物能够做什么。  
- 什么是对象 :
    - 对象：是一类事物的具体体现。对象是类的一个实例（对象并不是找个女朋友），必然具备该类事物的属性和行为 。 
- 类与对象的关系 :
    - 类是对一类事物的描述，是**抽象的**。
    - 对象是一类事物的实例，是**具体的**。
    - **类是对象的模板，对象是类的实体**。  

###  类的定义  

- 现实世界的一类事物：  

    属性：事物的状态信息。 行为：事物能够做什么。  

- Java中用class描述事物也是如此：  

    成员变量：对应事物的属性 成员方法：对应事物的行为  

- 类的定义格式

    - 定义类：就是定义类的成员，包括成员变量和成员方法。
    - 成员变量：和以前定义变量几乎是一样的。只不过位置发生了改变。在类中，方法外。
    - 成员方法：和以前定义方法几乎是一样的。只不过把static去掉，static的作用在面向对象后面课程中再详细讲解  

    ```java
    public class Student {
        //成员变量
        String name；//姓名
        int age；//年龄
        //成员方法
    	//学习的方法
        publicvoid study() {
        System.out.println("好好学习，天天向上");
        } //吃饭的方法
        publicvoid eat() {
        System.out.println("学习饿了要吃饭");
        }
    }
    ```

###   类的使用

- 导包：

    ```java
    import 包名称.类名称;
    ```

- 创建：

    ```java
    类名称 对象名 = new 类名称();
    ```

- 使用：

    ```java
    对象名.成员变量名;
    对象名.成员方法名（参数列表）;
    ```

- 成员变量的默认值 ：规则与数组默认值一致

    |                         | 数据类型                       | 默认值 |
    | ----------------------- | ------------------------------ | ------ |
    | 基本类型                | 整数（byte，short，int，long） | 0      |
    | 浮点数（float，double） | 0.0                            |        |
    | 字符（char）            | '\u0000'                       |        |
    | 布尔（boolean）         | false                          |        |
    | 引用类型                | 数组，类，接口                 | null   |

     

###   对象内存图

![image-20200529221900944](D:\MyLearning\img\image-20200529221900944.png)

- 成员方法在堆中存放的仅仅是其在方法区的地址值。对象调用方法时，根据对象中方法标记（地址值），去类中（方法区）寻找方法信息。这样哪怕是多个对象，方法信息只保存一份，节约内存空间。
- 对象作为参数，传递的是对象的地址值。
- 对象作为返回值，返回的是对象的地址值。

###   成员变量和局部变量区别  

- 在类中的位置不同 **重点**
    - 成员变量：类中，方法外
    - 局部变量：方法中或者方法声明上(形式参数)
- 作用范围不一样 **重点**
    - 成员变量：类中
    - 局部变量：方法中
- 初始化值的不同 **重点**
    - 成员变量：有默认值
    - 局部变量：没有默认值。必须先定义，赋值，最后使用。**参数在方法调用时，必然会被赋值。**
- 在内存中的位置不同 了解
    - 成员变量：堆内存
    - 局部变量：栈内存
- 生命周期不同 了解
    - 成员变量：随着对象的创建而存在，随着对象的消失而消失（java垃圾自动回收机制）
    - 局部变量：随着方法的调用（进栈）而存在，随着方法的调用完毕（出栈）而消失  

###   封装  

- **概述：**
    面向对象编程语言是对客观世界的模拟，客观世界里成员变量都是隐藏在对象内部的，外界无法直接操作和修改。封装可以被认为是一个保护屏障，防止该类的代码和数据被其他类随意访问。要访问该类的数据，必须通过指定的方式。适当的封装可以让代码更容易理解与维护，也加强了代码的安全性。  

- **原则：**
    将属性隐藏起来，若需要访问某个属性，提供公共方法对其访问。方法就是一种封装 ，关键字private也是一种封装。 

- 封装的步骤  

    1. 使用 private 关键字来修饰成员变量。

    2. 对需要访问的成员变量，提供对应的一对 getXxx 方法 、 setXxx 方法。 
    3. boolean类型的getter方法，**isXxx()**

- private的含义 ：
    1.  private是一个权限修饰符，代表最小权限。
    2. 可以修饰成员变量和成员方法。
    3. 被private修饰后的成员变量和成员方法，**只在本类中才能访问** ，超出本类不能直接访问。 

###   this关键字  

- 方法的局部变量和成员变量重名的时候，根据**就近原则**，优先使用局部变量
- this代表**所在类的当前对象**的引用（地址值），即对象自己的引用。  
- 通过谁调用的方法，谁就是this

###  构造方法  

- 当一个对象被创建时候，构造方法用来初始化该对象，给对象的成员变量赋初始值。通过new关键字调用  
- 构造方法的写法上，方法名与它所在的类名相同。它**不能有返回值**，所以不需要返回值类型，甚至不需要void。
- 无论你与否自定义构造方法，所有的类都有构造方法，因为Java自动提供了一个无参数构造方法，一旦自己定义了构造方法，Java自动提供的默认无参数构造方法就会失效。    
- 注意事项 ：
    1. 如果你不提供构造方法，系统会给出无参数构造方法。
    2. 如果你提供了构造方法，系统将不再提供无参数构造方法。
    3. 构造方法是可以重载的，既可以定义参数，也可以不定义参数。  

###   标准类——JavaBean  

- JavaBean 是 Java语言编写类的一种标准规范。符合 JavaBean 的类，要求类必须是具体的和公共的，并且具有无参数的构造方法，提供用来操作成员变量的 set 和 get 方法。  
- 四个组成部分
    1. 所有的成员变量使用private关键字修饰
    2. 每一个成员变量都有setter、getter方法
    3. 一个无参构造
    4. 一个全参构造

##   API 

- 概述 ： API(Application Programming Interface)，应用程序编程接口。Java API是一本程序员的 字典 ，是JDK中提供给我们使用的类的说明文档。这些类将底层的代码实现封装了起来，我们不需要关心这些类是如何实现的，只需要学习这些类如何使用即可。所以我们可以通过查询API的方式，来学习Java提供的类，并得知如何使用它们。  

###  API使用步骤  

1. 打开帮助文档。
2. 点击显示，找到索引，看到输入框。
3. 你要找谁？在输入框里输入，然后回车。
4. 看包。java.lang下的类不需要导包，其他需要。
5. 看类的解释和说明。
6. 学习构造方法。  

7. 使用成员方法。  

###  Scanner类  

- 一个可以解析基本类型和字符串的简单文本扫描器  

- Scanner使用步骤  :

    1. import导入后使用  import java.util.Scanner   

    2. 创建对象  

        ```java
        Scanner sc = new Scanner(System.in);	//键盘输入
        ```

    3. 调用方法  

        ```java
        int i = sc.nextInt(); // 接收一个键盘录入的整数
        String str = sc.next()	//接收一个键盘输入的字符串
        ```

###   匿名对象  

- 概念：没有变量名的对象 。创建对象时，只有创建对象的语句，却没有把对象地址值赋值给某个变量。虽然是创建对象的简化写法，但是应用场景非常有限。  

- 创建匿名对象直接调用方法，没有变量名，只能使用唯一的一次。  

    ```java
    new Scanner(System.in).nextInt();
    ```

- 匿名对象可以作为方法的参数和返回值  

    ```java 
    input(new Scanner(System.in));		//参数
    return new Scanner(System.in);		//返回值
    ```

###  Random类

- 随机数生成器

- 使用方法：

    ```java
    Random rd = new Random();
    int num = rd.nextInt();		//生成一个随机整数，范围是int类型的范围
    int num1 = rd.nextInt(10);	//生成[0,10)内的随机int整数
    int num2 = rd.nextInt(10)+1;//生成[1,10]内的随机整数
    ```

### ArrayList类

- java.util.ArrayList  

- 是大小**可变的数组**的实现，存储在内的数据称为元素  

- <E>泛型：只能是引用类型，不能是基本类型，一旦指定后不可更改

- 使用

    ```java
    ArrayList<String> list = new ArrayList<>();	//右侧的泛型可以不写，但保留尖括号
    boolean add(E e); //将指定的元素添加到此列表的尾部，添加成功返回true 
    E get(int index); //返回此列表中指定位置上的元素
    E remove(int index);	//移除此列表中指定位置上的元素。 
    int size();	//返回此列表中的元素数。 
    ```

- 存储基本数据类型：

    - 使用基本类型对应的包装类（位于java.lang包下）

        | 基本类型 | 基本类型包装类 |
        | :------- | :------------- |
        | byte     | Byte           |
        | short    | Short          |
        | int      | Integer        |
        | long     | Long           |
        | float    | Float          |
        | double   | Double         |
        | char     | Character      |
        | boolean  | Boolean        |

    - 从JDK1.5+开始，支持自动装箱、拆箱

###  String类

- java.lang.String

- `String` 类代表字符串。Java 程序中的所有字符串字面值（如 `"abc"`  ）都作为此类的实例实现。 

- 字符串是常量，它们的值在**创建之后不能更改**。

- 因为 String 对象是不可变的，所以**可以共享**。

- 字符串底层原理是byte[]数组

- 构造方法：

    ```java
    String();	//初始化一个新创建的 String 对象，使其表示一个空字符序列
    String str1 = new String();
    String(char[] value);	//分配一个新的 String，使其表示字符数组参数中当前包含的字符序列。
    char[] charArray = {'A','B','C'};
    String str1 = new String(charArray);
    String(byte[] bytes);	//通过 byte 数组，构造一个新的 String。
    byte[] byteArray= {97,98,99};
    String str1 = new String(byteArray);
    ```

- 直接创建：

    ```java
    String str1 = "abc";
    ```

    - JVM自动new了String对象。

- 字符串常量池：

    <img src="D:\MyLearning\img\01-字符串的常量池-1590816808696.png" alt="01-字符串的常量池" style="zoom:150%;" />

    - 直接双引号创建的字符串对象存储在堆中的字符串常量池里
    - new创建的字符串对象不在池中

- 方法：

    ```java
    public equals(Object obj);		//判断两个对象内容是否一致
    /* 
    	euqals方法具有对称性
    	如果比较的一方是字符串常量，推荐写法："abc".equals(str1);防止空指针异常
    */
    public equalsIgnoreCase(Stirng str);		//判断字符串内容是否一致，忽略大小写
    public length();	//返回字符串长度
    public concat(String str);	//拼接字符串，创建并返回一个新的字符串
    public charAt(int index);		//指定索引位置的单个字符
    public indexOf(String str);	//查找参数字符串在调用字符串中出现的第一个位置，不成功则返回-1
    public String substring(int beginIndex);	
    //返回一个子字符串，从beginIndex开始截取字符串到字符串结尾。
    public String substring (int beginIndex, int endIndex);
    //返回一个子字符串，从beginIndex到endIndex截取字符串。含beginIndex，不含endIndex
    
    
    public char[] toCharArray();	//将此字符串转换为新的字符数组。
    public byte[] getBytes();	//使用平台的默认字符集将该 String编码转换为新的字节数组
    public String replace(CharSequence target, CharSequence replacement);
    //将与target匹配的字符串使用replacement字符串替换。
    //CharSequence是一个接口，也是一种引用类型。作为参数类型，可以把String对象传递到方法中。

    public String[] split(String regex);
    //将此字符串按照给定的regex（规则）拆分为字符串数组。
    //regex是一个正则表达式："\\."，按"."分割
    ```
    

##   static关键字

###   概述

关于 static 关键字的使用，它可以用来修饰的成员变量和成员方法，被修饰的成员是**属于类**的，而不是单单是属于某个对象的。也就是说，既然属于类，就可以不靠创建对象来调用了。 

![02-静态static关键字概述](D:\MyLearning\img\02-静态static关键字概述.png)

###   定义和使用格式

- 静态变量  

    当 static 修饰成员变量时，该变量称为**类变量**。该类的每个对象都**共享**同一个类变量的值。任何对象都可以更改该类变量的值，但也可以在不创建该类的对象的情况下对类变量进行操作。

    - 定义格式：

        ```java
        static 数据类型 变量名;
        ```

    - 举例，通过numberOfStudent，自动生成sid

        ```java
        public class Student {
            private String name;
            private int age;
            // 学生的id
            private int sid;
            // 类变量，记录学生数量，分配学号
            public static int numberOfStudent = 0;
            public Student(String name, int age){
                this.name = name;
                this.age = age;
                // 通过 numberOfStudent 给学生分配学号
                this.sid = ++numberOfStudent;
            }
            ...
        }
        ```

- 静态方法  

    当 static 修饰成员方法时，该方法称为**类方法** 。静态方法在声明中有 static ，建议使用类名来调用，而不需要创建类的对象。调用方式非常简单。

    - 定义格式：  

        ```java
        修饰符 static 返回值类型 方法名 (参数列表){
        // 执行语句
        }
        ```

    - 调用方法：

        ```java
        //通过对象调用（不推荐）
        obj.staticMethod();
        //通过类名称调用
        className.staticMethod();	//本类中的静态方法，可以省略类名称
        ```

    - 注意事项：

        - 静态方法可以直接访问类变量和静态方法。  
        - 静态方法**不能直接访问**（非静态）普通成员变量或成员方法。反之，成员方法**可以**直接访问类变量或静态方法。原因：内存中**先**有静态内容**后**有非静态内容。
        - 静态方法中，不能使用this关键字。原因：this关键字代表本类对象

###   静态原理图解

![03-静态的内存图](D:\MyLearning\img\03-静态的内存图.png)

- static修饰的内容：
    - 是随着类的加载而加载的，且只加载一次。
    - 存储于方法区中一块固定的内存区域（静态区），所以可以直接被类名调用。
    - 它优先于对象存在，所以，可以被所有对象共享。  

###   静态代码块

定义在成员位置，使用static修饰的代码块  。

- 位置：类中方法外。

- 执行：随着类的加载而执行且执行**唯一一次**，**优先于main方法和构造方法的执行**。  

- 格式：  

    ```java
    public class ClassName{
        static {
        // 执行语句
        }
    }
    ```

- 作用：一次性的给静态成员变量进行初始化赋值。代码如下：

    ```java
    public class Game {
        public static int number;
        public static ArrayList<String> list;
        static {
        // 给类变量赋值
            number = 2;
            list = new ArrayList<String>();
            // 添加元素到集合中
            list.add("张三");
            list.add("李四");
        }
    }
    ```



###  静态方法工具类

- Array类

    - java.util.Arrays  ,此类包含用来操作数组的各种方法，比如排序和搜索等。其所有方法均为静态方法，调用起来非常简单。

    - public static String toString(E[] a)   返回指定数组内容的字符串表示形式。  

        ```java
        String s = Arrays.toString(arr);
        ```

    - public static void sort(E[] a)   对数组元素进行排序，默认升序。如果是自定义类，需要有*Comparable*和*Comparator*接口的支持

        ``` java
        Arrays.sort(chars);
        ```

- Math类

    - java.lang.Math 类包含用于执行基本数学运算的方法，如初等指数、对数、平方根和三角函数。类似这样的工具类，其所有方法均为静态方法，并且不会创建对象，调用起来非常简单。  

    - 常量和方法：

        ``` java
        static abs();//绝对值
        static double ceil();//向上取整
        static double floor();//向下取整
        static int round();//四舍五入
        static final double E//自然对数的底数
        static final double PI//圆周率
        ```

        

##  继承  

###   概述

多个类中存在相同属性和行为时，将这些内容抽取到单独一个类中，那么多个类无需再定义这些属性和行为，只要继承那一个类即可。  

- 定义
    继承：就是子类继承父类的属性和行为，使得子类对象具有与父类相同的属性、相同的行为。子类可以**直接访问**父类中的非私有的属性和行为，也可以有子类特有的属性和行为。  

- 好处

    1. **共性抽取**，提高代码的复用性。
    2. 类与类之间产生了关系，是**多态的前提**。  

- 继承的格式 ：extends关键字

    ``` java
    public class 子类 extends 父类 {
    ...
    }
    ```

###   继承后的特点  

- 成员变量  
    - 成员变量不重名：子类父类中出现**不重名**的成员变量，这时的访问是**没有影响**  
    - 成员变量重名：子父类中出现了同名的成员变量时，在子类中需要访问父类中非私有成员变量时，需要使用 super 关键字。
        - 规则：
            - 通过对象访问成员变量，等号左边是谁就优先用谁，没有则向上找
            - 类方法中调用成员变量时，方法属于谁（定义在哪个类），优先用谁，没有则向上找
- 成员方法
    - 成员方法不重名：子类父类中出现**不重名**的成员方法，调用**没有影响**
    - 成员方法重名：
        - 规则：创建（new）的对象是谁，优先用谁的方法，没有则向上找

###  方法的重写 Override

子类中出现与父类一模一样的方法时（方法名和参数列表都相同），会出现覆盖效果，也称为重写或者复写。声明不变，重新实现。

*设计原则：对于已经投入使用的类，尽量不进行修改，推荐定义一个新的类，重复利用其中共性内容，并且添加改动新内容。*  

- 方法重写的注意事项：

    - @Override，强制检查方法重写是否满足要求

    - 子类方法的返回值必须小于等于父类方法的返回值范围  
    - 子类方法的权限修饰符必须大于等于父类方法的权限修饰符
        - public  >  protected  >  啥也不写(*default*)  > private

###  构造方法的继承特点

- 构造方法的名字是与类名一致的。所以子类无法直接继承父类构造方法的。  

- 构造方法的作用是初始化成员变量的。所以子类的初始化过程中，必须先执行父类的初始化动作。

- 子类的构造方法中默认有一个无参的父类构造方法

    ``` java
    public ZiClassName(){
        super();
    }
    ```

- 子类可以通过*super*关键字调用父类重载构造

- 只有子类**构造方法**才可以通过*super*调用父类构造方法，**且必须是第一条语句**



###  *super*关键字的三种用法

- 在子类的成员方法中，访问父类的成员变量
- 在子类的成员方法中，访问父类的成员方法
- 在子类的构造方法中，访问父类的构造方法

### *this*关键字的三种用法

- 在本类的成员方法中，访问本类的成员变量，用于区别方法中的局部变量
- 在本类的成员方法中，访问本类的另一个成员方法，用于强调是本类的方法
- 在本类的构造方法中，访问本类的另一个构造方法，this()
    - 例如：本类的无参构造调用本类的有参构造
    - 注意：也必须是第一个语句，此时与super构造调用会冲突，两者只能选一个

###  super与this内存图

![03-super与this的内存图](D:\MyLearning\img\03-super与this的内存图.png)

- [super_class]标记由编译器自动生成，指向父类。

###  Java继承的特点  

- java只支持单继承，不支持多继承  
- Java支持多层继承(继承体系)  
    - 顶层父类是Object类。所有的类默认继承Object，作为父类。  
- 子类和父类是一种相对的概念  

![04-Java继承的三个特点](D:\MyLearning\img\04-Java继承的三个特点.png)



##  抽象类

###   概述  

父类中的方法，被它的子类们重写，子类各自的实现都不尽相同。那么父类的方法声明和方法主体，只有声明还有意义，而方法主体则没有存在的意义了。我们把没有方法主体的方法称为**抽象方法**。Java语法规定，包含抽象方法的类就是**抽象类**。  

- 定义：  
    - 抽象方法 ： 没有方法体的方法。
    - 抽象类：包含抽象方法的类。  

###   定义格式  

- 使用 abstract 关键字修饰的方法就成了抽象方法，抽象方法只包含一个方法名，而没有方法体。  

``` java
修饰符 abstract 返回值类型 方法名 (参数列表)；
public abstract void run()；
```

- 如果一个类包含抽象方法，那么该类必须是抽象类。  

    ```java
    abstract class 类名字 {
    }
    ```

  ###  使用步骤

- 不能直接new抽象类对象

- 必须用一个子类来继承抽象父类

- 子类必须覆盖重写抽象父类中的所有抽象方法，否则该子类扔是一个抽象类

- 重写方式为：去掉abstract，实现方法体

- 创建子类对象

    **注意事项：**

    - 抽象类**不能创建对象**，如果创建，编译无法通过而报错。只能创建其非抽象子类的对象。
        - 理解：假设创建了抽象类的对象，调用抽象的方法，而抽象方法没有具体的方法体，没有意义  。
    - 抽象类中，可以有构造方法，是供子类创建对象时，初始化父类成员使用的。  
        - 理解：子类的构造方法中，有默认的super()，需要访问父类构造方法。  
    - **抽象类中，不一定包含抽象方法**，但是有抽象方法的类必定是抽象类。
        - 理解：未包含抽象方法的抽象类，目的就是不想让调用者创建该类对象，通常用于某些特殊的类结构设计。 
    - 抽象类的子类，必须重写抽象父类中**所有的**抽象方法，否则，编译无法通过而报错。除非该子类也是抽象类。  
        - 理解：假设不重写所有抽象方法，则类中可能包含抽象方法。那么创建对象后，调用抽象的方法，没有意义。  

##  接口

###  概述  

接口，是Java语言中一种引用类型，是方法的集合，如果说类的内部封装了成员变量、构造方法和成员方法，那么接口的内部主要就是**封装了方法**，包含抽象方法（JDK 7及以前），默认方法和静态方法（JDK 8），私有方法（JDK 9）。  

接口的定义，它与定义类方式相似，但是使用 interface 关键字。它也会被编译成.class文件，但一定要明确它并不是类，而是另外一种引用数据类型（数组，类，接口  ）。  

接口的使用，它不能创建对象，但是可以被实现（ implements ，类似于被继承）。一个实现接口的类（可以看做是接口的子类），需要实现接口中所有的抽象方法，创建该类对象，就可以调用方法了，否则它必须是一个抽象类。  

###  定义格式  

```java
public interface 接口名称 {
// 常量
// 抽象方法
// 默认方法
// 静态方法
// 私有方法
}
```

- 抽象方法：使用 abstract 关键字修饰，可以省略，没有方法体。该方法供子类实现使用。  

    ```java
    public abstract void method();	//public,abstract这两个关键字可以省略
    ```

- 默认方法（Java8）：使用 default 修饰，不可省略，供子类调用或者子类重写。解决接口升级（增加抽象方法）后该接口的所有实现类需要修改（重写增加的抽象方法）的问题。

    - 接口的实现类可以直接调用接口的默认方法
    - 也可以被实现类覆盖重写

- 静态方法（Java8）：使用 static 修饰，供接口直接调用。  

    - 调用方法：接口名称 . 静态方法
    - **不能通过接口实现类的对象来调用**

    ````java
    public interface InterFaceName {
        public default void method() {//public可以省略
        // 执行语句
        } 
        public static void method2() {//public可以省略
        // 执行语句
        }
    }
    ````

- 私有方法（Java9）：使用 private 修饰，供接口中的默认方法或者静态方法调用，解决重复代码的问题。 只能在接口中使用，不能被实现类调用。

    - 普通私有方法：供默认方法调用
    - 静态私有方法：供静态方法调用

    ```java
    public interface InterFaceName {
        private void method1() {
        // 执行语句
        }
        private static void method2() {
        // 执行语句
        }
    }
    ```

- 常量：一旦赋值，不能更改。建议常量名使用**全大写加下划线**命名

    - 使用方法:  接口名称 . 常量名

    ```java
    public static final 数据类型 常量名称 = 数据值;
    //一旦使用final修饰，不可改变
    //public static final可以省略
    //必须进行赋值
    ```

- **注意事项：**

    - 接口没有静态代码块或者构造方法

    - 一个类只能有一个直接父类，但可以实现多个接口（必须实现每个接口的所有抽象方法）

        ```java
        public class 实现类名称 implements 接口名称1,接口名称2,...{}
        ```

    - 如果实现类的多个接口中存在重复的抽象方法，那么只需要覆盖重写**一次**即可

    - 如果实现类没有覆盖重写所以的抽象方法，那么该实现类是一个抽象类

    - 如果实现类的多个接口中存在重复的默认方法，那么实现类一定要对冲突的默认方法覆盖重写

    - 如果实现类的父类方法与接口默认方法冲突，优先使用父类方法（java中继承优先接口实现），不需要覆盖重写。



###  接口使用步骤

- 接口不能直接使用，必须有一个实现类来实现该接口

    ```java
    public class 实现类名称 implements 接口名称{
        //...........
    }
    ```

- 接口的实现类必须覆盖重写接口中所有的抽象方法。建议：实现类名称=接口名称Impl

- 创建实现类的对象。

- **注意：**实现类必须实现接口所有的抽象方法，否则该类仍然是一个抽象类

###   接口的多继承

一个接口能继承另一个或者多个接口，这和类之间的继承比较相似。接口的继承使用 extends 关键字，子接口继承父接口的方法。

- 如果父接口中的抽象方法有重名的，不管
- 如果父接口中的默认方法有重名的，那么子接口需要重写一次，不能省略default关键字。  

##  多态

###  概述  

多态(Polymorphism)是继封装、继承之后，面向对象的第三大特性。生活中，比如跑的动作，小猫、小狗和大象，跑起来是不一样的。再比如飞的动作，昆虫、鸟类和飞机，飞起来也是不一样的。可见，同一行为，通过不同的事物，可以体现出来的不同的形态。多态，描述的就是这样的状态。

- **定义：**多态是指同一行为，具有多个不同表现形式 。 
    1. 继承或者实现【二选一】
    2. 方法的重写【意义体现：不重写，无意义】
    3. 父类引用指向子类对象【格式体现】

###  多态的体现

- 格式：

    ```java
    父类类型 变量名 = new 子类对象；
    变量名.方法名();
    ```

    - 父类类型：指子类对象继承的父类类型，或者实现的父接口类型。  
    - 当使用多态方式调用方法时，**首先检查父类中是否有该方法**，如果没有，则编译错误；如果有，**执行的是子类重写后方法**。  

- 多态（左父右子）下的成员变量访问：

    - 直接通过对象访问：等号左边是谁（父），优先用谁（父），没有则向上找
    - 间接通过成员方法访问：看该方法属于谁，优先用谁，没有则向上找
        - 子类没有覆盖重写，就是父
        - 子类覆盖重写，就是子
    - 编译看左边；运行还看左边

- 多态（左父右子）下的成员方法访问：

    - new的是谁，就优先用谁，没有则向上找
    - 总结：编译看左边（父）；运行看右边（子），没有则向上找

###   多态的好处

- 实际开发的过程中，**父类类型**作为方法形式参数，传递**子类对象**给方法，进行方法的调用，更能体现出多态的扩展性与便利。  
- 无论等号右边new的时候创建的是哪个子类对象，等号左边调用方法都不会改变。

###  引用类型转换  

- 向上转型：多态本身是子类类型向父类类型向上转换的过程，这个过程是默认的。当父类引用指向一个子类对象时，便是向上转型。**向上转型一定是安全的**。

    ```java
    父类类型 变量名 = new 子类类型();
    如：Animal a = new Cat();//创建了一只猫，当作动物看待
    ```

    

- 向下转型： 父类类型向子类类型向下转换的过程，这个过程是强制的。一个已经向上转型的子类对象，将父类引用转为子类引用，可以使用强制类型转换的格式，便是向下转型。  

    ``` java
    子类类型 变量名 = (子类类型) 父类变量名;
    如:Cat c =(Cat) a;//此时c就可以调用Cat类特有的方法
    ```

    - 将父类对象还原成为一个子类对象。
    - **注意事项：**
        - 必须保证对象本类创建的时候，就是猫，才能向下转型为猫
        - 如果对象创建的时候不是猫，现在非要向下转型为猫，就会报错ClassCastException   

![05-对象的上下转型](D:\MyLearning\img\05-对象的上下转型.png)

- 引用变量做类型向下转型的校验 

    ```java
    变量名 instanceof 数据类型
    如果变量属于该数据类型，返回true。
    如果变量不属于该数据类型，返回false。
    ```

##  final关键字

###   概述  

学习了继承后，我们知道，子类可以在父类的基础上改写父类内容，比如，方法重写。那么我们能不能随意的继承API中提供的类，改写其内容呢？显然这是不合适的。为了避免这种随意改写的情况，Java提供了 final 关键字，用于修饰**不可改变**内容。

###  用法

-  可以用于修饰类、方法和变量 

    -  类：被修饰的类不能被继承。 该类中的所有方法不能被覆盖重写。

        ```java
        public final class 类名 {...}
        ```

    - 方法：被修饰的方法不能被重写。  **注意：**final与abstract不能同时使用

        ```java
        修饰符 final 返回值类型 方法名(参数列表){...}
        ```

    - 局部变量

        - 基本类型的局部变量，被final修饰后，只能赋值一次，不能再更改。 
        - 引用类型的局部变量，被final修饰后，只能指向一个对象，地址不能再更改。但是不影响对象内部的成员变量值的修改。

    - 成员变量：成员变量涉及到初始化的问题，初始化方式有两种，**只能二选一** 

        - 显式初始化，申明成员变量时直接赋值  
        - 构造方法初始化 ，必须保证所有重载的构造方法都对该成员变量赋值 

##  权限修饰符  

###  概述

- 在Java中提供了四种访问权限，使用不同的访问权限修饰符修饰时，被修饰的内容会有不同的访问权限。
    - public：公共的。
    - protected：受保护的
    - default：默认的，（不写）
    - private：私有的  

###  不同权限的访问能力  

|                        | public | protected | default（空的） | private |
| ---------------------- | ------ | --------- | --------------- | ------- |
| 同一类中               | √      | √         | √               | √       |
| 同一包中(子类与无关类) | √      | √         | √               |         |
| 不同包的子类           | √      | √         |                 |         |
| 不同包中的无关类       | √      |           |                 |         |



##  内部类  

###   概述  

将一个类A定义在另一个类B里面，里面的那个类A就称为**内部类**，B则称为**外部类**。  

###   成员内部类

- 定义在**类中方法外**的类。 
    -  **注意：**内用外，随意访问；外用内，必须通过内部类对象。
- 使用：
    - 间接使用：在外部类的方法中使用内部类，然后调用外部类的方法
    - 直接使用：外部类名称 . 内部类名称  **对象名**  = new 外部类名称() . new 内部类名称()
- 重名的问题
    - 内部类访问外部类成员变量：外部类名称 . this . 变量名

###   局部内部类

- 定义在**类中方法里**的类。 

- 使用
    - 只有当前的方法可以使用，在方法中创建局部内部类的对象直接使用
- 访问方法的局部变量：
    - 该局部变量必须是**有效final**的
    - 原因：局部变量跟着方法在栈内存中，当方法运行结束并出栈后局部变量消失；new出的对象在堆内存中会持续存在，直到垃圾回收，其生命周期更长。局部内部类会复制一份该局部变量，所以必须保证该局部变量是常量。

###   匿名内部类

- 是内部类的简化写法。它的本质是一个 带具体实现的父类或者父接口的匿名的**子类对象**。  

- 匿名内部类必须**继承一个父类**或者**实现一个父接口**。

-  匿名内部类创建对象的时候只能使用**唯一一次**，

- 使用方式 ：

    ``` java
    Myinterface obj = new Myinterface(){
        @Override
        public void method1(){
            //...
        }
        @Override
        public void method2(){
            //...
        }
    };
    obj.method1();
    ```

- 结合匿名对象

    ```java
    new Myinterface(){
        @Override
        public void method(){
            //...
        }
    }.method();
    ```

- 作为方法的参数

    ```java
    public static void showFly(FlyAble f) {...}
    showFly( new FlyAble(){
        public void fly() {
        System.out.println("我飞了~~~");
        }
    });
    ```

###  类的权限修饰符

- 外部类：public/(default)
- 成员内部类：public/protected/(default)/private
- 局部内部类：什么都不能写，但**也不是(default)**

##  引用类型用法总结  

- class作为成员变量  
- interface作为成员变量  
- interface作为方法参数和返回值类型 
    - 接口作为参数时，传递它的子类对象。
    - 接口作为返回值类型时，返回它的子类对象。



##  Object类

### 概述

`java.lang.Object`类是Java语言中的根类，即所有类的父类。它中描述的所有方法子类都可以使用。在对象实例化的时候，最终找的父类就是Object。如果一个类没有特别指定父类，	那么默认则继承自Object类。

```java
public class Person {  
    private String name;
    private int age;
}
```

###   toString方法

- `public String toString()`：返回该对象的字符串表示。
- toString方法返回该对象的字符串表示，其实该字符串内容就是对象的类型+@+内存地址值。

- 覆盖重写

```java
@Override
public String toString() {
    return "Person{" + "name='" + name + '\'' + ", age=" + age + '}';
}
```

###  equals方法

- `public boolean equals(Object obj)`：指示其他某个对象是否与此对象“相等”。

- 参数是Object,可以传递任意对象

- 如果没有覆盖重写equals方法，那么Object类中默认进行`==`运算符的对象地址比较，只要不是同一个对象，结果必然为false。

- 覆盖重写

    - 参数是Object，需要向下转型，
    - 增加一个判断，防止ClassCastException

    ```java
    @Override
    public boolean equals(Object o) {
        // 如果对象地址一样，则认为相同
        if (this == o)
            return true;
        // 如果参数为空，或者类型信息不一样，则认为不同
        //使用反射技术，判断o是否Person类型
        if (o == null || getClass() != o.getClass())
            return false;
        // 转换为当前类型
        Person person = (Person) o;
        // 要求基本类型相等，并且将引用类型交给java.util.Objects类的equals静态方法取用结果
        return age == person.age && Objects.equals(name, person.name);
    }
    ```

###  Objects类

- `java.util.Objects`类，在**JDK7**添加了一个Objects工具类，它提供了一些方法来操作对象，它由一些静态的实用方法组成，这些方法是null-save（空指针安全的）或null-tolerant（容忍空指针的），用于计算对象的hashcode、返回对象的字符串表示形式、比较两个对象。

- 在比较两个对象的时候，Object的equals方法容易抛出空指针异常，而Objects类中的equals方法就优化了这个问题。方法如下：

    ```java
    public static boolean equals(Object a, Object b){//判断两个对象是否相等。
        return (a == b) || (a != null && a.equals(b));  
    }
    ```

    

##  日期时间类

###  Date类

- `java.util.Date`类表示特定的瞬间，精确到毫秒。
- `public Date()`：空参构造，分配Date对象并获取当前系统的日期和时间。
- `public Date(long millis)`：带参构造，分配Date对象并初始化此对象，以表示自从标准基准时间（称为“历元（epoch）”，即1970年1月1日00:00:00 GMT）以来的指定long类型的毫秒数millis的日期。
    - 由于我们处于东八区，所以我们的基准时间为1970年1月1日8时0分0秒。
- `System.currentTimeMillis()`获取当前系统时间的毫秒值
- `public long getTime()` 把日期对象转换成对应的时间毫秒值。

###  DateFormat类

- `java.text.DateFormat` 是日期/时间格式化子类的**抽象类**，我们通过这个类可以帮我们完成日期和文本之间的转换,也就是可以在Date对象与String对象之间进行来回转换。
- 作用：
    - **格式化**：按照指定的格式，从Date对象转换为String对象。
    - **解析**：按照指定的格式，从String对象转换为Date对象。
- `DateFormat` 是抽象类，无法直接使用，我们使用它的子类

###   SimpleDateFormat

- `java.text.SimpleDateFormat`。这个类需要一个模式（格式）来指定格式化或解析的标准。

- 构造方法为：

    - `public SimpleDateFormat(String pattern)`：用给定的模式和默认语言环境的日期格式符号构造SimpleDateFormat。

    - 参数pattern是一个字符串，代表日期时间的自定义格式：

        | 标识字母（区分大小写） | 含义 |
        | ---------------------- | ---- |
        | y                      | 年   |
        | M                      | 月   |
        | d                      | 日   |
        | H                      | 时   |
        | m                      | 分   |
        | s                      | 秒   |

- 常用方法

    - `public String format(Date date)`：将Date对象格式化为字符串。
    - `public Date parse(String source)`：将字符串解析为Date对象。如果字符串和构造方法的模式不一样，则跑出异常，ParseException

- 代码举例：

    ``` java
    SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
    Date date1 = new Date();
    String str = sdf.format(date1);	//格式化
    Date date2 = sdf.parse(str);	//解析  
    ```

###  Calendar类

- `java.util.Calendar`是日历类，在Date后出现，替换掉了许多Date的方法。该类将所有可能用到的时间信息封装为静态成员变量，方便获取。日历类就是方便获取各个时间属性的。

- Calendar为抽象类，由于语言敏感性，Calendar类在创建对象时并非直接创建，而是通过静态方法创建。

    - `public static Calendar getInstance()`：使用默认时区和语言环境获得一个日历

        ``` java
        Calendar cal = Calendar.getInstance();
        ```

- 常用方法:

    - `public int get(int field)`：返回给定日历字段的值。
    - `public void set(int field, int value)`：将给定的日历字段设置为给定值。
    - `public abstract void add(int field, int amount)`：根据日历的规则，为给定的日历字段添加或减去指定的时间量。
    - `public Date getTime()`：返回一个表示此Calendar时间值（从历元到现在的毫秒偏移量）的Date对象。

- Calendar类中提供很多成员常量，代表给定的日历字段：

    | 字段值       | 含义                                  |
    | ------------ | ------------------------------------- |
    | YEAR         | 年                                    |
    | MONTH        | 月（从0开始，可以+1使用）             |
    | DAY_OF_MONTH | 月中的天（几号）                      |
    | HOUR         | 时（12小时制）                        |
    | HOUR_OF_DAY  | 时（24小时制）                        |
    | MINUTE       | 分                                    |
    | SECOND       | 秒                                    |
    | DAY_OF_WEEK  | 周中的天（周几，周日为1，可以-1使用） |

- 代码举例：

    ```java
    // 创建Calendar对象
    Calendar cal = Calendar.getInstance();
    // 获取年 
    int year = cal.get(Calendar.YEAR);
    // 获取月
    int month = cal.get(Calendar.MONTH) + 1;
    // 获取日
    int dayOfMonth = cal.get(Calendar.DAY_OF_MONTH);
    // 设置年 
    cal.set(Calendar.YEAR, 2020);
    // 同时设置年月日
    cal.set(2020，8，8);
    // 使用add方法
    cal.add(Calendar.DAY_OF_MONTH, 2); // 加2天
    cal.add(Calendar.YEAR, -3); // 减3年
    // 返回日期
    Date date = cal.getTime();
    ```

- 小贴士：

    - 西方星期的开始为周日，中国为周一。
    - 在Calendar类中，月份的表示是以0-11代表1-12月。
    - 日期是有大小关系的，时间靠后，时间越大。

    

##   System类

###  概述

`java.lang.System`类中提供了大量的静态方法，可以获取与系统相关的信息或系统级操作，在System类的API文档中。

###  常用方法

- `currentTimeMillis`方法

    - `public static long currentTimeMillis()`：返回以毫秒为单位的当前时间，当前系统时间与1970年01月01日00:00点之间的毫秒差值。

- `arraycopy`方法

    - `public static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)`：将数组中指定的数据拷贝到另一个数组中。

    - 数组的拷贝动作是系统级的，性能很高。System.arraycopy方法具有5个参数，含义分别为：

        | 参数序号 | 参数名称 | 参数类型 | 参数含义             |
        | -------- | -------- | -------- | -------------------- |
        | 1        | src      | Object   | 源数组               |
        | 2        | srcPos   | int      | 源数组索引起始位置   |
        | 3        | dest     | Object   | 目标数组             |
        | 4        | destPos  | int      | 目标数组索引起始位置 |
        | 5        | length   | int      | 复制元素个数         |

- 代码举例：

    ``` java 
    int[] src = new int[]{1,2,3,4,5};
    int[] dest = new int[]{6,7,8,9,10};
    //将src数组中前3个元素，复制到dest数组的前3个位置上
    System.arraycopy( src, 0, dest, 0, 3}
    ```



##  StringBuilder类

###   概述

字符串的底层是一个被final修饰的数组`private final byte[] value;`，所以String类的对象内容不可改变，每当进行字符串拼接时，总是会在内存中创建一个新的对象。如果对字符串进行拼接操作，每次拼接，都会构建一个新的String对象，既耗时，又浪费空间。为了解决这一问题，可以使用`java.lang.StringBuilder`类。

StringBuilder又称为可变字符序列，它是一个类似于 String 的字符串缓冲区，通过某些方法调用可以改变该序列的长度和内容。即它是一个容器，容器中可以装很多字符串。并且能够对其中的字符串进行各种操作。

它的内部拥有一个数组用来存放字符串内容，进行字符串拼接时，直接在数组中加入新内容。StringBuilder会自动维护数组的扩容。

###  构造方法

- `public StringBuilder()`：构造一个空的StringBuilder容器，默认长度为16。
- `public StringBuilder(String str)`：构造一个StringBuilder容器，并将字符串添加进去。

###  常用方法

- `public StringBuilder append(...)`：添加任意类型数据的字符串形式，并返回当前对象自身。

- `public String toString()`：将当前StringBuilder对象转换为String对象。

    ```java
    StringBuilder builder = new StringBuilder();
    builder.append("hello");
    String str = builder.toString();
    ```



##  包装类

###  概述

Java提供了两个类型系统，基本类型与引用类型，使用基本类型在于效率，然而很多情况，会创建对象使用，因为对象可以做更多的功能，如果想要我们的基本类型像对象一样操作，就可以使用基本类型对应的包装类，如下：

| 基本类型 | 对应的包装类（位于java.lang包中） |
| -------- | --------------------------------- |
| byte     | Byte                              |
| short    | Short                             |
| int      | **Integer**                       |
| long     | Long                              |
| float    | Float                             |
| double   | Double                            |
| char     | **Character**                     |
| boolean  | Boolean                           |

###  装箱与拆箱

- 基本类型与对应的包装类对象之间，来回转换的过程称为”装箱“与”拆箱“：

    - **装箱**：从基本类型转换为对应的包装类对象。

        - 使用字符串作为参数时，注意NunberFormatException

        ``` java 
        Integer i = new Integer(4);//使用构造函数函数，已过时
        Integer ii = new Integer("4");
        Integer iii = Integer.valueOf(4);//使用包装类中的valueOf方法
        Integer iiii = Integer.valueOf("4");
        ```

    - **拆箱**：从包装类对象转换为对应的基本类型。

        ``` java
        int num = i.intValue();
        ```

###  自动装箱与自动拆箱

- 由于我们经常要做基本类型与包装类之间的转换，从Java 5（JDK 1.5）开始，基本类型与包装类的装箱、拆箱动作可以自动完成。

    ```java
    Integer i = 4;//自动装箱。相当于Integer i = Integer.valueOf(4);
    i = i + 5;//等号右边：将i对象转成基本数值(自动拆箱) i.intValue() + 5;
    //加法运算完成后，再次装箱，把基本数值转成对象。
    ArrayList<Integer> list = new ArrayList<>();
    list.add(1);	//自动装箱
    int a = list.get(1);	//自动拆箱
    ```

###  基本类型与字符串之间的转换

- 基本类型转为字符串：
    - 基本类型直接与””相连接即可；如：34+""
    - 包装类的静态方法，`static String toString(int i)`
    - String类的静态方法，`static String valueOf(int i)`

- 字符串转为基本类型：

    - 包装类的静态方法，`static String parseXxx(String s)`

        - 除了Character类之外，其他所有包装类都具有parseXxx静态方法可以将字符串参数转换为对应的基本类型

        - parseByte

        - parseShort

        - parseInt

        - parseLong

        - parseFloat

        - parseDouble

        - parseBoolean

            ```java
            int num = Integer.parseInt("100");
            ```

    - 注意:如果字符串参数的内容无法正确转换为对应的基本类型，则会抛出`java.lang.NumberFormatException`异常。

##  Collection集合

###  概述

集合是java中提供的一种容器，可以用来存储多个数据。

集合和数组既然都是容器，它们有啥区别呢？

* 数组的长度是固定的。集合的长度是可变的。
* 数组中存储的是同一类型的元素，可以存储基本数据类型值，也可以存储对象。集合存储的都是对象。而且对象的类型可以不一致。在开发中一般当对象多的时候，使用集合进行存储。

###  集合框架

集合按照其存储结构可以分为两大类，分别是单列集合`java.util.Collection`和双列集合`java.util.Map`。

![01_集合框架介绍](D:\MyLearning\img\01_集合框架介绍.bmp)

- **Collection**：单列集合类的根接口，用于存储一系列符合某种规则的元素，它有两个重要的子接口，分别是`java.util.List`和`java.util.Set`。其中，`List`的特点是元素有序、元素可重复。`Set`的特点是元素无序，而且不可重复。`List`接口的主要实现类有`java.util.ArrayList`和`java.util.LinkedList`，`Set`接口的主要实现类有`java.util.HashSet`和`java.util.TreeSet`。

###  Collection 常用功能

Collection是所有单列集合的父接口，因此在Collection中定义了单列集合(List和Set)通用的一些方法，这些方法可用于操作所有的单列集合。方法如下：

* `public boolean add(E e)`：  把给定的对象添加到当前集合中 。
* `public void clear()` :清空集合中所有的元素。
* `public boolean remove(E e)`: 把给定的对象在当前集合中删除。
* `public boolean contains(E e)`: 判断当前集合中是否包含给定的对象。
* `public boolean isEmpty()`: 判断当前集合是否为空。
* `public int size()`: 返回集合中元素的个数。
* `public Object[] toArray()`: 把集合中的元素，存储到数组中。



##  Iterator迭代器

###  Iterator接口

在程序开发中，经常需要遍历集合中的所有元素。针对这种需求，JDK专门提供了一个接口`java.util.Iterator`。`Iterator`接口也是Java集合中的一员，但它与`Collection`、`Map`接口有所不同，`Collection`接口与`Map`接口主要用于存储元素，而`Iterator`主要用于迭代访问（即遍历）`Collection`中的元素，因此`Iterator`对象也被称为迭代器。

- `public Iterator iterator()`: 获取集合对应的迭代器，用来遍历集合中的元素的。

- **迭代**：即Collection集合元素的通用获取方式。在取元素之前先要判断集合中有没有元素，如果有，就把这个元素取出来，继续在判断，如果还有就再取出出来。一直把集合中的所有元素全部取出。这种取出方式专业术语称为迭代。

- Iterator接口的常用方法如下：

    - `public E next()`:返回迭代的下一个元素。
    - `public boolean hasNext()`:如果仍有元素可以迭代，则返回 true。

- 迭代器的使用步骤：

    - 使用集合中的iterator()获取迭代器的实现类对象，使用Iterator接口接收

    - 使用Iterator接口中的hasNext()方法判断还有没有下一个元素

    - 使用Iterator接口中的next()方法获取集合的下一个元素

        ```java
        // 使用多态方式 创建对象
        Collection<String> coll = new ArrayList<String>();
        
        // 添加元素到集合
        coll.add("串串星人");
        coll.add("吐槽星人");
        coll.add("汪星人");
        
        //遍历
        //使用迭代器 遍历   每个集合对象都有自己的迭代器
        Iterator<String> it = coll.iterator();
        //  泛型指的是 迭代器 元素的数据类型
        while(it.hasNext()){ //判断是否有迭代元素
            String s = it.next();//获取迭代出的元素
            System.out.println(s);
        }
        ```

###  迭代器的实现原理

![02_迭代器的实现原理(D:\MyLearning\img\02_迭代器的实现原理(1).bmp)](D:\BaiduNetdiskDownload\02-Java语言进阶\day02_Collection、泛型\resource\02_迭代器的实现原理(1).bmp)

在调用Iterator的next方法之前，迭代器的索引**位于第一个元素之前**，不指向任何元素，当第一次调用迭代器的next方法后，迭代器的索引会向后移动一位，指向第一个元素并将该元素返回，当再次调用next方法时，迭代器的索引会指向第二个元素并将该元素返回，依此类推，直到hasNext方法返回false，表示到达了集合的末尾，终止对元素的遍历。

###  增强for

增强for循环(也称for each循环)是**JDK1.5**以后出来的一个高级for循环，专门用来遍历数组和集合的。它的内部原理其实是个Iterator迭代器，用于遍历**Collection和数组**，所以在遍历的过程中，不能对集合中的元素进行增删操作。

``` java 
for(元素的数据类型  变量 : Collection集合or数组){ 
  	//写操作代码
}
```



##  泛型

在JDK5之后，新增了**泛型**(**Generic**)语法，让你在设计API时可以指定类或方法支持泛型，这样我们使用API的时候也变得更为简洁，并得到了编译时期的语法检查。

- **泛型**：可以在类或方法中预知地使用未知的类型。一般在创建对象时，将未知的类型确定具体的类型。当没有指定泛型时，默认类型为Object类型。

###  泛型的好处

- 将运行时期的ClassCastException，转移到了编译时期变成了编译失败。
- 避免了类型强转的麻烦。
- 弊端：泛型是什么类型就只能存储什么类型的数据





