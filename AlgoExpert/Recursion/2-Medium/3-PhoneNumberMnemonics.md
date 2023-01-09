# Phone Number Mnemonics


<p>If you open the keypad of your mobile phone, it'll likely look like this:</p>
<pre>   ----- ----- -----
  |     |     |     |
  |  1  |  2  |  3  |
  |     | abc | def |
   ----- ----- -----
  |     |     |     |
  |  4  |  5  |  6  |
  | ghi | jkl | mno |
   ----- ----- -----
  |     |     |     |
  |  7  |  8  |  9  |
  | pqrs| tuv | wxyz|
   ----- ----- -----
        |     |
        |  0  |
        |     |
         -----
</pre>
<p>
  Almost every digit is associated with some letters in the alphabet; this
  allows certain phone numbers to spell out actual words. For example, the phone
  number <span>8464747328</span> can be written as <span>timisgreat</span>;
  similarly, the phone number <span>2686463</span> can be written as
  <span>antoine</span> or as <span>ant6463</span>.
</p>
<p>
  It's important to note that a phone number doesn't represent a single sequence
  of letters, but rather multiple combinations of letters. For instance, the
  digit <span>2</span> can represent three different letters (a, b, and c).
</p>
<p>
  A mnemonic is defined as a pattern of letters, ideas, or associations that
  assist in remembering something. Companies oftentimes use a mnemonic for their
  phone number to make it easier to remember.
</p>
<p>
  Given a stringified phone number of any non-zero length, write a function that
  returns all mnemonics for this phone number, in any order.
</p>
<p>
  For this problem, a valid mnemonic may only contain letters and the digits
  <span>0</span> and <span>1</span>. In other words, if a digit is able to be
  represented by a letter, then it must be. Digits <span>0</span> and
  <span>1</span> are the only two digits that don't have letter representations
  on the keypad.
</p>
<p>
  Note that you should rely on the keypad illustrated above for digit-letter
  associations.
</p>
<h3>Sample Input</h3>
<pre><span class="CodeEditor-promptParameter">phoneNumber</span> = "1905"
</pre>
<h3>Sample Output</h3>
<pre>[
  "1w0j",
  "1w0k",
  "1w0l",
  "1x0j",
  "1x0k",
  "1x0l",
  "1y0j",
  "1y0k",
  "1y0l",
  "1z0j",
  "1z0k",
  "1z0l",
]
<span class="CodeEditor-promptComment">// The mnemonics could be ordered differently.</span>
</pre>

<h2>Hints</h2>

<p>
The first thing you'll need to do is create a mapping from digits to letters. You can do this by creating a hash table mapping all string digits to lists of their respective characters.
</p>
<p>
This problem can be solved fairly easily using recursion. Try generating all characters for the first digit in the phone number one at a time, and for each character, recursively performing the same action on the the next digit, and then on the digit after that, and so on and so forth until you've done so for all digits in the phone number.
</p>
<p>
You can recursively generate characters one digit at a time and store the intermediate results in a array. Once you've reached the last digit in the phone number, you can add the currently generated mnemonic (stored in the previously mentioned array) to a final array that stores all the results.
</p>
<h2>Optimal Space & Time Complexity</h2>

<div class="wydVeRqMMtvFhbtm0Oda " style="transition: height 400ms linear 0s; height: auto;"><div class="ya7hOTvkcvOlBTsWTi3l"><div class="U1quNvMraAr3Hbq2JfVQ">O(4^n * n) time | O(4^n * n) space - where n is the length of the phone number</div></div></div>


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
