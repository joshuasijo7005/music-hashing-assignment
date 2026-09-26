# Music Application - Hashing Assignment

## Aim

To implement a hash table using the Division Method and compare
hashing with linear search.

## Input

105, 210, 315, 420, 525, 630, 735, 840

## Hash Function

h(k) = k % 10

## Collision Resolution

Linear Probing

## Table Size

10

## Load Factor

0.8

## Results

Hashing:
- Total operations = 20
- Average operations = 2.5

Linear Search:
- Total comparisons = 36
- Average comparisons = 4.5

## Complexity

Hashing average case: O(1)
Hashing worst case: O(n)

Linear Search average case: O(n)
Linear Search worst case: O(n)

## Conclusion

Hashing is suitable for the music application because it provides
better average search performance than linear search. Collisions
must be controlled by selecting an appropriate table size and
hash function.
