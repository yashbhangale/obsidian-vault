

https://neetcode.io/practice?tab=blind75

![[Pasted image 20250529121142.png]]



![[Pasted image 20250529123125.png]]


### Method 1 : with the help of stack
```java
class Solution {
    public ListNode reverseList(ListNode head) {
        Stack<Integer> valueStack = new Stack<>();
        while (head != null) {
            valueStack.push(head.val);
            head = head.next;
        }

        ListNode reversedList = new ListNode(Integer.MIN_VALUE);
        ListNode ptr = reversedList;

        while (!valueStack.isEmpty()) {
            ptr.next = new ListNode(valueStack.pop());
            ptr = ptr.next;
        }
        return reversedList.next;
    }
}
```

#### time complexity : o(n), Space complexity o(n)

not that efficient we have to reduce space complexity

### Method 2 (with out using any DS here we can reduse space complexity o(1))


reference : https://youtu.be/3IN0BP9Ni6E?t=521 


```java
class Solution {
    public ListNode reverseList(ListNode head) {

        if (head == null){
            return null;
        }

        if (head.next == null){
            return head;
        }

        ListNode preNode = null;
        ListNode currNode = head;

        while (currNode != null) {
            ListNode nextNode = currNode.next;
            currNode.next = preNode;
            preNode = currNode;
            currNode = nextNode;
        }

        head = preNode;
        return head;
    }
}
```
