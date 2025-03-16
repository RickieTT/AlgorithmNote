25 k个一组翻转链表

https://leetcode.cn/problems/reverse-nodes-in-k-group/?envType=study-plan-v2&envId=top-interview-150





``` java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseKGroup(ListNode head, int k) {
        // 先统计一共有多少个节点
        int count = 0;
        for(ListNode i = head; i != null; i = i.next){
            count++;
        }

        // 哨兵节点
        ListNode dummy = new ListNode(0, head);
        // 前置节点
        ListNode pre = null;
        // 当前节点
        ListNode cur = head;
        ListNode p0 = dummy;

        // k个一组处理
        for(int i = count; i >= k; i -= k ){
            for(int j = 0; j < k; j++){
                ListNode next = cur.next;
                cur.next= pre;
                pre = cur;
                cur = next;
            }
            // 将现在的next赋值 为之前p0的next
            ListNode next = p0.next;
            // 此时已经是k之后的那个节点了
            p0.next.next = cur;
            p0.next = pre;
            p0 = next;
        }
        return dummy.next;
    }
}
```

