##**Question**
Hey mentor,

I was working through an assignment last night and came across a bug. I'm so confused!

The text in the alert is showing up as "undefined" instead of either "A Unicorn", "A hug", or "Fresh Laundry" and I'm not quite sure what's going on. Can you point me in the right direction?

-Student

```
  <button id="btn-0">Button 1!</button>
  <button id="btn-1">Button 2!</button>
  <button id="btn-2">Button 3!</button>

  <script type="text/javascript">
    var prizes = ['A Unicorn!', 'A Hug!', 'Fresh Laundry!'];
    for (var btnNum = 0; btnNum < prizes.length; btnNum++) {
        // for each of our buttons, when the user clicks it...
        document.getElementById('btn-' + btnNum).onclick = function() {
            // tell her what she's won!
            alert(prizes[btnNum]);
        };
    }
  </script>

```

##**Response**
This is a very common bug that many JavaScript developers experience (even experienced ones!!). It centers
around incorrectly defining functions inside of `for` loops.

Before we go through the solution it would be great to have some background knowledge on Immediately Invoked
Function Expressions (IIFE). You will come across these often in your career as you code in JavaScript. Check
out "Closures and Locking in State" from the following article in particular:
<a href='https://www.kirupa.com/html5/immediately_invoked_function_expressions_iife.htm'>https://www.kirupa.com/html5/immediately_invoked_function_expressions_iife.htm
</a>

Let me walk you through what's going on in your particular segment of code:
1. Your `for` loop is completing before the "onclick" callback is being invoked. This means that whenever
     you click one of the buttons on your home page the "onclick" callback that is being attached is:
     ```
     function() {
         // tell her what she's won!
         alert(prizes[btnNum]);
    ```
    but with whatever the value of  `btnNum` was at the end of your `for` loop. To check this out, modify your
    code to alert the value of btnNum in the browser by changing `alert(prizes[btnNum]);` to `alert(btnNum);`.
    The number you're seeing in the alert should be "3", which is the value of btnNum at the end of your
    `for` loop.
2. To alleviate this we want to define the "onclick" callback function with the current value of btnNum as it
    loops through the `for` loop. A technique that allows you to do this is the IIFE we read about earlier:
    ```
    var prizes = ['A Unicorn!', 'A Hug!', 'Fresh Laundry!'];
    for (var btnNum = 0; btnNum < prizes.length; btnNum++) {
        // for each of our buttons, when the user clicks it...

        (function(btnNum) {
          document.getElementById('btn-' + btnNum).onclick = function() {
              // tell her what she's won!
              alert(prizes[btnNum]);
          };
        })(btnNum);
    }
   ```
   On each loop the IIFE that we defined is being run with the current value of btnNum, so for example on the first iteration in the loops (when btnNum = 0 ) the "onclick" calback being defined is:
   ```
   function() {
       // tell her what she's won!
       alert(prizes[0]);
  ```

##**Suggestions**
1. Carefully read through the above and make sure you understand the content.
2. Run your original code and your updated code and make sure you can pinpoint
   where the error came from.
3. Practice using IIFE's in similar projects.

Let me know if you have any questions or if you need any topics cleared up.

Best regards,

Stefan
