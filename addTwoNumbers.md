
# https://leetcode.com/problems/add-two-numbers/
Define a class called ListNode to represent a node in the linked list. Each node has a val (digit) and a next pointer to the next node.



    public function __construct($val = 0, $next = null) {
        $this->val = $val;
        $this->next = $next;
    }

Implement the addTwoNumbers function, which takes two linked lists ($l1 and $l2) as input and returns the sum as a new linked list.




    $dummy = new ListNode(0); // Dummy node to track the head of the result linked list
    
    $current = $dummy; // Pointer to the current node in the result linked list
    $carry = 0; // Carry value initialized to 0
    
    
    while ($l1 != null || $l2 != null) {
        $sum = $carry; // Initialize the sum with the carry value

        // Add the values of the current nodes of l1 and l2, if they exist
        if ($l1 != null) {
            $sum += $l1->val;
            $l1 = $l1->next;
        }
        if ($l2 != null) {
            $sum += $l2->val;
            $l2 = $l2->next;
        }

        $carry = (int)($sum / 10); // Calculate the carry value
        $sum = $sum % 10; // Calculate the remainder (digit)

        $current->next = new ListNode($sum); // Create a new node with the calculated digit
        $current = $current->next; // Move the current pointer forward
    }

    if ($carry > 0) {
        $current->next = new ListNode($carry); // If there's a remaining carry, add it as a new node
    }

    return $dummy->next; // Return the head of the result linked list (excluding the dummy node)
