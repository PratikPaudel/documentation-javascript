## this keyword:
It is a special variable that is created for every execution context (every function). Takes the value of or points to the "owner" of the function in which the this keyword is used. 'this' is not static. It depends on how the function is called, and its value is only assigned when the function is actually called. In JavaScript, the this keyword is dynamic and its value is determined by how a function is called. When you invoke cat.calculateAge(), this refers to the cat object. The calculateAge method is shared between the objects dog and cat, but the context (this) changes based on which object calls the method. 

```javascript linenums=1
const dog = {
    birthYear: 2015,
    
    calculateAge: function () {
        console.log(2037 - this.birthYear);
        console.log(this);
        console.log("Woof!");
    }
};

const cat = {
    birthYear: 2018
};

cat.calculateAge = dog.calculateAge;

cat.calculateAge(); // When cat.calculateAge() is called, this inside the calculateAge method refers to cat because calculateAge was called as a method of the cat object.
dog.calculateAge();
```
In this example, when cat.calculateAge() is called, the this keyword inside the calculateAge method refers to cat because calculateAge was called as a method of the cat object. Similarly, when dog.calculateAge() is called, this refers to the dog object. This demonstrates how the context (this) is dynamic and depends on the calling object.

### 'this' keyword in different contexts
- Method call: When a method is called on an object, this refers to the object that called the method.
- Simple Function Call: In a regular function call, this refers to the global object (window in browsers, global in Node.js). In strict mode, this is undefined.
```javascript linenums=1
function showThis() {
    console.log(this); // `this` refers to the global object or `undefined` in strict mode
}

showThis(); // Output: global object (or `undefined` in strict mode)
```
- Arrow Functions: Arrow functions do not have their own this. Instead, this is lexically inherited from the surrounding function at the time the arrow function is created.
```javascript "linenums=1"
const rabbit = {
    birthYear: 2020,
    calculateAge: function() {
        const showThis = () => {
            console.log(this); // `this` refers to the rabbit object
        };
        showThis();
    }
};

rabbit.calculateAge(); // Output: { birthYear: 2020, ... }
```
- Event Listener: In an event listener, this refers to the element that received the event.
```javascript "linenums=1"
document.getElementById('myButton').addEventListener('click', function() {
    console.log(this); // `this` refers to the button element
    this.style.backgroundColor = 'blue';
});
```
 
