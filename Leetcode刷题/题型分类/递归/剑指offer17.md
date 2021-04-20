## 题目描述：输入数字 n，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。


## 源码
```java
class Solution {
    int res[];
    int count=0;
    public int[] printNumbers(int n) {
     res=new int[(int)Math.pow(10,n)-1];
     for(int digit=1;digit<n+1;digit++){
         for(char first='1';first<='9';first++){
             char num[]=new char[digit];
             num[0]=first;
             dfs(1,num,digit);
         }
     }
   return res;  
}
    public void dfs(int index,char[]num,int digit){
        if(index==digit){
            res[count++]=Integer.parseInt(String.valueOf(num));
            return;
        }
        for(char a='0';a<='9';a++){
            num[index]=a;
            dfs(index+1,num,digit);   //在某次for循环中(continue)的那次，随着return语句的结束，会接着下次for循环,直到某个digit循环结束
        }
    }
}
```
## 源码分析
   1.res[]和count是全局静态变量，避免了递归时传参的麻烦
   2.在某次for循环中(continue)的那次，随着return语句的结束，会接着下次for循环，重在理解。
