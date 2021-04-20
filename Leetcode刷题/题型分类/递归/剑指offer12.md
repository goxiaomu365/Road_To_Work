## 题目描述：
给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false 。
单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

## 题解分析
[题解分析](https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof/solution/mian-shi-ti-12-ju-zhen-zhong-de-lu-jing-shen-du-yo/)
看DFS分析过程中的动态图，尤其是返回那一部分
还要多理解递归终条件那一块

## 源代码
```java
class Solution {
    public boolean exist(char[][] board, String word) {
     int m=board.length;
     int n=board[0].length;
     //char[]words=word.toCharArray();
     for(int i=0;i<m;i++){
         for(int j=0;j<n;j++)
        if(dfs(board,i,j,0,word))
        return true;
     }  
     return false;
}
    public boolean dfs(char[][]board,int i,int j,int index,String word){
        if(i<0||i>=board.length||j<0||j>=board[0].length||board[i][j]!=word.charAt(index))    //递归终止条件
        return false;
        if(index==word.length()-1)     //递归终止条件
        return true;
        board[i][j]='\0';
        boolean res=dfs(board,i+1,j,index+1,word)||dfs(board,i-1,j,index+1,word)||dfs(board,i,j+1,index+1,word)||dfs(board,i,j-1,index+1,word);
        board[i][j]=word.charAt(index);    //分析：递归搜索匹配字符串过程中，需要 board[i][j] = '/' 来防止 ”走回头路“ 。当匹配字符串不成功时，会回溯返回，此时需要board[i][j] = tmp    来”取消对此单元格的标记”。 在DFS过程中，每个单元格会多次被访问的， board[i][j] = '/'只是要保证在当前匹配方案中不要走回头路。注意当前匹配方案这几个词
            return res;
    }
}
```



