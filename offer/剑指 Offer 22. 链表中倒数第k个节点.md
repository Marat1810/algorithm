#### 剑指 Offer 22. 链表中倒数第k个节点

输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。例如，一个链表有6个节点，从头节点开始，它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个节点是值为4的节点。

 

示例：

给定一个链表: 1->2->3->4->5, 和 k = 2.

返回链表 4->5.



解题思路：双指针，先走k-1步，再一起走

注意几个特殊情况：

1、头指针为空

2、k<=0

3、**k大于链表的长度**



```java
public class GetKthNode_22 {
    public class ListNode{
        int val;
        ListNode next;
        ListNode(int x){val=x;}
    }
    public ListNode getKthNode(ListNode head,int k){
        //头节点为空的情况,k<=0无意义
        if (head==null||k<=0) return null;
        //只有头节点的情况
        if (head.next==null) return head;
        ListNode p=head,q=head;
        while (k-1>0){
            //防止 k 大于链表长度的情况出现
            if (q.next!=null){
                q=q.next;
                k--;
            }
            else return null;
        }
        while (q.next!=null){
            p=p.next;
            q=q.next;
        }
        return p;
    }
}
```

