# Logic and Control Flow

## Logic

We're ready to incorporate logic into our Ruby programs. We'll soon build
programs that react dynamically to logical propositions. For now, we'll learn
how to construct those propositions and examine the Ruby interpreter's
evaluation of them.


## Comparison Operators

Ruby provides several operators that compare one object to another. Some are
familiar from elementary mathematics. `>`, `<`, `>=`, `<=`, `==`, and `!=` mean
what you'd expect: "greater than," "less than," "greater than or equal to,"
"less than or equal to", "equal to", and "not equal to." Note that `==`, not `=`
checks for equality. Recall that `=` is the assignment operator. Comparison
operators allow one to build expressions that the Ruby interpreter can evaluate
as logical propositions. The expression generally evaluates to `true` if the
proposition is valid and to `false` if it is invalid.

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/49?lite=true"></iframe>

Ruby also permits string comparison. `"cat" < "dog"` returns `true` because
"cat" precedes "dog" alphabetically. One can compare different data types only
when checking for equality. `"cat" < 4` throws an error. `"cat" != false`
returns `true`. One can compare arrays only for equality, i.e., one array is
neither greater nor less than another:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/72?lite=true"></iframe>


## Logical Operators

Ruby has three logical operators, `&&` (AND), `||` (OR), and `!` (NOT). `&&`
evaluates to `true` if both its operands are true. `||` evaluates to `true` if
at least one operand is true. `!` returns `true` if its operand is `false` and
`true` if its operand is `false`.

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/56?lite=true"></iframe>

In `true || false`, the Ruby interpreter doesn't evaluate the code after `||`
because it's irrelevant. Since the first operand is `true`, the expression will
be true regardless of the second operand. This behavior is an example of
**short-circuit evaluation**, where the second operand of a logical operator is
evaluated only if the first operand does not suffice to determine the value of
the expression. Conversely, `false && true` is also an example of
short-circuiting (the expression will be false regardless of the second
operand).

`!`, sometimes known as _bang_, reverses the boolean value of its operand.
Though `!` receives a single operand, that operand can be the result of an
expression. `!(false || true)` returns `false`. `!false || true` would return
`true` and would short-circuit.

`&&` and `||` also permit expressions as operands:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/57?lite=true"></iframe>


## Control Flow

So far the Ruby interpreter has executed all of our programs sequentially and
continuously:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/55?lite=true"></iframe>

More sophisticated programs require manipulating **control flow**, the order in
which instructions are executed within a program. One modifies control flow
using **control structures**, blocks of code that alter the control flow based
on analysis of given parameters. We'll first examine **conditional statements**,
which instruct the interpreter to execute different branches of code depending
upon whether a condition is true or false.


## Conditional Statements

The simplest conditional statement is the _if statement_.

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/51?lite=true"></iframe>

If the test expression following the `if` keyword is true, then the Ruby
interpreter will execute the subordinate block of code. An if statement always
begins with the `if` keyword and ends with the `end` keyword.

Like English, Ruby features an if-else statement:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/52?lite=true"></iframe>

The Ruby interpreter executes the block subordinate to `else` (`puts "Two is
even. All is well!"`) if `2.odd?` is false. If the test expression following
`if` were true, then the block subordinate to `else` would not be executed.

Unlike English, Ruby also has an if-elsif-else construction. Like `if`, `elsif`
precedes a test expression. One can stack an arbitrary number of `elsif`
statements, but there can be only one `if` and one `else`, though `else` is
optional. `if` introduces the control structure, and `else` acts as a kind of
fail-safe. The block subordinate to `else` is executed only if none of the prior
`if` or `elsif` conditions are true. If no conditions are true and the
conditional statement lacks an `else` block, then the entire statement evaluates
to `nil`.

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/53?lite=true"></iframe>

Only one subordinate block is ever executed in an if, if-else, or if-elsif-else
statement. If one of the test expressions is true, then the result of its
subordinate block is the result of the entire conditional statement. The
interpreter skips over all subsequent code in the conditional statement and
resumes execution after the `end`.

Ruby permits nested conditional statements, though overly nested code
can be difficult to read. Note that subordinate blocks may be any
number of lines. As in method definition, the result of the last line in a block
is the result of the entire block.

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/73?lite=true"></iframe>


## Loops

Loops are the second fundamental control structure in Ruby. **Loops** instruct
the interpreter to repeatedly execute a section of code while a condition holds.
Loops are tremendously powerful: they allow one to execute a potentially
infinite number of operations with a few lines of code.


## While Loops

<iframe src="https://player.vimeo.com/video/208761086?rel=0&autoplay=0" width="100%" height="400px" frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="" style="line-height: 1.6em;" rel="line-height: 1.6em;"></iframe>

The only loop you'll need to know for our online coding challenge is the _while
loop_. If you run the following snippet in Repl.it, the code will never stop
executing. Can you guess why?

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/58?lite=true"></iframe>

Like if statements, while loops begin with a keyword (`while`) followed by a
conditional expression. They also end with `end`. If the conditional
expression is true, then the interpreter executes the subordinate block. The
interpreter then rechecks the condition and executes the block again if it's
still true. A while loop instructs the Ruby interpreter to execute its
subordinate block until its conditional expression becomes false.

The above code is an example of an **infinite loop**, a sequence of instructions
that loops endlessly. This example loops endlessly because `2` is always less
than `3`. An infinite loop is almost always a mistake.

How might you introduce a terminating condition to a while loop? This condition
must be true at first but would eventually become false, so as to terminate
the loop. The most common approach is to assign a counter variable outside of
the loop and increment it within the loop:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/59?lite=true"></iframe>

The interpreter evaluates the expression following `while` for truth at the
start of each loop. After the counter is incremented to `11`, the condition
becomes false, so the loop terminates.

_A note on terminology_: An **iteration** is the act of repeating a procedure, hence looping is an
iterative technique. Each repetition itself is also called an "iteration."  

For the challenge, you'll typically use while loops to iterate through an array or string. This technique uses the counter to index into elements one at a time.

<iframe src="https://player.vimeo.com/video/208761850?rel=0&autoplay=0" width="100%" height="400px" frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="" style="line-height: 1.6em;" rel="line-height: 1.6em;"></iframe>

Take a look at this video to see how you'd use while loops and control
statements to solve a difficult problem:

<iframe src="https://player.vimeo.com/video/208761487?rel=0&autoplay=0" width="100%" height="400px" frameborder="0" webkitallowfullscreen="" mozallowfullscreen="" allowfullscreen="" style="line-height: 1.6em;" rel="line-height: 1.6em;"></iframe>

Although a while loop is technically an expression in that it evaluates to a
single value, that value is always `nil`. If the while loop is within the body
of a method definition, one can explicitly return a value from the loop (and the
method) using the `return` keyword:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/81?lite=true"></iframe>

One can nest loops just as one would conditional statements:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/80?lite=true"></iframe>

Nested loops are useful for solving complex problems. You'll absolutely want to
practice them before taking our coding challenge. Let's combine using `return`
in a while loop with a nested loop to solve this difficult problem: Define a
method that returns a boolean indicating whether any two elements in the
argument (an array) sum to 0.

Because we want to track two elements as we iterate through an array, we'll want
to set up two loops. As we check each element, we also need to check every
_other_ element. We'll use our counter to index into the array and to ensure
that we don't check the same element twice. This pattern is quite common.
Memorize it.

First try to code up your own implementation then check our solution:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/74?lite=true"></iframe>

Our solution:

<iframe frameborder="0" width="100%" height="500px" src="https://repl.it/GD3i/67?lite=true"></iframe>
