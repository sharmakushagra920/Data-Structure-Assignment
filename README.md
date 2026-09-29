Q1.Design and implement a stack using an array without using any built-in stack library.
Perform the following operations:
 PUSH(x)
 POP()
 PEEK()
 DISPLAY()
Your program must handle both Stack Overflow and Stack Underflow conditions.
Additional Task:
Explain the time complexity and space complexity of each operation. Also discuss what
happens when the stack size is fixed and the user attempts to insert more elements than its
capacity.

Answer-
Aim
To design and implement a stack using an array without using any built-in stack library. The stack should perform:
PUSH(x)
POP()
PEEK()
DISPLAY()
It should also handle Stack Overflow and Stack Underflow conditions.

C Program
#include <stdio.h>
#define MAX 5
int stack[MAX];
int top = -1;
void push(int x)
{
    if (top == MAX - 1)
    {
        printf("Stack Overflow! Stack is full.\n");
    }
    else
    {
        top++;
        stack[top] = x;
        printf("%d pushed into stack.\n", x);
    }
}
void pop()
{
    if (top == -1)
    {
        printf("Stack Underflow! Stack is empty.\n");
    }
    else
    {
        printf("%d popped from stack.\n", stack[top]);
        top--;
    }
}
void peek()
{
    if (top == -1)
    {
        printf("Stack is empty.\n");
    }
    else
    {
        printf("Top element is: %d\n", stack[top]);
    }
}
void display()
{
    if (top == -1){
          printf("Stack is empty.\n");
    }
    else
    {
        printf("Stack elements are:\n");}
    for (int i = top; i >= 0; i--)
        {
            printf("%d\n", stack[i]);
        }
    }
}
int main()
{
    int choice, value;
    while (1)
    {
        printf("\n--- STACK MENU ---\n");
        printf("1. PUSH\n");
        printf("2. POP\n");
        printf("3. PEEK\n");
        printf("4. DISPLAY\n");
        printf("5. EXIT\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice)
        {
            case 1:
                printf("Enter value to push: ");
                scanf("%d", &value);
                push(value);
                break;
            case 2:
                pop();
                break;
            case 3:
                peek();
                break;
            case 4:
                display();
                break;
            case 5:
                printf("Program ended.\n");
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
    return 0;
}

A stack is a linear data structure which follows the LIFO (Last In, First Out) principle. This means the element inserted last will be removed first.

Here, an array named stack is used to store the elements. The variable top keeps track of the top position of the stack.

Initially:

top = -1;

This means that the stack is empty.

1. PUSH Operation

The PUSH operation inserts a new element into the stack.

Before inserting, we check:

if (top == MAX - 1)

If this condition is true, the stack is already full and Stack Overflow occurs.

Otherwise, top is increased and the new value is stored.

2. POP Operation

The POP operation removes the top element from the stack.

If:

top == -1

the stack is empty, so Stack Underflow occurs.

Otherwise, the top element is removed and top is decreased.

3. PEEK Operation

PEEK displays the top element without removing it.

If the stack is empty, it displays an appropriate message.

4. DISPLAY Operation

DISPLAY prints all elements starting from the top element and moving towards the bottom.

Time and Space Complexity of Stack Operations
Operation	Time Complexity	Space Complexity
PUSH	O(1)	O(1)
POP	O(1)	O(1)
PEEK	O(1)	O(1)
DISPLAY	O(n)	O(1)
Entire Stack	—	O(n)

PUSH, POP, and PEEK take constant time because they work only with the top element. DISPLAY takes O(n) because it may need to visit every element.

What happens when the stack has fixed size?

In this program, the stack size is fixed at:

#define MAX 5

So, the stack can store only 5 elements. If the user tries to insert a 6th element, there is no free space in the array. Therefore, Stack Overflow occurs and the new element is not inserted.

For example:

Stack capacity = 5

10
20
30
40
50

If we try:

PUSH(60)
The program displays:
Stack Overflow! Stack is full.
This prevents writing outside the allocated array.

Q2. Implement a Circular Queue using an array. The queue should support:
 ENQUEUE(x)
 DEQUEUE()
 FRONT()
 DISPLAY()
The implementation must correctly distinguish between a full queue and an empty queue.
Additional Task:
Compare the circular queue with a simple linear queue and explain:
Today 6:08 PM
Q1.Design and implement a stack using an array without using any built-in stack library.
Perform the following operations:
 PUSH(x)
 POP()
 PEEK()
 DISPLAY()
Your program must handle both Stack Overflow and Stack Underflow conditions.
Additional Task:
Explain the time complexity and space complexity of each operation. Also discuss what
happens when the stack size is fixed and the user attempts to insert more elements than its
capacity.
Q2. Implement a Circular Queue using an array. The queue should support:
 ENQUEUE(x)
 DEQUEUE()
 FRONT()
 DISPLAY()
The implementation must correctly distinguish between a full queue and an empty queue.
Additional Task:
Compare the circular queue with a simple linear queue and explain:
1. Why a circular queue provides better utilization of memory.
2. Time complexity of ENQUEUE and DEQUEUE.
3. Space complexity of the queue.
4. What problem occurs in a linear queue when REAR reaches the last index even
though unused positions exist at the beginning?
In c bca 2nd year assignment

Sure. Below is a BCA 2nd-year assignment-style answer in C, written in simple and direct language. It includes the programs, explanation, complexity, and required comparison.

Data Structures Assignment
Q1. Stack Implementation Using Array in C
Aim

To design and implement a stack using an array without using any built-in stack library. The stack should perform:

PUSH(x)
POP()
PEEK()
DISPLAY()

It should also handle Stack Overflow and Stack Underflow conditions.

C Program
#include <stdio.h>

#define MAX 5

int stack[MAX];
int top = -1;

// PUSH operation
void push(int x)
{
    if (top == MAX - 1)
    {
        printf("Stack Overflow! Stack is full.\n");
    }
    else
    {
        top++;
        stack[top] = x;
        printf("%d pushed into stack.\n", x);
    }
}

// POP operation
void pop()
{
    if (top == -1)
    {
        printf("Stack Underflow! Stack is empty.\n");
    }
    else
    {
        printf("%d popped from stack.\n", stack[top]);
        top--;
    }
}

// PEEK operation
void peek()
{
    if (top == -1)
    {
        printf("Stack is empty.\n");
    }
    else
    {
        printf("Top element is: %d\n", stack[top]);
    }
}

// DISPLAY operation
void display()
{
    if (top == -1)
    {
        printf("Stack is empty.\n");
    }
    else
    {
        printf("Stack elements are:\n");

        for (int i = top; i >= 0; i--)
        {
            printf("%d\n", stack[i]);
        }
    }
}

int main()
{
    int choice, value;

    while (1)
    {
        printf("\n--- STACK MENU ---\n");
        printf("1. PUSH\n");
        printf("2. POP\n");
        printf("3. PEEK\n");
        printf("4. DISPLAY\n");
        printf("5. EXIT\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice)
        {
            case 1:
                printf("Enter value to push: ");
                scanf("%d", &value);
                push(value);
                break;

            case 2:
                pop();
                break;

            case 3:
                peek();
                break;

            case 4:
                display();
                break;

            case 5:
                printf("Program ended.\n");
                return 0;

            default:
                printf("Invalid choice!\n");
        }
    }

    return 0;
}
Explanation

A stack is a linear data structure which follows the LIFO (Last In, First Out) principle. This means the element inserted last will be removed first.

Here, an array named stack is used to store the elements. The variable top keeps track of the top position of the stack.

Initially:

top = -1;

This means that the stack is empty.

1. PUSH Operation

The PUSH operation inserts a new element into the stack.

Before inserting, we check:

if (top == MAX - 1)

If this condition is true, the stack is already full and Stack Overflow occurs.

Otherwise, top is increased and the new value is stored.

2. POP Operation

The POP operation removes the top element from the stack.

If:

top == -1

the stack is empty, so Stack Underflow occurs.

Otherwise, the top element is removed and top is decreased.

3. PEEK Operation

PEEK displays the top element without removing it.

If the stack is empty, it displays an appropriate message.

4. DISPLAY Operation

DISPLAY prints all elements starting from the top element and moving towards the bottom.

Time and Space Complexity of Stack Operations
Operation	Time Complexity	Space Complexity
PUSH	O(1)	O(1)
POP	O(1)	O(1)
PEEK	O(1)	O(1)
DISPLAY	O(n)	O(1)
Entire Stack	—	O(n)

PUSH, POP, and PEEK take constant time because they work only with the top element. DISPLAY takes O(n) because it may need to visit every element.

What happens when the stack has fixed size?

In this program, the stack size is fixed at:

#define MAX 5

So, the stack can store only 5 elements. If the user tries to insert a 6th element, there is no free space in the array. Therefore, Stack Overflow occurs and the new element is not inserted.

For example:

Stack capacity = 5

10
20
30
40
50

If we try:

PUSH(60)

the program displays:

Stack Overflow! Stack is full.

This prevents writing outside the allocated array memory.

Q2. Circular Queue Implementation Using Array in C
Aim

To implement a Circular Queue using an array with the following operations:

ENQUEUE(x)
DEQUEUE()
FRONT()
DISPLAY()

The implementation should correctly identify both full and empty conditions.

C Program
#include <stdio.h>
#define MAX 5
int queue[MAX];
int front = -1;
int rear = -1;
void enqueue(int x)
{
    if ((rear + 1) % MAX == front)
    {
        printf("Queue Overflow! Queue is full.\n");
        return;
    }
    if (front == -1)
    {
        front = 0;
        rear = 0;
    }
    else
    {
        rear = (rear + 1) % MAX;
    }
    queue[rear] = x;
    printf("%d inserted into queue.\n", x);
}
void dequeue()
{
    if (front == -1)
    {
        printf("Queue Underflow! Queue is empty.\n");
        return;
    }
    printf("%d deleted from queue.\n", queue[front]);
    if (front == rear)
    {
        front = -1;
        rear = -1;
    }
    else
    {
        front = (front + 1) % MAX;
    }
}
void showFront()
{
    if (front == -1)
    {
        printf("Queue is empty.\n");
    }
    else
    {
        printf("Front element is: %d\n", queue[front]);
    }
}
void display()
{
    if (front == -1)
    {
        printf("Queue is empty.\n");
        return;
    }
    printf("Queue elements are:\n");
    int i = front;
    while (1)
    {
        printf("%d ", queue[i]);
        if (i == rear)
            break;
            i = (i + 1) % MAX;
    }
    printf("\n");
}

int main()
{
    int choice, value;
    while (1)
    {
        printf("\n--- CIRCULAR QUEUE MENU ---\n");
        printf("1. ENQUEUE\n");
        printf("2. DEQUEUE\n");
        printf("3. FRONT\n");
        printf("4. DISPLAY\n");
        printf("5. EXIT\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice)
        {
            case 1:
                printf("Enter value to insert: ");
                scanf("%d", &value);
                enqueue(value);
                break;
            case 2:
                dequeue();
                break;
            case 3:
                showFront();
                break;
            case 4:
                display();
                break;
            case 5:
                printf("Program ended.\n");
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
    return 0;
}
Explanation

A queue follows the FIFO (First In, First Out) principle. The element inserted first is removed first.
A circular queue is different from a simple linear queue because the last position of the array is connected back to the first position.
In the program, two variables are used:
front → points to the first element.
rear → points to the last element.
The circular movement is achieved using:
(rear + 1) % MAX
and
(front + 1) % MAX
This allows the queue to move back to index 0 after reaching the last index.

1. Why a circular queue provides better utilization of memory.
Answer-
In a simple linear queue, once rear reaches the last index, new elements cannot normally be inserted even if some positions at the beginning of the array have become empty after deletion.
A circular queue solves this problem by allowing rear to move back to the beginning of the array. Therefore, the empty positions can be reused.
For example:
After some deletions:
[ _ ][ _ ][30][40][50]
          F         R
In a linear queue, the first two empty positions may remain unused.
In a circular queue, new elements can use those positions:
[60][70][30][40][50]
So, memory is used more efficiently.

2. Time complexity of ENQUEUE and DEQUEUE.
Answer-
Both operations take:
ENQUEUE = O(1)
DEQUEUE = O(1)
Only the front or rear position needs to be changed, so no shifting of elements is required.

3. Space complexity of the queue.
Answer-
If the queue has a capacity of n, the array requires:
O(n)
space.
For this program:
#define MAX 5
so the queue can store a maximum of 5 elements.

4. What problem occurs in a linear queue when REAR reaches the last index even
though unused positions exist at the beginning?
Answer-
Suppose the queue has 5 positions:
[10][20][30][40][50]
After deleting the first two elements:
[__][__][30][40][50]
There are two unused positions at the beginning. However, if rear is already at the last index, a simple linear queue may report that the queue is full and will not insert another element.
This situation is sometimes called false overflow.
A circular queue avoids this problem by wrapping rear around to the beginning and using the available positions.
