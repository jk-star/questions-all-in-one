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