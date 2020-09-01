#### 剑指 Offer 18. 删除链表的节点

给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。

返回删除后的链表的头节点。

注意：此题对比原题有改动

示例 1:

输入: head = [4,5,1,9], val = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9.
示例 2:

输入: head = [4,5,1,9], val = 1
输出: [4,5,9]
解释: 给定你链表中值为 1 的第三个节点，那么在调用了你的函数之后，该链表应变为 4 -> 5 -> 9.



解题思路：

- 注意特殊情况：删除的是第一个节点，删除的是最后一个节点



```java
public class deleteNode_18 {
    public class ListNode{
        int val;
        ListNode next;
        ListNode(int x){val=x;}
    }
    
    //val是int类型
    public ListNode deleteNode_1(ListNode head,int val){
        if (head==null) return null;
        if (head.val==val) return head.next;//删除的是第一个节点
        ListNode pre = head, p = head.next;
        while (p!=null){
            if (p.val == val) pre.next = p.next;
            pre=pre.next;
            p=p.next;
        }
        return head;
    }
    
    //val是链表，时间复杂度为O(1)
    public ListNode deleteNode_2(ListNode head,ListNode val){
        if (head==null) return null;
        // 待删除节点不是尾节点
        if (val.next!=null){
            ListNode pnext = val.next;
            val.val = pnext.val;
            val.next = pnext.next;
        }
        //val的next是null的情况有两种  a.val是头节点，且仅此一个节点  b.val是尾节点
        else if (head==val) return null;
        else {
            ListNode pre = head, cur = pre.next;
            while (cur!=null){
                if (cur.val==val.val){
                    pre.next=cur.next;
                }
                pre=pre.next;
                cur=cur.next;
            }
        }
        return head;
    }
}
```

