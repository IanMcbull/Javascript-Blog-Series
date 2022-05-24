# What does Asynchronous and Synchronous even mean?
All around us, we have synchronous and asynchronous activities happening. Can you think of any examples of synchronous operations?
- Taking a shower
- Sleeping

What about asynchronous activities?
- Cooking
- Watching TV

We’ve all heard the phrase, ‘you cannot serve two masters at a time’. This is exactly what synchronous means. You have to do one thing at a time. Most of the time, the nature of the operation will not allow you to do anything else.
An easy-to-understand activity that all of us do, is taking a shower. Have you ever tried to take a shower and cook at the same time? Don’t try it, it won’t end well. You can’t take a shower and eat pizza. Have you ever found yourself taking a jog while you’re asleep? Probably not. 
These are day to day examples of synchronous activities that we all do.

What about asynchronous operations? Watching TV is an asynchronous activity. You can watch TV and eat pizza. You can watch TV and sleep, hi mum. Cooking is also an asynchronous activity. Just because the rice isn’t ready yet, doesn’t mean you can’t make a phone call, or do dishes. You can do something else as the rice is cooking. This is what we mean by asynchronous tasks. You can do other things while the async task is being fulfilled.
Now let’s look at why we need asynchronous code. Couldn’t we just right code synchronously and be on our merry way. Well, yes, we can. You can write your code In a manner that it doesn’t utilize the non-blocking model. Let’s look at an example.
Loops are synchronous by default. 

```js
console.log("I am step 1");

for(let i = 0; i < 10; i++){
console.log(i)
}

console.log("I am step 2")
```

