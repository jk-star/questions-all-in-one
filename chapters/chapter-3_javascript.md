
# <u>`JavaScript Complete Interview Questions & Answers`</u>
## <u>`1. JavaScript kya hai?`</u>
- JavaScript ek high-level, dynamically typed programming language hai jo web pages ko interactive banane ke liye use hoti hai. Browser ke alawa Node.js jaise runtimes me bhi chalti hai.

## <u>`JavaScript Complete Interview Questions & Answers`</u>

| Feature              | var      | let   | const |
| -------------------- | -------- | ----- | ----- |
| Scope                | Function | Block | Block |
| Reassign             | ✅        | ✅     | ❌     |
| Redeclare same scope | ✅        | ❌     | ❌     |
| Hoisted              | ✅        | ✅     | ✅     |
| TDZ                  | ❌        | ✅     | ✅     |

<code><pre>
let age = 25;
age = 26; // allowed

const name = "Amit";
// name = "Rahul"; ❌
</pre></code>

- Modern JavaScript me generally **`const`** first choice aur reassignment ho to **`let`**.


## <u>`Part 1 — Data Types`</u>

**3. JavaScript ke data types?**

**`Primitive`**

1. String
1. Number
1. Boolean
1. Undefined
1. Null
1. BigInt
1. Symbol

**`Non-Primitive`**

1. Object
1. Array
1. Function

**4. Primitive vs Non-Primitive?**
- Primitive values immutable values hote hain.
<code><pre>
let name = "Amit";
let age = 25;
</pre></code>

- Objects reference values hote hain.

<code><pre>
const user = {
  name: "Amit"
};
</pre></code>

**5. `typeof` kya karta hai?**

- Value ka type check karta hai.

<code><pre>
typeof "Hello";     // "string"
typeof 10;          // "number"
typeof true;        // "boolean"
typeof undefined;   // "undefined"
</pre></code>

- Famous tricky question: **`typeof null;`**
- Output: **`object`** Ye JavaScript ka historical behavior hai.

## <u>`Part 2 — Operators`</u>
**6. == aur === me difference? 🔥🔥**

- **`==`** type coercion kar sakta hai. **`5 == "5"; // true`**
- **`===`** type + value dono compare karta hai without coercing operands to the same type. **`5 === "5"; // false`**

**7. != vs !==?**
<code><pre>
5 != "5";  // false
5 !== "5"; // true
</pre></code>

- **`!==`** strict inequality hai.


## <u>`Part 3 — Conditions`</u>
**8. Ternary operator kya hai?**
- Short conditional expression:
<code><pre>
const result = age >= 18
  ? "Adult"
  : "Minor";
</pre></code>

**9. Logical AND &&?**
- Dono operands ko left-to-right evaluate karta hai aur short-circuit karta hai.

<code><pre>
true && true; // true
true && false; // false
</pre></code>

**10. Logical OR ||?**
- First truthy value return kar sakta hai:
- **`const name = username || "Guest";`**

11. Nullish coalescing ?? kya hai? 🔥
- Sirf **`null`** ya **`undefined`** hone par fallback deta hai.
<code><pre>
const count = 0;
console.log(count || 10); // 10
console.log(count ?? 10); // 0
</pre></code>

## <u>`Part 4 — Functions`</u> 🔥🔥
**12. Function Declaration?**
<code><pre>
function add(a, b) {
  return a + b;
}
</pre></code>

**13. Function Expression?**
<code><pre>
const add = function(a, b) {
  return a + b;
};
</pre></code>

**14. Arrow Function? 🔥**
<code><pre>
const add = (a, b) => {
  return a + b;
};
</pre></code>

- **Short: `const add = (a, b) => a + b;`**

**15. Normal function vs Arrow function?**
- Important difference: arrow function ka apna **`this`** nahi hota; wo surrounding lexical **`this`** use karti hai.
- Normal function ka **`this`** call-site ke according determine ho sakta hai.
- Arrow functions constructors ke roop me bhi use nahi hoti.

**16. Default parameters?**

<code><pre>

function greet(name = "Guest") {
  return `Hello ${name}`;
}
</pre></code>

**17. Rest parameter? 🔥**
- Multiple arguments ko array me collect karta hai.
<code><pre>
function sum(...numbers) {
  return numbers.reduce(
    (total, num) => total + num,
    0
  );
}
</pre></code>

## <u>`Part 5 — Scope`</u> 🔥🔥

**18. Scope kya hai?**
- Variable kaha accessible hai, ye scope determine karta hai.
**`Important:`**
<code><pre>
Global Scope
Function Scope
Block Scope
</pre></code>

**19. Block Scope?**
<code><pre>
{
  let age = 25;
  const name = "Amit";
}

console.log(age); // Error
</pre></code>

- **`let`** aur **`const`** block scoped hain.

**20. Function Scope?**
<code><pre>
function test() {
  var name = "Amit";
}

console.log(name); // Error
</pre></code>

## <u>`Part 6 — Hoisting`</u> 🔥🔥🔥
**21. Hoisting kya hai?**
- JavaScript execution se pehle declarations ko process karta hai.

**`Example:`**
<code><pre>
console.log(a);
var a = 10;
</pre></code>

**`Output: undefined`**

**`Conceptually:`**
<code><pre>
var a;
console.log(a);
a = 10;
</pre></code>

**22. let ko declaration se pehle access karein?**
<code><pre>
console.log(a);
let a = 10;
</pre></code>

**`Output: ReferenceError`**

**23. Temporal Dead Zone kya hai?**
- Block start hone se let/const declaration execute hone tak ka period jahan variable ko access nahi kar sakte.
<code><pre>
console.log(name); // ReferenceError
let name = "Amit";
</pre></code>

## <u>`Part 7 — Arrays`</u> 🔥🔥🔥
**24. map() kya karta hai?**
- Har item ko transform karke new array return karta hai.
<code><pre>
const numbers = [1, 2, 3];
const result = numbers.map(
  num => num * 2
);
</pre></code>

**`Result: [2, 4, 6]`**

**25. filter()?**
- Condition match karne wale elements ka new array.
<code><pre>
const numbers = [1, 2, 3, 4];
const result = numbers.filter(
  num => num > 2
);
</pre></code>

**`Result: [3, 4]`**

**26. find()?**
- First matching element return karta hai.
<code><pre>
const users = [
  { id: 1, name: "Amit" },
  { id: 2, name: "Rahul" }
];

const user = users.find(
  user => user.id === 2
);
</pre></code>

**27. findIndex()?**
- First matching element ka index return karta hai.
<code><pre>
const index = users.findIndex(
  user => user.id === 2
);
</pre></code>

**28. forEach()?**
- Har element par callback execute karta hai.

<code><pre>
users.forEach(user => {
  console.log(user.name);
});
</pre></code>

**29. map() vs forEach()? 🔥**

- **`map()`** → new array return karta hai.
- **`forEach()`** → return value transformation ke liye useful nahi; method itself **`undefined`** return karta hai.

**30. reduce()? 🔥**
- Array ko single accumulated result me reduce karta hai.
<code><pre>
const numbers = [10, 20, 30];
const total = numbers.reduce(
  (sum, number) => sum + number,
  0
);
</pre></code>

**`Result: 60`**

**31. some()?**
- Kya kam se kam ek element condition satisfy karta hai?
<code><pre>
const result = [1, 2, 3].some(
  num => num > 2
);
</pre></code>

**`true`**

**32. every()?**
- Kya sabhi elements condition satisfy karte hain?

<code><pre>
[2, 4, 6].every(
  num => num % 2 === 0
);
</pre></code>

**`true`**

**33. includes()?**
- Value exist karti hai ya nahi.
<code><pre>
[1, 2, 3].includes(2);
</pre></code>

**`true`**
**34. push() vs pop()?**
<code><pre>
arr.push(10);
</pre></code>

- End me add.
<code><pre>
arr.pop();
</pre></code>

- End se remove.
- Dono original array ko mutate karte hain.

**35. shift() vs unshift()?**
<code><pre>
arr.shift();
</pre></code>

- Beginning se remove.
<code><pre>
arr.unshift(10);
</pre></code>

- Beginning me add.

**36. slice() vs splice()?** 🔥🔥

- **`slice()`** original array ko mutate nahi karta.

<code><pre>
const result = arr.slice(1, 3);
</pre></code>

- **`splice()`** original array ko modify karta hai.

<code><pre>
arr.splice(1, 2);
</pre></code>

## <u>`Part 8 — Objects`</u> 🔥🔥
**37. Object kya hai?**
- Key-value pairs ka collection.
<code><pre>
const user = {
  name: "Amit",
  age: 25
};
</pre></code>

**38. Object property access?**
- **`user.name`** Ya **`user["name"]`**

39. **Destructuring?** 🔥🔥
<code><pre>
const user = {
  name: "Amit",
  age: 25
};

const { name, age } = user;
</pre></code>

**`Array:`**
<code><pre>
const numbers = [10, 20];
const [first, second] = numbers;
</pre></code>

## <u>`Part 9 —  Spread & Rest`</u> 🔥🔥🔥
**40. Spread operator?**
- Array/object ko expand/copy/merge karne me useful.

<code><pre>
const arr1 = [1, 2];
const arr2 = [
  ...arr1,
  3
];
</pre></code>

**`Result: [1, 2, 3]`**

**`Object:`**

<code><pre>
const updatedUser = {
  ...user,
  name: "Rahul"
};
</pre></code>

**41. Spread vs Rest?**

- **`Syntax same: ...`**

**`Spread`** → values ko expand karta hai.
**`Rest`** → multiple values ko collect karta hai.

<code><pre>
function test(...args) {
}
</pre></code>

## <u>`Part 9 — Strings`</u>
**42. Template literals?** 🔥
<code><pre>
const name = "Amit";

const message = `Hello ${name}`;
</pre></code>

**43. Useful string methods?**
<code><pre>
toUpperCase()
toLowerCase()
includes()
startsWith()
endsWith()
trim()
replace()
slice()
split()
</pre></code>

## <u>`Part 10 — Truthy / Falsy`</u> 🔥🔥
**44. Falsy values kaunse hain?**

- Common falsy values:
<code><pre>
false
0
-0
0n
""
null
undefined
NaN
</pre></code>

**45. Truthy values?**

- Falsy values ko chhodkar almost everything truthy hota hai.

**`Tricky:`**

<code><pre>
Boolean([]); // true
Boolean({}); // true
</pre></code>

## <u>`Part 11 — null vs undefined`</u>
**46. Difference?** 🔥

- **`undefined`** → value assign nahi hui / missing.
<code><pre>
let name;
</pre></code>

- **`null`** → intentionally empty value.
<code><pre>
let user = null;
</pre></code>

## <u>`Part 12 — Optional Chaining`</u>
**47. ?. kya hai?** 🔥
- Nested property safely access karne ke liye.
<code><pre>
const city = user?.address?.city;
</pre></code>

- Agar intermediate value nullish hai to error ki jagah **`undefined`**.

## <u>`Part 13 — Callbacks`</u> 🔥🔥
**48. Callback function kya hai?**
- Ek function jo dusre function ko argument ke roop me diya jata hai.
<code><pre>
function greet(name, callback) {
  console.log(`Hello ${name}`);

  callback();
}

greet("Amit", () => {
  console.log("Done");
});
</pre></code>

## <u>`Part 14 — Higher-Order Functions`</u>

**49. Higher-order function kya hai?**

Jo function:
- function ko argument le, ya
- function return kare.

**`Examples:`**
<code><pre>
map()
filter()
reduce()
</pre></code>

## <u>`Part 15 — Closure`</u> 🔥🔥🔥
**50. Closure kya hai?**
- Inner function apne outer lexical scope ke variables ko outer function execute hone ke baad bhi access kar sakta hai.
<code><pre>
function counter() {
  let count = 0;

  return function() {
    count++;
    return count;
  };
}

const increment = counter();

console.log(increment()); // 1
console.log(increment()); // 2
</pre></code>

- Ye very common interview question hai.

## Part 16 — this Keyword 🔥🔥🔥
**51. `this` kya hai?**

- **`this`** ka value function ko kaise call kiya gaya hai us par depend karta hai (arrow functions lexical this use karti hain).
<code><pre>
const user = {
  name: "Amit",

  showName() {
    console.log(this.name);
  }
};

user.showName();
</pre></code>

**`Output: Amit`**

## Part 17 — call, apply, bind 🔥🔥
**52. `call()` kya hai?**
- Function ko immediately call karke **`this`** specify karta hai.
<code><pre>
greet.call(user, "Hello");
</pre></code>

**52. `apply()` kya hai?**
- **`call()`** jaisa, lekin arguments array/array-like form me.
<code><pre>
greet.apply(user, ["Hello"]);
</pre></code>

**54. bind()?**
- Naya function return karta hai jiska this bound hota hai.
<code><pre>
const newFunction = greet.bind(user);
newFunction();
</pre></code>

**`Remember:`**
<code><pre>
call  → execute now, args separately
apply → execute now, args array
bind  → new bound function
</pre></code>

## Part 18 — Async JavaScript 🔥🔥🔥
**55. Synchronous vs Asynchronous?**

**`Synchronous:`**

<code><pre>
Task 1
↓
Task 2
↓
Task 3
</pre></code>

- Asynchronous operations waiting ke dauran program dusra work continue kar sakta hai.
**Examples:**
<code><pre>
API requests
Timers
File/network operations
</pre></code>

## Part 19 — Promise 🔥🔥🔥
**56. Promise kya hai?**
- Asynchronous operation ke eventual completion/failure ko represent karta hai.

**`States:`**
<code><pre>
Pending
Fulfilled
Rejected
</pre></code>

**57. Promise example?**
<code><pre>
const promise = new Promise(
  (resolve, reject) => {
    const success = true;

    if (success) {
      resolve("Success");
    } else {
      reject("Error");
    }
  }
);
</pre></code>

**58. Promise handle?**
<code><pre>
promise
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.log(error);
  })
  .finally(() => {
    console.log("Finished");
  });
</pre></code>

## Part 20 — Async/Await 🔥🔥🔥
**59. async/await kya hai?**
- Promises ko readable async syntax me handle karta hai.
<code><pre>
async function getUsers() {
  const response = await fetch(url);

  const data = await response.json();

  return data;
}
</pre></code>

**60. Async/Await error handling?**
<code><pre>
async function getUsers() {
  try {
    const response = await fetch(url);
    const data = await response.json();

    return data;
  } catch (error) {
    console.error(error);
  }
}
</pre></code>

## Part 21 — Event Loop 🔥🔥🔥
**61. Event Loop kya hai?**

- JavaScript execution model me event loop tasks ko coordinate karta hai, including call stack aur queued asynchronous callbacks.

**`Simplified:`**
<code><pre>
Call Stack
    ↕
Event Loop
    ↓
Task / Microtask Queues
</pre></code>

**62. Output kya hoga?** 🔥🔥

<code><pre>
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

console.log("C");
</pre></code>

**`Output:`**
<code><pre>
A
B
C
</pre></code>

**63. Promise vs setTimeout output?** 🔥🔥🔥

<code><pre>
console.log("A");

setTimeout(() => {
  console.log("B");
}, 0);

Promise.resolve().then(() => {
  console.log("C");
});

console.log("D");
</pre></code>

**`Output:`**
<code><pre>
A
D
C
B
</pre></code>

- Promise callback microtask queue me hota hai, jo timer task se pehle process hota hai.


## Part 22 — DOM 🔥🔥
**64. DOM kya hai?**

**`Document Object Model`**
- Browser HTML document ko objects/tree ke form me represent karta hai.

**65. Element select kaise?**
<code><pre>
document.getElementById("title");
document.querySelector(".box");
document.querySelectorAll(".box");
</pre></code>

**66. Content change?**
<code><pre>
element.textContent = "Hello";
</pre></code>

**`HTML:`**
<code><pre>
element.textContent = "Hello";
</pre></code>

- Untrusted input ke saath **`innerHTML`** security risk create kar sakta hai.

**67. CSS class add/remove?**
<code><pre>
element.classList.add("active");

element.classList.remove("active");

element.classList.toggle("active");
</pre></code>

## Part 23 — Events 🔥🔥
**68. Event listener?**
<code><pre>
button.addEventListener(
  "click",
  function() {
    console.log("Clicked");
  }
);
</pre></code>

**69. Event bubbling kya hai?**
- Event target se ancestors ki taraf bubble karta hai.
<code><pre>
button
 ↓
div
 ↓
body
 ↓
document
</pre></code>

**70. Event capturing?**
- Event ancestor se target ki taraf capture phase me travel karta hai.
<code><pre>
document
 ↓
body
 ↓
div
 ↓
button
</pre></code>

**71. Event delegation?** 🔥🔥🔥
- Parent par listener lagakar child events handle karna.
<code><pre>
document
  .querySelector("#list")
  .addEventListener("click", e => {

    if (e.target.matches(".delete")) {
      console.log("Delete");
    }

  });
</pre></code>

- Dynamic lists me useful.

## Part 24 — Storage 🔥🔥
**72. localStorage kya hai?**
- Browser me persistent key/value storage.
<code><pre>
localStorage.setItem(
  "name",
  "Amit"
);

localStorage.getItem("name");
</pre></code>

**73. Object localStorage me kaise store karein?**
<code><pre>
const user = {
  name: "Amit"
};

localStorage.setItem(
  "user",
  JSON.stringify(user)
);
</pre></code>

**`Retrieve:`**
<code><pre>
const user = JSON.parse(
  localStorage.getItem("user")
);
</pre></code>

**74. localStorage vs sessionStorage?**

- **`localStorage`** → browser sessions ke across persist karta hai until removed.
- **`sessionStorage`** → current tab/page session tak.

## Part 25 — JSON
**75. JSON kya hai?**
- JavaScript Object Notation
- Data exchange format.
- Convert object → JSON string:
<code><pre>
JSON.stringify(user);
</pre></code>

- JSON → JS value:
<code><pre>
JSON.parse(data);
</pre></code>

## Part 26 — Shallow vs Deep Copy 🔥🔥
**76. Shallow copy?**
<code><pre>
const copy = {
  ...user
};
</pre></code>

- Spread nested objects ko recursively clone nahi karta.

**77. Deep copy?**
- Supported values ke liye modern approach:
<code><pre>
const copy = structuredClone(user);
</pre></code>

- **`JSON.parse(JSON.stringify(...))`** limited workaround hai aur har JS value/type ko preserve nahi karta.

## Part 27 — ES Modules
**78. Export?**
<code><pre>
export const name = "Amit";
</pre></code>

**`Default:`**
<code><pre>
export default User;
</pre></code>

**79. Import?**
<code><pre>
import User from "./User.js";
</pre></code>

**`Named:`**
<code><pre>
import { name } from "./data.js";
</pre></code>

- React me extremely important.

## Part 28 — Error Handling
**80. try/catch?**
<code><pre>
try {
  riskyOperation();
} catch (error) {
  console.error(error);
} finally {
  console.log("Done");
}
</pre></code>
