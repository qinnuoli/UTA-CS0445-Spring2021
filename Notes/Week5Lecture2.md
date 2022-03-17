# Week 5 Lecture 2

### Project 4: the Knapsack Problem

Write an algorithm that find all the possible subsets of weights that sum up to a specific total weight.

If you have n bit, you can represent 2^n different numbers ranging from 0 to 2^n - 1.

If you have an array with n elements, you can generate 2^n subsets.

**Strategy**: write an algorithm that generates all possible subsets and check if the sum equals the target sum.

**Technique**: bit maps.

### Illustration of Bit Map

index → [0, 1, 2, 3, 4, 5, 6, 7]

array → [7, 1, 11, 13, 2, 5, 9, 12]

byte bitmap = 7;

Although this bitmap is not of the identical length as the array, as

> an int is 32 bits, a byte is 8 bits → an int is 4 bytes.
> 

We could, however, use the bitmap to represent all the possible subsets of the array by having each slot being either 0 or 1, indicating if the element is included in the specific subset.

 

```java
for (bitmap = 0; bitmap < 2^8; bitmap++)

int[] subset = { ... } // starts fresh every time we generate a new subset

// for each number, it has its own bit representation which is how it is stored in java
// for each number, there is an inner for loop that goes from the start of the bitmap to the end
// and generate a new subset

// how to generate a new subset:
// if n-th bit of bitmap is 1,
// subsetp[n] = array[n]
```

In order to ask the question of, is the i-th bit a 0 or a 1, we will use a `bit string` instead of a `bit map`. We could make use of `bitString.charAt[i]`.

```java
String bitmap

for i = 1 up to 255
	bitmap = toBitString(i)
	for j = 0 up to 7
	if bitmap.charAt[j] == '1'
		copy the j-th element in the array into the subset
```