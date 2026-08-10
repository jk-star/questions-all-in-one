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

## `Part 4 — State` 🔥🔥🔥

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

## Part 5 — Events

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

# Part 6 — Conditional Rendering

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

## Part 7 — List Rendering 🔥🔥
**27. Array ko UI me kaise display karte hain?**

`map()`

<code><pre>
const users = ["Amit", "Rahul", "Neha"];

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

## Part 9 — useEffect 🔥🔥🔥
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

## Part 10 — API Calling 🔥🔥🔥
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

## Part 11 — Hooks 🔥🔥
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

## Part 12 — useRef 🔥
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

## Part 13 — Context API 🔥🔥🔥
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