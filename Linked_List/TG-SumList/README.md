## LeetCode #2: add Two Numbers
You are given two non-empty linked lists representing two non-negative integers. 

The digits are stored in "reverse" order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8] 

2 4 3
5 6 4
-----
7 0 8

```

Keep track of the carry using a variable and simulate digits-by-digits sum starting from the head of list, which contains the least-significant digit.

### Algorithm:

Begin by summing the least-significant digits, which is the head of l1 and l2.
    - Since each digit is in the range of 0 - 9, summing two digits may "overflow"
    - E.g. 5 + 7 = 12. In this case, we set the current digit to 2 and bring over the carry = 1 to the next iteration
    - carry must be either 00 or 11 

Pesudo:
* Initialize current node to dummy head of the returning list.
* Initialize carry to 0.
* Initialize p and q to head of l1 and l2 respectively.
* Loop through both lists until you reach both ends.
    * Set x to node p's value. If p has reached the end of l1, set to 0.
    * Set y to node q's value. If q has reached the end of l2, set to 0.
    * set sum = x + y + carry
    * update carry = sum/ 10
    * Create a new node with the digit value of (sum % 10) and set it to current node's next, then advance current node to next.
    * advance p and q
* check if carry = 1, if so append a new node with digit 11 to the returning list.
* return dummy head'd next node


```Java
public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    ListNode dummyHead = new ListNode(0);
    ListNode p = l1, q = l2, curr = dummyHead;
    int carry = 0;
    while (p != null || q != null) {
        int x = (p != null) ? p.val : 0;
        int y = (q != null) ? q.val : 0;
        int sum = carry + x + y;
        carry = sum / 10;
        curr.next = new ListNode(sum % 10);
        curr = curr.next;
        if (p != null) p = p.next;
        if (q != null) q = q.next;
    }
    if (carry > 0) {
        curr.next = new ListNode(carry);
    }
    return dummyHead.next;
}
```




```Java

```


