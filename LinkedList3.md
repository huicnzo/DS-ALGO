A node can be added in three ways 
1) At the front of the linked list 
2) After a given node. 
3) At the end of the linked list.

# Add a node at the front: (4 steps process)
The new node is always added before the head of the given Linked List. And newly added node becomes the new head of the Linked List. 


```
/* Given a reference (pointer to pointer)
to the head of a list and an int,
inserts a new node on the front of the list. */
void push(Node** head_ref, int new_data)
{
	/* 1. allocate node */
	Node* new_node = new Node();

	/* 2. put in the data */
	new_node->data = new_data;

	/* 3. Make next of new node as head */
	new_node->next = (*head_ref);

	/* 4. move the head to point to the new node */
	(*head_ref) = new_node;
}
```

Time complexity of push() is O(1) as it does a constant amount of work.


# Add a node after a given node: (5 steps process) 
We are given a pointer to a node, and the new node is inserted after the given node.

```
// Given a node prev_node, insert a
// new node after the given
// prev_node
void insertAfter(Node* prev_node, int new_data)
{

	// 1. Check if the given prev_node is NULL
	if (prev_node == NULL)
	{
		cout << "the given previous node cannot be NULL";
		return;
	}

	// 2. Allocate new node
	Node* new_node = new Node();

	// 3. Put in the data
	new_node->data = new_data;

	// 4. Make next of new node as
	// next of prev_node
	new_node->next = prev_node->next;

	// 5. move the next of prev_node
	// as new_node
	prev_node->next = new_node;
}

```

Time complexity of insertAfter() is O(1) as it does a constant amount of work.

# Add a node at the end: (6 steps process) 
The new node is always added after the last node of the given Linked List.
ince a Linked List is typically represented by the head of it, we have to traverse the list till the end and then change the next to last node to a new node.
```
// Given a reference (pointer to pointer) to the head
// of a list and an int, appends a new node at the end
void append(Node** head_ref, int new_data)
{

	// 1. allocate node
	Node* new_node = new Node();

	// Used in step 5
	Node *last = *head_ref;

	// 2. Put in the data
	new_node->data = new_data;

	// 3. This new node is going to be
	// the last node, so make next of
	// it as NULL
	new_node->next = NULL;

	// 4. If the Linked List is empty,
	// then make the new node as head
	if (*head_ref == NULL)
	{
		*head_ref = new_node;
		return;
	}

	// 5. Else traverse till the last node
	while (last->next != NULL)
		last = last->next;

	// 6. Change the next of last node
	last->next = new_node;
	return;
}

```

Time complexity of append is O(n) where n is the number of nodes in linked list. Since there is a loop from head to end, the function does O(n) work. 
This method can also be optimized to work in O(1) by keeping an extra pointer to the tail of linked list/
