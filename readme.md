# LeetCode 30 Days of JavaScript

This repository contain the question and solution to the LeetCode 30 days of JavaScript challenge.

Note - The challenge will be done in Typescript

[My LeetCode Profile 🧑‍💻](https://leetcode.com/huebart16/)

[Join the Challenge](https://leetcode.com/studyplan/30-days-of-javascript/)

## Table of Content

- [01 Create Hello World Function ↗️](#01-create-hello-world-function)
- [02 Counter ↗️](#02-Counter)
- [03 To Be Or Not Be ↗️](#03-To-Be-Or-Not-Be)
- [04 Counter 2 ↗️](#04-Counter-2)
- [05 Apply Transform Over Each Element in Array↗️](#05-Apply-Transform-Over-Each-Element-in-Array)
- [06 Filter Element from Array↗️](#06-Filter-Elements-from-Array)
- [07 Apply Transform Over Each Element in Array↗️](#07-Array-Reduce-Transformation)
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

## 03 To Be Or Not Be

### [Problem Statement ↗️](https://leetcode.com/problems/to-be-or-not-to-be/?envType=study-plan-v2&envId=30-days-of-javascript)

Write a function expect that helps developers test their code. It should take in any value val and return an object with the following two functions.

- toBe(val) accepts another value and returns true if the two values === each other. If they are not equal, it should throw an error "Not Equal".
- notToBe(val) accepts another value and returns true if the two values !== each other. If they are equal, it should throw an error "Equal".
### Solution

```js
type ToBeOrNotToBe = {
    toBe: (val: any) => boolean;
    notToBe: (val: any) => boolean;
};

function expect(val: any): ToBeOrNotToBe {
	return {
        toBe: (val1: any):boolean => {
            if (val1=== val){
                return true
            } else {
                throw "Not Equal"
            }
        },
        notToBe: (val2: any):boolean  => {
             if (val2!== val){
                return true
            } else {
                throw "Equal"
            }
        }
    }
};

/**
 * expect(5).toBe(5); // true
 * expect(5).notToBe(5); // throws "Equal"
 */

```

## 04 Counter 2

### [Problem Statement ↗️](https://leetcode.com/problems/counter-ii/?envType=study-plan-v2&envId=30-days-of-javascript)

Write a function createCounter. It should accept an initial integer init. It should return an object with three functions.

The three functions are:

- increment() increases the current value by 1 and then returns it.
- decrement() reduces the current value by 1 and then returns it.
- reset() sets the current value to init and then returns it.
### Solution

```js
type ReturnObj = {
    increment: () => number,
    decrement: () => number,
    reset: () => number,
}

function createCounter(init: number): ReturnObj {
    let val1 = init
	return {
        increment: () => {
            val1 += 1
            return val1
        },
         reset: () => {
            val1 = init
            return val1
        },
        decrement: () => {
           val1 -= 1
           return val1
        },
       
    }
};

/**
 * const counter = createCounter(5)
 * counter.increment(); // 6
 * counter.reset(); // 5
 * counter.decrement(); // 4
 */

```

## 05 Apply Transform Over Each Element in Array
### [Problem Statement ↗️](https://leetcode.com/problems/apply-transform-over-each-element-in-array/?envType=study-plan-v2&envId=30-days-of-javascript)

Given an integer array arr and a mapping function fn, return a new array with a transformation applied to each element.

The returned array should be created such that returnedArray[i] = fn(arr[i], i).

Please solve it without the built-in Array.map method.

### Solution 
```javascript
function map(arr: number[], fn: (n: number, i: number) => number): number[] {
	const newArray: number [] = []
    arr.forEach((item, index) => {
        const val = fn(item, index)
        newArray.push(val)
    })
    return newArray
};

```

## 06 Filter Elements from Array
### [Problem Statement ↗️](https://leetcode.com/problems/filter-elements-from-array/submissions/?envType=study-plan-v2&envId=30-days-of-javascript)

Given an integer array `arr` and filtering function `fn`, return a filtered array `filteredArr`.
The `fn` function takes one or two arguments
- arr[i] - number from the arr
- `i` - index of arr[i]
filteredArr should only contain the elements from the arr for which the expression fn(arr[i], i) evaluates to a truthy value. A truthy value is a value where Boolean(value) returns true.

Please solve it without the built-in Array.filter method.
### Solution 
```javascript
type Fn = (n: number, i: number) => any

function filter(arr: number[], fn: Fn): number[] {
    const newArray: number[] = []

    arr.forEach((item, index) =>{
        const val = fn(item, index)
        if(val){
            newArray.push(item)
        }
    })
    return newArray
};
```


## 7 Array Reduce Transformation
### [Problem Statement ↗️](https://leetcode.com/problems/filter-elements-from-array/description/?envType=study-plan-v2&envId=30-days-of-javascript)

Given an integer array nums, a reducer function fn, and an initial value init, return a reduced array.

A reduced array is created by applying the following operation: val = fn(init, nums[0]), val = fn(val, nums[1]), val = fn(val, nums[2]), ... until every element in the array has been processed. The final value of val is returned.

If the length of the array is 0, it should return init.

Please solve it without using the built-in Array.reduce method.
### Solution 
```javascript
type Fn = (accum: number, curr: number) => number

function reduce(nums: number[], fn: Fn, init: number): number {
    let result:number = init

    if(nums.length === 0){
        return result
    }

    nums.forEach((item) => {
        result = fn(result, item)
        
    })
    return result
};
```