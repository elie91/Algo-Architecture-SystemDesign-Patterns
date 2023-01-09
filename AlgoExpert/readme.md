# Notes

# Table of Contents
1. [Complexity Analysis](#complexity-analysis)
2. [Memory](#memory)
3. [Big O Notation](#big-o-notation)
4. [Logarithm](#logarithm)
5. [Arrays](#arrays)
6. [Linked Lists](#linked-lists)
7. [Hash Table](#hash-table)
8. [Stack And Queues](#stack-and-queues)
9. [Strings](#strings)
10. [Graphs](#graphs)
11. [Trees](#trees)



## Complexity Analysis

#### `Complexity Analysis`

* The process of determining how efficient an algorithm is. Complexity analysis usually involves finding both the `time complexity` and the `space complexity` of an algorithm


#### `Time Complexity`

* A measure of how fast an algorithm runs, time complexity is a central concept in the field of algorithms and in coding interviews.
* It's expressed using  `Big O` notation

#### `Space Complexity`

* A measure of how much auxiliary memory an algorithm takes up, space complexity is a central concept in the field of algorithms and in coding interviews.
* It's expressed using  `Big O` notation


## Memory

#### `Bit` 

* Short for `binary digit`, a bit is a fundamental unit of information in Computer Science that represents a state with one of two values, typically `0` and `1`.
* Any data stored in a computer is, at the most basic level, represented in bits.

#### `Byte`

<div class="html">
<p>A group of eight <b>bits</b>. For example, <b>01101000</b> is a byte.</p>
<p>
  A single byte can represent up to <b>256</b> data values (<b>2<sup>8</sup></b>).
</p>
<p>
  Since a <b>binary number</b> is a number expressed with only two symbols, like
  <b>0</b> and <b>1</b>, a byte can effectively represent all of the numbers
  between 0 and 255, inclusive, in binary format.
</p>
<p>
  The following bytes represent the numbers 1, 2, 3, and 4 in binary format.
</p>
<pre>1: 00000001
2: 00000010
3: 00000011
4: 00000100
</pre>
</div>

#### `Fixed-Width Integer`

<div class="html">
<p>
  An integer represented by a fixed amount of <b>bits</b>. For example, a
  <b>32-bit integer</b> is an integer represented by 32 bits (4 bytes), and a
  <b>64-bit integer</b> is an integer represented by 64 bits (8 bytes).
</p>
<p>
  The following is the 32-bit representation of the number 1, with clearly
  separated bytes:
</p>
<pre>00000000 00000000 00000000 00000001
</pre>
<p>
  The following is the 64-bit representation of the number 10, with clearly
  separated bytes:
</p>
<pre>00000000 00000000 00000000 00000000 00000000 00000000 00000000 00001010
</pre>
<p>
  Regardless of how large an integer is, its fixed-width-integer representation
  is, by definition, made up of a constant number of bits.
</p>
<p>
  It follows that, regardless of how large an integer is, an operation performed
  on its fixed-width-integer representation consists of a constant number of bit
  manipulations, since the integer is made up of a fixed number of bits.
</p>
</div>

#### `Memory`

<div class="html">
<p>
  Broadly speaking, memory is the foundational layer of computing, where all
  data is stored.
</p>
<p>
  In the context of coding interviews, it's important to note the following
  points:
</p>
<ul>
  <li>Data stored in memory is stored in bytes and, by extension, bits.</li>
  <li>
    Bytes in memory can "point" to other bytes in memory, so as to store
    references to other data.
  </li>
  <li>
    The amount of memory that a machine has is bounded, making it valuable to
    limit how much memory an algorithm takes up.
  </li>
  <li>
    Accessing a byte or a fixed number of bytes (like 4 bytes or 8 bytes in the
    case of <b>32-bit</b> and <b>64-bit integers</b>) is an elementary
    operation, which can be loosely treated as a single unit of operational
    work.
  </li>
</ul>
</div>


## Big O Notation

<div class="html">
<p>
  The notation used to describe the <b>time complexity</b> and
  <b>space complexity</b> of algorithms.
</p>
<p>
  Variables used in Big O notation denote the sizes of inputs to algorithms. For
  example, <b>O(n)</b> might be the time complexity of an algorithm that
  traverses through an array of length <b>n</b>; similarly,
  <b>O(n + m)</b> might be the time complexity of an algorithm that traverses
  through an array of length <b>n</b> and through a string of length <b>m</b>.
</p>
<p>
  The following are examples of common complexities and their Big O notations,
  ordered from fastest to slowest:
</p>
<ul>
  <li><b>Constant</b>: O(1)</li>
  <li><b>Logarithmic</b>: O(log(n))</li>
  <li><b>Linear</b>: O(n)</li>
  <li><b>Log-linear</b>: O(nlog(n))</li>
  <li><b>Quadratic</b>: O(n<sup>2</sup>)</li>
  <li><b>Cubic</b>: O(n<sup>3</sup>)</li>
  <li><b>Exponential</b>: O(2<sup>n</sup>)</li>
  <li><b>Factorial</b>: O(n!)</li>
</ul>
<p>
  Note that in the context of coding interviews, Big O notation is usually
  understood to describe the
  <b>worst-case</b> complexity of an algorithm, even though the worst-case
  complexity might differ from the <b>average-case</b> complexity.
</p>
<p>
  For example, some sorting algorithms have different time complexities
  depending on the layout of elements in their input array. In rare cases, their
  time complexity will be much worse than in more common cases. Similarly, an
  algorithm that takes in a string and performs special operations on uppercase
  characters might have a different time complexity when run on an input string
  of only uppercase characters vs. on an input string with just a few uppercase
  characters.
</p>
<p>
  Thus, when describing the time complexity of an algorithm, it can sometimes be
  helpful to specify whether the time complexity refers to the average case or
  to the worst case (e.g., "this algorithm runs in O(nlog(n)) time on average
  and in O(n<sup>2</sup>) time in the worse case").
</p>
</div>

https://developerinsider.co/big-o-notation-explained-with-examples/

https://www.bigocheatsheet.com/

https://visualgo.net/en

## Logarithm

<div class="html">
<p>A mathematical concept that's widely used in Computer Science and that's defined by the following equation:</p>
<p><b>log<sub>b</sub>(x) = y</b> if and only if <b>b<sup>y</sup> = x</b></p>
<p>In the context of coding interviews, the logarithm is used to describe the complexity analysis of algorithms, and
    its usage always implies a logarithm of base <b>2</b>. In other words, the logarithm used in the context of coding
    interviews is defined by the following equation:</p>
<p><b>log(n) = y</b> if and only if <b>2<sup>y</sup> = n</b></p>
<p>In plain English, if an algorithm has a logarithmic time complexity (<b>O(log(n))</b>, where n is the size of the
    input), then whenever the algorithm's input doubles in size (i.e., whenever <b>n</b> doubles), the number of
    operations needed to
    complete the algorithm only increases by one unit. Conversely, an algorithm with a linear time complexity would
    see its number of operations double if its input size doubled.</p>
<p>As an example, a linear-time-complexity algorithm with an input of size 1,000 might take roughly 1,000 operations to
    complete, whereas a logarithmic-time-complexity algorithm with the same input would take roughly 10 operations to
    complete, since <b>2<sup>10</sup> ~= 1,000</b>.</p>
</div>

## Logarithm explication

* When we talk about logarithm, we have to specify a base
* In computer science, we assume that the base of the logarithm is always 2 (binary logarithm)
* So <b>log(n) = y</b> if and only if <b>2<sup>y</sup> = n</b>
  * Example: <b>log(1) = 0</b> because <b>2<sup>1</sup> = 0</b>
  * Example: <b>log(16) = 4</b> because <b>2<sup>4</sup> = 16</b>
* When we increase a power of two, we doubling what ever number we have previously 
  * Example: <b>2<sup>4</sup> = 2<sup>3</sup> * 2</b>
* So, when we double <b>N</b>, we only increasing the logarithm <b>by 1</b>
  *  Example: <b>2<sup>4</sup> = 16 </b> -> We double <b>16</b> -> So we increase the exponent by <b>1</b> -> So  <b>2<sup>5</sup> = 32 </b>
* <b>2<sup>20</sup> = 1M -> 2<sup>30</sup> = 1B </b> -> In the input increase from 1M to 1B, we have only 10 more operations to do
* In Complexity Analysis, O(log(N)) is really good, because if we double the input, the number of operations only increase by 1
* Example: 
```javascript
 // Array of length 8
 let test = [0,1,2,3,4,5,6,7]

 // We have an algorithm with a bunch of steps
 // At each step, we eliminat half of the array
 // Exemple: 
 // At step 1, we eliminat half of the array, so we have
 test = [0,1,2,3]
 // At step 2, we cut again the resulting array
 test = [0,1,]
 // At step 3, we cut again the resulting array
 test = [0] 
 // And we perform something with the 0
```
* In total, the amount of operations that we performed with this algorithm on our original array, is basicaly equal to `log(N)`, in this case `log(8)` : (<b>2<sup>3</sup> = 8</b>)
* Imagine we double the length of the input, so array of length 16, we only add one operation to cut the array of 16 in array of 8
* Another classic exemple of `log(N)` algorithm in where we dealing with a `Binary Tree` that we cut half every time

  

## Arrays


<div class="html">
<p>
  A linear collection of data values that are accessible at numbered indices,
  starting at index 0.
</p>
<p>
  The array items are stored in `back-to-back` memory slots, so we need to have multiple back-to-back memory slots available in memory
</p>
<p>
  The following are an array's standard operations and their corresponding time
  complexities:
</p>
<ul>
  <li><b>Accessing a value at a given index</b>: O(1)</li>
  <li><b>Updating a value at a given index</b>: O(1)</li>
  <li><b>Inserting a value at the beginning</b>: O(n)</li>
  <li><b>Inserting a value in the middle</b>: O(n)</li>
  <li>
    <b>Inserting a value at the end</b>:
    <ul>
      <li>amortized O(1) when dealing with a <b>dynamic array</b></li>
      <li>O(n) when dealing with a <b>static array</b></li>
    </ul>
  </li>
  <li><b>Removing a value at the beginning</b>: O(n)</li>
  <li><b>Removing a value in the middle</b>: O(n)</li>
  <li><b>Removing a value at the end</b>: O(1)</li>
  <li><b>Copying the array</b>: O(n)</li>
</ul>
<p>
  A static array is an implementation of an array that allocates a fixed amount
  of memory to be used for storing the array's values. Appending values to the
  array therefore involves copying the entire array and allocating new memory
  for it, accounting for the extra space needed for the newly appended value.
  This is a linear-time operation.
</p>
<p>
  A dynamic array is an implementation of an array that preemptively allocates
  double the amount of memory needed to store the array's values. Appending
  values to the array is a constant-time operation until the allocated memory is
  filled up, at which point the array is copied and double the memory is once
  again allocated for it. This implementation leads to an amortized
  constant-time insertion-at-end operation.
</p>
<p>
  A lot of popular programming languages like JavaScript and Python implement
  arrays as dynamic arrays.
</p>
</div>

## Linked Lists

#### `Singly Linked List`

<div class="html">
<p>
  A data structure that consists of nodes, each with some value and a pointer to
  the next node in the linked list. A linked list node's value and next node are
  typically stored in <span>value</span>
  and
  <span>next</span> properties, respectively.
</p>
<p>
Unlike arrays, the nodes of a Linked List are not necessarily stored in back-to-back memory slots.
The nodes of a Linked List can indeed be stored individually anywhere in the memory, since each node has a pointer to the next node
</p>
<p>
  The first node in a linked list is referred to as the <b>head</b> of the
  linked list, while the last node in a linked list, whose
  <span>next</span> property points to the <span>null</span> value, is known as
  the <b>tail</b> of the linked list.
</p>
<p>
  Below is a visual representation of a singly linked list whose nodes hold
  integer values:
</p>
<pre>0 -&gt; 1 -&gt; 2 -&gt; 3 -&gt; 4 -&gt; 5 -&gt; null
</pre>
<p>
  A singly linked list typically exposes its head to its user for easy access.
  While finding a node in a singly linked list involves traversing through all
  of the nodes leading up to the node in question (as opposed to instant access
  with an array), adding or removing nodes simply involves overwriting
  <span>next</span> pointers (assuming that you have access to the node right
  before the node that you're adding or removing).
</p>
<p>
  The following are a singly linked list's standard operations and their
  corresponding time complexities:
</p>
<ul>
  <li><b>Accessing the head</b>: O(1)</li>
  <li><b>Accessing the tail</b>: O(n)</li>
  <li><b>Accessing a middle node</b>: O(n)</li>
  <li><b>Inserting / Removing the head</b>: O(1)</li>
  <li><b>Inserting / Removing the tail</b>: O(n) to access + O(1)</li>
  <li><b>Inserting / Removing a middle node</b>: O(n) to access + O(1)</li>
  <li><b>Searching for a value</b>: O(n)</li>
</ul>
</div>

#### `Doubly Linked List`

<div class="html">
<p>
  Similar to a <b>singly linked list</b>, except that each node in a doubly
  linked list also has a pointer to the previous node in the linked list. The
  previous node is typically stored in a <span>prev</span> property.
</p>
<p>
  Just as the <span>next</span> property of a doubly linked list's
  <b>tail</b> points to the <span>null</span> value, so too does the
  <span>prev</span> property of a doubly linked list's <b>head</b>.
</p>
<p>
  Below is a visual representation of a doubly linked list whose nodes hold
  integer values:
</p>
<pre>null &lt;- 0 &lt;-&gt; 1 &lt;-&gt; 2 &lt;-&gt; 3 &lt;-&gt; 4 &lt;-&gt; 5 -&gt; null
</pre>
<p>
  While a doubly linked list typically exposes both its head and tail to its
  user, as opposed to just its head in the case of a singly linked list, it
  otherwise behaves very similarly to a singly linked list.
</p>
<p>
  The following are a doubly linked list's standard operations and their
  corresponding time complexities:
</p>
<ul>
  <li><b>Accessing the head</b>: O(1)</li>
  <li><b>Accessing the tail</b>: O(1)</li>
  <li><b>Accessing a middle node</b>: O(n)</li>
  <li><b>Inserting / Removing the head</b>: O(1)</li>
  <li><b>Inserting / Removing the tail</b>: O(1)</li>
  <li><b>Inserting / Removing a middle node</b>: O(n) to access + O(1)</li>
  <li><b>Searching for a value</b>: O(n)</li>
</ul>
</div>


#### `Circular Linked List`

<div class="html">
<p>
  A linked list that has no clear <b>head</b> or <b>tail</b>, because its "tail"
  points to its "head," effectively forming a closed circle.
</p>
<p>
  A circular linked list can be either a <b>singly circular linked list</b> or a
  <b>doubly circular linked list</b>.
</p>
</div>


## Hash Table

<div class="html">
<p>
  A data structure that provides fast insertion, deletion, and lookup of
  key/value pairs.
</p>
<p>
  Under the hood, a hash table uses a <b>dynamic array</b> of
  <b>linked lists</b> to efficiently store key/value pairs. When inserting a
  key/value pair, a hash function first maps the key, which is typically a
  string (or any data that can be hashed, depending on the implementation of the
  hash table), to an integer value and, by extension, to an index in the
  underlying dynamic array. Then, the value associated with the key is added to
  the linked list stored at that index in the dynamic array, and a reference to
  the key is also stored with the value.
</p>
<p>
  Hash tables rely on highly optimized hash functions to minimize the number of
  <b>collisions</b> that occur when storing values: cases where two keys map to
  the same index.
</p>
<p>Below is an example of what a hash table might look like under the hood:</p>
<pre>[
  0: (value1, key1) -&gt; null
  1: (value2, key2) -&gt; (value3, key3) -&gt; (value4, key4)
  2: (value5, key5) -&gt; null
  3: (value6, key6) -&gt; null
  4: null
  5: (value7, key7) -&gt; (value8, key8)
  6: (value9, key9) -&gt; null
]
</pre>
<p>
  In the hash table above, the keys <b>key2</b>, <b>key3</b>, and
  <b>key4</b> collided by all being hashed to <b>1</b>, and the keys
  <b>key7</b> and <b>key8</b> collided by both being hashed to <b>5</b>.
</p>
<p>
  The following are a hash table's standard operations and their corresponding
  time complexities:
</p>
<ul>
  <li>
    <b>Inserting a key/value pair</b>: O(1) on average; O(n) in the worse case
  </li>
  <li>
    <b>Removing a key/value pair</b>: O(1) on average; O(n) in the worse case
  </li>
  <li><b>Looking up a key</b>: O(1) on average; O(n) in the worse case</li>
</ul>
<p>
  The worst-case linear-time operations occur when a hash table experiences a
  lot of collisions, leading to long linked lists internally, which take O(n)
  time to traverse.
</p>
<p>
  However, in practice and especially in coding interviews, we typically assume
  that the hash functions employed by hash tables are so optimized that
  collisions are extremely rare and constant-time operations are all but
  guaranteed.
</p>
</div>


## Stack And Queues


#### `Stack`

<div class="html">
<p>
  An array-like data structure whose elements follow the <b>LIFO</b> rule: <b>L</b>ast <b>I</b>n, <b>F</b>irst
  <b>O</b>ut.
</p>
<p>
  A stack is often compared to a stack of books on a table: the last book that's placed on the stack of books is the
  first one that's taken off the stack.
</p>
<p>
  The following are a stack's standard operations and their
  corresponding time complexities:
</p>
<ul>
  <li><b>Pushing an element onto the stack</b>: O(1)</li>
  <li><b>Popping an element off the stack</b>: O(1)</li>
  <li><b>Peeking at the element on the top of the stack</b>: O(1)</li>
  <li><b>Searching for an element in the stack</b>: O(n)</li>
</ul>
<p>
  A stack is typically implemented with a <b>dynamic array</b> or with a <b>singly linked list</b>.
</p>
</div>


#### `Queue`

<div class="html">
<p>
  An array-like data structure whose elements follow the <b>FIFO</b> rule: <b>F</b>irst <b>I</b>n, <b>F</b>irst
  <b>O</b>ut.
</p>
<p>
  A queue is often compared to a group of people standing in line to purchase items at a store: the first person to get
  in line is the
  first one to purchase items and to get out of the queue.
</p>
<p>
  The following are a queue's standard operations and their
  corresponding time complexities:
</p>
<ul>
  <li><b>Enqueuing an element into the queue</b>: O(1)</li>
  <li><b>Dequeuing an element out of the queue</b>: O(1)</li>
  <li><b>Peeking at the element at the front of the queue</b>: O(1)</li>
  <li><b>Searching for an element in the queue</b>: O(n)</li>
</ul>
<p>
  A queue is typically implemented with a <b>doubly linked list</b>.
</p>
</div>


## Strings

<div class="html">
<p>
  One of the fundamental data types in Computer Science, strings are stored in
  <b>memory</b> as <b>arrays</b> of integers, where each character in a given
  string is mapped to an integer via some character-encoding standard like
  <b>ASCII</b>.
</p>
<p>
  Strings behave much like normal arrays, with the main distinction being that,
  in most programming languages (C++ is a notable exception), strings are
  <b>immutable</b>, meaning that they can't be edited after creation. This also
  means that simple operations like appending a character to a string are more
  expensive than they might appear.
</p>
<p>
  The canonical example of an operation that's deceptively expensive due to
  string immutability is the following:
</p>
<pre>string = "this is a string"
newString = ""

for character in string:
    newString += character
</pre>
<p>
  The operation above has a time complexity of <b>O(n<sup>2</sup>)</b> where n
  is the length of <span>string</span>, because each addition of a character to
  <span>newString</span> creates an entirely new string and is itself an
  <b>O(n)</b> operation. Therefore, n O(n) operations are performed, leading to
  an O(n<sup>2</sup>) time-complexity operation overall.
</p>
</div>


## Graphs


#### `Graph`
<div class="html">
<ul>
<li><b>Storing a graph : Number of Vertices (V) + Number of edges (E) </b>: O(V+E)</li>
<li><b>Traversing the Graph : Depth First Search (DFS) </b>: O (V+E) </li>
<li><b>Traversing the Graph : Breadth First Search (BFS) </b>: O (V+E) </li>
</ul>
<p>A collection of nodes or values called <b>vertices</b> that might be related; relations between vertices are
    called <b>edges</b>.</p>
<p>Many things in life can be represented by graphs; for example, a social network can be represented by a graph whose
    vertices are users and whose edges are friendships between the users. Similarly, a city map can be represented by a
    graph whose vertices are locations in the city and whose edges are roads between the locations.</p>
</div>

#### `Graph Cycle`

<div class="html">
<p>
  Simply put, a cycle occurs in a <b>graph</b> when three or more
  <b>vertices</b> in the graph are connected so as to form a closed loop.
</p>
<p>
  Note that the definition of a graph cycle is sometimes broadened to include
  cycles of length two or one; in the context of coding interviews, when dealing
  with questions that involve graph cycles, it's important to clarify what
  exactly constitutes a cycle.
</p>
</div>

#### `Acyclic Graph`
<div class="html">
<p>A <b>graph</b> that has no <b>cycles</b>.</p>
</div>

#### `Cyclic Graph`

<div class="html">
<p>A <b>graph</b> that has at least one <b>cycle</b>.</p>
</div>

#### `Directed Graph`

<div class="html">
<p>
  A <b>graph</b> whose <b>edges</b> are directed, meaning that they can only be
  traversed in one direction, which is specified.
</p>
<p>
  For example, a graph of airports and flights would likely be directed, since a
  flight specifically goes from one airport to another (i.e., it has a
  direction), without necessarily implying the presence of a flight in the
  opposite direction.
</p>
</div>

#### `Undirected Graph`

<div class="html">
<p>
  A <b>graph</b> whose <b>edges</b> are undirected, meaning that they can be
  traversed in both directions.
</p>
<p>
  For example, a graph of friends would likely be undirected, since a friendship
  is, by nature, bidirectional.
</p>
</div>

#### `Connected Graph`

<div class="html">
<p>
  A <b>graph</b> is connected if for every pair of <b>vertices</b> in the graph,
  there's a path of one or more <b>edges</b> connecting the given vertices.
</p>
<p>In the case of a <b>directed graph</b>, the graph is:</p>
<ul>
  <li>
    <b>strongly connected</b> if there are bidirectional connections between the
    vertices of every pair of vertices (i.e., for every vertex-pair
    <span>(u, v)</span> you can reach <span>v</span> from <span>u</span> and
    <span>u</span> from <span>v</span>)
  </li>
  <li>
    <b>weakly connected</b> if there are connections (but not necessarily
    bidirectional ones) between the vertices of every pair of vertices
  </li>
</ul>
<p>A graph that isn't connected is said to be <b>disconnected</b>.</p>
</div>


## Trees

#### `Tree`

Tree = Type of Graph 
* Graph rooted, with a root node
* Graph directed, the edges have a direction that points to the nodes below
* Graph Acyclic, without cycles
* Not allowed to be disconnected = all nodes are connected
* Each node in the tree can only have one parent

<div class="html">

Generally: 
<ul>
<li><b>Storing a tree</b>: O(N)</li>
<li><b>Traversing ALL NODES in a tree :</b>: O (N) </li>
<li><b>Traversing tree by eliminate other paths</b>: O (log(N)) </li>
</ul>
<p>
  A data structure that consists of nodes, each with some value and pointers to
  child-nodes, which recursively form <b>subtrees</b> in the tree.
</p>
<p>
  The first node in a tree is referred to as the <b>root</b> of the tree, while
  the nodes at the bottom of a tree (the nodes with no child-nodes) are referred
  to as <b>leaf nodes</b> or simply <b>leaves</b>. The paths between the root of
  a tree and its leaves are called <b>branches</b>, and the <b>height</b> of a
  tree is the length of its longest branch. The <b>depth</b> of a tree node is
  its distance from its tree's root; this is also known as the node's
  <b>level</b> in the tree.
</p>
<p>
  A tree is effectively a <b>graph</b> that's <b>connected</b>, <b>directed</b>,
  and <b>acyclic</b>, that has an explicit root node, and whose nodes all have a
  single <b>parent</b> (except for the root node, which effectively has no
  parent). Note that in most implementations of trees, tree nodes don't have a
  pointer to their parent, but they can if desired.
</p>
<p>
  There are many types of trees and tree-like structures, including
  <b>binary trees</b>, <b>heaps</b>, and <b>tries</b>.
</p>
</div>

#### `Binary Tree`

<div class="html">
<p>A <b>tree</b> whose nodes have up to <b>two</b> child-nodes.</p>
<p>
  The structure of a binary tree is such that many of its operations have a
  logarithmic time complexity, making the binary tree an incredibly attractive
  and commonly used data structure.
</p>
</div>

#### `K-ary Tree`

<div class="html">
<p>
  A <b>tree</b> whose nodes have up to <b>k</b> child-nodes. A
  <b>binary tree</b> is a k-ary tree where <b>k == 2</b>.
</p>
</div>

#### `Perfect Binary Tree`

<div class="html">
<p>
  A <b>binary tree</b> whose interior nodes all have two child-nodes and whose
  <b>leaf nodes</b> all have the same <b>depth</b>. Example:
</p>
<pre>           1
      /         \
     2           3
   /   \       /   \
  4     5     6     7
 / \   / \   / \   / \
8   9 10 11 12 13 14 15
</pre>
</div>

#### `Complete Binary Tree`

<div class="html">
<p>
  A <b>binary tree</b> that's <i>almost</i> <b>perfect</b>; its interior nodes
  all have two child-nodes, but its <b>leaf nodes</b> don't necessarily all have
  the same <b>depth</b>. Furthermore, the nodes in the last <b>level</b> of a
  complete binary tree are as far left as possible. Example:
</p>
<pre>          1
       /     \
      2       3
    /   \   /   \
   4     5 6     7
 /   \
8     9
</pre>
<p>
  Conversely, the following binary tree <i>isn't</i> complete, because the nodes
  in its last level aren't as far left as possible:
</p>
<pre>          1
       /     \
      2       3
    /   \   /   \
   4     5 6     7
         /   \
        8     9
</pre>
</div>

#### `Balanced Binary Tree`

<div class="html">
<p>
  A <b>binary tree</b> whose nodes all have left and right <b>subtrees</b> whose
  <b>heights</b> differ by no more than 1.
</p>
<p>
  A balanced binary tree is such that the logarithmic time complexity of its
  operations is maintained.
</p>
<p>
  For example, inserting a node at the bottom of the following
  <i>imbalanced</i> binary tree's left subtree would cleary not be a
  logarithmic-time operation, since it would involve traversing through most of
  the tree's nodes:
</p>
<pre>             1
          /     \
         2       3
       /
      4
    /
   8
  /
10
</pre>
<p>The following is an example of a balanced binary tree:</p>
<pre>          1
       /     \
      2       3
    /   \   /   \
   4     5 6     7
 /   \         /   
10    9       8
</pre>
</div>

#### `Full Binary Tree`

<div class="html">
<p>
  A <b>binary tree</b> whose nodes all have either two child-nodes or zero
  child-nodes. Example:
</p>
<pre>    1
 /     \
2       3
      /   \
     6     7
   /   \
  8     9
</pre>
</div>
