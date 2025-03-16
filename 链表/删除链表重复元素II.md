82 删除链表重复元素II

https://leetcode.cn/problems/remove-duplicates-from-sorted-list-ii/description/?envType=study-plan-v2&envId=top-interview-150



``` java

class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy = new ListNode(0, head);
        ListNode cur = dummy;
        while(cur.next != null && cur.next.next != null){
            int val = cur.next.val;
            // 看下一个节点和下下一个节点的值是否一样
            if(val == cur.next.next.val){
                while(cur.next != null && cur.next.val == val){
                    //删除下一个节点
                    cur.next = cur.next.next;
                }
            } else {
                cur = cur.next;
            }
        }
        return dummy.next;
        
    }
}
```

