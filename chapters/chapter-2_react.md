# <u>`React Complete Interview Questions & Answers`</u>

## Part 1 — React Basics

**1. React kya hai?**
- React ek JavaScript library hai jo reusable components ki help se user interfaces banane ke liye use hoti hai.

**Main points:**
- Component-based
- Declarative
- Reusable UI
- Virtual DOM
- One-way data flow

**2. React library hai ya framework?**
- React library hai, full framework nahi.
- React mainly UI layer handle karta hai. Routing ke liye React Router jaise additional packages use kiye ja sakte hain.


**3. SPA kya hai?**
- **SPA = Single Page Application**
- Page ko har navigation par completely reload karne ke bajay required UI dynamically update hoti hai.

**Examples:**

<code><pre>
/dashboard
/users
/profile
</pre></code>

**4. Component kya hai?** 
- Component reusable UI ka piece hota hai.

<code><pre>
function Welcome() {
  return &lt;h1&gt;Hello&lt;/h1&gt;;
}
</pre></code>

**Use:** `<Welcome />`

**5. Functional Component kya hai?**
- JavaScript function jo JSX return karta hai.
<code><pre>
function Header() {
  return &lt;h1&gt;My Website&lt;/h1&gt;;
}
</pre></code>

- Modern React me functional components standard approach hain.

**6. Class Component kya hai?**

- Older React style:

<code><pre>
class Welcome extends React.Component {
  render() {
    return &lt;h1&gt;Hello&lt;/h1&gt;;
  }
}
</pre></code>

- Aaj functional components + Hooks generally preferred hain.

## Part 2 — JSX

**7. JSX kya hai?**
- JSX = JavaScript Syntax Extension
- JavaScript ke andar HTML-like syntax likhne deta hai.
- `const heading = <h1>Hello React</h1>;`

**8. JSX me JavaScript kaise likhte hain?**
- Curly braces `{}` ke andar.

<code><pre>
const name = "Jyoti";
return &lt;h1&gt;Hello {name}&lt;/h1&gt;;
</pre></code>

**9. JSX me `class` ki jagah `className` kyun?**
- `<div className="container">`
- JSX DOM properties ke naming conventions follow karta hai; CSS class ke liye property className hai.    

**10. Inline CSS kaise?**

<code><pre>
&lt;h1 style={{ color: "red" }}&gt;
  Hello
&lt;/h1&gt;
</pre></code>

- Outer `{}` → JavaScript expression.
- Inner `{}` → style object.

**11. React Fragment kya hai?**

- Extra DOM element ke bina multiple elements group karta hai.
<code><pre>
&lt;&gt;
  &lt;h1&gt;Hello&lt;/h1&gt;
  &lt;p&gt;Welcome&lt;/p&gt;
&lt;/&gt;
</pre></code>

## <u>`Part 3 — Props`</u> 🔥🔥

Parent component se child component ko data pass karne ke liye.

Parent: Parent component se child component ko data pass karne ke liye.

**Parent: `<User name="Jonh" />`**

**Child:**

<code><pre>
function User(props) {
  return &lt;h1&gt;{props.name}&lt;/h1&gt;;
}
</pre></code>

**13. Props destructuring?**

<code><pre>
function User({ name, age }) {
  return (
    &lt;p&gt;
      {name} - {age}
    &lt;/p&gt;
  );
}
</pre></code>

**14. Kya child props modify kar sakta hai?**
- Nahi. Props read-only hote hain.
- React ka data flow generally:

<code><pre>
Parent
  ↓
Child
</pre></code>

- Isliye React me one-way data flow kaha jata hai.

## <u>`Part 4 — State`</u> 🔥🔥🔥

**15. State kya hai?**
- Component ke andar change hone wala data.
- **`const [count, setCount] = useState(0);`**

- **`count`** → current state

- **`setCount`** → state update function

- **`0`** → initial value

**16. `useState` kya hai?**

- React Hook jo functional component me state add karta hai.

<code><pre>
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      {count}
    </button>
  );
}
</pre></code>

import { useState } from "react";

**17. State directly modify kyun nahi karte?**

**❌ Wrong: `count = count + 1;`**

**✅ Correct:: `setCount(count + 1);`**

- React ko state setter ke through update batana hota hai taaki rendering properly schedule ho.

**18. Previous state ke basis par update?**

Best:

- **`setCount(prev => prev + 1);`**

**19. Props vs State?** 🔥

| Props                  | State                      |
| ---------------------- | -------------------------- |
| Parent se milti hain   | Component manage karta hai |
| Read-only              | Update ho sakti hai        |
| Data passing           | Dynamic data               |
| Child shouldn't modify | Setter se update           |

## <u>`Part 5 — Events`</u>

**20. Click event kaise handle karenge?**

<code><pre>
function handleClick() {
  console.log("Clicked");
}

return (
  &lt;button onClick={handleClick}&gt;
    Click
  &lt;/button&gt;
);
</pre></code>

**21. Function me argument pass karna ho?**

<code><pre>
&lt;button onClick={() => deleteUser(10)}&gt;
  Delete
&lt;/button&gt;
</pre></code>

**22. Ye galat kyun hai?**

`<button onClick={deleteUser(10)}>`

- Kyuki function render ke time execute ho jayega.

- Use: `onClick={() => deleteUser(10)}`

## <u>`Part 6 — Conditional Rendering`</u>

**23. Conditional rendering kya hai?**

- Condition ke basis par different UI show karna.
<code><pre>
if (isLoggedIn) {
  return &lt;Dashboard /&gt;;
}

return &lt;Login /&gt;;
</pre></code>

**24. Ternary operator?**

`{isLoggedIn ? <Dashboard /> : <Login />}`

**25. Sirf true condition par element show?**

`&&`

- `{isAdmin && <AdminPanel />}`

**26. `&&` vs `ternary` ?**

- Sirf true par UI: **`{isLoggedIn && <Logout />}`**

- True/false dono cases: `**{isLoggedIn ? <Logout /> : <Login />}**`

## <u>`Part 7 — List Rendering`</u> 🔥🔥
**27. Array ko UI me kaise display karte hain?**

`map()`

<code><pre>
const users = ["Amit", "John", "Neha"];

return (
  &lt;&gt;
    {users.map(user => (
      &lt;p&gt;{user}&lt;/p&gt;
    ))}
  &lt;/&gt;
);
</pre></code>

**28. key prop kya hai?** 🔥
- React ko list items uniquely identify karne me help karta hai.
<code><pre>
{users.map(user => (
  &lt;p key={user.id}&gt;
    {user.name}
  &lt;/p&gt;
))}
</pre></code>

**29. Array index ko key banana sahi hai?**

`key={index}`

- Static list me kabhi acceptable ho sakta hai, lekin insert/delete/reordering wali lists me stable unique ID preferred hai.

`key={user.id}`

## <u>`Part 8 — Forms`</u> 🔥🔥🔥

**30. Controlled Component kya hai?**

- Form input jiska value React state control karti hai.
const [name, setName] = useState("");

<code><pre>
&lt;input value={name} onChange={e => setName(e.target.value)} /&gt;
</pre></code>

**31. Form submit?**

<code><pre>
function handleSubmit(e) {
  e.preventDefault();

  console.log(name);
}

&lt;form onSubmit={handleSubmit}&gt;
</pre></code>

**32. preventDefault() kyun?**

- Browser ka default form submission/page reload prevent karne ke liye.

**33. Multiple inputs kaise manage karenge?**

<code><pre>
const [form, setForm] = useState({
  name: "",
  email: ""
});

function handleChange(e) {
  const { name, value } = e.target;

  setForm(prev => ({
    ...prev,
    [name]: value
  }));
}
</pre></code>

**Inputs:**

<code><pre>
&lt;input
  name="name"
  value={form.name}
  onChange={handleChange}
/&gt;

&lt;input
  name="email"
  value={form.email}
  onChange={handleChange}
/&gt;
</pre></code>

## <u>`Part 9 — useEffect`</u> 🔥🔥🔥
**34. useEffect kya hai?**
- Component ko external systems ke saath synchronize karne ke liye Hook hai, jaise API/network request, subscription, timer, browser APIs etc.
<code><pre>
useEffect(() => {
  console.log("Effect");
}, []);
</pre></code>

**35. Empty dependency array `[]`?**
<code><pre>
useEffect(() => {

}, []);
</pre></code>

- Effect initial mount ke baad run hota hai. Development me Strict Mode ki wajah se extra setup/cleanup cycle dikh sakta hai.

**36. Dependency array nahi ho?**

<code><pre>
useEffect(() => {

});
</pre></code>

- Effect har render ke baad run karega.

**37. Dependency ho?**
<code><pre>
useEffect(() => {

}, [count]);
</pre></code>

- Initial run aur count change hone par effect re-run hoga.

**38. Cleanup function kya hai?**
<code><pre>
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Hello");
  }, 1000);

  return () => {
    clearInterval(timer);
  };
}, []);
</pre></code>

- Subscriptions, timers, event listeners etc. cleanup karne ke liye.

## <u>`Part 10 — API Calling`</u> 🔥🔥🔥
**39. Fetch se API call?**
<code><pre>
useEffect(() => {
  fetch("https://example.com/users")
    .then(res => res.json())
    .then(data => setUsers(data))
    .catch(error => console.error(error));
}, []);
</pre></code>

**40. Async/Await se?**
<code><pre>
useEffect(() => {
  async function fetchUsers() {
    try {
      const response = await fetch(
        "https://example.com/users"
      );

      const data = await response.json();

      setUsers(data);
    } catch (error) {
      console.error(error);
    }
  }

  fetchUsers();
}, []);
</pre></code>

**41. Loading state?**

<code><pre>
const [loading, setLoading] = useState(true);
</pre></code>

**Example:**

<code><pre>
if (loading) {
  return &lt;p&gt;Loading...&lt;/p&gt;;
}
</pre></code>

**42. Error handling?**
<code><pre>
const [error, setError] = useState(null);

try {
  // request
} catch (err) {
  setError(err.message);
}
</pre></code>

## <u>`Part 11 — Hooks`</u> 🔥🔥
**43. Hooks kya hain?**

- Hooks functions hain jo functional components ko React features use karne dete hain.

**Important:**

<code><pre>
useState
useEffect
useContext
useRef
useReducer
useMemo
useCallback
</pre></code>

**44. Hooks ke important rules?**

**Hooks:**

- Top level par call karein.
- Loops/conditions ke andar directly call na karein.
- React components ya custom Hooks me call karein.

## <u>`Part 12 — useRef`</u> 🔥
**45. useRef kya hai?**
- Value/reference ko renders ke beech retain karta hai aur .current change karne se re-render trigger nahi hota.

- Common use: DOM reference.

<code><pre>
const inputRef = useRef(null);

&lt;input ref={inputRef} /&gt;

&lt;button
  onClick={() => inputRef.current.focus()}
&gt;
  Focus
&lt;/button&gt;
</pre></code>

**46. useState vs useRef?**

- **`useState`** update → re-render.
- **`useRef.current`** update → normally re-render nahi.

## <u>`Part 13 — Context API`</u> 🔥🔥🔥
**47. Context API kya hai?**

- Deep component tree me repeatedly props pass kiye bina shared data available karne ka mechanism.
- Useful for:
<code><pre>
Theme
Authentication
Language
Shared app settings/state
</pre></code>

**48. Context create?**
<code><pre>
import { createContext } from "react";

export const UserContext = createContext(null);
</pre></code>

**49. Provider?**
- Modern React me context object ko provider ki tarah use kiya ja sakta hai:

<code><pre>
&lt;UserContext value={user}&gt;
  &lt;App /&gt;
&lt;/UserContext&gt;
</pre></code>

Legacy/common syntax me:

<code><pre>
&lt;UserContext.Provider value={user}&gt;
  &lt;App /&gt;
&lt;/UserContext.Provider&gt;
</pre></code>

**50. Context consume?**
- **`const user = useContext(UserContext);`**

**51. Prop drilling kya hai?**
- Jab data ko intermediate components ke through sirf neeche kisi deeply nested component tak pahunchane ke liye repeatedly props pass karte hain.
<code><pre>
App
 ↓
Layout
 ↓
Header
 ↓
Profile
</pre></code>

- Context kuch situations me ise avoid kar sakta hai.

## <u>`Part 14 — React Router`</u> 🔥🔥🔥
**52. React Router kya hai?**
- React applications me client-side routing ke liye popular library.

**Example routes:**
<code><pre>
/
/users
/login
/profile
</pre></code>

**53. Basic routing?**
<code><pre>
&lt;Routes&gt;
  &lt;Route path="/" element={&lt;Home /&gt;} /&gt;
  &lt;Route path="/users" element={&lt;Users /&gt;} /&gt;
&lt;/Routes&gt;
</pre></code>

**54. `Link` kyun use karte hain?**
<code><pre>
&lt;Link to="/users"&gt;
  Users
&lt;/Link&gt;
</pre></code>

- Client-side navigation ke liye.

**55. `useNavigate()` ?**

- Programmatically navigate karne ke liye.
<code><pre>
const navigate = useNavigate();

navigate("/dashboard");
</pre></code>

**56. URL parameter?**

**Route :**
<code><pre>
&lt;Route
  path="/user/:id"
  element={&lt;User /&gt;}
/&gt;
</pre></code>

**Read : `const { id } = useParams();`**

## <u>`Part 15 — Custom Hooks`</u> 🔥🔥
**57. Custom Hook kya hai?**

- Reusable stateful logic ko extract karne ka function.

**Convention: `useSomething`**

**Example:**
<code><pre>
function useCounter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(c => c + 1);
  };

  return { count, increment };
}
</pre></code>

**58. Custom Hook ka naam use se kyun?**
- React tooling/linting Hooks rules ko identify/apply kar sake aur convention clear rahe.

## <u>`Part 16 — Performance Questions`</u>
**59. React.memo() kya hai?**
- Component ko unnecessary re-renders se bachane me help karta hai when props are unchanged.
<code><pre>
const User = React.memo(function User({ name }) {
  return &lt;h1&gt;{name}&lt;/h1&gt;;
});
</pre></code>

- Memoization har jagah automatically beneficial nahi hoti.

**60. `useMemo()` kya hai?**

- Calculated value ko cache/memoize kar sakta hai.
<code><pre>
const total = useMemo(() => {
  return calculateTotal(items);
}, [items]);
</pre></code>

**61. `useCallback()` kya hai?**

- Function definition ko memoize karta hai.

<code><pre>
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
</pre></code>

**62. `useMemo` vs `useCallback`?**

<code><pre>
useMemo     → calculated value cache
useCallback → function cache
</pre></code>

## <u>`Part 17 — State Immutability`</u> 🔥🔥
**63. Object state update?**

**❌ Avoid:**

- **`user.name = "John";`**

**Better:**
<code><pre>
setUser(prev => ({
  ...prev,
  name: "John"
}));
</pre></code>

**64. Array me item add?**
<code><pre>
setUsers(prev => [
  ...prev,
  newUser
]);
</pre></code>

**65. Array se delete?**
<code><pre>
setUsers(prev =>
  prev.filter(user => user.id !== id)
);
</pre></code>

**66. Array item update?**
<code><pre>
setUsers(prev =>
  prev.map(user =>
    user.id === id
      ? { ...user, name: "Amit" }
      : user
  )
);
</pre></code>

## <u>`Part 18 — Important Conceptual Questions`</u>

**67. Virtual DOM kya hai?**

- React UI ka lightweight in-memory representation maintain karta hai. State/props changes ke baad React naya UI tree calculate karta hai aur required DOM updates efficiently commit karta hai.

**68. Reconciliation kya hai?**

- React old aur new rendered trees compare karke determine karta hai ki UI me kya update karna hai.

**69. One-way data binding/data flow kya hai?**

- Data normally parent se child ki taraf props ke through flow karta hai.

<code><pre>
Parent
 ↓
Child
</pre></code>

**70. Lifting State Up kya hai?**

- Do sibling components ko same data chahiye to shared state unke closest common parent me move kar dete hain.

<code><pre>
      Parent
      state
      /   \
Child A   Child B
</pre></code>

**71. `children` prop kya hai?**

- Component tags ke beech ka content.
<code><pre>
&lt;Card&gt;
  &lt;h1&gt;Hello&lt;/h1&gt;
&lt;/Card&gt;

function Card({ children }) {
  return &lt;div&gt;{children}&lt;/div&gt;;
}
</pre></code>

**72. StrictMode kya hai?**

- Development tool hai jo potential issues aur unsafe patterns identify karne me help karta hai.

<code><pre>
&lt;StrictMode&gt;
  &lt;App /&gt;
&lt;/StrictMode&gt;
</pre></code>

- Production behavior ko duplicate nahi karta.

## <u>`Part 19 — JavaScript Questions React Interview Me`</u> 🔥🔥🔥

- React interview me JavaScript bhi strong hona chahiye.

**73. `map()` ?**

- Array transform karta hai aur new array return karta hai.

<code><pre>
const numbers = [1, 2, 3];

const result = numbers.map(n => n * 2);
</pre></code>

**Result: `[2, 4, 6]`** 

**74. `filter()`?**

- Condition match karne wale elements ka new array.
- **`users.filter(user => user.active);`**

**75. `find()` ?**

- First matching element return karta hai.
- **`users.find(user => user.id === 10);`**

**76. Spread operator?**

<code><pre>
const newUser = {
  ...user,
  name: "John"
};
</pre></code>

**77. Destructuring?**
<code><pre>
const { name, email } = user;
const [first, second] = items;
</pre></code>

**78. Template literal?**
<code><pre>
const message = `Hello ${name}`;
</pre></code>

**79. Arrow function?**
<code><pre>
const add = (a, b) => a + b;
</pre></code>

**80. let, const, var?**

- Modern JS me generally **`const`** default aur reassignment chahiye to **`let`**.
- **`var`** function-scoped hota hai aur hoisting behavior different hota hai.

**81. == vs ===?**

<code><pre>
5 == "5"   // true
5 === "5"  // false
</pre></code>

- **`===`** type coercion nahi karta, isliye generally preferred.

**82. Promise kya hai?**

- Asynchronous operation ke eventual result ko represent karta hai.

**States:**
<code><pre>
Pending
Fulfilled
Rejected
</pre></code>

**83. Async/Await?**
- Promises handle karne ka cleaner syntax:

<code><pre>
async function getUsers() {
  const response = await fetch(url);
  const data = await response.json();

  return data;
}
</pre></code>

## <u>`Part 21 — Interview Tricky Questions`</u> 🔥
**84. `setCount(count + 1)` 3 baar likhen to kya hoga?**
<code><pre>
setCount(count + 1);
setCount(count + 1);
setCount(count + 1);
</pre></code>

- Same render ke **`count`** value par based hone ki wajah se expected +3 nahi mil sakta.

**Use functional updates:**
<code><pre>
setCount(c => c + 1);
setCount(c => c + 1);
setCount(c => c + 1);
</pre></code>
Now +3.

**85. useEffect infinite loop kaise ho sakta hai?**

**Example:**

<code><pre>
useEffect(() => {
  setCount(count + 1);
}, [count]);
</pre></code>

- **`count`** change → effect → count change → effect...

**86. `map()` vs `forEach()` ?**

- **`map()`** new array return karta hai.

- **`forEach()`** return value ko transformation ke liye use nahi karta.

**React list rendering me commonly:**

- **`users.map(...)`**

**87. State update immediately available hoti hai?**

- State update schedule hota hai; current event/render ke state variable ko immediately mutate nahi karta.

<code><pre>
setCount(count + 1);

console.log(count);
</pre></code>

- **`console.log`** current render ka old **`count`** dikha sakta hai.

**88. Props drilling ka solution?**

- **Depending on requirement:**

<code><pre>
Component composition
Context API
State management library
</pre></code>

- Har prop drilling case me Redux zaroori nahi.

**89. useEffect API calling ke liye hi hai?**

- Nahi. It is for synchronization with external systems. API call ek common example hai.

**Others:**

<code><pre>
Timers
Subscriptions
Event listeners
Browser APIs
Third-party widgets
</pre></code>

**90. React component kab re-render hota hai?**

**Common reasons:**

<code><pre>
State update
Parent render
Context value change
External subscribed state change
</pre></code>

- Props change bhi relevant hain, especially memoized components ke behavior me.

## <u>`Part 22 — Rapid Fire Revision`</u>

| Question                 | Answer                      |
| ------------------------ | --------------------------- |
| React kya hai?           | UI library                  |
| JSX?                     | JavaScript syntax extension |
| Component?               | Reusable UI unit            |
| Props?                   | Parent → Child data         |
| State?                   | Component's dynamic state   |
| Hook for state?          | `useState`                  |
| Side effects/sync?       | `useEffect`                 |
| DOM reference?           | `useRef`                    |
| Shared context?          | Context + `useContext`      |
| List render?             | `map()`                     |
| List identification?     | `key`                       |
| Conditional UI?          | `if`, ternary, `&&`         |
| API?                     | `fetch` etc.                |
| Form reload stop?        | `preventDefault()`          |
| Navigation?              | `useNavigate()`             |
| URL params?              | `useParams()`               |
| Value memoization?       | `useMemo()`                 |
| Function memoization?    | `useCallback()`             |
| Component memoization?   | `memo()`                    |
| Reusable stateful logic? | Custom Hook                 |
| Parent → child?          | Props                       |
| Child → parent?          | Callback prop               |
| Global-ish shared data?  | Context                     |
| Array add?               | Spread                      |
| Array delete?            | `filter()`                  |
| Array update?            | `map()`                     |
