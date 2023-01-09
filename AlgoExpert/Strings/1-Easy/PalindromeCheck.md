# Palindrome Check

<div class="html">
<p>
  Write a function that takes in a non-empty string and that returns a boolean
  representing whether the string is a palindrome.
</p>
<p>
  A palindrome is defined as a string that's written the same forward and
  backward. Note that single-character strings are palindromes.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">string</span> = "abcdcba"
</pre>
<h3>Sample Output</h3>
<pre>true <span class="CodeEditor-promptComment">// it's written the same forward and backward</span>
</pre>
</div>
<h2>Hints</h2>

<p>
Start by building the input string in reverse order and comparing this newly built string to the input string. Can you do this without using string concatenations?
</p>
<p>
Can you optimize your algorithm by using recursion? What are the implications of recursion on an algorithm's space-time complexity analysis?
</p>
<p>
Go back to an iterative solution and try using pointers to solve this problem: start with a pointer at the first index of the string and a pointer at the final index of the string. What can you do from there?
</p>
<h2>Optimal Space & Time Complexity</h2>

O(n) time | O(1) space - where n is the length of the input string

```javascript
  // O(n) time | O(1) space
  // Iterative
function isPalindrome(string) {
  let start = 0;
  let end = string.length - 1;

  while (start < end) {
    if (string[start] !== string[end]) {
      return false
    }
    start++
    end--
  }
  return true
}

// Do not edit the line below.
exports.isPalindrome = isPalindrome;


```

```javascript
// O(n) time | O(n) space
// Recursive
function isPalindrome(string, i = 0) {
  const j = string.length - 1 - i;
  return i >= j ? true : string[i] === string[j] && isPalindrome(string, i + 1)
}

// Do not edit the line below.
exports.isPalindrome = isPalindrome;

```