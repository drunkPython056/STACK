Stack and Queue in C++

This README explains the implementation of Stack and Queue using arrays in C++.

1. Stack

What is a Stack?

A Stack is a linear data structure that follows the:

LIFO — Last In, First Out

This means the element inserted last is removed first.

Example

If we insert:

10 → 20 → 30

The top of the stack is:

30

If we perform pop(), 30 is removed first.

30 ← removed
20
10

Stack Representation

       TOP
        ↓
      | 30 |
      | 20 |
      | 10 |
      ------

The variable top keeps track of the top element.

Initially:

top = -1;

This means the stack is empty.

Stack Operations

1. Push

push() is used to insert an element into the stack.

Working

Check whether stack is full
        ↓
Increase top
        ↓
Store element at stack[top]

Example:

void push(int value)
{
    if (top == MAX - 1)
    {
        cout << "Stack Overflow";
        return;
    }

    top++;
    stack[top] = value;
}

2. Pop

pop() removes the top element.

Working

Check whether stack is empty
        ↓
Access stack[top]
        ↓
Decrease top

Example:

void pop()
{
    if (top == -1)
    {
        cout << "Stack Underflow";
        return;
    }

    cout << stack[top];
    top--;
}

3. Display

Display prints elements from top to the bottom.

void display()
{
    if (top == -1)
    {
        cout << "Stack is empty";
        return;
    }

    for (int i = top; i >= 0; i--)
    {
        cout << stack[i] << " ";
    }
}

Stack Conditions

Stack Overflow

Occurs when we try to insert an element into a full stack.

top == MAX - 1

Stack Underflow

Occurs when we try to delete an element from an empty stack.

top == -1

2. Queue

What is a Queue?

A Queue is a linear data structure that follows:

FIFO — First In, First Out

This means the element inserted first is removed first.

Example

If we insert:

10 → 20 → 30

Then 10 will be removed first.

FRONT                 REAR
  ↓                     ↓
| 10 | 20 | 30 |

Queue Representation

A queue uses two important variables:

front — points to the first element

rear — points to the last element

Initially:

front = -1;
rear = -1;

This means the queue is empty.

Queue Operations

1. Enqueue

enqueue() is used to insert an element into the queue.

The element is inserted at the rear.

Working

Check whether queue is full
        ↓
Set front if necessary
        ↓
Increase rear
        ↓
Store element at queue[rear]

Example:

void enqueue(int value)
{
    if (rear == MAX - 1)
    {
        cout << "Queue Overflow";
        return;
    }

    if (front == -1)
        front = 0;

    rear++;
    queue[rear] = value;
}

2. Dequeue

dequeue() removes an element from the front.

Working

Check whether queue is empty
        ↓
Access queue[front]
        ↓
Increase front

Example:

void dequeue()
{
    if (front == -1 || front > rear)
    {
        cout << "Queue Underflow";
        return;
    }

    cout << queue[front];
    front++;
}

3. Display

Display prints the elements from front to rear.

void display()
{
    if (front == -1 || front > rear)
    {
        cout << "Queue is empty";
        return;
    }

    for (int i = front; i <= rear; i++)
    {
        cout << queue[i] << " ";
    }
}

Queue Conditions

Queue Overflow

Occurs when the queue is full.

For the simple linear array implementation:

rear == MAX - 1

Queue Underflow

Occurs when the queue is empty.

front == -1

or after all elements have been removed:

front > rear

Stack vs Queue

Feature

Stack

Queue

Principle

LIFO

FIFO

Full Form

Last In First Out

First In First Out

Insertion

push()

enqueue()

Deletion

pop()

dequeue()

Main Pointer

top

front, rear

Insertion Location

Top

Rear

Deletion Location

Top

Front

Complete Stack Program

#include <iostream>
using namespace std;

#define MAX 5

int stack[MAX];
int top = -1;

void push(int value)
{
    if (top == MAX - 1)
    {
        cout << "Stack Overflow" << endl;
        return;
    }

    top++;
    stack[top] = value;
}

void pop()
{
    if (top == -1)
    {
        cout << "Stack Underflow" << endl;
        return;
    }

    cout << "Deleted element: " << stack[top] << endl;
    top--;
}

void display()
{
    if (top == -1)
    {
        cout << "Stack is empty" << endl;
        return;
    }

    for (int i = top; i >= 0; i--)
    {
        cout << stack[i] << " ";
    }

    cout << endl;
}

int main()
{
    push(10);
    push(20);
    push(30);

    cout << "Stack: ";
    display();

    pop();

    cout << "After pop: ";
    display();

    return 0;
}

Output

Stack: 30 20 10
Deleted element: 30
After pop: 20 10

Complete Queue Program

#include <iostream>
using namespace std;

#define MAX 5

int queue[MAX];
int front = -1;
int rear = -1;

void enqueue(int value)
{
    if (rear == MAX - 1)
    {
        cout << "Queue Overflow" << endl;
        return;
    }

    if (front == -1)
        front = 0;

    rear++;
    queue[rear] = value;
}

void dequeue()
{
    if (front == -1 || front > rear)
    {
        cout << "Queue Underflow" << endl;
        return;
    }

    cout << "Deleted element: " << queue[front] << endl;
    front++;
}

void display()
{
    if (front == -1 || front > rear)
    {
        cout << "Queue is empty" << endl;
        return;
    }

    for (int i = front; i <= rear; i++)
    {
        cout << queue[i] << " ";
    }

    cout << endl;
}

int main()
{
    enqueue(10);
    enqueue(20);
    enqueue(30);

    cout << "Queue: ";
    display();

    dequeue();

    cout << "After dequeue: ";
    display();

    return 0;
}

Output

Queue: 10 20 30
Deleted element: 10
After dequeue: 20 30

Time Complexity

Operation

Stack

Queue

Insert

O(1)

O(1)

Delete

O(1)

O(1)

Display

O(n)

O(n)

Easy Way to Remember

Stack

PUSH → Insert

POP → Delete

TOP → Tracks top element

LIFO → Last In, First Out

     PUSH ↓
    | 30 |
    | 20 |
    | 10 |
     ----
     POP ↑

Queue

ENQUEUE → Insert

DEQUEUE → Delete

REAR → Insertion

FRONT → Deletion

FIFO → First In, First Out

ENQUEUE → | 10 | 20 | 30 | → DEQUEUE
             ↑          ↑
           FRONT       REAR
