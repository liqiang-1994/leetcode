### Invert Binary Tree

* Invert a binary tree.

``` 
    4
   /   \
  2     7
 / \   / \
1   3 6   9

to
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```
* 反转二叉树
``` java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root == null) return null;
        if(root.left==null && root.right==null) return root;
        
        TreeNode temp = invertTree(root.left);
        root.left = invertTree(root.right);
        root.right = temp;
        return root;
    }
}
```
``` java
public class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root==null) return null;
        Deque<TreeNode> stack = new LinkedList<>();
        stack.push(root);
        
        while(!stack.isEmpty()){
             TreeNode node = stack.pop();
             TreeNode left = node.left;
             node.left = node.right;
             node.right= left;
             
             if(node.left!=null) {
                 stack.push(node.left);
              }
              if(node.right!=null) {
                 stack.push(node.right);
              }
        }
        return root;
    }
}
```
* 按水平顺序遍历：E poll(),获取并移除此列表的头，boolean offer(E e),将指定元素添加到此列表的末尾
``` java
public class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root ==null) return null;
        Deque<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        
        while(!queue.isEmpty()) {
            TreeNode node=queue.poll();
            TreeNode left = node.left;
            node.left = node.right;
            node.right = left;
            
            if(node.left!=null) queue.offer(node.left);
            if(node.right!=null) queue.offer(node.right);
         }
        return root;
    }
}
```