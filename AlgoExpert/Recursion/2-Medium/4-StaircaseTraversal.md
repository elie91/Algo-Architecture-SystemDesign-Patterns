# Staircase Traversal

<div class="html">
<p>
  You're given two positive integers representing the height of a staircase and
  the maximum number of steps that you can advance up the staircase at a time.
  Write a function that returns the number of ways in which you can climb the
  staircase.
</p>
<p>
  For example, if you were given a staircase of <span>height = 3</span> and
  <span>maxSteps = 2</span> you could climb the staircase in 3 ways. You could
  take <b>1 step, 1 step, then 1 step</b>, you could also take
  <b>1 step, then 2 steps</b>, and you could take <b>2 steps, then 1 step</b>.
</p>
<p>Note that <span>maxSteps &lt;= height</span> will always be true.</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">height</span> = 4
<span class="CodeEditor-promptParameter">maxSteps</span> = 2
</pre>
<h3>Sample Output</h3>
<pre>5
<span class="CodeEditor-promptComment">// You can climb the staircase in the following ways: </span>
<span class="CodeEditor-promptComment">// 1, 1, 1, 1</span>
<span class="CodeEditor-promptComment">// 1, 1, 2</span>
<span class="CodeEditor-promptComment">// 1, 2, 1</span>
<span class="CodeEditor-promptComment">// 2, 1, 1</span>
<span class="CodeEditor-promptComment">// 2, 2</span>
</pre>
</div>
<h2>Hints</h2>

<p>
  If you can advance <span>2</span> steps at a time, how many ways can you reach
  a staircase of height <span>1</span> and of height <span>2</span>? Think
  recursively.
</p>
<p>
  Continuing from Hint #1, if you know the number of ways to climb a staircase
  of height <span>1</span> and of height <span>2</span>, how many ways are there
  to climb a staircase of height <span>3</span> (assuming the same max steps of
  <span>2</span>)?
</p>
<p>
  The number of ways to climb a staircase of height <span>k</span> with a max
  number of steps <span>s</span> is:
  <span>numWays[k - 1] + numWays[k - 2] + ... + numWays[k - s]</span>. This is
  because if you can advance between <span>1</span> and <span>s</span> steps,
  then from each step <span>k - 1, k - 2, ..., k - s</span>, you can directly
  advance to the top of a staircase of height <span>k</span>. By adding the
  number of ways to reach all steps that you can directly advance to the top
  step from, you determine how many ways there are to reach the top step.
</p>
<h2>Optimal Space & Time Complexity</h2>

<div class="ya7hOTvkcvOlBTsWTi3l"><div class="U1quNvMraAr3Hbq2JfVQ">O(n) time | O(n) space - where n is the height of the staircase</div></div>

```javascript
const DIGIT_LETTERS = {
  0: ["0"],
  1: ["1"],
  2: ["a", "b", "c"],
  3: ["d", "e", "f"],
  4: ["g", "h", "i"],
  5: ["j", "k", "l"],
  6: ["m", "n", "o"],
  7: ["p", "q", "r", "s"],
  8: ["t", "u", "v"],
  9: ["w", "x", "y", "z"],
}


function phoneNumberMnemonics(phoneNumber) {
  debugger;
  const currentMnemonic = new Array(phoneNumber.length).fill('0')
  const mnemonicsFound = [];

  phoneNumberMnemonicsHelper(0, phoneNumber, currentMnemonic,  mnemonicsFound)
  return mnemonicsFound
}

function phoneNumberMnemonicsHelper(idx, phoneNumber, currentMnemonic,  mnemonicsFound) {
  debugger;
  if (idx === phoneNumber.length) {
    const mnemonic = currentMnemonic.join('')
    mnemonicsFound.push(mnemonic)
  } else {
    const digit = phoneNumber[idx]
    const letters = DIGIT_LETTERS[digit]
    for (const letter of letters) {
      currentMnemonic[idx] = letter
      phoneNumberMnemonicsHelper(idx + 1, phoneNumber, currentMnemonic, mnemonicsFound)
    }
  }
}

// Do not edit the line below.
exports.phoneNumberMnemonics = phoneNumberMnemonics;


```
