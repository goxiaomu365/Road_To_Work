## 1.题目描述
输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。
序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

## 2.解题思路
从初始位置i=0到i=target/2进行枚举，注意一旦初始位置固定，若满足条件，则最终的位置也是固定的，也即一个初始位置最多只对应一个解
最后注意不规则二维数组的表述方法，笔记里已经记录

## 3.源代码
```java
class Solution {
    public int[][] findContinuousSequence(int target) {
       List<int[]>res=new ArrayList<>();
       int index=(target-1)/2;
       int sum=0;
       for(int i=1;i<=index;i++){
           for(int j=i;;j++){
               sum+=j;
               if(sum>target){
                   sum=0;
                   break;
               }else if(sum==target){
                   int []temp=new int[j-i+1];
                   for(int k=i;k<=j;k++)
                   temp[k-i]=k;
                   res.add(temp);
                   sum=0;
                   break;
               }
           }
       }
       return res.toArray(new int[res.size()][]);
    }
}
```
