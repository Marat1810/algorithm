## 剑指 Offer 06. 从尾到头打印链表

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

**示例 1：**

```
输入：head = [1,3,2]
输出：[2,3,1]
```



解题思路：

先想到将指针反过来

顺序反过来，想到**栈**的特性

```java
import java.util.Arrays;
import java.util.LinkedList;
import java.util.List;
import java.util.Scanner;

public class reverseList {
    public static class ListNode{
        int val;
        ListNode next;
        ListNode(int x){val=x;}
    }
    public static int[] reversePrint(ListNode head){
        LinkedList<Integer> stack = new LinkedList<>();
        int count = 0;
        while (head!=null){
            stack.addLast(head.val);
            head=head.next;
            count++;
        }
        int[] res = new int[count];
        for (int i=0;i<count;i++){
            res[i]=stack.removeLast();
        }
        return res;
    }
    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(3);
        head.next.next = new ListNode(5);
        head.next.next.next = new ListNode(8);
        System.out.println(Arrays.toString(reversePrint(head)));
    }
}
```

