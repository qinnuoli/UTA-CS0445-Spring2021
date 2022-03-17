# Week 5 Lecture 1

### Definition of Recursion

- A problem solving technique where an algorithm is defined in terms of itself
- A recursive method is a method that calls itself
- A recursive algorithm breaks down the input or the search space and applies the same logic to a smaller and smaller piece of the problem until the remaining piece is solvable without recursion

### Purpose of Writing Helper Methods

`main()` calls public methods to perform some action

public methods calls private, helper methods

### Illustration of `size()`

```java
public int size()
{
	return sizeHelper(this.head);
}

private int sizeHelper(Node<T> head)
{
	if (head == null) return 0;
	return 1 + sizeHelper(head.next);
}
```

### Call Stack of `sizeHelper()`

![Screen Shot 2022-02-08 at 9.01.41 PM.png](Week%205%20Lec%20e882f/Screen_Shot_2022-02-08_at_9.01.41_PM.png)

### Copy Constructor

```java
// in main: copy constructor
LinkedList<T> LL2 = new LinkedList<T>(LL1);

// in linked list class: shallow copy vs. deep copy
public LinkedList(LinkedList<T> other)
{
	head = other.head;
}

public LinkedList(LinkedList<T> other)
{
	for (Node<T> curr = other.head; curr != null; curr = curr.next)
	{
		// start from the first node in `other`
		// and copy each node into `this` list 
		insertAtTail(curr.data);
	}
}
```