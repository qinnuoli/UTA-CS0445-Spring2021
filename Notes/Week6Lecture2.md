# Week 6 Lecture 2

Define a variable that defines this flat file with type TreeMap and TreeSet

- Single String being the key, value being the set of Strings

```java
TreeMap<String, TreeSet<String>> member2pacs = new TreeMap<String, TreeSet<String>>();

// Read in the input file
while (member2pacsFile.ready())
{
	BufferedReader file = new BufferedReader(new FileReader(member2pacs.txt));
	String line = member2pacsFile.readLine();
	
	// [member] [pac1] [pac2] [pac3]
	String[] tokens = line.split("\\s+");
	TreeSet<String> pacs = new TreeSet<String>();
	for (int i = 1; i < tokens.length; i++)
		pacs.add(tokens[i]);
	member2pacs.put(token[0], pacs.);

	// OR

	// Transform the String to a list
	// and pass in the list to the c'tor of TreeSet
}

// Map is now filled now, traverse and print
for (String member: member2pacs.keySet())
{
	System.out.print(member);
	TreeSet<String> pacs = member2pacs.get(member);
	for (String pac: pacs)
		System.out.print(" " + pac);
	System.out.println();
}
```

Map: members → all pacs

Inverse of the map: pac → all members

```java
TreeMap<String, TreeSet<String>> pac2members = new TreeMap<String, TreeSet<String>>();

BufferedReader member2pacsFile = new BufferedReader(new FileReader(member2pacs.txt));
String[] tokens = member2pacsFile.readLine().split("\\s+");
String member = tokens[0];

// Walk the tokens list from 1 to the end (skip member)
// With each pac, see if it's already a key in the map (check dupes)
// Create a new entry in the map, key being the pac, create a TreeSet with the member

// Use containsKey() to see if it's in the map yet
// If it's not there, use put() to add new entry
// If it is there, use get() to pull out the TreeSet of the current members of the pac,
// and add() the new member to it
// then put() to update the entry
```

map:

BFPR {gjetson}

AFCTC  {gjetson, jsandbug}

ACLU  {gjetson}

SDS  {gjetson}

YCL  {jsandbug}