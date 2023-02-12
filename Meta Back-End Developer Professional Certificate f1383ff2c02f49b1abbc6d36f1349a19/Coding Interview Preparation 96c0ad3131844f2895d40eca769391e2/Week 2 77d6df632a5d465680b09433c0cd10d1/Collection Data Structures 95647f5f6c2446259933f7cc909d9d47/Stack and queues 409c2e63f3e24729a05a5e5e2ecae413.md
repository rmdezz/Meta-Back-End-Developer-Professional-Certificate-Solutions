# Stack and queues

# Introduction

In this guide, you will learn about two important data structures, Stacks and Queues, and understand the differences between them. These data structures are commonly used in programming languages and provide a structured way of accessing and inserting data.

# Stack

## What is a Stack?

A stack is a linear data structure with strict rules for adding and removing items. The name "stack" refers to the concept that items are stacked on top of each other, like a deck of cards. Stacks operate on a First-In, Last-Out (FILO) or Last-In, First-Out (LIFO) basis, meaning that items can only be retrieved from the top of the stack.

## Methods of a Stack:

- Push: Adds an item to the top of the stack.
- Pop: Removes the item from the top of the stack.
- Peek: Views the top item without removing it from the stack.
- isEmpty: Returns true if the stack is empty.
- isFull: Returns true if the stack is full.

## Example

Suppose you have a deck of cards represented as a stack. Each time a card is dealt, it is removed from the top of the stack, just as in a real deck. Using a stack in this way simplifies the code required for maintaining the state of the deck.

```python
deck = [] # initialize an empty deck

# add cards to the deck
deck.push("Ace of Spades")
deck.push("King of Hearts")
deck.push("Queen of Diamonds")

# peek at the top card without removing it
print(deck.peek()) # Output: "Queen of Diamonds"

# remove the top card
deck.pop()
print(deck.peek()) # Output: "King of Hearts"
```

# Queues

## What is a queue?

A queue is similar to a stack, but operates on a First-In, First-Out (FIFO) basis. A queue is like a line of people waiting in line, where the first person to enter the line gets served first, and each subsequent customer stands behind the one in front.

## Methods of a queue

- Enqueue: Adds an item to the end of the queue.
- Dequeue: Removes the item from the front of the queue.
- Peek: Views the front item without removing it from the queue.
- isEmpty: Returns true if the queue is empty.
- isFull: Returns true if the queue is full.

## Example

Imagine a server balancing system that uses a queue to retrieve tasks. The queue holds each task in order of insertion, and when a server becomes available to process the task, the first task entered into the queue is removed and passed to that server.

```python
queue = [] # initialize an empty queue

# add tasks to the queue
queue.enqueue("Task 1")
queue.enqueue("Task 2")
queue.enqueue("Task 3")

# peek at the front task without removing it
print(queue.peek()) # Output: "Task 1"

# remove the front task
queue.dequeue()
print(queue.peek()) # Output: "Task 2"
```

# Conclusion

In conclusion, stacks and queues are two important data structures that are useful to have in your programming toolkit. They have their own strengths and weaknesses, and knowing when to use them will give you an advantage when dealing with problems requiring a structured way of accessing and inserting data. 

Stacks work on a Last-In, First-Out (LIFO) basis, where elements can only be retrieved from the top of the stack. 

Queues work on a First-In, First-Out (FIFO) basis, where elements are processed in the order in which they are added to the queue. 

Understanding these concepts and being able to implement them effectively will help you to write more efficient and effective code.