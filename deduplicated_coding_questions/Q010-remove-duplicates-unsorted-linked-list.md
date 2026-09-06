# Q010 — Remove Duplicates from Unsorted Linked List

## Student Question

Remove Duplicates from Unsorted Linked List

Consider an implementation of a singly linked list, where each node is created using the given class Node. Suppose it has a head variable that contains the reference to the first node of the linked list.

You are given non-empty unsorted singly linked list containing integers. Your task is to remove all duplicate elements from the list. The relative order of the first occurrence of distinct elements should be preserved in the output linked fist.

Complete the function remove_duplicate(head), that removes nodes with duplicate values from the given linked list. The function should modify the same input-linked list and should Not return any value.

**Sample input**
```text
1 3 1 2 1 3 3 4 7 4 1 5 9 9
```

**Output**
```text
Output Linked List: 1 3 2 4 7 5 9
```

### Student Function
```python
def remove_duplicate(head):
```

## Full Reference Code
```python
class Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None

def remove_duplicate(head):
    if not head:
        return
    seen = set()
    seen.add(head.data)
    current_node = head
    while current_node.next:
        if current_node.next.data in seen:
            current_node.next = current_node.next.next
        else:
            seen.add(current_node.next.data)
            current_node = current_node.next

def create_linked_list(values):
    head = Node(values[0])
    current_node = head
    for value in values[1:]:
        current_node.next = Node(value)
        current_node = current_node.next
    return head
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/RemoveDuplicaresFromUnsortedLinkedList.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
