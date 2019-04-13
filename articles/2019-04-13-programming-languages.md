---
title: The Frontend Guide to Languages
route: /programming-languages
date: 2019-04-13
description: 
---

Today, we're going to make a programming language.

No, it won't take a PhD, or years of your time (or even days for that matter). You and I, together, are going to learn what a programming language _is_ and actually build one that can evaluate programs.

By the end of this post we'll have written a JavaScript function, `evaluate`, which interprets a small programming language with strings and variables. You won't be going off and rewriting your stack in it (though you're certainly welcome to try!), but I hope it's a fun exercise to learn a lot from.

## Hello, world!

To kick things off, we'll write an interpreter for the HelloWorld language, and use it write a [Hello, world! program](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program). 

Here's our goal:

```js
const program = { type: "HelloWorld" };
console.log(evaluate(program));
// => Hello, world!
```

I'm sure you have questions. _Real quick_, let's introduce some terms that we'll more clearly define as we go.

* Our "**program**" is represented by the JavaScript object `{ type: "HelloWorld" }`. Throughout this post, we'll be adding more and more things to this object. For now, there's not much to it.
* Our "**evaluator**" (or "interpreter" - it's your call) is a single JavaScript function that accepts a "**program**."
* We receive a "**value**" from our "**evaluator**," which we send to the wonderful `console.log` function you're all familiar with.

Now let's build our **evaluator**.

```js
function evaluate(node) {
  switch (node.type) {
    case "HelloWorld":
      return "Hello, world!";
    default:
      throw `evaluate -- unknown node type ${node.type}`;
  }
}
```

This function is not terribly interesting, but I'd like to call out a few details.

* Our function accepts a parameter that we call `node` as in, a **node** of a tree. (_dramatic foreshadowing_)
* The crux of this function is a single `switch` statement that operates on the `type` field of our node. Our language is very simple, so we only have a single "node type."
* For the "HelloWorld" **expression** - we return a string containing "Hello, world!"
* If we see something we don't recognize - we throw an error. The programmer (us) messed up!

At this point we have 8 lines of code that evaluate a simple HelloWorld language. I'll emphasize the _simple_ here, there are no variables, no loops, no modules, not even numbers - but it's a language. Our language has a very small **grammar**, but it's a language.

Let's make things more interesting.
