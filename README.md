# Palindrome-Linked-List



class Solution {

    public ListNode reverse(ListNode head){
        if(head == null || head.next == null){
            return head;
        }
         ListNode prev = head;
         ListNode curr = head.next;
         while(curr != null){
             ListNode next = curr.next;
             curr.next = prev;
             prev= curr;
             curr  = next;
         }
         head.next = null;
         head = prev;
         return head;
    }

    
   public ListNode firstMiddle( ListNode head)
   {
       ListNode hare=head;
       ListNode turtle=head;
       while(hare.next!=null && hare.next.next!=null){
           hare=hare.next.next;
           turtle=turtle.next;
       }
       return turtle;
   }
    
    
    //Main 
    public boolean isPalindrome(ListNode head) {
        if(head==null && head.next==null){
            return true;
        }
        ListNode  middle =firstMiddle(head);
        ListNode secondfirst=reverse(middle.next);
        ListNode firststart=head;
        while(secondfirst!=null){
            if(firststart.val!=secondfirst.val){
                return false;
            }
            firststart=firststart.next;
            secondfirst=secondfirst.next;
            
        }
       return true;
    }
}
