## 题目描述：
地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，
它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。
例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。
请问该机器人能够到达多少个格子？

## 图解题解了解递归过程，注意图中的返回值
[图解学习链接了解递归过程](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/solution/mian-shi-ti-13-ji-qi-ren-de-yun-dong-fan-wei-dfs-b/)

## 源代码
```java
class Solution {
    boolean [][]visited;
    public int movingCount(int m, int n, int k) {
         visited=new boolean[m][n];
         int result= dfs(m,n,0,0,visited,k);
         return result;
    }
    private int dfs(int m,int n,int row,int colum,boolean[][]visited,int k){
        
         int a=bitSum(row);
         int b=bitSum(colum);
        /* while(row>0){
          a=a+row%10;
          row=row/10;
         }
         while(colum>0){
             b=b+colum%10;
             colum=colum/10;
         }
         */
        
         if(row>=m||colum>=n||(a+b)>k||visited[row][colum])
         return 0;
         visited[row][colum]=true;
         return 1+dfs(m,n,row+1,colum,visited,k)+dfs(m,n,row,colum+1,visited,k);
    }
    private int bitSum(int n) {
        int sum = 0;
        while(n > 0) {
            sum += n % 10;
            n /= 10; 
        }
        return sum;
    }
    
}
```

## 错误分析
1.第21行,27行在计算row,colum的位和时改变了其自身值，导致在后面判断colum>=m已经不是我们所需要的那个colum和row了，
所以最好调用一个函数来计算位和，这样，row和colum值就不会改变了
2.注意终止条件的判别


