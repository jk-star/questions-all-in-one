# <u> `jQuery Complete Interview Questions & Answers` </u>

## Part 1 — jQuery Basics
**1. jQuery kya hai?**

- jQuery ek JavaScript library hai jo DOM manipulation, events, AJAX, animations aur cross-browser operations ko easier banati hai.

**`Common syntax:`**

<code><pre>
$(selector).action();

</pre></code>

**`Example:`**

<code><pre>
$("#title").hide();

</pre></code>

**2. jQuery use karne ke advantages?**
1. Short/easy syntax
1. DOM manipulation
1. Event handling
1. AJAX
1. Animations
1. Cross-browser abstractions

- Modern browsers me vanilla JavaScript kaafi powerful ho gaya hai, lekin existing PHP/CodeIgniter projects me jQuery abhi bhi milti hai.

**3. `$` kya hai?**

- **`$`** generally jQuery function ka alias hai.

<code><pre>
$("#box")

</pre></code>

**`Equivalent:`**
<code><pre>
jQuery("#box")

</pre></code>

**4. jQuery ka basic syntax?**
<code><pre>
$(selector).action();

</pre></code>

**`Example:`**
<code><pre>
$("#box").hide();

</pre></code>

- **`#box`** → selector
- **`hide()`** → action/method


## Document Ready 🔥
**5. $(document).ready() kya hai?**
- DOM ready hone ke baad code execute karne ke liye.

<code><pre>
$(document).ready(function () {
    console.log("DOM Ready");
});

</pre></code>

**`Short form:`**

<code><pre>
$(function () {
    console.log("DOM Ready");
});

</pre></code>

**6. document.ready vs window.onload?**
- **`document.ready`** DOM parse/ready hone par run kar sakta hai.
- **`window.onload`** images aur other dependent resources load hone ke baad fire hota hai.


## Selectors 🔥🔥🔥

| Selector            | Example                    | Kya select karta hai                  |
| ------------------- | -------------------------- | ------------------------------------- |
| **ID**              | **`$("#box")`**                | **`id="box"`** wala element               |
| **Class**           | **`$(".item")`**               | **`class="item"`** wale sab elements      |
| **Element/Tag**     | **`$("p")`**                   | Sab **`<p>`** elements                    |
| **Universal**       | **`$("*")`**                   | Page ke sab elements                  |
| **Multiple**        | **`$("h1, p")`**               | **`<h1>`** aur **`<p>`** dono                 |
| **Attribute**       | **`$("[type]")`**              | **`type`** attribute wale elements        |
| **Attribute Value** | **`$("[type='text']")`**       | **`type="text"`**                         |
| **Descendant**      | **`$(".box p")`**              | **`.box`** ke andar ke sab **`<p>`**          |
| **Child**           | **`$(".box > p")`**            | **`.box`** ke direct **`<p>`** children       |
| **First**           | **`$("li:first")`**            | First **`<li>`**                          |
| **Last**            | **`$("li:last")`**             | Last **`<li>`**                           |
| **Even**            | **`$("tr:even")`**             | Even-indexed rows                     |
| **Odd**             | **`$("tr:odd")`**              | Odd-indexed rows                      |
| **Eq**              | **`$("li:eq(2)")`**            | Index **`2`** wala element                |
| **Gt**              | **`$("li:gt(2)")`**            | Index 2 se greater elements           |
| **Lt**              | **`$("li:lt(2)")`**            | Index 2 se smaller elements           |
| **First-child**     | **`$("li:first-child")`**      | Parent ka first child **`<li>`**          |
| **Last-child**      | **`$("li:last-child")`**       | Parent ka last child **`<li>`**           |
| **Nth-child**       | **`$("li:nth-child(2)")`**     | Parent ka 2nd child                   |
| **Contains**        | **`$("p:contains('Hello')")`** | **`Hello`** text contain karne wale **`<p>`** |
| **Has**             | **`$("div:has(p)")`**          | Jinke andar **`<p>`** hai                 |
| **Not**             | **`$("input:not(.email)")`**   | **`.email`** ko chhodkar inputs           |
| **Checked**         | **`$(":checked")`**            | Checked checkbox/radio                |
| **Selected**        | **`$(":selected")`**           | Selected **`<option>`**                   |
| **Disabled**        | **`$(":disabled")`**           | Disabled form elements                |
| **Enabled**         | **`$(":enabled")`**            | Enabled form elements                 |
| **Empty**           | **`$("div:empty")`**           | Empty elements                        |
| **Visible**         | **`$("div:visible")`**         | Visible elements                      |
| **Hidden**          | **`$("div:hidden")`**          | Hidden elements                       |
| **Input**           | **`$(":input")`**              | Input, textarea, select, button etc.  |


## DOM Manipulation 🔥🔥🔥
**14. Text get/set kaise?**

**`Get:`**
<code><pre>
let text = $("#title").text();
</pre></code>

**`Set:`**
<code><pre>
$("#title").text("Hello");

</pre></code>

**15. `.html()` kya karta hai?**

**`Get:`**
<code><pre>
$("#box").html();

</pre></code>

**`Set:`**
<code><pre>
$("#box").html("<b>Hello</b>");

</pre></code>

**16. `.text()` vs `.html()` ?**

**`Given:`**
<code><pre>
&lt;b&gt;Hello&lt;/b&gt;
</code></pre>

- **`.text()`** markup ko text ki tarah treat karta hai.
- **`.html()`** HTML markup read/write karta hai.
- Untrusted user input ko **`.html()`** me directly inject nahi karna chahiye.

**17. Input ki value kaise get karenge?**
**`Get:`**
<code><pre>
let name = $("#name").val();
</code></pre>

**`Set:`**
<code><pre>
$("#name").val("Jyoti");

</code></pre>


**18. Attribute get/set?**

**`Get:`**
<code><pre>
$("#image").attr("src");

</code></pre>

**`Set:`**
<code><pre>
$("#image").attr(
    "src",
    "image.jpg"
);

</code></pre>

**19. Attribute remove?**
<code><pre>
$("#input").removeAttr("disabled");

</code></pre>

**20. .prop() kya hai?** 🔥

- DOM properties handle karne ke liye.

<code><pre>
$("#checkbox").prop("checked");

</code></pre>

**`Set:`**
<code><pre>
$("#checkbox").prop("checked", true);

</code></pre>

**21. `.attr()` vs `.prop()` ?**

- **`attr()`** HTML attribute ko deal karta hai.

- **`prop()`** current DOM property/state ko.

- Checkbox ke current checked state ke liye:

<code><pre>
$("#checkbox").prop("checked");

</code></pre>

- preferred hai.

## CSS & Classes 🔥
**22. CSS change?**
<code><pre>
$("#title").css("color", "red");

</code></pre>

**`Multiple:`**

<code><pre>
$("#title").css({
    color: "red",
    fontSize: "30px"
});

</code></pre>

**23. Class add?**
<code><pre>
$("#box").addClass("active");

</code></pre>

**24. Class remove?**
<code><pre>
$("#box").removeClass("active");

</code></pre>

**25. Toggle class?**
<code><pre>
$("#box").toggleClass("active");

</code></pre>

**26. Class exist karti hai?**
<code><pre>
$("#box").hasClass("active");

</code></pre>

- Returns boolean.

## Add / Remove Elements
**27. .append()?**
- Element ke andar end me content add karta hai.
<code><pre>
$("#list").append(
    "<li>New Item</li>"
);

</code></pre>

**28. .prepend()?**
- Element ke andar beginning me.
<code><pre>
$("#list").prepend(
    "<li>First</li>"
);

</pre></code>


**29. .before()?**
- Selected element ke bahar usse pehle.
<code><pre>
$("#box").before("<p>Hello</p>");

</pre></code>

**30. .after()?**
- Selected element ke bahar uske baad.

<code><pre>
$("#box").after("<p>Hello</p>");

</pre></code>

**31. Element remove?**
<code><pre>
$("#box").remove();

</pre></code>

**32. .empty()?**
- Selected element ko nahi hatata, uske child content ko remove karta hai.

<code><pre>
$("#box").empty();

</pre></code>

**33. remove() vs empty()?**
- **`remove()`** → selected element + descendants remove
- **`empty()`**  → descendants/content remove, container remains