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
- [08 Function Composition↗️](#08-Function-Composition)
- [09 Return Length of Arguments Passed ↗️](#09-Return-Length-of-Arguments-Passed)
- [10 Allow One Function Call ↗️](#10-Allow-On-Function-Call)
- [11 Memoize ↗️](#10-Memoize)
- [12 Add Two Promise ↗️](#12-Add-Two-Promise)
- [13 Sleep ↗️](#13-Sleep)
- [14 Timeout Cancellation ↗️](#14-Timeout-Cancellation)

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

## 08 Function Composition
### [Problem Statement ↗️](https://leetcode.com/problems/function-composition/description/?envType=study-plan-v2&envId=30-days-of-javascript)

Given an array of functions [f1, f2, f3, ..., fn], return a new function fn that is the function composition of the array of functions.

The function composition of [f(x), g(x), h(x)] is fn(x) = f(g(h(x))).

The function composition of an empty list of functions is the identity function f(x) = x.

You may assume each function in the array accepts one integer as input and returns one integer as output.
### Solution 
```javascript
type F = (x: number) => number;

function compose(functions: F[]): F {
    
	return function(x) {
      let output = x
      for(let i = functions.length-1; i>= 0; i--){
          output = functions[i](output)
      }  
      return output;
    }
};

/**
 * const fn = compose([x => x + 1, x => 2 * x])
 * fn(4) // 9
 */
```
## 09 Return Length of Arguments Passed
### [Problem Statement ↗️](https://leetcode.com/problems/return-length-of-arguments-passed/description/?envType=study-plan-v2&envId=30-days-of-javascript)
Write a function argumentsLength that returns the count of arguments passed to it

### solution
```javascript
type JSONValue = null | boolean | number | string | JSONValue[] | { [key: string]: JSONValue };

function argumentsLength(...args: JSONValue[]): number {
	return args.length
};

/**
 * argumentsLength(1, 2, 3); // 3
 */
```

## 10 Allow On Function Call
### [Problem statement ↗️](https://leetcode.com/problems/allow-one-function-call/?envType=study-plan-v2&envId=30-days-of-javascript)
Given a function fn, return a new function that is identical to the original function except that it ensures fn is called at most once.

- The first time the returned function is called, it should return the same result as fn.
- Every subsequent time it is called, it should return undefined.
 
### Solution

```javascript
type JSONValue = null | boolean | number | string | JSONValue[] | { [key: string]: JSONValue };
type OnceFn = (...args: JSONValue[]) => JSONValue | undefined

function once(fn: Function): OnceFn {
    let flag = false
	return function (...args) {
        if(flag){
            return undefined
        } else {
            flag = true
            return fn(...args)
        }
	};
}

/**
 * let fn = (a,b,c) => (a + b + c)
 * let onceFn = once(fn)
 *
 * onceFn(1,2,3); // 6
 * onceFn(2,3,6); // returns undefined without calling fn
 */
```

## 11 Memoize
### [Problem statement ↗️](https://leetcode.com/problems/memoize/?envType=study-plan-v2&envId=30-days-of-javascript)
Given a function fn, return a memoized version of that function
A memoized function is a function that will never be called twice with the same inputs. Instead it will return a cached value.

You can assume there are 3 possible input functions: sum, fib, and factorial.

sum accepts two integers a and b and returns a + b.
fib accepts a single integer n and returns 1 if n <= 1 or fib(n - 1) + fib(n - 2) otherwise.
factorial accepts a single integer n and returns 1 if n <= 1 or factorial(n - 1) * n otherwise.

### Solution

```javascript
type Fn = (...params: number[]) => number

function memoize(fn: Fn): Fn {
    const cache = {}
    return function(...args) {
        const key: any = args
        if(key in cache) {
            return cache[key]
        }
        const output = fn(...args);
        cache[key] = output
        return output
    }
}


/** 
 * let callCount = 0;
 * const memoizedFn = memoize(function (a, b) {
 *	 callCount += 1;
 *   return a + b;
 * })
 * memoizedFn(2, 3) // 5
 * memoizedFn(2, 3) // 5
 * console.log(callCount) // 1 
 */
```

## 12 Add Two Promise
### [Problem statement ↗️](https://leetcode.com/problems/add-two-promises/description/?envType=study-plan-v2&envId=30-days-of-javascript)
Given two promises promise1 and promise2, return a new promise. promise1 and promise2 will both resolve with a number. The returned promise should resolve with the sum of the two numbers.

### Solution

```javascript
type P = Promise<number>

async function addTwoPromises(promise1: P, promise2: P): P {
	const n1 = await promise1
    const n2 = await promise2

    return n1 + n2
};

/**
 * addTwoPromises(Promise.resolve(2), Promise.resolve(2))
 *   .then(console.log); // 4
 */
```
## 13 Sleep
### [Problem statement ↗️](https://leetcode.com/problems/sleep/description/?envType=study-plan-v2&envId=30-days-of-javascript)
Given a positive integer millis, write an asynchronous function that sleeps for millis milliseconds. It can resolve any value.

### Solution

```javascript
async function sleep(millis: number): Promise<void> {
    await new Promise((resolve) =>  setTimeout(resolve, millis))
}
/** 
 * let t = Date.now()
 * sleep(100).then(() => console.log(Date.now() - t)) // 100
 */
```

## 14 Timeout Cancellation
### [Problem statement ↗️](https://leetcode.com/problems/timeout-cancellation/description/?envType=study-plan-v2&envId=30-days-of-javascript)
Given a function fn, an array of arguments args, and a timeout t in milliseconds, return a cancel function cancelFn.

After a delay of t, fn should be called with args passed as parameters unless cancelFn was invoked before the delay of t milliseconds elapses, specifically at cancelT ms. In that case, fn should never be called.

### Solution

```javascript
type JSONValue = null | boolean | number | string | JSONValue[] | { [key: string]: JSONValue };
type Fn = (...args: JSONValue[]) => void

function cancellable(fn: Fn, args: JSONValue[], t: number): Function {
    // here, the fn function with args should be pass after a delay t
	const timeOver = setTimeout(() => fn(...args), t)
    // cancelfn should be call, making never being called
    const cancelFn = () => clearTimeout(timeOver)
    return cancelFn
};

/**
 *  const result = []
 *
 *  const fn = (x) => x * 5
 *  const args = [2], t = 20, cancelT = 50
 *
 *  const start = performance.now() 
 *
 *  const log = (...argsArr) => {
 *      const diff = Math.floor(performance.now() - start);
 *      result.push({"time": diff, "returned": fn(...argsArr)})
 *  }
 *       
 *  const cancel = cancellable(log, args, t);
 *
 *  const maxT = Math.max(t, cancelT)
 *           
 *  setTimeout(() => {
 *     cancel()
 *  }, cancelT)
 *
 *  setTimeout(() => {
 *     console.log(result) // [{"time":20,"returned":10}]
 *  }, maxT + 15)
 */
```
