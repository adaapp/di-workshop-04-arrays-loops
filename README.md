# Workshop 4 - Arrays & Loops

You’ll be working in pairs again - **driver/navigator** style, same as before.
Start by setting up the workshop as usual.

For each of the **bold** questions below:

<h3 align="center">
  🗣 Discuss &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  👩‍💻 Change &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  👀 Observe &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  🔄 Repeat
</h3>

1. **🗣 Discuss** the question with your partner
1. **👩‍💻 Change the code** - what do you expect your changes to do?
1. **👀 Observe the results** - what happened when you ran your code? How did it
   differ from your expectations
1. **🔄 Repeat** - keep discussing, changing, and running the code until you
   feel you understand it

**Remember, it’s about exploration and understanding. Take your time!**

**Don’t move on until you fully understand what’s happening.**

# Part 1

**Read through the below code and predict what it will draw on screen. Trace
through on paper if it'll help.**

```js
function setup() {
  size(400, 400)
  background(200)
}

function draw() {
  var x = 10

  rect(x, 10, 10, 10)
  x = x + 20

  rect(x, 10, 10, 10)
  x = x + 20

  rect(x, 10, 10, 10)
  x = x + 20

  rect(x, 10, 10, 10)
  x = x + 20

  rect(x, 10, 10, 10)
  x = x + 20
}
```

Create a new sketch with the code and check it matched your prediction.

**What's wrong with this code?**

**How could we improve it?**

There's a lot of repetition in the code here. Generally, as programmers, we try
to avoid repetition - often the more code we have, the more space there is for
errors.

Luckily, we can avoid repeating ourselves with a **loop**. **Replace `draw` with
the following:**

```js
function draw() {
  var x = 10
  var count = 5

  var i = 0
  while (i < count) {
    rect(x, 10, 10, 10)
    x = x + 20

    i = i + 1
  }
}
```

**How does changing `count` effect your sketch?**

Let's talk through this line by line:

---

```js
var x = 10
var count = 5
```

These two lines should be pretty familiar by now. `x` is the x coordinate of the
box, and it's the same `x` as in the previous example of the sketch.

---

```js
var i = 0
```

Now, we have this other variable called `i`. `i` isn't a great variable name,
but it's really commonly used in loops as a counter. Often when you see loops,
you'll see `i` (short for `index`) as the number that the current loop is on.

In this example, `i` will start at `0` at first, then increase to `1`, `2`, `3`
and `4` for each rectangle that gets drawn.

---

```js
while (i < count) {
```

Here's something new! This is the start of a `while` loop. It looks a lot like
an `if` statement, and actually is pretty similar!

A while loop will check the condition (question) in the `()` just like `if`. If
the condition is true, it runs the code inside the `{}`.

The key difference comes at the end: when we get to the end of an `if`
statement, the code just carries on with whatever comes next. In a `while`
statement, when we get to the end, **it checks the condition/question again**.
If it's true, the entire process gets repeated. That means that a `while` loop
will just keep running the code inside it until the condition/question becomes
`false`.

It's really easy to write dodgy code in this way that results in an infinite
loop:

```js
// EXAMPLE:
// the 'question' here is always just true - so this loop never ends.
while (true) {}
```

In this specific example, we're checking that `i` is less than `count`. So the
`while` loop will keep running again and again until `i` is at least `5`.

---

```
rect(x, 10, 10, 10)
x = x + 20
```

**Write a description for these two lines in here**

---

```js
  i = i + 1
}
```

At the end of the loop, we increase `i` by 1. This means that `i` slowly counts
up until it reaches `count`, and then the loop stops.

---

**Draw a flowchart and write pseudocode for `draw`**

**Trace through the execution of this code (including every time x and i change)
on paper**

---

`while` is the most basic type of loop, but it makes it pretty easy to shoot
yourself in the foot with an infinite loop. The way we used it above - counting
with a variable from one number to another - is one of the most common ways we
loop through code.

JavaScript (and programming languages like it) give us another way of writing
the same thing which is clearer and less error prone: the `for` loop.

With a `for` loop, our example from before:

```js
var count = 5
var i = 0
while (i < count) {
  doSomething()

  i = i + 1
}
```

becomes

```js
var count = 5
for (var i = 0; i < count; i = i + 1) {
  doSomething()
}
```

With a `for` loop, everything about _how the loop works_ (by counting `i` from 0
to 5) gets moved to the `for` line. This makes things a lot easier to follow.

**Go through the for loop and match each section to the while loop - all the
same bits are there, they've just moved around**.

**Replace the `while` loop in your sketch with a `for` loop**

**Change your code to create a grid of squares instead of a single line. Note:
you can put a loop in another loop!**

**Refactor your code into functions. Try not to have any function longer than
about 5 lines**

**What's the most interesting looking sketch you can create with a `for` loop?**

# Part 2

**Read through this sketch and predict the result. Use a pen and paper to help
you!**

```js
var yOne = 20
var yTwo = 100
var yThree = 180
var speedOne = 3
var speedTwo = 3
var speedThree = 3

function setup() {
  createCanvas(400, 400)
  background(200)
}

function draw() {
  background(200)

  yOne = yOne + speedOne
  if (yOne < 0 || yOne > height) {
    speedOne = speedOne * -1
  }
  rect(30, yOne, 20, 20)

  yTwo = yTwo + speedTwo
  if (yTwo < 0 || yTwo > height) {
    speedTwo = speedTwo * -1
  }
  rect(60, yTwo, 20, 20)

  yThree = yThree + speedThree
  if (yThree < 0 || yThree > height) {
    speedThree = speedThree * -1
  }
  rect(90, yThree, 20, 20)
}
```

**Create a new sketch with the code and run it. Was your prediction correct?**

As in the previous example, we've got a lot of repetition here. **How would you
refactor the code to avoid the repetition?**

It looks like we might be able to use a loop as we're doing basically the same
thing a bunch of times. There's a problem though - although the repeated code
here has a very similar structure, it's not identical like it was before.
There's different pieces of data around, with different variable names to refer
to it. We can't fix this by just moving the code into a loop.

We need to use something called an array. Array is one of the ways that
programmers talk about lists. That's all an array is - a list of stuff.

**Open up the console in your browser and we'll try using some arrays.**

With each of the lines below:

1. read it carefully and make a prediction as to what you think will happen -
   **this is the most important step!**
2. type it into the console and press enter
3. Record the actual result
4. Try to figure out **why**, especially if your guess was incorrect.

Take your time, and feel free to explore and play if something unexpected
happens.

> **Note:** don’t copy-paste! If you copy paste these lines, some of them won’t
> run correctly. Type them out by hand - it’s better practice anyway.

| Line                      | Expected Result | Actual Result | Were you right? Why? |
| ------------------------- | --------------- | ------------- | -------------------- |
| `[]`                      |                 |               |                      |
| `[1, 2, 3]`               |                 |               |                      |
| `['a', 'b', 'c']`         |                 |               |                      |
| `['a', 2, false]`         |                 |               |                      |
| `[].length`               |                 |               |                      |
| `[5, 6, 7].length`        |                 |               |                      |
| `var myArray = [5, 6, 7]` |                 |               |                      |
| `myArray`                 |                 |               |                      |
| `myArray.length`          |                 |               |                      |
| `myArray[1]`              |                 |               |                      |
| `myArray[0]`              |                 |               |                      |
| `myArray[2]`              |                 |               |                      |
| `myArray[3]`              |                 |               |                      |
| `myArray[1] = 'hi'`       |                 |               |                      |
| `myArray[1]`              |                 |               |                      |
| `myArray`                 |                 |               |                      |
| `myArray.push(14)`        |                 |               |                      |
| `myArray`                 |                 |               |                      |
| `myArray.length`          |                 |               |                      |
| `var index = 1`           |                 |               |                      |
| `myArray[index]`          |                 |               |                      |
| `index = 2`               |                 |               |                      |
| `myArray[index]`          |                 |               |                      |

Hopefully you'll be able to see that:

- An array is a list of stuff, separated by `,` commas
- It starts with a `[` and ends with a `]`
- It has a `.length` which tells us how many things are in it
- We can get individual items from the array using `[someNumber]`
- The number can also be a variable
- The number counts from 0, not 1
- We can change the contents using `=` just like with variables
- `.push(someItem)` adds things to the end of the array

So, how can we use this to help us with the code from earlier? We can start by
replacing our repeated similar variables with lists instead.

Change:

```js
var yOne = 20
var yTwo = 100
var yThree = 180
```

into

```js
var ys = [20, 100, 180]
```

Then go through the rest of your code and replace `yOne` with `ys[0]`, `yTwo`
with `ys[1]`, and `yThree` with `ys[2]`. **Run your code again - it should still
work as before. Go through and replace the `speed` variables with an array
called `speeds` as well.**

We've almost done it! Finally, we need to create a `for` loop that counts from
`0` up to `3`. Create your loop, then move _one_ of the three repeated sections
inside it. Inside, replace every hard-coded number that we're using to access
the array with `i`, or whatever you're using for the index variable in your
loop.

<details><summary>Result (click to expand)</summary><p>

```js
var ys = [20, 100, 180]
var speeds = [3, 3, 3]

function setup() {
  createCanvas(400, 400)
  background(200)
}

function draw() {
  background(200)

  for (var i = 0; i < 3; i++) {
    ys[i] = ys[i] + speeds[i]
    if (ys[i] < 0 || ys[i] > height) {
      speeds[i] = speeds[i] * -1
    }
    rect(30 * (i + 1), ys[i], 20, 20)
  }
}
```

</p></details>

Tasks:

- [ ] **Add a variable `count` that controls the number of boxes on screen.**
  - Hint: use an empty array `[]`, another `for` loop, and `.push()` to create
    the starting arrays
- [ ] **Have the boxes move left and right as well as up and down**
- [ ] **Give each box a random start speed**
- [ ] **Create a new moving box at the position of the mouse when the user
      clicks the sketch**
- [ ] **Add gravity! Each frame, add a small amount to the boxes y speed to
      simulate falling**

---

# Part 3

Go to codewars and complete as many Array (and string) kata's as you can!
They'll cover a lot of new unfamiliar stuff that you'll need to research, but if
you find you get stuck on something for too long just move on to a different
one.
