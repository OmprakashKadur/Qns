# 📚 JavaScript Interview Notes

---

## 🎯 Hoisting in JavaScript

### **Q: What is hoisting?**

**A:**  
Hoisting is JavaScript's behavior of moving **declarations** to the top of their scope during the compilation phase. Only the declaration is hoisted — **not the assignment**.

#### **Example:**
```js
console.log(a); // undefined
var a = 5;
```

#### **Follow-up Q:**  
Are `let` and `const` also hoisted?

**A:**  
Yes, but they are not initialized. Accessing them before declaration results in a ReferenceError due to the Temporal Dead Zone.

#### **Example:**
```js
console.log(b); // ReferenceError
let b = 10;
```

---

## 🆚 let vs var vs const

### **Q: What are the differences between variables created using `let`, `var`, or `const`?**

**A:**  
- `var`: Function-scoped, can be redeclared/updated, hoisted (initialized as `undefined`).
- `let`: Block-scoped, can be updated but not redeclared in the same scope, hoisted (not initialized).
- `const`: Block-scoped, cannot be updated or redeclared, must be initialized at declaration.

#### **Example:**
```js
{
  var x = 1;
  let y = 2;
  const z = 3;
}
console.log(x); // 1
console.log(y); // ReferenceError
console.log(z); // ReferenceError
```

#### **Follow-up Q:**  
Can you change the value of a `const` object?

**A:**  
You cannot reassign the variable, but you can mutate the object's properties.

```js
const obj = { a: 1 };
obj.a = 2; // Allowed
obj = {};  // Error
```

---

## 🟰 == vs ===

### **Q: What is the difference between `==` and `===` in JavaScript?**

**A:**  
- `==` checks for value equality with type coercion.
- `===` checks for both value and type equality (strict equality).

#### **Example:**
```js
console.log(2 == '2');  // true
console.log(2 === '2'); // false
```

#### **Follow-up Q:**  
When should you use `==` over `===`?

**A:**  
Prefer `===` to avoid unexpected type coercion.

---

## 🔄 Event Loop

### **Q: What is the event loop in JavaScript runtimes?**

**A:**  
The event loop allows JavaScript to perform non-blocking operations by offloading operations to the browser or Node.js, and executing callbacks from the message queue when the call stack is empty.

#### **Example:**
```js
console.log('A');
setTimeout(() => console.log('B'), 0);
console.log('C');
// Output: A, C, B
```

#### **Follow-up Q:**  
Why does `'B'` print after `'C'`?

**A:**  
Because `setTimeout` is asynchronous; its callback is queued and runs after the synchronous code.

---

## 🏷️ Event Delegation

### **Q: Explain event delegation in JavaScript**

**A:**  
Event delegation is a technique where a single event listener is added to a parent element to manage events for its child elements, using event bubbling.

#### **Example:**
```js
document.getElementById('parent').addEventListener('click', function(e) {
  if (e.target.matches('.child')) {
    console.log('Child clicked:', e.target.textContent);
  }
});
```

#### **Follow-up Q:**  
Why use event delegation?

**A:**  
It improves performance and simplifies code when handling events for many child elements.

---

## 🔄 `this` Keyword

### **Q: How does `this` work in JavaScript?**

**A:**  
`this` refers to the object that is executing the current function. Its value depends on how the function is called.

#### **Example:**
```js
const obj = {
  name: 'Alice',
  greet() {
    console.log(this.name);
  }
};
obj.greet(); // 'Alice'
```

#### **Follow-up Q:**  
What is `this` in an arrow function?

**A:**  
Arrow functions do not have their own `this`; they inherit it from the enclosing scope.

---

## 🍪 Cookie vs sessionStorage vs localStorage

### **Q: Describe the difference between a cookie, `sessionStorage`, and `localStorage` in browsers**

**A:**  
- **Cookie:** Sent to server with every request, size limit ~4KB, can have expiry.
- **sessionStorage:** Stores data for one session, cleared on tab close.
- **localStorage:** Stores data with no expiry, persists across sessions.

#### **Example:**
```js
localStorage.setItem('key', 'value');
sessionStorage.setItem('key', 'value');
document.cookie = "key=value";
```

#### **Follow-up Q:**  
Which storage is accessible from the server?

**A:**  
Only cookies are sent to the server.

---

## 📜 `<script>`, `<script async>`, `<script defer>`

### **Q: Describe the difference between `<script>`, `<script async>`, and `<script defer>`**

**A:**  
- `<script>`: Blocks HTML parsing until script loads and executes.
- `<script async>`: Loads script asynchronously, executes as soon as loaded.
- `<script defer>`: Loads script asynchronously, executes after HTML parsing.

#### **Example:**
```html
<script src="a.js"></script>
<script async src="b.js"></script>
<script defer src="c.js"></script>
```

#### **Follow-up Q:**  
When should you use `defer`?

**A:**  
Use `defer` for scripts that depend on the DOM being fully parsed.

---

## ❓ null vs undefined vs undeclared

### **Q: What's the difference between a JavaScript variable that is: `null`, `undefined`, or undeclared?**

**A:**  
- `null`: Explicitly set to "no value".
- `undefined`: Declared but not assigned a value.
- Undeclared: Variable does not exist in the current scope.

#### **Example:**
```js
let a;
console.log(a); // undefined
let b = null;
console.log(b); // null
console.log(c); // ReferenceError: c is not defined
```

#### **Follow-up Q:**  
What is the type of `null` and `undefined`?

**A:**  
`typeof null` is `"object"` (legacy bug), `typeof undefined` is `"undefined"`.

---

## 📞 .call vs .apply

### **Q: What's the difference between `.call` and `.apply` in JavaScript?**

**A:**  
Both invoke a function with a given `this` value, but:
- `.call` takes arguments separately.
- `.apply` takes arguments as an array.

#### **Example:**
```js
function sum(a, b) { return a + b; }
console.log(sum.call(null, 1, 2));    // 3
console.log(sum.apply(null, [1, 2])); // 3
```

#### **Follow-up Q:**  
When would you use `.apply` over `.call`?

**A:**  
Use `.apply` when you have an array of arguments to pass to the function.

---