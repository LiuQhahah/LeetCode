## [21. Merge Two Sorted Lists 合并两个排好序的链表](https://leetcode.com/problems/merge-two-sorted-lists/description/)


合并两个排序后的链接列表并将其作为新列表返回。 新列表应通过拼接前两个列表的节点来完成。

### Example:

      Input: 1->2->4, 1->3->4
      Output: 1->1->2->3->4->4


### 思路1 递归

    class Solution {

      //递归
      public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
          if(l1==null) return l2;
          if(l2==null) return l1;
          if(l1.val<l2.val){
              l1.next = mergeTwoLists(l1.next,l2);
              System.out.println("l1.next: "+l1.toString());
              return l1;
          }else{
              l2.next = mergeTwoLists(l1,l2.next);
               System.out.println("l2.next: "+l2.toString());
              return l2;
          }
      }
  }

### 思路2 迭代


    class Solution {
        public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
            ListNode head = new ListNode(0);
            ListNode temp = head;
            while (l1 != null && l2 != null) {
                if (l1.val < l2.val) {
                    temp.next = l1;
                    l1 = l1.next;
                } else {
                    temp.next = l2;
                    l2 = l2.next;
                }
                temp = temp.next;
            }
            temp.next = l1 != null ? l1 : l2;
            return head.next;
        }
    }
