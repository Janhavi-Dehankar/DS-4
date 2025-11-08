# DS-4
DS code
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int arr[SIZE];
int front1 = -1, rear1 = -1;
int front2 = SIZE, rear2 = SIZE;

void enqueue1(int x) {
    if (rear1 + 1 == rear2)
        printf("Queue Overflow in Queue 1\n");
    else {
        if (front1 == -1) front1 = 0;
        arr[++rear1] = x;
    }
}

void enqueue2(int x) {
    if (rear1 + 1 == rear2)
        printf("Queue Overflow in Queue 2\n");
    else {
        if (front2 == SIZE) front2 = SIZE - 1;
        arr[--rear2] = x;
    }
}

void dequeue1() {
    if (front1 == -1 || front1 > rear1)
        printf("Queue Underflow in Queue 1\n");
    else
        printf("Dequeued from Queue 1: %d\n", arr[front1++]);
}

void dequeue2() {
    if (front2 == SIZE || front2 < rear2)
        printf("Queue Underflow in Queue 2\n");
    else
        printf("Dequeued from Queue 2: %d\n", arr[front2--]);
}

void display() {
    int i;
    printf("\nQueue 1: ");
    if (front1 == -1 || front1 > rear1) printf("Empty");
    else for (i = front1; i <= rear1; i++) printf("%d ", arr[i]);

    printf("\nQueue 2: ");
    if (front2 == SIZE || front2 < rear2) printf("Empty");
    else for (i = front2; i >= rear2; i--) printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    int choice, value;
    while (1) {
        printf("\n1. Enqueue in Queue 1\n2. Enqueue in Queue 2\n3. Dequeue from Queue 1\n4. Dequeue from Queue 2\n5. Display\n6. Exit\nEnter choice: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1: printf("Enter value: "); scanf("%d", &value); enqueue1(value); break;
            case 2: printf("Enter value: "); scanf("%d", &value); enqueue2(value); break;
            case 3: dequeue1(); break;
            case 4: dequeue2(); break;
            case 5: display(); break;
            case 6: exit(0);
            default: printf("Invalid choice\n");
        }
    }
    return 0;
}
