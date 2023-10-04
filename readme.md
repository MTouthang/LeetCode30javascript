# LeetCode 30 Days of JavaScript

This repository contain the question and solution to the LeetCode 30 days of JavaScript challenge.

Note - The challenge will be done in Typescript

[My LeetCode Profile 🧑‍💻](https://leetcode.com/huebart16/)

[Join the Challenge](https://leetcode.com/studyplan/30-days-of-javascript/)

## Table of Content

- [01 Create Hello World Function ↗️](#01-create-hello-world-function)
- [01 Counter ↗️](#02-Counter)

## 01 Create Hello World Function

### [Problem Statement ↗️](https://leetcode.com/problems/create-hello-world-function/?envType=study-plan-v2&envId=30-days-of-javascript)

Write a function createHelloWorld. It should return a new function that always returns "Hello World".

### Solution

```js
function createHelloWorld() {
  return function (...args): string {
    return "Hello World";
  };
}
/*
 * const f = createHelloWorld();
 * f(); // "Hello World"
 */
```

### Explanation

Inside the return statement of the createHelloWorld function we just have to return the string "Hello World" as it is a simple hello world program.

## 02 Counter

### [Problem Statement ↗️](https://leetcode.com/problems/counter/?envType=study-plan-v2&envId=30-days-of-javascript)

Given an integer n, return a counter function. This counter function initially returns n and then returns 1 more than the previous value every subsequent time it is called (n, n + 1, n + 2, etc).

### Solution

```js
function createCounter(n: number): () => number {
    let numb = n - 1
    return function() {
        numb += 1
        return numb
    }
}

/** 
 * const counter = createCounter(10)
 * counter() // 10
 * counter() // 11
 * counter() // 12
 */
```

### Explanation
---
