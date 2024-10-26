# Detect Cycle in a Linked List

This Python script implements a solution to detect if a singly linked list contains a cycle. It's designed to work with HackerRank's environment and includes the necessary boilerplate code for input/output handling.

## Problem Description

Given the head of a singly linked list, determine if it contains a cycle. A linked list is said to contain a cycle if any node is visited more than once while traversing the list.

**Examples:**
1. Input: 1 → 2 → 3 → NULL
   Output: 0 (No cycle)

2. Input: 1 → 2 → 3 → 1 → NULL
   Output: 1 (Cycle detected)

## Function Description

The main logic is implemented in the `has_cycle` function:

```python
def has_cycle(head):
    if not head or not head.next:
        return 0 
    
    slow = head
    fast = head.next

    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        
        if slow == fast:
            return 1
        
    return 0 
```

This function takes the head of a linked list as input and returns 1 if a cycle is detected, 0 otherwise.

## Applications

Cycle detection in linked lists has several practical applications:

1. **Memory Leak Detection**: In memory management systems, cycle detection can help identify circular references that may lead to memory leaks.

2. **Deadlock Detection**: In operating systems and databases, cycle detection algorithms are used to identify potential deadlocks in resource allocation graphs.

3. **Data Integrity**: In data structures like hash tables with separate chaining, detecting cycles can help identify corrupted data structures.

4. **Network Topology**: In computer networks, cycle detection can be used to identify loops in network topologies, which is crucial for routing algorithms.

5. **Garbage Collection**: Some garbage collection algorithms use cycle detection to identify and collect cyclic data structures.

6. **Infinite Loop Detection**: In certain program analysis tools, cycle detection can help identify potential infinite loops in code execution paths.

7. **Graph Algorithms**: Cycle detection is a fundamental operation in many graph algorithms, such as finding strongly connected components.


## Constraints

- 0 ≤ list size ≤ 1000

## Usage

This script is designed to run in HackerRank's environment. To use it locally:

1. Ensure you have Python 3 installed.
2. Modify the input method to accept user input or read from a file.
3. Change the output method to print to console or write to a file.

## Data Structure

The linked list is implemented using the `SinglyLinkedListNode` class:

```python
class SinglyLinkedListNode:
    def __init__(self, node_data):
        self.data = node_data
        self.next = None
```

## Algorithm

The solution uses Floyd's Cycle-Finding Algorithm (also known as the "tortoise and hare" algorithm):

1. Initialize two pointers, `slow` and `fast`, to the head of the list.
2. Move `slow` one step and `fast` two steps at a time.
3. If there's a cycle, `fast` will eventually meet `slow` at some point in the cycle.
4. If `fast` reaches the end of the list (null), there's no cycle.

## Time and Space Complexity

- Time Complexity: O(n), where n is the number of nodes in the linked list
- Space Complexity: O(1), as only two pointers are used regardless of the list size
