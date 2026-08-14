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

## Events 🔥🔥🔥
**34. Click event?**
<code><pre>
$("#btn").click(function () {
    alert("Clicked");
});

</code></pre>

**`Preferred/general:`**

<code><pre>
$("#btn").on("click", function () {
    alert("Clicked");
});

</code></pre>

**35. .on() kya hai?**

- Event handlers attach karne ka general-purpose method.
<code><pre>
$("#btn").on("click", function () {
    console.log("Clicked");
});

</code></pre>

**36. Multiple events?**
<code><pre>
$("#input").on(
    "focus blur",
    function () {
        console.log("Event");
    }
);

</code></pre>

**37. Event object?**
<code><pre>
$("#btn").on("click", function (e) {
    console.log(e);
});

</code></pre>

**38. preventDefault()?** 🔥
- Browser ka default action prevent karta hai.
<code><pre>
$("form").on("submit", function (e) {
    e.preventDefault();
});

</code></pre>

- AJAX forms me common.

**39. stopPropagation()?**

- Event ko ancestor elements ki taraf propagate/bubble hone se rokta hai.
<code><pre>
e.stopPropagation();

</code></pre>

## this in jQuery 🔥
**40. `$(this)` kya hai?**
- Traditional function event handler me this generally current DOM element hota hai.

<code><pre>
$(".delete").on("click", function () {
    $(this).hide();
});

</code></pre>

**41. `this` vs $(this)?**

- **`this`** → raw DOM element.

- **`$(this)`** → us DOM element ka jQuery wrapper.

**`Example:`**
<code><pre>
this.value
</pre></code>

**`vs:`**

<code><pre>
$(this).val()

</pre></code>

**42. Arrow function ke saath $(this) ka issue?**
<code><pre>
$("#btn").on("click", () => {
    console.log($(this));
});

</pre></code>

- Arrow function apna event-handler this bind nahi karti.
- Isliye jab current element ka this chahiye:

<code><pre>
$("#btn").on("click", function () {
    console.log($(this));
});

</pre></code>


## Traversing 🔥🔥
**43. .parent()?**

**`Immediate parent:`**
<code><pre>
$("#child").parent();

</pre></code>

**44. .parents()?**

**`Matching ancestors:`**

<code><pre>
$("#child").parents();

</pre></code>

**`Specific:`**

<code><pre>
$("#child").parents(".container");

</pre></code>

**45. .children()?**

**`Direct children:`**

<code><pre>
$("#box").children();

</pre></code>

**46. .find()?**
- Descendants me matching elements search karta hai.

<code><pre>
$("#box").find(".item");

</pre></code>

**47. .closest()?** 🔥

- Current element se start karke nearest matching ancestor/self find karta hai.

<code><pre>
$(this).closest("tr");

</pre></code>

- CRUD delete/edit me bahut common.

**48. .siblings()?**
<code><pre>
$("#item").siblings();

</pre></code>

- Same parent wale sibling elements.

**49. .next() / .prev()?**
<code><pre>
$("#item").next();
$("#item").prev();

</pre></code>

## Effects / Animation
**50. Hide/Show?**
<code><pre>
$("#box").hide();
$("#box").show();
$("#box").toggle();

</pre></code>

**51. Fade methods?**
<code><pre>
fadeIn()
fadeOut()
fadeToggle()

</pre></code>

**52. Slide methods?**
<code><pre>
slideDown()
slideUp()
slideToggle()

</pre></code>

**53. Custom animation?**
<code><pre>
$("#box").animate({
    width: "300px"
}, 500);

</pre></code>

## Forms 🔥🔥🔥
**54. Form submit event?**
<code><pre>
$("#userForm").on("submit", function (e) {
    e.preventDefault();

    // validation / AJAX
});

</pre></code>

**55. Input change event?**
<code><pre>
$("#country").on("change", function () {
    let country = $(this).val();
});

</pre></code>

**56. Input typing detect?**
<code><pre>
$("#search").on("input", function () {
    let value = $(this).val();
});

</pre></code>

**57. Checkbox checked hai?**
<code><pre>
if ($("#agree").is(":checked")) {
    console.log("Checked");
}

</pre></code>

**`Ya:`**

<code><pre>
$("#agree").prop("checked");

</pre></code>

**58. Selected option value?**
<code><pre>
$("#country").val();

</pre></code>

**`Selected text:`**
<code><pre>
$("#country option:selected").text();

</pre></code>

## serialize() 🔥🔥
**59. .serialize() kya hai?**
- Form controls ko URL-encoded query string me convert karta hai.
<code><pre>
let data = $("#userForm").serialize();
</pre></code>

**`Example:`**
<code><pre>
name=Jyoti&email=test%40example.com
</pre></code>

- AJAX form submission me useful.

**60. .serializeArray()?**
- Form values ko array of name/value objects me return karta hai.
<code><pre>
$("#userForm").serializeArray();

</pre></code>

**`Conceptual result:`**
<code><pre>
[
    { name: "name", value: "Jyoti" },
    { name: "email", value: "test@example.com" }
]
</pre></code>

## AJAX 🔥🔥🔥🔥
- Ye PHP/CodeIgniter interviews me jQuery ka sabse important part hai.

**61. AJAX kya hai?**
**`Asynchronous JavaScript and XML`**
- Page ko full reload kiye bina server ke saath request/response communicate kar sakte hain. Naam me XML hai, lekin modern applications commonly JSON use karti hain.

**62. Basic jQuery AJAX?**
<code><pre>
$.ajax({
    url: "/users",
    type: "GET",

    success: function (response) {
        console.log(response);
    },

    error: function (xhr) {
        console.log(xhr);
    }
});
</pre></code>

**63. POST AJAX request?** 🔥🔥
<code><pre>
$.ajax({
    url: "/users/store",
    type: "POST",

    data: {
        name: $("#name").val(),
        email: $("#email").val()
    },

    success: function (response) {
        console.log(response);
    }
});
</pre></code>

**64. AJAX form submit?**
<code><pre>
$("#userForm").on("submit", function (e) {
    e.preventDefault();

    $.ajax({
        url: "/users/store",
        type: "POST",
        data: $(this).serialize(),

        success: function (response) {
            console.log(response);
        },

        error: function (xhr) {
            console.log(xhr.responseText);
        }
    });
});
</pre></code>

**65. `dataType: "json"` kya karta hai?**
- Expected server response JSON specify karta hai.
<code><pre>
$.ajax({
    url: "/users",
    dataType: "json",

    success: function (response) {
        console.log(response);
    }
});
</pre></code>

**66. `contentType` aur `dataType` difference?** 🔥
- **`contentType`** → server ko jo request body bhej rahe hain uska media type.
- **`dataType`** → jQuery server se kis response type ki expectation rakhe.

**67. $.get()?**
- GET request shortcut.
<code><pre>
$.get("/users", function (response) {
    console.log(response);
});

</pre></code>

**68. $.post()?**

- POST shortcut.

<code><pre>
$.post(
    "/users/store",
    {
        name: "Jyoti"
    },
    function (response) {
        console.log(response);
    }
);

</pre></code>

## File Upload with AJAX 🔥🔥🔥
**69. AJAX se file upload kaise?**
- **`FormData`** use karte hain.

<code><pre>
let formData = new FormData(
    $("#userForm")[0]
);
$.ajax({
    url: "/upload",
    type: "POST",

    data: formData,

    processData: false,
    contentType: false,

    success: function (response) {
        console.log(response);
    }
});

</pre></code>

**70. `processData: false` kyun?**
- jQuery ko FormData ko normal query string me transform/process karne se rokta hai.

**71. `contentType: false` kyun?**
- Browser ko multipart request ka correct Content-Type aur boundary automatically set karne deta hai.


## Event Delegation 🔥🔥🔥
**72. Dynamic elements par click kaise handle karenge?**

**`Ye:`**
<code><pre>
$(".delete").click(function () {
});

</pre></code>

- later dynamically added elements ke liye handler attach nahi karega.

**`Delegation:`**
<code><pre>
$(document).on(
    "click",
    ".delete",
    function () {
        console.log("Delete");
    }
);

</pre></code>

- Better hai closest stable parent use karna:
<code><pre>
$("#userTable").on(
    "click",
    ".delete",
    function () {
        // ...
    }
);

</pre></code>

**73. Event delegation kya hai?**

- Event listener parent element par attach hota hai aur bubbling ke through matching child events handle karta hai.
- Dynamic content ke liye extremely useful.

## AJAX CRUD 🔥🔥🔥
**74. Delete user AJAX se?**

**`HTML:`**

<code><pre>
&lt;button
    class="delete-user"
    data-id="10"
&gt;
    Delete
&lt;/button&gt;
</pre></code>

**`jQuery:`**
<code><pre>
$(document).on(
    "click",
    ".delete-user",
    function () {

        const button = $(this);
        const id = button.data("id");

        $.ajax({
            url: "/users/delete/" + id,
            type: "POST",

            success: function () {
                button
                    .closest("tr")
                    .remove();
            }
        });
    }
);
</pre></code>

75. **`data-*`** attribute kaise read karenge?

**`HTML:`**

<code><pre>
&lt;button data-id="10"&gt;
    Edit
&lt;/button&gt;

</pre></code>

**`jQuery:`**
<code><pre>
const id = $(this).data("id");
</pre></code>

**76. AJAX loading indicator?**
<code><pre>
$.ajax({
    url: "/users",

    beforeSend: function () {
        $("#loader").show();
    },

    success: function (response) {
        // handle
    },

    complete: function () {
        $("#loader").hide();
    }
});
</pre></code>

## AJAX Response Handling

**77. Server JSON return kare:**
<code><pre>
{
    "status": true,
    "message": "User created"
}
</pre></code>

**`Handle:`**
<code><pre>
success: function (response) {
    if (response.status) {
        alert(response.message);
    }
}
</pre></code>

**78. AJAX validation errors kaise show karenge?**

**`Suppose:`**
<code><pre>
{
    "status": false,
    "errors": {
        "email": "Email is required"
    }
}
</pre></code>

**`jQuery:`**

<code><pre>
if (response.errors?.email) {
    $("#emailError")
        .text(response.errors.email);
}

</pre></code>

- **`Note:`** optional chaining JavaScript feature hai, jQuery feature nahi.

## AJAX Search 🔥🔥
**79. Live search ka basic pattern?**
<code><pre>
$("#search").on("input", function () {

    const keyword = $(this).val();

    $.ajax({
        url: "/users/search",
        type: "GET",
        data: {
            search: keyword
        },

        success: function (response) {
            $("#results").html(response);
        }
    });
});

</pre></code>

- Production me live search ke saath debounce useful hota hai.

## AJAX Dependent Dropdown 🔥🔥
**80. Country → State dropdown?**
<code><pre>
$("#country").on("change", function () {

    const countryId = $(this).val();

    $.ajax({
        url: "/states/" + countryId,
        type: "GET",

        success: function (states) {

            $("#state").empty();

            $.each(states, function (_, state) {
                $("#state").append(
                    `<option value="${state.id}">
                        ${state.name}
                    </option>`
                );
            });
        }
    });
});

</pre></code>

- Very common practical interview task.

## Utility Methods
**81. $.each()?**
<code><pre>
$.each(users, function (index, user) {
    console.log(user.name);
});

</pre></code>

**82. each()?**

- Selected jQuery elements iterate karta hai.
<code><pre>
$(".item").each(function () {
    console.log($(this).text());
});

</pre></code>

**83. $.each() vs .each()?**
- **`$.each()`** → arrays/objects iterate kar sakta hai.
- **`.each()`** → jQuery collection iterate karta hai.

## Chaining
**84. Method chaining kya hai?**
- Same jQuery object par multiple operations:
<code><pre>
$("#box")
    .addClass("active")
    .slideDown()
    .text("Hello");

</pre></code>

## noConflict

**85. `$.noConflict()` kya hai?**

- Agar $ kisi aur library ke saath conflict kare:

<code><pre>
const jq = $.noConflict();

jq("#box").hide();
</pre></code>

**86. `.filter()` kya karta hai?**

- Selected elements mein se condition ke according elements filter karta hai.

```js
$(".item").filter(".active");
```

- Sirf **`.active`** wale elements milenge.

**87. `.not()` kya karta hai?**

- Specified elements ko exclude karta hai.

```js
$("li").not(".active");
```

- **`.active`** ko chhodkar baaki `li` select honge.

**88. `.is()` kya karta hai?**

- Check karta hai ki selected element given condition ko match karta hai ya nahi.

```js
if ($("#box").is(".active")) {
    console.log("Active");
}
```

- Return value: **`true` / `false`**.

**89. `.first()` aur `:first` mein kya difference hai?**

```js
$("li:first");
```

- jQuery selector hai.

```js
$("li").first();
```

- jQuery method hai.

- Dono first matching element ko target kar sakte hain, lekin `.first()` traversal/filtering ke context mein useful hota hai.

**90. `.last()` kya karta hai?**

- Collection ka last element return karta hai.

```js
$(".item").last();
```

**91. `.eq()` kya karta hai?**

- Specific index ka element select karta hai.

```js
$("li").eq(2);
```

- Ye third **`li`** ko select karega because index **`0`** se start hota hai.

**92. `.slice()` kya karta hai?**

- Collection ka ek portion select karta hai.

```js
$("li").slice(1, 4);
```

- Index **`1`** se **`3`** tak elements select honge.

**93. `.map()` kya karta hai?**

- jQuery collection ke elements ko transform karke new values ki collection banane ke liye use hota hai.

```js
let names = $(".user").map(function() {
    return $(this).text();
}).get();

console.log(names);
```

**94. `.get()` kya karta hai?**

- jQuery object ko normal JavaScript array/DOM element mein convert/access karne ke liye use hota hai.

```js
let items = $(".item").get();
```

**Specific index:**

```js
let item = $(".item").get(0);
```

**95. `.toArray()` kya karta hai?**

- jQuery collection ko JavaScript array mein convert karta hai.

```js
let items = $(".item").toArray();
```
**96. `.clone()` kya karta hai?**

- Element ki copy create karta hai.

```js
let copy = $("#box").clone();

$("#container").append(copy);
```

- Events/data ko clone karne ke liye:

```js
$("#box").clone(true);
```

**97. `.replaceWith()` kya karta hai?**

- Selected element ko naye content se replace karta hai.

```js
$("#old").replaceWith("<div>New Content</div>");
```

**98. `.wrap()` kya karta hai?**

- Element ko kisi wrapper ke andar wrap karta hai.

```js
$("p").wrap("<div class='wrapper'></div>");
```

**99. `.wrapAll()` kya karta hai?**

- Multiple selected elements ko ek single wrapper ke andar wrap karta hai.

```js
$("p").wrapAll("<div class='wrapper'></div>");
```

**100. `.unwrap()` kya karta hai?**

- Parent wrapper ko remove karta hai, lekin selected element ko rakhta hai.

```js
$("p").unwrap();
```

## Events — Advanced

**101. Event namespace kya hai?**

- Events ko logically group/identify karne ke liye namespace use kar sakte hain.

```js
$("#btn").on("click.myEvent", function() {
    console.log("Clicked");
});
```

**Remove:**

```js
$("#btn").off("click.myEvent");
```

**102. `.off()` kya karta hai?**

- Previously attached event handler ko remove karta hai.

```js
$("#btn").off("click");
```

**Specific handler:**

```js
function handleClick() {
    console.log("Clicked");
}

$("#btn").on("click", handleClick);

$("#btn").off("click", handleClick);
```

**103. `.one()` kya karta hai?**

- Event ko **sirf ek baar** execute karta hai.

```js
$("#btn").one("click", function() {
    alert("Only once");
});
```

- Button ko kitni bhi baar click karo, handler ek hi baar execute hoga.

**104. `.trigger()` kya karta hai?**

- Programmatically event trigger karta hai.

```js
$("#btn").trigger("click");
```

- Isse click handler execute ho sakta hai.

---

**105. `.triggerHandler()` kya hai?**

- Ye element par handler trigger karta hai, lekin normal `.trigger()` ki tarah event bubbling nahi karta.

```js
$("#btn").triggerHandler("click");
```

---

**106. `.bind()` kya hai?**

- Old jQuery API mein event attach karne ke liye use hota tha.

```js
$("#btn").bind("click", function() {
});
```

**Modern code mein `on()` use karna chahiye.**

---

**107. `.unbind()` kya hai?**

- Old API mein events remove karne ke liye use hota tha.

```js
$("#btn").unbind("click");
```

**Modern alternative:**

```js
$("#btn").off("click");
```

**108. `.live()` kya tha?**

- Old jQuery mein dynamically created elements ke events handle karne ke liye use hota tha.

```js
$(".btn").live("click", function() {});
```

**Deprecated/removed.**

**Modern approach:**

```js
$(document).on("click", ".btn", function() {});
```

---

**109. `.delegate()` kya tha?**

- Old event delegation API tha.

```js
$("#container").delegate(".btn", "click", function() {});
```

**Modern approach:**

```js
$("#container").on("click", ".btn", function() {});
```

## AJAX — Advanced

**110. AJAX mein `beforeSend()` kya karta hai?**

- Request send hone se **pehle** execute hota hai.

```js
$.ajax({
    url: "/users",
    beforeSend: function() {
        $("#loader").show();
    },
    success: function(response) {
        console.log(response);
    }
});
```

**111. AJAX mein `complete()` kya karta hai?**

- Request complete hone ke baad execute hota hai, chahe success ho ya error.

```js
$.ajax({
    url: "/users",

    complete: function() {
        $("#loader").hide();
    }
});
```

**112. `success`, `error` aur `complete` mein difference?**

| Callback | Kab execute hota hai |
|---|---|
| **`beforeSend`** | Request se pehle |
| **`success`** | Successful response par |
| **`error`** | Request fail hone par |
| **`complete`** | Request complete hone ke baad |

### 113. AJAX request cancel kaise karenge?

- **`$.ajax()`** ek **`jqXHR`** object return karta hai.

```js
let request = $.ajax({
    url: "/users"
});
```

**Cancel:**

```js
request.abort();
```

**114. `$.ajax()` kya return karta hai?**

- Ye **jqXHR object** return karta hai, jo XMLHttpRequest functionality ke saath jQuery Deferred/Promise-like methods provide karta hai.

```js
let request = $.ajax({
    url: "/users"
});
```

**115. AJAX success ko `.done()` se kaise handle karenge?**

```js
$.ajax({
    url: "/users"
})
.done(function(response) {
    console.log(response);
})
.fail(function(error) {
    console.log(error);
})
.always(function() {
    console.log("Completed");
});
```

- Ye modern jQuery code mein kaafi useful pattern hai.

**116. `.done()`, `.fail()`, `.always()` kya hain?**

**`.done()`**

- Successful completion ke liye.

```js
request.done(function(response) {
    console.log(response);
});
```

**`.fail()`**

- Failure ke liye.

```js
request.fail(function(error) {
    console.log(error);
});
```

**`.always()`**

- Success ya failure dono ke baad.

```js
request.always(function() {
    console.log("Finished");
});
```

**117. jQuery Deferred kya hai?**

- Deferred asynchronous operation ki state aur callbacks ko manage karne ke liye jQuery ka mechanism hai.

**Example:**

```js
let deferred = $.Deferred();

deferred.done(function(value) {
    console.log(value);
});

deferred.resolve("Success");
```

**118. AJAX mein timeout kaise set karenge?**

```js
$.ajax({
    url: "/users",
    timeout: 5000,

    success: function(response) {
        console.log(response);
    },

    error: function(xhr, status) {
        console.log(status);
    }
});
```

`5000` milliseconds = **5 seconds**.

**119. AJAX request mein headers kaise send karenge?**

```js
$.ajax({
    url: "/users",
    type: "POST",

    headers: {
        "Authorization": "Bearer token"
    },

    success: function(response) {
        console.log(response);
    }
});
```

**120. JSON data POST karna ho to `contentType` kaise use karenge?**

```js
$.ajax({
    url: "/users",
    type: "POST",

    contentType: "application/json",

    data: JSON.stringify({
        name: "Jyoti",
        email: "test@example.com"
    }),

    success: function(response) {
        console.log(response);
    }
});
```

## Interview mein yaad rakho

```text
contentType
     ↓
Request mein hum kya bhej rahe hain?

dataType
     ↓
Server se hum kya receive/expect kar rahe hain?
```
