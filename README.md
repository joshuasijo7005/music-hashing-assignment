# music-hashing-assignment
#include <stdio.h>

#define SIZE 10

int hashTable[SIZE];

void initialize()
{
    for (int i = 0; i < SIZE; i++)
        hashTable[i] = -1;
}

void insert(int key)
{
    int index = key % SIZE;
    int original = index;
    int collisions = 0;

    while (hashTable[index] != -1)
    {
        collisions++;
        index = (index + 1) % SIZE;

        if (index == original)
        {
            printf("Hash table is full!\n");
            return;
        }
    }

    hashTable[index] = key;

    printf("Inserted %d at index %d, Collisions = %d\n",
           key, index, collisions);
}

int hashSearch(int key, int *operations)
{
    int index = key % SIZE;
    int start = index;

    *operations = 0;

    while (hashTable[index] != -1)
    {
        (*operations)++;

        if (hashTable[index] == key)
            return index;

        index = (index + 1) % SIZE;

        if (index == start)
            break;
    }

    return -1;
}

int linearSearch(int arr[], int n, int key, int *comparisons)
{
    *comparisons = 0;

    for (int i = 0; i < n; i++)
    {
        (*comparisons)++;

        if (arr[i] == key)
            return i;
    }

    return -1;
}

void display()
{
    printf("\nFinal Hash Table:\n");

    for (int i = 0; i < SIZE; i++)
    {
        if (hashTable[i] == -1)
            printf("Index %d : Empty\n", i);
        else
            printf("Index %d : %d\n", i, hashTable[i]);
    }
}

int main()
{
    int songs[] = {105, 210, 315, 420, 525, 630, 735, 840};
    int n = 8;

    initialize();

    printf("HASH TABLE INSERTION\n");
    printf("--------------------\n");

    for (int i = 0; i < n; i++)
        insert(songs[i]);

    display();

    printf("\nSEARCH COMPARISON\n");
    printf("-----------------\n");

    for (int i = 0; i < n; i++)
    {
        int hashOperations;
        int linearComparisons;

        hashSearch(songs[i], &hashOperations);
        linearSearch(songs, n, songs[i], &linearComparisons);

        printf("ID %d : Hashing = %d operations, "
               "Linear Search = %d comparisons\n",
               songs[i], hashOperations, linearComparisons);
    }

    return 0;
}
