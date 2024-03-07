## JS Interviwe Preperation
#### To share code window [codeshare.io](https://codeshare.io/)  

>User Api : [https://jsonplaceholder.typicode.com/comments](https://jsonplaceholder.typicode.com/comments)  

---

###### Febonisis series of first 4 numbers
```javascript
let febo = (num) => {
  let count = 0;
  let n1  = 0; let n2=1;
  let n3=0;
  console.log( n1 );
  console.log( n2 );
  while( count < num ) {
    n3 = n1 + n2;
    n1 = n2;
    n2 = n3;
    console.log( n3 );
    count ++;
  }
}
febo(5);
// O/p: 0 1 1 2 3 5
```
---


###### Empty Array using splice
```javascript
let arr = [1,2,5];
console.log(arr.splice())
```
---
###### Reverse The string `Good Morning People`
**Output** => _`elpoeP gninroM dooG`_
```javascript
let string = "Good Morning People";
function reverseString(str,seperator) {
    let res = str.split(seperator) //['G', 'o', 'o', 'd', ' ',....'l', 'e']
    res= res.reverse()             //['e', 'l', 'p', 'o', 'e', 'P'....'d', 'o', 'o', 'G']
    return res.join(seperator);;   // elpoeP gninroM dooG
}
console.log(reverseString(string,"")); //
  > OUTPUT: elpoeP gninroM dooG
```


---
###### Print only values from the object  
`user = { name: "Vishal", address: { primary: { house: "109", street: { main: "21", cross: "32" } } } }`;  
**Output** => `Vishal  109 21 31`

```javascript
var user = { name: "Vishal", address: { primary: { house: "109", street: { main: "21", cross: "32" } } } };

function printData(user) {
  for( x in user ) {
    if ( typeof user[x] != 'object' ) {
        console.log( user[x] );
    } else {
      printData( user[x] );
    }
  }
}   
printData( user );
```


---
######  Flatten the array let obj = `[0,1,[2,4,[5,6,[7,8,[9]],10],11],12,[13,14]]`;
**Output** => `[0, 1, 2, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]`
```javascript
const flattenArray = (arr) => {
  let res = [];
  arr.map((current)=>{
    if( Array.isArray(current)) {
      res = [...res, ...flattenArray(current)]
    } else {
      res = [...res, current];
    }
  })
  return res
}

let arr = [0,1,[2,4,[5,6,[7,8,[9]],10],11],12,[13,14]]
console.log(flattenArray(arr));
```
---


###### let obj = `[{a:2},{a:2},{b:3},{b:6}]`;
**Output** => `[{a:4},{b:9}]`
```javascript
let res = {}
for(x in obj) {
        for( y in obj[x]) {
                if( typeof res[y] == 'number') {
                        res[y] += obj[x][y];
                } else {
                        res[y] = obj[x][y];
                }
        }
}
console.log(res)
```
---


###### What is `Proto` or `Prototype`
```javascript
let obj = {
    name:'persistent'
}
let newObj = {
        age: 20,
    __proto__: obj
}

newObj.name                 // persistent
obj.name = 'infosys'
newObj.name                 // infosys
// This is called deep copy
```
---


###### What is polyfill : update prototype of inbuild object  
Create polyfill of `Array.filter()` function
```javascript
Array.prototype.myfilter = function(fn) {
  let res = []
  for(let i = 0 ; i < this.length ; i++) {
    if( fn(this[i]) ) {
      res.push(this[i])
    }
  }
  return res
}
// To use the pollyfil
let arr = [1,2,3,4]
let filteredArray = arr.myfilter((item) => item > 2)
console.log(filteredArray)
```
---


###### Polyfill Convert Object to Array
```javascript
Object.prototype.toArray = function(obj) {
  let res = [];
  const indexes = Object.keys(obj);
  for(let i=0; i < indexes.length; i++) {
    obj[i] && res.push(obj[i])
  }
  return res;
}

let obj = {0:"Apple", 1:"Mango", 2:"banana"}
const res = ;
console.log(Object.toArray(obj));
```
---


###### Extract the name in which english subject exists
**Output** => `[ 'nitin', 'swapnil' ]`
```javascript
const course = {
    sachin:['arts','algebra'],
    nitin:['geo','english'],
    rupnesh:['science','marathi'],
    swapnil:['english','math']
}

const str = 'english'
let res = [];
for(const item in course) {
    if(course[item].length) {
        let aa = course[item].filter((subject)=>{
            return subject.toLowerCase() === str 
        })
        if(aa.length) {
            res.push(item);
        }
    }
}
console.log(res)
```
---



###### From an array of unordered sequence between 1-20, generate the array in which first 10 values will be ascending order i.e. 1-10. and further element should be in descending order from 20-11  
`const arr = [11,2,20,4,5,6,18,8,9,10,1,12,13,14,15,16,17,7,19,3];`  
**Output** => `[ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 20, 19, 18, 17, 16, 15, 14, 13, 12, 11 ]`
```javascript
let res1=[];
let res2=[];
arr.map((item, inded)=>{
    if(item <=10){
        res1.push(item)
    } else {
        res2.push(item)
    }
})
res1.sort((a,b)=>{return a-b});
res2.sort((a,b)=>{return a-b});
res2=resr.reverse();
const result = [...res1,...res2];
console.log(result);
```
---


###### Write a code to find sum of digits of a number untill the sum becomes single digits
**Output** => `5431 => 5+4+3+1 => 13 => 1+3 => 4`
```javascript
const sumNum = (num) => {
  num = num.toString();
  sum = 0;
  for(let i=0 ; i<num.length; i++) {
    sum = sum + parseInt(num[i]);
  }
  
  if(sum.toString().length > 1) {
    console.log(`Recalling sum on ${num} | Sum : ${sum}`);
    sumNum(sum)
  } else {
    console.log(`Result is : ${sum}`);
  }
}

sumNum(543);
```
---


###### Get only non-repetitive elements  
`[1, 9, 0, 2, 3, 7, 4, 3, 3, 4, 9, 1, 2, 5, 5]`  
**Output** => `[0, 7]`
```javascript
let _arr = [1, 9, 0, 2, 3, 7, 4, 3, 3, 4, 9, 1, 2, 5, 5];
let occur = [];
_arr.map((val, index) => {
  if (_arr.indexOf(val) === index && _arr.lastIndexOf(val) === index) {
    occur.push(val);
  }
});
console.log(occur);
```
---



###### Filter unique objects
```
langArray = [ { lang: 'JavaScript' }, 
              { lang: 'JavaScript' },      
              { lang: 'TypeScript' } ]
```
**Output** => `[{lang:'JavaScript'},{lang:'TypeScript'}]`
```javascript
let temp = [];
let resLang = [];

langArray.map((lang)=>{
  if(!temp.includes(lang.lang)) {
    temp = [...temp, lang.lang];
    resLang = [...resLang, lang]
  }
})

console.log(resLang)
```
---


###### Remove null and undefined
`{ a: undefined, b:null, c: "hello", d: 25, e: "Hero" }`  
**Output** => `{ c: "hello",  d: 25,  e: "Hero"}`
```javascript
  const obj = { a: undefined, b:null, c: "hello", d: 25, e: "Hero" };
  
  let res = Object.entries(obj);        // array => [[key,val],[key,val]]
  res = res.filter(([_, val]) => {      // array destructure
    return val != null;
  });

  res = Object.fromEntries(res)         // convert array => object
```
---


###### Find the pair of array element for which sum is equal to given target value
(two sum problem)
`arr  = [1,2,3,4,6,7,8,9]`  
**Output** => `[ [1,8],  [ 2, 7],  [3,6] ]`
```javascript
let sumTwo = (arr, target) => {
    arr = arr.sort((a,b) => a-b);
    let res = [];
    let temp = [];
    arr.map((num, index) => {
        const dif = target - num;
        if(arr.includes(dif) && !temp.includes(dif)) {
            res.push([num, dif])
            temp.push(num);
        }
    })
    return res;
}

let arr  = [1,2,3,4,6,7,8,9];
console.log(sumTwo(arr, 9))
```

---

###### Sort the array by name values
```javascript
const books = [
  { name: "Harry Potter", author: "Joanne Rowling" },
  { name: "Warcross", author: "Marie Lu" },
  { name: "The Hunger Games", author: "Suzanne Collins" }]
  
  let bRes = books.sort((a,b)=>{
	  return a.name.localeCompare(b.name) // local compare is use to compare two strings
  })
console.log(bRes);
```

---

###### Print count each minute until 5  
```javascript
for(let i = 1; i <=5 ; i++) {
  setTimeout(() => {
    console.log(i);
  }, i*1000);
}
```

-------
###### Sum of array with recursion
**Note:** ` without uring map, filter, reduce, for, while loops, iterations`  
```javascript
let arr = [1,2,3]
let l = arr.length
console.log(sumArr(arr, l))

let sumArr  = (arr, l) => {
  if(l == 0) {
    return 0;
  }
  return (sumArr(arr, l-1) + arr[l-1])
}
```

--------
###### Memoize Program
```javascript
function memoize(fn, type) {
    let cache = {sum: {}, fact:{}}
    return (...arg) => {
          let strArg = JSON.stringify(arg);
         if(cache[type][strArg]) {
           return cache[type][strArg]
         } else {
           const res = fn(...arg);
           cache[type][strArg] = res;
           return res;
         }
    }
}
// Calling
let sum = (a,b) => a+b;
let fact = (n) => {
 let fact=1
 for(let i =1; i<= n ; i++) {
  fact = fact * i;
 }
 return fact;
}
 
const sumM = memoize(sum, 'sum');
const factM = memoize(fact, 'fact');
console.log(sumM(4,5));
console.log(sumM(4,5));
console.log(factM(4));
console.log(factM(4));
```

---













