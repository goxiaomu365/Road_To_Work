## 1.题目描述
请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

## 2.题解：
与３２－ＩＩ相似，只不过在添加的时候的一个临时容器ｔｅｍｐ需要根据ｒｅｓ的大小选择进行ａｄｄＦｉｓｒｔ操作还是ａｄｄＬａｓｔ操作


## 3.源代码
```java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
     List<List<Integer>>res=new ArrayList<>();
     Queue<TreeNode>queue=new LinkedList<>();
     if(root!=null)
     queue.offer(root);
     while(!queue.isEmpty()){
         LinkedList<Integer>temp=new LinkedList<>();
         for(int i=queue.size();i>0;i--){
             TreeNode node=queue.poll();
             if(res.size()%2==0)
             temp.addLast(node.val);
             else
             temp.addFirst(node.val);
             if(node.left!=null)
             queue.offer(node.left);
             if(node.right!=null)
             queue.offer(node.right);
         }
         res.add(temp);
     }
     return res;
    }
}
  ｀｀｀

