437 路径总和III

https://leetcode.cn/problems/path-sum-iii/?envType=study-plan-v2&envId=top-100-liked



``` java
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
    int ans = 0;
    public int pathSum(TreeNode root, int targetSum) {
        Map<Long, Integer> count = new HashMap<>();
        count.put(0L,1);
        dfs(root, 0, targetSum, count);
        return ans;
    }

    private void dfs(TreeNode node, long sum, int targetSum, 
                Map<Long, Integer> count){
        if (node == null) {
            return ;    
        }
        sum += node.val;
        ans += count.getOrDefault(sum - targetSum, 0);
        // 计算前缀和
        count.merge(sum, 1, Integer::sum);
        dfs(node.left, sum, targetSum, count);
        dfs(node.right, sum, targetSum, count);
        // 恢复到递归前原来的值，否则如果同层级还有其他节点，那么就会出现
        // 涉及到的左子树的节点的个数，计算出的正确答案会更大
        count.merge(sum, -1, Integer::sum);
    }
}
```

