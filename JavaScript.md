## 🎯 Hoisting in JavaScript

**Q:** What is hoisting?

**A:**  
Hoisting is JavaScript's behavior of moving declarations to the top of their scope.  
Only the declaration is hoisted — not the assignment.

```js
console.log(a); // undefined
var a = 5;
