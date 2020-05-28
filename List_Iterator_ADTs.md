-   单词

    1.  egitimate
    	英 [lɪˈdʒɪtɪmət]   美 [lɪˈdʒɪtɪmət]
    	adj.正当合理的;合情合理的;合法的;法律认可的;法定的;合法婚姻所生的
    	vt.使合法;给予合法的地位;通过法律手段给（私生子）以合法地位;正式批准;授权
    2.  demonstrate
        英 [ˈdemənstreɪt]   美 [ˈdemənstreɪt] 
    	v.证明;证实;论证;说明;表达;表露;表现;显露;示范;演示
    3.  in essence
    	英 [ɪn ˈesns]   美 [ɪn ˈesns] 
        实质上
    4.  subtle
        英 [ˈsʌtl]   美 [ˈsʌtl] 
        adj.不易察觉的;不明显的;微妙的;机智的;机巧的;狡猾的;巧妙的
    5.  defunct
        英 [dɪˈfʌŋkt]   美 [dɪˈfʌŋkt] 
        adj.不再存在的;不再起作用的;不再使用的
        n.死者;死人
    6.  convention
        英 [kənˈvenʃn]   美 [kənˈvenʃn] 
        n.习俗;常规;惯例;(某职业、政党等成员的)大会，集会;(国家或首脑间的)公约，协定，协议
    7.  snapshot
        英 [ˈsnæpʃɒt]   美 [ˈsnæpʃɑːt]  
        n.简介;简要说明
        vt.给…拍快照拍快照
    8.  upfront
        英 [ˌʌpˈfrʌnt]   美 [ˌʌpˈfrʌnt]  
        adj.坦率的;诚实的;直爽的;预付的;预交的
    9.  piecewise
        分段;分片;分段式;逐段
    10.  downside
         英 [ˈdaʊnsaɪd]   美 [ˈdaʊnsaɪd]  
         n.缺点;不利方面
    11.  embed
         英 [ɪmˈbed]   美 [ɪmˈbed]  
         v.把…牢牢地嵌入(或插入、埋入);派遣(战地记者、摄影记者等);
    12.  Heuristic
         英 [hjuˈrɪstɪk]   美 [hjuˈrɪstɪk]  
         启发式;启发法;启发式搜索;启发式的;启发式算法
    
    
    
    
    
    



# List and Iterator ADTs

##  The List ADT

##  Iterators  

1.  snapshot iterator
    -   maintains its own private copy of the sequence of elements
    -   unaffected by any subsequent changes to the primary collection that may
        occur.  
    -   requires a simple traversal of the primary structure  
    -   requires O(n) time and O(n) auxiliary space, upon construction, to copy and store a collection of n elements.  
2.  lazy iterator  
    -   does not make an upfront copy, instead  performing a piecewise traversal of the primary structure only when the next() method is called    
    -   its behavior is affected if the primary structure is modified  
    -   requires only O(1) space and O(1) construction time   
    -   fail-fast：快速失败，在用迭代器遍历一个集合对象时，如果遍历过程中对集合对象的内容进行了修改（增加、删除、修改），则会抛出Concurrent Modification Exception。



##  Java Collections Framework

-   java.util package  
-   The root interface in the Java collections framework is named Collection.   

##    

