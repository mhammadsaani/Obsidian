# Essential Concepts

1. Know what  ***this*** is at any time?

```
1) in the global context (global object, undefined in strict mode)
2) as a method on an object (object on left side of dot)
3) as a constructor function or class constructor (the instance itself with new)
4) as a DOM event handler (the element itself)
```
What is this?
this is basically a reference to object. but the problem we face is that reference of *this* changes according to the context. 

1. In global context, **this** refers to window object.
	` console.log(this)  // output will be window`
2. When called inside a normal function
	1. without strict mood
		```
		function whatIsThis(){
			console.log(this)
		}
		// this will still be refering to window object
		```
	2. with strict mood
		 ``` 
		 function whatIsThis(){
			 'use strict'
			 console.log(this)
		 }
		// this will be undefined
		 ```
		 
	The benifits of not refering *this* to window object in strict mood is 
	Look at the below code :-)
```
function whatIsThis() {
//   console.log(this);
 this.something = 2;
 console.log(something);
}
whatIsThis();
console.log(something)

```

When we set value using this.something inside the scope of function, as this is refering to global object, window. something = 2 will be accessible outside of the scope too.

3. As a method on an object

```
user = {
	first: "Hammad",
	last: "Sani"
	greetUser(){
		console.log(this.first + " " + this.last)
	}
}

// will refer to object itself.
```

4. As constructor function or class constructor
      1. It refers to the instance created using new keyword
```
class User {
  constructor(first, age) {
    this.first = first;
    this.age = age;  
  }  
  
  getAge() {
    console.log(`${this.first}'s age is ${this.age}`);  
  }
}

const user = new User('Bob', 24);
user.getAge();
```

2. 
```
function User(first, age) {
  this.first = first;
  this.age = age;
}

User.prototype.getAge = function() {
  console.log(`${this.first}'s age is ${this.age}`);  
}

const user2 = new User('jane', 25);
user2.getAge();

```

5. DOM Event Handler

it refers to event.target
```
const button = document.createElement('button');
button.textContent = "Click";
document.body.appendChild(button);

button.addEventListener('click', function() {
  console.log(this);
  console.log(event.target);

})

// button
```




### State 
State is data that has to be managed (we have to keep track) provided by user.
State is important because it tells us about the status.

```
State is an object which stores all user data 
and
State Management is basically what data should be visible to a user when He is using an app
```

### Analogy to understand
One way to do program is that we have an auth function which tells what things to render based on whether the user is present or not.
The other way is that we have an object (commonly refered as state) which store the auth attribute and if user is present, then the state is changed to true and now the rendering is happening based on auth property in state object. 
The second approach is more readable and clear.


## A Simple Graph
1. State – an object that stores all the app data
2. View – a function that returns a string of HTML based on the current state
3. Update – a function that is the only way to change the state and re-render the view

### How reducer helps manage state???
A reducer is simply a function which takes two parameters (state, action) and change the state based on action.