117 [填充每个节点的下一个右侧节点指针 II](https://leetcode.cn/problems/populating-next-right-pointers-in-each-node-ii/)



``` java

class Solution {
    public Node connect(Node root) {
        if(root == null) {
            return null;
        }
        
        List<Node> queue = new ArrayList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            // 用于遍历
            List<Node> temp = queue;
            // queue的引用为空的ArrayList temp不变
            queue = new ArrayList<>();
            for(int i = 0; i < temp.size(); i++){
                Node node = temp.get(i);
                if (i > 0) {
                    // 前一个node的next 放在当前的
                    temp.get(i-1).next = node;
                }
                if(node.left != null){
                    queue.add(node.left);
                }
                if (node.right != null) {
                    queue.add(node.right);
                }
            }
        }
        return root;
    }
}
```

