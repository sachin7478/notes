## JS Interviwe Guess The output
#### To share code window [codeshare.io](https://codeshare.io/)
---

**Question**
```
let a=10;
setTimeout(()=>{console.log(a)}, 1000);
console.log("Hello")
```
>**o/p:** //a will get printed after 1000ms  
Hello
10 
---


**Question**
```
for(var i=0; i<3; i++) {
   setTimeout(()=>{console.log(i)},100)
}
```
>**o/p:** 3 3 3     
// if use let - forms a closure and remembers the memory referance of ***i***  
0 1 2
---


**Question**
```
var a = 10;
function a() {
  console.log("20")
}
a();
```
>**o/p:** error:  **a** is not defined  
---


**Quenstion**
```
function sayHi() {
	return () => 0;
}
console.log(typeof sayHi())
console.log(typeof sayHi()())
```
>**op**  
`console.log(typeof sayHi())` // function  
`console.log(typeof sayHi()())` // number

---


**Question**
```
function foo() {
  let a = b = 0;
  a++;
  return a;
}
foo();
typeof a; // => ???
typeof b; // => ???
```
>**o/p:** a is not defined, accidentaly global var b created  
>`undefined`      // undefined   
>`number`              // 0  
---


**Question**
```
(()=>{let x = y = 10})()
(()=>{let x = y = 20})()
console.log(y)
```
>**o/p:**
>```
>(()=>{let x = y = 10})() // "var" y =10 accidentaly gets created
>(()=>{let x = y = 20})() // y becomes 20
>console.log(y) // 20
>```

---


**Question**
```
function foo() {
  let a;
  window.b = 0;
  a = window.b;
  a++;
  return a;
}
foo();
typeof a;        
typeof window.b; 
```
>**o/p:** // a is out of the block i.e. a is undefined, b=0 is var  
`undefined`  
`number`
---


**Question**
```
// Array hole and flat property
const arr = [1, 3, 5];
arr[100] = 199;               // [1, 3, 5, empty × 97, 199]
console.log(arr.length);      // 101
```
---


**Question**
```
function foo() {
	'use strict'
	age=20;
	console.log(20)
}
foo()
```
>**o/p** error - age is not defined  
in strict mode varibale should have var, let , const
---


**Question**
```
var a=10
function test (){
        console.log(a)
        let a = 100;
}
test(); 
```
> **o/p:** Error: Uncaught ReferenceError: Cannot access 'a' before initialization
---


**Question**
```
let num = 10;
var num = 20;
console.log(num) 
```
> **o/p:** - // SyntaxError: Identifier 'num' has already been declared  
if we do var num = 10 (1st line) => num = 20


---
**Question**
```
<div onlclick="console.log('div')">
  <p onlclick="console.log('p')">
    Click Here!
  </p>
<div>
```
> **o/p:** - p div
When we click on p tag, immediately call div due to event bubbling


---
**Question**
```
function sayHi() {
 console.log(name);
 console.log(age);
 var name = 'Lydia';
 let age = 21;
}
sayHi();
```
>**o/p:** Uncaught ReferenceError: Cannot access 'age' before initialization
---

**Question**
```
  console.log(1 +  "2" + "2")
  console.log(1 +  +"2" + "2")
  console.log(1 +  -"1" + "2")
  console.log(+"1" +  "1" + "2")
  console.log( "A" - "B" + "2")
  console.log( "A" - "B" + 2)
  console.log(!'abc') // false  
  console.log(+true)  // true  
  const obj = {a:"1",a:"2"} console.log(obj)
```
  >**o/p:**
> `console.log(1 +  "2" + "2");`   [str] => 122   
  `console.log(1 +  +"2" + "2");`  [str] => 1+ +'2'=> 3+'2'=>32  
  `console.log(1 +  -"1" + "2");`  [str] => 1+ -'1'=> 0+'2'=>02  
  `console.log(+"1" +  "1" + "2");` [str] => +'1'=> 1+'1'=> '11'+2=>'112'  
  `console.log( "A" - "B" + "2");` [str] => NaN2  
  `console.log( "A" - "B" + 2);`   [str] => NAN  
  `console.log(!'abc')`   // false  
  `console.log(+true)`   // true   
  `const obj = {a:"1",a:"2"} console.log(obj)` **o/p** => { a: '2' } // same key

---


**Question**
```
console.log(1+2+"3"+4+5);
console.log(1+2+"3"-4+5);
console.log(1+2+"8"/4+5);
console.log(1+2+"3"*4+5);
```
>**o/p:**
>`console.log(1+2+"3"+4+5);` => 1+'3'=>'33' +4 => '334'+5 =>'3345'  
`console.log(1+2+"3"-4+5);` => '33'-4 => 29 + 5 => 34  
`console.log(1+2+"8"/4+5);` => bodmas "8"/4 => 2 + 8 => 10  
`console.log(1+2+"3"*4+5);` => bodmas "3"*4 => 12 => 20  
---


```
let a = 3; // type number
let b = new Number(3); // type object
console.log(a == b); // true
console.log(a === b); // false
typeof typeof 1   // typeof 1 => 'number' => typeof 'number' => ans=> 'string'
console.log(!true - true) => (0 - 1) => -1
console.log(true + +"10") => 11
console.log('10*10+5'); // '10*10+5'
```
---

**Qustion**
```
let a = {size:"small"}
let d;
d = a;
a.size="Big";
console.log(d, a);
```
>**o/p:**  `{ size: 'Big' } { size: 'Big' }   `

---

**Qustion**
```
let x = 1; 
if (function f() {}) { 
    x += typeof f; 
} 
console.log(x); 
```

>**o/p:** `1undefined`
---


**Qustion**
```
let obj1 = { key: "value" };
let obj2 = obj1;
let obj3 = obj2;

obj1.key = "new value";

obj2 = { key: "another value" };
console.log(obj1.key, obj2.key, obj3.key);
```
>**o/p:** ` new value  |  another value  |   new value `
---

