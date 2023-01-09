# Permutations

<div class="html">
<p>
  Write a function that takes in an array of unique integers and returns an
  array of all permutations of those integers in no particular order.
</p>
<p>If the input array is empty, the function should return an empty array.</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">array</span> = [1, 2, 3]
</pre>
<h3>Sample Output</h3>
<pre>[[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
</pre>
</div>

<h2>Hints</h2>

<p>
A permutation is defined as a way in which a set of things can be ordered. Thus, for the list [1, 2, 3], there exist some permutations starting with 1, some starting with 2, and some starting with 3. For the permutations starting with 1, there will be a permutation where 2 is the second number and one where 3 is the second number. For permutations starting with 3, there will be a permutation where 1 is the second number and one where 2 is the second number. The idea is that, in order to construct a permutation, we can pick a random number from our list to be the first number, then we can pick a random number from the remaining list (without the first number) to be the second number, then we can pick a random number from the remaining list (without the first and second numbers) to be the third number, and we can repeat the process until we exhaust all of our list of numbers. At that point, we will have constructed a valid permutation. How can we implement this construction algorithmically, without picking numbers at random?
</p>
<p>
Iterate through the list of numbers, and begin constructing new permutations starting with each number. For each permutation that you've begun constructing, remove the number already used (the first number of each permutation) from the list of numbers - you'll likely have to make copies of the original list. Repeat this process by recursively iterating through the mutated lists of numbers, appending numbers to the corresponding permutations you've already begun constructing and then removing those numbers from the respective mutated lists; repeat this until your mutated lists are empty, at which point your constructed permutations will be as big as the original list and will be valid permutations.
</p>
<p>
Do you have to create so many mutated lists of numbers? Can you come up with an alternative approach that would allow you to only rely on the original list of numbers, without ever copying it and without removing numbers from it?
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n*n!) time | O(n*n!) space - where n is the length of the input array

```javascript
// Upper Bound: O(n^2*n!) time | O(n*n!) space
// Roughly: O(n*n!) time |  O(n*n!) space
function getPermutations(array) {
  const perms = [];
  permutationsHelper(array, [], perms)
  return perms
}

function permutationsHelper(array, currentPermutation, permutations) {
  if (!array.length && currentPermutation.length) {
    // Hit N Factorial times (n!)
    permutations.push(currentPermutation)
  } else {
    array.forEach((num, index) => {
      const updatedArray = array.slice(0, index).concat(array.slice(index + 1)) // O(n)
      const newPermutation = [...currentPermutation, num] // O(n)
      // 0 (n! * n * n) time
      // n! => number of permutations that we have
      // * n, because we have a total of n times n! calls
      // * n, because each call doing o(n) operations (remove and append to the array)
      // So (n^2 * n!)

      // O (n*n!) space, because n! permutations of length n
      permutationsHelper(updatedArray, newPermutation, permutations)
    })
  }
}


// Do not edit the line below.
exports.getPermutations = getPermutations;

```

```javascript
// O (n*n!) time | O(n*n!) space
function getPermutations(array) {
  debugger;
  const permutations = [];
  permutationsHelper(0, array, permutations)
  return permutations
}

function permutationsHelper(i, array, permutations) {
  debugger;
  if (i === array.length - 1) {
    permutations.push(array.slice())
  } else {
    for (let j = i; j < array.length; j++) {
      swap(i, j, array)
      permutationsHelper(i + 1, array, permutations)
      swap(i, j, array)
    }
  }
}

function swap(i, j, array) {
  debugger;
  const temp = array[i]
  array[i] = array[j]
  array[j] = temp
}

// Do not edit the line below.
exports.getPermutations = getPermutations;

```