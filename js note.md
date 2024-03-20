# Javascript Notes  
[Shreyians coding school](https://www.youtube.com/watch?v=qJGR9lLcRc0&t=113s)  

---


#### Prototype and Prototype inheritence  
```javascript
let obj = {name:'sachin'};
obj.name = 'supriya';
let person = {age:25, name:obj.name, getAge:function(){return this.age}} // shallow copy
let person2 = {age:26, __proto__:person} // as proptotype inheritance
// call

console.log(person.getAge.call(person2));
```
---


#### Call Bind Apply
```javascript
let person = {
  name: 'sachin',
}

function sayHi(age) {
  return `Name is ${this.name}, Agi is ${age}`;
}
console.log(sayHi.call(person,21)); // Name is sachin, Agi is 21
console.log(sayHi.apply(person,21)); // 
console.log(sayHi.bind(person,21)()); // Name is sachin, Agi is 21
```

---

#### Bind functionality  
```javascript
const sachin = { 
                name: "Sachin", 
                sayName: function(){ console.log(this.name) }
	        }
const nikita = {name: "Nikit"}
setTimeout(sachin.sayName, 3000) // undefined - after 3 sec the context of this changes
setTimeout(sachin.sayName.bind(nikita), 3000) // w.r.t above line binding nikita object
```
---


#### Check if the val is integer or not  
```javascript
let a = 12;
const checkInteger = (val) => a % 1 === 0
```
-------------
#### DEEP COPY AND SHALLOW COPY  
**Ref:** [https://youtu.be/mk7RpyHMUrU?si=1mSkhWwA4hJVazeP]  
```javascript
let obj = {
  name: 'sachin',
  address: {
    city: "Nagpur",
    state: "maharashtra"
  }
}

let user = Object.assign({}, obj); // shallow copy
let user = {...obj}  // shallow copy
 
user.address.city = "Pune";
console.log("this is obj: ", obj);
console.log("this is user: ", user);
```

>object.assign,{...obj} => these are copying by reference i.e. memory location.
There is no way to do deep copy of object.
If there are nested object, it affects the source object i.e. its shallow copy.
it fails to maintain saperete copy of user and object. 
To bring deep copy i.e. nested object should not affect, we can use loadash externaly
via cdn or npm package
```javascript
//Syntax
let user = let user = _.cloneDeep(obj);
```

--------------
#### DEBOUNCING  
To reduce amount of time function calling. 
Optimize function calling on change Event
Hold function call for some-time.
```html
<input type="text" onChange={myDebounce(doSomething,1000)} laceholder="Enter text here"/>
```

```javascript
  let counter = 0;
  const doSomething = (e) => {
    console.log("Fetchin data : ", counter++, e.target.value)
  }

  function myDebounce (fun, t=1000) {
    let timer;
    return (...event) => {
      clearTimeout(timer)
      timer = setTimeout(()=>{fun(...event)}, t)
    }
  }
```
---------
#### THROTTLING  
Use case - On submiting the form, if user hit submit multiple times.
then it should call only once
```html
<button type="button" class="mt-4" onclick="tryThrottle()" id="app">
            Multiple click Here
</button>
```

```javascript
let tcount = 0;
let boolThrottle = true;
function tryThrottle() {
  (() => {
    if (boolThrottle) {
      div.querySelector("#t_count").innerHTML = tcount++;
      boolThrottle = false;
      setTimeout(() => {
        boolThrottle = true;
      }, 1000);
    }
  })();
}
```
----------

#### WEB VITALS  
[Reference](www.google.com)   |   Project example [jest-demo-project](https://github.com/sachin7478/jest_demo_project/tree/master/src)  

These are performance measuring matrices.
In react the package "web-vitals" is being used
>**CLS** - Cumulative layout shift - Visual stability - switching time between landscape to portrate or infinite scroll app
CLS is a very important metric that measures the visual stability of the web page. The metric is called “cumulative” because the score of each shift is added up over the life of a page. Long-lived web pages, like Single-Page Apps (SPAs) or infinite scroll apps, naturally build up more CLS over time.
*`Ensure having CLS score of 0.1 or less.`*



>**FID** - First Input Delay - interactivity - input delay of 100ms or Less
It’s important to look at First Input Delay (FID) when you’re trying to figure out how quickly web pages load because it measures how long it takes people to interact with them. A low FID makes sure that the page is usable.
FID is a measure of how long it takes for a user to interact with a page and for the browser to be able to start processing event handlers as a result.
*`Ideally, FID should be less than 100ms`*
In order to keep FID fast, cut down on third-party code that slows down the whole process. Keep the number of requests and the size of the transfers small to keep the main thread’s work as low as possible. The Requests and Transfer Size values for the Total row are computed by adding the values for the Image, Script, Font, Stylesheet, Other, Document, and Media rows.



>**FCP** - First Contentful Paint -
metric that tracks the time it takes from when the page first loads to when any part of the page’s content appears on the screen. Text, images (including background images), `<svg>` elements, and non-white `<canvas>` elements are all considered “content” for this metric. 
*`Ideally, fcp should be less than 1.8sec`*
A reasonable threshold to measure is the 75th percentile of page loads, split by mobile and desktop devices.



>**LCP** - The Largest Contentful Paint (LCP) statistic measures the amount of time it takes for the largest image or text block visible within the viewport to be rendered in comparison to the time it took for the page to begin loading.
*`A good LCP score is < 2.5 seconds or less`*
>Elements like `<img>` , `<image>` and `<video>` are key contributors in determining LCP score.



>**TTFB** - Time to first byte
TTFB is a metric that measures the time between the request for a resource and when the first byte of a response begins to arrive.
*`A good TFFB score is < 0.8 seconds or less`*

---

#### CURRYING in Javascript  
```javascript
const getSum = (a) => {
  return (b) => {
    return (c) => {
      return (d) => {
        return (e) => {
          // this function forms closure,can grasp all outer arguments
          return a + b + c + d + e;
        }
      }
    }
  }
}
const sum = getSum (1)(2)(3)(4)(5)
console.log(sum);
```
---


#### Google map , redirect to location   
```html
<a href={gmapsLinkGen(props.addressItem)}>  {`${address1} ${address2} ${city} </a>
```
```javascript
const gmapsLinkGen = (officeObj: any) => {
	return (
		"https://maps.google.com/?q=" +
		officeObj.address1 +
		(officeObj.address2 ? ", " + officeObj.address2 : "") +
		(officeObj.city ? ", " + officeObj.city : "") +
		(officeObj.state ? ", " + officeObj.state : "") +
		(officeObj.zip ? ", " + officeObj.zip : "")
	);
};
```

---


#### What is Lazy loading in React ?  
> infinite scrolling
Reference : [Reference](https://www.linkedin.com/posts/saikrishnanangunuri_javascript-javascriptdeveloper-reactjs-activity-7170814145364258817-pTQv?utm_source=share&utm_medium=member_desktop)  
---


- "argument" object of js function [not works on arrow function]

---

- What is web api => fetch, setTimeout, ajax, api calls, setInterval, storage,dom
- Event loop : [Reference Video](https://www.youtube.com/watch?v=fuTWE0Mupzk )
     - execution stack / Call Stack - Runs the code line by line, once any async found, moved to webApi
	   - web api's = Runs the event in isolated/seperate environment that are callback, settimeouts, storage, ajax, fetch
					 - After time completion the event moved to event queue
	   - event queue => moves the event to execution stack that are being moved from webApi's


---
- Css proprocessors
- CSS Object Model
---
