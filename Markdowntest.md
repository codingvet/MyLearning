# 1.AAAAA

-   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA 

    -   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
    -   AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

-   回到上级标题，连续回车

-   BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB

    -   BBBBBBBBBBBBBBBBBBBBBBBBBBB

    -   代码块

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

    -   注释
    
    



##  1.1BBBB

-   BBBBBBBBBBBB



###   1.1.1CCCCC

CCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCC



# 2.DDDDDDDDDDDDDD

##  2.1 EEEEEEEEEE

###   2.1.1FFFFFFFFFFFFFFFFFFFF















































































































