# What is asynchronous programming
There are generally two ways to write code, synchronously and asynchronously.Before we dive into the code, let's take a step back, and identify some real life synchronous and asynchronous operations.

## The Supermarket (synchronous/blocking)
Think of a time you went to the supermarket and found a long queue at the checkout counter. The nature of this transaction is synchronous because:
1. A cashier can only serve one customer at a time.
1. The cashier is responsible for starting and completing the entire transaction.
1. If for whatever reason the cashier cannot complete a transaction, the queue will come to a stop. The cashier will be *blocked*.

## The restaurant (asynchronous/non-blocking)
Think about the last time you went to a restauraunt. If you're like me, the first thing you did, was walk over to the counter and make your order.The cashier will then pass your order down to the kitchen staff, who will start preparing it for you. The cashier doesn't have to wait for your order to complete, to serve more customers. He/she can continue serving other customers, as your meal is being prepared. 
When your order is ready, they'll call out your name, and you'll be on your way in no time.
The nature of this trasnaction is asynchronous because:
1. The cashier can serve multiple customers at a time, as the meal is being prepared. 
2. The cashier is not responsible for the entire transaction.After the order has been made, he/she will pass the order down to the kitchen staff who will proceed to prepare the meal. Once the meal is done, they will notify the cashier, who will then notify the customer and complete the transaction.

## Getting started with asynchronous Javascript
What it does it mean to be asynchronous in jvascript. Let's have a look at a definitions;

> Asynchronous means that things can happen independently of the main program flow. -**nodejs.dev**

> Asynchronous programming is a technique that enables your program to start a potentially long-running task, and then rather than having to wait until that task has finished, to be able to continue to be responsive to other events while the task runs. Once the task is completed, your program is presented with the result. - **MDN**

In simple terms, asynchronous code, simply means, writing code that does not block the main execution flow of the program. 
Javascript runs on a single thread, and is synchronous by default. So javascript cannot take advantage of concepts like multithreading. So how do we achieve asynchronous code. The browser provides APIs that provide asynchronous functionality.

Let's have a look at how synchronous code looks like

```js
for(let i = 0;i < 10;i++){
console.log(i)
}
console.log('I will print after the for loop is done.')
```
The code is run top-down and is executed line by line. While the for loop is running, no other operation can be handled by the program. Every other code that needs to be executed, will have to wait until the for loop has finished.
This is what will be printed to the console:

```js
0
1
2
3
4
5
6
7
8
9
"I will print after the for loop is done."
```
This isn't a problem when looping through a small set of numbers. It starts becoming an issue when we need to loop over a huge set of numbers. Imagine trying to loop from 0 - 10,000,000.
This would take longer. Which means, that as long as the main thread is blocked, your program will not be able to do anything else.

As we've seen writing synchronous code, can become problematic. We can however solve this by writing asynchronous javascript. Javascript provides three main ways of writing asynchronous code:

- callbacks
- promises
- Async/Await

### callbacks
In my opinion,the best way to illustrate a callback and how they work, is by writing some code.
Let's revisit the loop we did previously, but this time, let's write it asynchronously using callbacks:

```js
setTimeout(()=>{
for(let i = 0;i < 10;i++){
console.log(i)
}
},0)
console.log("I will run before the for loop")
```
This is what will be printed to the console:
```js
"I will run before the for loop"
0
1
2
3
4
5
6
7
8
9
```
settimeout takes in two parameters. A callback function, and a number which represents how long the function should wait before being invoked. In our implementation, we called settimeout after zero milliseconds. 