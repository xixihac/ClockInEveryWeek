### Leetcode地址

https://leetcode-cn.com/problems/path-sum-iii/

代码如下：

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int res = 0;
    public int pathSum(TreeNode root, int targetSum) {
        if(root==null){
            return 0;
        }
        recursion(root,targetSum);
        pathSum(root.left,targetSum);
        pathSum(root.right,targetSum);
        return res;

    }

    public void recursion(TreeNode root,int sum){
        if(root==null){
            return;
        }
        if(sum == root.val){
            res++;
        }
        recursion(root.left,sum-root.val);
        recursion(root.right,sum-root.val);
        
    }
}
```

