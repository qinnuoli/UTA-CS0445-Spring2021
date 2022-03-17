# Week 10 Lecture 1

### Circular Doubly Linked Lists

When compared to Singly Linked List:

Pro: `insertAtTail` and `removeAtTail` is more efficient, O(1)

Con: use more memory on the `prev` pointers for each Node

When there is no Node in the circular doubly linked list:

`head` points to `null`

When there is only one Node in the circular doubly linked list:

- `head` points to the only Node
- `head.next` points to itself
- `head.prev` also points to itself

```java
insertAtFront(T data)
{
	// if empty, create a new Node and have `head` point to it
	CDLL_Node head = new CDLL_Node(data='A');
	head.setPrev(head);
	head.setNext(head);
	
	// else, `head` is not empty

	// example: head -> A <-> B <-> C <-> D <- head
	CDLL_Node newNode = new CDLL_Node(data='E', prev=head.prev, next=head);
	// we just made E points to D as prev and A as next
	
	head.prev = newNode; // A's prev points back to E
	head.prev.next = newNode; // D's next points to E
	head = newNode; // updates head
}
```

Code reuse:

- If `insertAtTail()`, call `insertAtFront()` and undo the last step
- What if we have written `insertAtTail()` first instead? How do we go about writing `insertAtFront()` then?
    - Call `insertAtTail()` and adjust the `head`

```java
int size(T data)
{
	// just to stimulate thinking on how to traverse a CDLL
}
```

### Interfaces

The user should not need to concern himself with HOW the functionality is implemented; rather, he should only need to know WHAT it offers/WHAT it can do.