# CS 0445 Lecture 4 Notes

### What is a set?  

Collection of items or values that have some properties in common.

### The set itself also has properties:  

1. Every set has cardinality: the size of the set.

2. No dupes allowed.
- What operation must be well defined on the members of the set?
- A test for equality

On primitives it is == sign

On objects it is `.equals(Object other)` call

### set 1 = {A, B, C, D}
### set 2 = {B, C, D, E}


**the union operation: set1 + set2**
- dump all the contents of both sets into a third set BUT any duplicated bounce off
- set1 + set2 = {A, B, C, D, E}
- order of set1 and set2 is interchangable, arbitrary

**the intersect operation: set1 * set2**
- set1 * set2 = {B, C, D}
- order of set1 and set2 is interchangable, arbitrary

**the difference operation: set 1 - set2, set2 - set1**
- set1 - set2 = {A}, set2 - set1 = {E}

**the xor operation: set1 xor set2**
- xor = union - intersection
- set1 xor set2 = (set1 + set2) - (set1 * set2)
- set1 xor set2 = {A, E}
- one single return statement

### For the union, intersect, and diff you will have to do the following:

for each element in set1
	search set2 to see if it's there
	if it is, then act accordingly for this specific operation
	i.e. if you are doing union, then reject the element from set1

this means, you must write a `static boolean contains(String elem, String[] set)`

### Union

step 0: figure out the minimum needed size to dimension the result array
		once you fill this array you will return it from the union method
		in the case of union, size = sum of length of both arrays (worst case, no elements in common)
step 1: define an array of String at the top of the method, `unionResult`
		also define a coounter `unionCount` and initialize to 0
step 2: dump all the elements from set1 into the union result (increment the counter)
		optimize by doing a test to see which set is larger and adjust your tests accordingly
step 3: for each element of set2, call contains(elem, unionResult)
		if contains comes back false then ADD element to unionResult
step 4: return the trimmed version of the array
		(with a method you will write that takes the array and its actual count
		and returns a trimmed array with exactly count-long with the elements in it)
		this way main is always dealing with arrays that are guaranteed to be FULL
		and main does not need to have count variable following that array around
		(.length is the count)

`static String[] union (String[] set1, String[] set2)
{
	String[] unionResult = new String[set1.length + set2.length];
	int unionCount = 0;
	for (String elem: set1)
		unionResult[unionCount++] = elem;
	for (String elem: set2)
	{
		if (!contains(elem, unionResult))
			unionResult[unionCount++] = elem;
	}
	return trimArray(unionResult, unionCount);
}
`

### doubleLength()

step 1: create an array in here called bigger array (2x length)
step 2: copy elements from incoming array into the bigger array
step 3: return the ref to the bigger array
