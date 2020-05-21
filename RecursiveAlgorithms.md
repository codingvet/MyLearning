-   单词
    1.  rigorous
        英 [ˈrɪɡərəs]   美 [ˈrɪɡərəs] 
        adj.谨慎的;细致的;彻底的;严格的;严厉的
        
    2.  crucial
        英 [ˈkruːʃl]   美 [ˈkruːʃl] 
        adj.至关重要的;关键性的
        
    3.  portray
        英 [pɔːˈtreɪ]   美 [pɔːrˈtreɪ] 
        v.描绘;描画;描写;将…描写成;给人以某种印象;表现;扮演(某角色)
        
    4.  manifestation
        英 [ˌmænɪfeˈsteɪʃn]   美 [ˌmænɪfeˈsteɪʃn] 
        n.显示;表明;表示;(幽灵的)显现，显灵
        
    5.  invocation
        英 [ˌɪnvəˈkeɪʃn]   美 [ˌɪnvəˈkeɪʃn] 
        n.(向神或权威人士的)求助;祈祷;调用;启用
        
    6.  terminology
       英 [ˌtɜːmɪˈnɒlədʒi]   美 [ˌtɜːrmɪˈnɑːlədʒi] 
       n.(某学科的)术语;有特别含义的用语;专门用语
       
    7.  trivial
        英 [ˈtrɪviəl]   美 [ˈtrɪviəl] 
        adj.不重要的;琐碎的;微不足道的
        
    8.  simultaneously
        英 [ˌsɪməlˈteɪniəsli]   美 [ˌsaɪməlˈteɪniəsli]
        adv.同时;联立;急切地
        
    9.  configuration
        英 [kənˌfɪɡəˈreɪʃn]   美 [kənˌfɪɡjəˈreɪʃn]
        n.布局;结构;构造;格局;形状;(计算机的)配置







# Recursion

-   Line Recursion:a method makes one recursive calls  

```java
Public static int linearSum(int[] data, int n){
    if (n == 0)
        return 0;
    else
        retun linearSum(data, n-1) + data[n-1];
}

```

-   Binary Recursion:a method makes two recursive calls  
-   一个方法两次递归调用

```java
public class DrawRuler {
    public static void main(String[] args) {
        drawRuler(2,3);
    }

    public static void drawRuler(int nInches, int majorLength){

        drawLine(majorLength,0);        //打印标签为0的刻度
        for (int j = 1; j <= nInches; j++) {

            drawInterval(majorLength-1);
            drawLine(majorLength, j);
        }
    }
    private static void drawInterval(int centralLength) {
        if (centralLength >= 1){
            drawInterval(centralLength - 1);
            drawLine(centralLength);
            drawInterval(centralLength - 1);
        }
    }
    private static void drawLine(int tickLength, int tickLabel) {
        for (int j = 0; j < tickLength; j++)
            System.out.print("-");
        if (tickLabel >=0)
            System.out.print(" " + tickLabel);
        System.out.println();
    }
    //函数重载
    private static void drawLine(int tickLength){
        drawLine(tickLength, -1);       //当标签为负数时，不打印标签
    }
}
```



-   Mutiple Recursion: a method makes more than two recursive calls 

```java
public class DiskUsage {

    public static void main(String[] args) {
        File root = new File("D:\\IdeaProjects\\basic-code\\day04-code");
        Long total = diskUsage(root);
        System.out.println(total);

    }
    public static long diskUsage(File root){
        long total = root.length();
        if (root.isDirectory()) {
            for (String childName : root.list()) {
                File child = new File(root, childName);
                total += diskUsage(child);
            }
        }
        System.out.println(total + "\t" +root);
        return total;
    }
}
```









