# AJAX Complete Interview Questions — Hinglish

## 1. AJAX kya hai?
- AJAX ka full form hai **Asynchronous JavaScript and XML**.
- AJAX ek technique hai jiske through hum **page ko completely reload kiye bina server se data send/receive** kar sakte hain.

```javascript
$.ajax({
    url: "getUser.php",
    type: "POST",
    data: {
        id: 10
    },
    success: function(response) {
        console.log(response);
    }
});
```

- Yahan browser background mein server ko request bhejta hai aur response aane ke baad page ke required part ko update karta hai.

---

## 2. AJAX ka full form kya hai?

```text
A = Asynchronous  
J = JavaScript  
A = And  
X = XML
```

- Lekin aaj ke time AJAX mein XML compulsory nahi hai. Mostly **JSON** use hota hai.

---

## 3. AJAX ka use kyun karte hain?

- AJAX ka main purpose hai:

    - Page reload avoid karna
    - Server se background mein request bhejna
    - Dynamic data load karna
    - Better user experience
    - Fast UI updates
    - Form submit without page refresh
    - Search suggestions
    - Filtering
    - Pagination
    - CRUD operations

**`Example:`**

- User search box mein **`"php"`** type karta hai → AJAX server ko request bhejta hai → results aa jaate hain → **poora page reload nahi hota**.

---

## 4. AJAX kaise work karta hai?

**`Typical flow:`**

```text
User Action
    ↓
JavaScript / jQuery
    ↓
AJAX Request
    ↓
Web Server
    ↓
PHP / CodeIgniter
    ↓
Database
    ↓
Response
    ↓
JavaScript
    ↓
DOM Update
```

**`Example:`**

```text
Button Click
     ↓
AJAX
     ↓
Controller
     ↓
Model
     ↓
Database
     ↓
JSON Response
     ↓
HTML Update
```
---

## 5. AJAX mein asynchronous ka kya meaning hai?

- Asynchronous ka matlab hai browser request bhejne ke baad **poore page ko block/reload nahi karta**.

**`Example:`**

```javascript
$.ajax({
    url: "users.php",
    success: function(response) {
        console.log(response);
    }
});

console.log("Hello");
```
- Request background mein ja rahi hoti hai aur meanwhile JavaScript doosra kaam kar sakti hai.

---

## 6. AJAX synchronous kya hota hai?

- Synchronous request mein browser request complete hone ka wait karta hai.

**`Conceptually:`**

```text
Request
   ↓
Wait
   ↓
Response
   ↓
Continue
```

- Synchronous AJAX generally avoid kiya jata hai because UI freeze/block ho sakti hai.

---

## 7. Kya AJAX ek programming language hai?

- No. AJAX koi programming language nahi hai.
- Ye ek **web development technique/pattern** hai jo JavaScript aur HTTP requests ka use karti hai.

---

## 8. AJAX mein kaun-kaun si technologies use hoti hain?

**`Commonly:`**

- JavaScript
- XMLHttpRequest
- Fetch API
- jQuery
- JSON
- HTTP
- HTML
- CSS
- Server-side language — PHP, Node.js, etc.

---

## 9. `XMLHttpRequest` kya hai?

- **`XMLHttpRequest`** browser ka built-in JavaScript object hai jo server ke saath HTTP requests communicate karne ke liye use hota hai.

**`Example:`**

```javascript
let xhr = new XMLHttpRequest();

xhr.open("GET", "users.php", true);

xhr.onload = function() {
    if (xhr.status === 200) {
        console.log(xhr.responseText);
    }
};

xhr.send();
```

---

## 10. `XMLHttpRequest` ke important methods kaun se hain?

**`Important methods:`**

```javascript
open()
send()
setRequestHeader()
abort()
```

**`Example:`**

```javascript
xhr.open("POST", "login.php", true);
xhr.setRequestHeader(
    "Content-Type",
    "application/x-www-form-urlencoded"
);
xhr.send("email=test@gmail.com");
```

---

## 11. AJAX ke liye XMLHttpRequest ke alawa kya use kar sakte hain?

**`Modern JavaScript mein:`**

**`Fetch API`**

```javascript
fetch("users.php")
    .then(response => response.json())
    .then(data => {
        console.log(data);
    });
```

**`Aur jQuery mein:`**

```javascript
$.ajax();
```

---

## 12. Fetch aur AJAX mein difference?

- Strictly speaking, **Fetch API bhi AJAX-style asynchronous HTTP communication ka modern approach hai**.

**`Interview mein bol sakti hain:`**

- AJAX ek technique/concept hai, jabki Fetch API us technique ko implement karne ka modern JavaScript API hai.

---

## 13. jQuery AJAX kya hai?

- jQuery AJAX methods server ko asynchronous HTTP requests bhejne ko easy banate hain.

**`Example:`**

```javascript
$.ajax({
    url: "users.php",
    type: "GET",
    success: function(response) {
        console.log(response);
    }
});
```
---

## 14. `$.ajax()` kya hai?

- **`$.ajax()`** jQuery ka generic AJAX method hai.
- Ismein hum specify kar sakte hain:

```javascript
$.ajax({
    url: "url",
    type: "POST",
    data: {},
    dataType: "json",
    success: function(response) {},
    error: function(xhr) {},
    complete: function() {}
});
```
---

## 15. `$.get()` kya hai?
- GET request ke liye jQuery ka shorthand method.

```javascript
$.get("users.php", function(response) {
    console.log(response);
});
```

---

## 16. `$.post()` kya hai?
- POST request ke liye shorthand method.

```javascript
$.post(
    "save.php",
    {
        name: "Jyoti",
        email: "test@gmail.com"
    },
    function(response) {
        console.log(response);
    }
);
```
---

## 17. `$.ajax()` vs `$.get()` vs `$.post()`?

| Method | Use |
|---|---|
| **`$.ajax()`** | Full control |
| **`$.get()`** | Simple GET |
| **`$.post()`** | Simple POST |

**`Interview mein:`**

- **`$.ajax()`** more configurable hai, while `$.get()` aur `$.post()` shorthand methods hain.

---

## 18. AJAX GET request kya hoti hai?
- GET ka use generally server se data retrieve karne ke liye hota hai.

```javascript
$.ajax({
    url: "users.php",
    type: "GET",
    success: function(response) {
        console.log(response);
    }
});
```
---

## 19. AJAX POST request kya hoti hai?
- POST ka use generally data server ko send karne ke liye hota hai.

```javascript
$.ajax({
    url: "save-user.php",
    type: "POST",
    data: {
        name: "Jyoti",
        email: "test@gmail.com"
    },
    success: function(response) {
        console.log(response);
    }
});
```
---

## 20. GET vs POST?

| GET | POST |
|---|---|
| Data URL/query string mein hota hai | Data request body mein hota hai |
| Retrieval ke liye common | Create/update actions ke liye common |
| URL mein parameters visible ho sakte hain | Parameters URL mein normally visible nahi |
| Length limitations ho sakti hain | Larger payload support karta hai |
| Cache ho sakta hai | Generally cache nahi |

**Important:** POST automatically secure nahi hota. Security HTTPS, authentication, authorization, validation etc. se aati hai.

---

## 21. AJAX mein JSON kya hai?
- JSON = **JavaScript Object Notation**
- Server aur client ke beech structured data exchange ke liye commonly use hota hai.

**`Example:`**

```json
{
    "id": 1,
    "name": "Jyoti",
    "email": "test@gmail.com"
}
```

---

## 22. PHP se JSON response kaise bhejenge?

```php
$data = [
    "status" => true,
    "message" => "User found"
];

header('Content-Type: application/json');

echo json_encode($data);
```
---

## 23. AJAX response ko JSON mein kaise receive karenge?
**`jQuery:`**

```javascript
$.ajax({
    url: "user.php",
    type: "GET",
    dataType: "json",
    success: function(response) {
        console.log(response.name);
    }
});
```
---

## 24. `dataType` kya hota hai?
- **`dataType` batata hai ki client response ko kis format mein expect kar raha hai**.

**`Example:`**

```javascript
dataType: "json"
```

**`Possible values:`**

```text
json
html
text
xml
script
```
---

## 25. `contentType` kya hota hai?
- **`contentType`** batata hai ki **client server ko kis format mein data send kar raha hai**.

**`Example:`**

```javascript
contentType: "application/json"
```

**`Important interview point:`**

- > **`contentType`** request ke body format se related hai, while `dataType` response ke expected format se related hai.

---

## 26. `data` property kya karti hai?
- AJAX request ke saath server ko data send karne ke liye.

```javascript
$.ajax({
    url: "save.php",
    type: "POST",
    data: {
        name: "Jyoti",
        age: 28
    }
});
```
---

## 27. AJAX mein `success` kya hai?
- Request successful hone par callback execute hota hai.

```javascript
success: function(response) {
    console.log(response);
}
```
---

## 28. AJAX mein `error` kya hai?

Request fail hone par execute hota hai.

```javascript
error: function(xhr, status, error) {
    console.log(error);
}
```
---

## 29. AJAX mein `complete` kya hai?
- Request complete hone ke baad execute hota hai, chahe success ho ya failure.

```javascript
complete: function() {
    console.log("Request completed");
}
```

---

## 30. `beforeSend` kya hota hai?
- Request send hone se pehle execute hota hai.
- Commonly loader show karne ke liye:

```javascript
beforeSend: function() {
    $("#loader").show();
}
```
---

## 31. AJAX loader kaise banayenge?

```javascript
$.ajax({
    url: "users.php",

    beforeSend: function() {
        $("#loader").show();
    },

    success: function(response) {
        $("#result").html(response);
    },

    complete: function() {
        $("#loader").hide();
    }
});
```
---

## 32. AJAX mein HTTP status code kya hota hai?

**`Important codes:`**

```text
200 → OK
201 → Created
400 → Bad Request
401 → Unauthorized
403 → Forbidden
404 → Not Found
422 → Validation Error
500 → Internal Server Error
```
---

## 33. AJAX mein 404 error ka meaning?

**`404 = Resource Not Found`**

**`Usually:`**

- URL wrong
- Route wrong
- File missing
- Controller route missing

**`Example:`**

```javascript
url: "user/list"
```

- Agar route exist nahi karta → 404 aa sakta hai.

---

## 34. AJAX mein 500 error ka meaning?

**`500 = Internal Server Error`**

- Usually server-side problem:

    - PHP fatal error
    - Database error
    - Exception
    - Controller issue
    - Model issue
    - Server configuration problem

---

## 35. AJAX mein 401 vs 403?
**`401 Unauthorized`**
- Usually authentication missing/invalid.

**`403 Forbidden`**
- User authenticated ho sakta hai but uske paas requested resource ka permission nahi hai.

---

## 36. AJAX form submit kaise karenge?

```javascript
$("#userForm").submit(function(e) {

    e.preventDefault();

    $.ajax({
        url: "save-user.php",
        type: "POST",
        data: $(this).serialize(),

        success: function(response) {
            console.log(response);
        }
    });

});
```
---

## 37. `preventDefault()` kyun use karte hain?
- Normal form submit browser ko page reload/navigation karwa sakta hai.

```javascript
e.preventDefault();
```
- default browser behavior ko prevent karta hai.
- Then AJAX request manually bhejte hain.

---

## 38. `serialize()` kya hai?

- Form ke fields ko URL-encoded string mein convert karta hai.

**`HTML:`**

```html
<form id="userForm">
    <input type="text" name="name">
    <input type="email" name="email">
</form>
```

**`JavaScript:`**

```javascript
let data = $("#userForm").serialize();
```

**`Result conceptually:`**

```text
name=Jyoti&email=test%40gmail.com
```
---

## 39. AJAX mein FormData kya hai?

- **`FormData`** form data ko easily request ke through send karne ke liye use hota hai.
- Especially **file upload** ke liye useful hai.

```javascript
let formData = new FormData(
    document.getElementById("userForm")
);

$.ajax({
    url: "upload.php",
    type: "POST",
    data: formData,
    processData: false,
    contentType: false
});
```
---

## 40. AJAX se image/file upload kaise karenge?

```javascript
let formData = new FormData();

formData.append("name", "Jyoti");
formData.append("image", $("#image")[0].files[0]);

$.ajax({
    url: "upload.php",
    type: "POST",
    data: formData,
    processData: false,
    contentType: false,

    success: function(response) {
        console.log(response);
    }
});
```
---

## 41. `processData: false` kyun?
- jQuery normally data ko query-string format mein process karta hai.
- File/FormData ke case mein hume ye processing nahi chahiye.

**`Isliye:`**

```javascript
processData: false
```
---

## 42. `contentType: false` kyun?

- Browser ko FormData ka correct multipart content type/boundary automatically set karne dene ke liye.

```javascript
contentType: false
```
---

## 43. AJAX mein dynamic dropdown kaise banayenge?

**Example:**

```text
Country
   ↓
State
   ↓
City
```

**Country change:**

```javascript
$("#country").change(function() {

    let country_id = $(this).val();

    $.ajax({
        url: "get-states.php",
        type: "POST",
        data: {
            country_id: country_id
        },

        success: function(response) {
            $("#state").html(response);
        }
    });

});
```

---

## 44. AJAX dependent dropdown kya hai?

Jab ek dropdown ki value ke according doosre dropdown ka data change ho, use dependent dropdown kehte hain.

**`Example:`**

```text
Country → State → City
Category → Subcategory → Product
Department → Employee
```

---

## 45. AJAX search autocomplete kaise work karta hai?

**`User type karta hai:`**

```text
jav
```

**`AJAX request:`**

```text
jav → server
```

**`Server results return karta hai:`**

```text
Java
JavaScript
Java Developer
```

- Frontend results show karta hai.
---

## 46. AJAX pagination kya hai?

**`Traditional pagination:`**

```text
Page 1
↓
Full page reload
↓
Page 2
```

**`AJAX pagination:`**

```text
Page 1
↓
Click Page 2
↓
AJAX request
↓
Only table/list update
```
---

## 47. AJAX CRUD kya hai?

**`CRUD:`**

```text
C → Create
R → Read
U → Update
D → Delete
```

**`AJAX ke through:`**

```text
Add User → AJAX POST
Get Users → AJAX GET
Update User → AJAX POST/PUT/PATCH
Delete User → AJAX DELETE/POST
```
---

## 48. AJAX CRUD ka real example?

```javascript
$.ajax({
    url: "/users/save",
    type: "POST",
    data: $("#userForm").serialize(),

    success: function(response) {
        loadUsers();
    }
});
```

**`Then:`**

```javascript
function loadUsers() {

    $.ajax({
        url: "/users/list",
        type: "GET",

        success: function(response) {
            $("#userTable").html(response);
        }
    });

}
```
---

## 49. AJAX DELETE request possible hai?

Yes.

```javascript
$.ajax({
    url: "/users/10",
    type: "DELETE",

    success: function(response) {
        console.log(response);
    }
});
```

- But framework/application architecture ke according POST bhi use kiya ja sakta hai.

---

## 50. AJAX mein `async: false` kya hai?

**`Example:`**

```javascript
$.ajax({
    url: "test.php",
    async: false
});
```

- Isse synchronous behavior request kiya jata tha.
- Modern applications mein synchronous XHR avoid karna chahiye because it can block the UI.

---

## 51. AJAX mein timeout kya hota hai?

- Maximum time define karne ke liye:

```javascript
$.ajax({
    url: "users.php",
    timeout: 5000
});
```

- Yahan 5000 milliseconds = 5 seconds.

---

## 52. AJAX request cancel kaise karenge?

- jQuery AJAX **`jqXHR`** object return karta hai.

```javascript
let request = $.ajax({
    url: "users.php"
});

request.abort();
```

- Useful for autocomplete/search requests.

---

## 53. AJAX request mein headers kaise bhejenge?

```javascript
$.ajax({
    url: "api/users",

    headers: {
        "Authorization": "Bearer TOKEN"
    }
});
```
---

## 54. AJAX mein CSRF kya hai?
- CSRF = **Cross-Site Request Forgery**
- Attacker victim ke authenticated browser ka misuse karke unwanted request karne ki koshish karta hai.
- Frameworks like CodeIgniter CSRF protection provide karte hain.

---

## 55. AJAX request mein CSRF token kaise bhejenge?

**`Conceptually:`**

```javascript
$.ajax({
    url: "/user/save",
    type: "POST",
    data: {
        name: "Jyoti",
        csrf_token: csrfToken
    }
});
```

- Actual token name/framework configuration ke according different ho sakta hai.

---

## 56. CORS kya hai?
- CORS = **Cross-Origin Resource Sharing**
- Agar frontend aur backend different origins par hain, browser security policy request ko restrict kar sakti hai.

**`Example:`**

```text
Frontend:
https://example.com

Backend:
https://api.example.com
```

- Server ko appropriate CORS headers provide karne pad sakte hain.

---

## 57. Same-Origin Policy kya hai?

- Browser security mechanism hai jo different origins ke resources ke access ko restrict karta hai.

**`Origin generally:`**

```text
Protocol + Domain + Port
```

**`Example:`**

```text
https://example.com
```

and

```text
http://example.com
```

- different origins hain because protocol different hai.

---

## 58. AJAX aur CORS ka relation kya hai?
- AJAX/fetch request cross-origin ho sakti hai, lekin browser CORS policy apply karta hai.
- Server ko appropriate permission headers return karne padte hain.

---

## 59. Preflight request kya hoti hai?

- CORS mein kuch cross-origin requests ke liye browser pehle:

```text
OPTIONS
```

- request bhejta hai.
- Isse **preflight request** kehte hain.
- Server batata hai ki actual request allowed hai ya nahi.

---

## 60. AJAX mein authentication kaise handle karenge?

**`Common methods:`**

- Session/cookies
- Token authentication
- JWT
- OAuth
- API keys depending on architecture

**`Example bearer token:`**

```javascript
headers: {
    "Authorization": "Bearer " + token
}
```

---

## 61. AJAX mein session kaise work karta hai?

- Agar browser session cookie maintain kar raha hai, AJAX requests same session ke saath server tak ja sakti hain, subject to same-origin/CORS/cookie policies.

**`PHP:`**

```php
$_SESSION['user_id']
```

- AJAX request mein server session identify kar sakta hai.

---

## 62. AJAX mein SQL injection se kaise bachenge?

- AJAX hone se SQL injection automatically prevent nahi hota.

**`Server side:`**

1. Prepared statements
1. Query builder
1. ORM
1. Input validation

- use karna chahiye.

- CodeIgniter mein Query Builder commonly use hota hai.

---

## 63. AJAX mein XSS kya hai?
- XSS = **Cross-Site Scripting**
- Attacker malicious JavaScript inject karne ki koshish karta hai.

**`Example:`**

```javascript
$("#result").html(userInput);
```

- Agar **`userInput`** untrusted hai, problem ho sakti hai.
- Context ke according escaping/sanitization aur safe DOM APIs use karne chahiye.

---

## 64. `.html()` vs `.text()`?

```javascript
$("#result").html(response);
```

- HTML interpret karega.

```javascript
$("#result").text(response);
```

- Text ke form mein treat karega.
- Untrusted user input ke case mein **`.text()`** safer choice ho sakta hai.

---

## 65. AJAX response ko HTML mein kaise insert karenge?

```javascript
success: function(response) {
    $("#result").html(response);
}
```
---

## 66. AJAX response ko JSON mein kaise process karenge?

```javascript
success: function(response) {

    if (response.status) {
        console.log(response.message);
    }

}
```

**`Example server response:`**

```json
{
    "status": true,
    "message": "User saved"
}
```
---

## 67. AJAX mein race condition kya hai?

- Suppose user rapidly type karta hai:

```text
j
ja
jav
java
```

- Multiple requests simultaneously ja sakti hain.
- Ho sakta hai old request ka response latest request ke baad aaye aur UI mein outdated data show kar de.

**`Isse avoid karne ke liye:`**

- Debouncing
- Request cancellation
- Request IDs
- Server-side handling

use kar sakte hain.

---

## 68. Debouncing kya hai?

- Rapid events ke beech function ko immediately execute karne ke bajay wait karna. Search autocomplete ke liye useful.

**`Example:`**

```text
User types:
J
Ja
Jav
Java

Wait 300ms
↓
Only one AJAX request
```
---

## 69. AJAX autocomplete mein debounce kyun use karenge?

**`Without debounce:`**

```text
J → request
Ja → request
Jav → request
Java → request
```

- Bahut requests ja sakti hain.

**`Debounce se:`**

```text
Java
↓
Wait
↓
One request
```

- Server load reduce hota hai.

---

## 70. AJAX request fail hone par kya karenge?

- User ko meaningful error show karenge:

```javascript
error: function(xhr) {

    if (xhr.status === 500) {
        alert("Server error");
    } else if (xhr.status === 404) {
        alert("Requested resource not found");
    } else {
        alert("Something went wrong");
    }

}
```

- Production mein generic user message aur detailed server-side logging better hoti hai.

---

## 71. AJAX mein network error kaise debug karenge?

**`Browser DevTools:`**

```text
F12
↓
Network
↓
Request select
↓
Headers
Payload
Response
Status
Timing
```

- Check karenge.

---

## 72. AJAX request browser mein kaise check karenge?

- Chrome DevTools → **Network tab**

**`Then request select karke:`**

- Request URL
- Method
- Status
- Headers
- Payload
- Response
- Preview
- Cookies
- Timing

check kar sakte hain.

---

## 73. AJAX mein 200 status hai but error aa raha hai. Why?

**`Possible reasons:`**

- Response expected JSON nahi hai
- Invalid JSON
- PHP warning/notice response mein aa gaya
- HTML error response aa gaya
- Wrong `dataType`
- JavaScript parsing error
- Application-level error

**`Example:`**

```javascript
dataType: "json"
```

but server returns:

```text
Warning...
{"status":true}
```

To JSON parsing fail ho sakti hai.

---

## 74. AJAX mein JSON parse error kyun aata hai?

Server valid JSON nahi bhej raha.

**`Wrong:`**

```text
User saved
{"status":true}
```

**`Correct:`**

```json
{
    "status": true
}
```

**`Server side:`**

```php
header('Content-Type: application/json');
echo json_encode($data);
```

---

## 75. AJAX request duplicate kyun ho sakti hai?

**`Common reasons:`**

- Event handler multiple times bind hua
- Button multiple times click hua
- Script duplicate load hua
- Form submit + AJAX dono execute ho rahe hain
- Event delegation incorrectly implemented

---

## 76. Duplicate AJAX request ko kaise prevent karenge?

**`Button temporarily disable:`**

```javascript
$("#submitBtn").prop("disabled", true);
```

**`Complete hone par:`**

```javascript
complete: function() {
    $("#submitBtn").prop("disabled", false);
}
```

- Aur event binding architecture check karenge.

---

## 77. AJAX mein button double click issue kaise solve karenge?

```javascript
$("#btn").click(function() {

    let btn = $(this);

    if (btn.prop("disabled")) {
        return;
    }

    btn.prop("disabled", true);

    $.ajax({
        url: "save.php",
        type: "POST",
        complete: function() {
            btn.prop("disabled", false);
        }
    });

});
```

---

## 78. AJAX mein caching kya hai?
- Browser/server previous GET response ko cache kar sakta hai.
- Dynamic data ke cases mein unwanted stale response aa sakta hai.

**`jQuery:`**

```javascript
cache: false
```

- use kiya ja sakta hai in applicable cases, although proper HTTP cache headers are generally the better solution.

---

## 79. AJAX aur normal form submit mein difference?

**`Normal form`**

```text
Submit
 ↓
Request
 ↓
Full page reload
```

**`AJAX`**

```text
Submit
 ↓
AJAX request
 ↓
Response
 ↓
Required UI update
```

---

## 80. AJAX aur API mein difference?
- **AJAX** client-side asynchronous HTTP communication ka technique/pattern hai.
- **API** ek interface/endpoint hai jiske through applications communicate karti hain.
- AJAX API ko call kar sakta hai.

**`Example:`**

```text
Browser
   ↓
AJAX / Fetch
   ↓
REST API
   ↓
PHP / CodeIgniter
   ↓
Database
```

---

## 81. AJAX aur REST API ka relation?

- REST API backend endpoints provide karti hai.
- AJAX/fetch frontend se un endpoints ko call kar sakta hai.

**`Example:`**

```javascript
fetch("/api/users")
```

**`Yahan:`**

- `fetch` → client-side HTTP mechanism
- `/api/users` → API endpoint

---

## 82. AJAX mein PUT aur PATCH kya hain?

**`REST APIs mein:`**

```text
POST   → Create
GET    → Read
PUT    → Full update/replacement
PATCH  → Partial update
DELETE → Delete
```

**`Example:`**

```javascript
fetch("/api/users/10", {
    method: "PATCH",
    body: JSON.stringify({
        name: "Jyoti"
    })
});
```

---

## 83. AJAX mein Promise kya hai?

- Modern JavaScript APIs jaise **`fetch()`** Promise return karti hain.

**`Example:`**

```javascript
fetch("users.php")
    .then(response => response.json())
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.log(error);
    });
```

---

## 84. Async/Await se AJAX kaise karenge?

```javascript
async function getUsers() {

    try {

        const response = await fetch("/users");

        const data = await response.json();

        console.log(data);

    } catch (error) {

        console.log(error);

    }
}
```

---

## 85. jQuery AJAX mein Promise hota hai?

- jQuery ka **`$.ajax()` `jqXHR`** object return karta hai jo Promise-like interface provide karta hai.

**`Example:`**

```javascript
$.ajax({
    url: "users.php"
})
.done(function(response) {
    console.log(response);
})
.fail(function(error) {
    console.log(error);
});
```

---

## 86. `success/error` vs `.done/.fail`?

**`Old/common style:`**

```javascript
$.ajax({
    success: function(response) {},
    error: function(xhr) {}
});
```

**`Promise-style:`**

```javascript
$.ajax({
    url: "users.php"
})
.done(function(response) {})
.fail(function(xhr) {});
```

- Dono jQuery AJAX mein use kiye ja sakte hain.

---

## 87. AJAX request mein credentials kya hain?

- Cross-origin requests mein cookies/auth credentials ke behavior ko control karna pad sakta hai.

**`Fetch:`**

```javascript
fetch(url, {
    credentials: "include"
});
```

- CORS + cookies ke case mein server-side configuration bhi required hoti hai.

---

## 88. CodeIgniter mein AJAX request kaise identify karenge?

- CodeIgniter version ke according approach differ kar sakti hai.

**`CI3 mein commonly:`**

```php
if ($this->input->is_ajax_request()) {
    // AJAX request
}
```

**`Lekin important:`**

- Security decision sirf AJAX check par based nahi hona chahiye, because request headers can be spoofed.

- Authentication, authorization, CSRF and validation properly implement karna chahiye.

---

## 89. CodeIgniter mein AJAX se data kaise receive karenge?

**`CI3:`**

```php
$name = $this->input->post('name');
$email = $this->input->post('email');
```

**`AJAX:`**

```javascript
$.ajax({
    url: "user/save",
    type: "POST",
    data: {
        name: "Jyoti",
        email: "test@gmail.com"
    }
});
```

---

## 90. CodeIgniter mein JSON response kaise denge?

**`CI3 mein:`**

```php
$data = [
    'status' => true,
    'message' => 'User saved'
];

$this->output
    ->set_content_type('application/json')
    ->set_output(json_encode($data));
```

---

## 91. CodeIgniter AJAX CRUD architecture kya hogi?

**`A typical CI3 project:`**

```text
View
 ↓
jQuery AJAX
 ↓
Controller
 ↓
Model
 ↓
Database
 ↓
Model
 ↓
Controller
 ↓
JSON
 ↓
AJAX Success
 ↓
DOM Update
```

---

## 92. AJAX security ke liye kya-kya karna chahiye?
- AJAX request ko secure karne ke liye HTTPS, authentication, authorization, CSRF protection, server-side validation, output encoding, SQL injection protection aur proper CORS configuration use karni chahiye.

---

## 93. AJAX request ko sirf AJAX hone par allow karna secure hai?

**No.**

**`Example:`**

```php
$this->input->is_ajax_request()
```

- sirf request type identify karne ke liye useful ho sakta hai.
- But attacker request ko manually create kar sakta hai.

**``Security ke liye:``**

```text
Authentication
Authorization
CSRF
Validation
Rate limiting
```

etc. important hain.

---

## 94. AJAX mein validation client-side ya server-side?

**Both.**

**`Client-side:`**

```javascript
if (name === "") {
    alert("Name required");
}
```

User experience ke liye.

**`Server-side:`**

```php
$this->form_validation->set_rules(
    'name',
    'Name',
    'required'
);
```

- Security/data integrity ke liye.

- Server-side validation mandatory hai.

---

## 95. AJAX request mein sensitive data kaise protect karenge?

- HTTPS
- Never put passwords/secrets in URLs
- Proper authentication
- Authorization
- Secure cookies
- CSRF protection where applicable
- Avoid exposing sensitive data in responses
- Don't trust client-side validation

---

## 96. AJAX mein rate limiting kya hai?

- Agar user repeatedly API/AJAX endpoint hit kare, server resources consume ho sakte hain.

- Rate limiting request frequency limit karti hai.

**`Example concept:`**

```text
100 requests / minute
```

- Uske baad temporary block/429 response.

---

## 97. AJAX mein HTTP 429 kya hai?

**`429 = Too Many Requests`**

- Usually rate limiting ke context mein use hota hai.

---

## 98. AJAX request slow ho to kya karenge?

**`Interview answer:`**

1. Network request inspect karungi
2. Backend response time check karungi
3. SQL query optimize karungi
4. Payload size reduce karungi
5. Unnecessary AJAX calls remove karungi
6. Debouncing use karungi
7. Pagination use karungi
8. Caching consider karungi
9. Compression consider karungi
10. Server logs/profile data check karungi

---

## 99. AJAX performance kaise improve karenge?

**`Important points:`**

```text
Debouncing
Caching
Pagination
Smaller payload
Efficient SQL
Lazy loading
Request cancellation
Batch requests
Avoid duplicate requests
Compression
```

---

## 100. Interview mein AJAX ka real project example kaise explain karein?

**`Aap ye answer bol sakti hain:`**

- "Maine AJAX ka use CRUD operations mein kiya hai. For example, user management module mein add, edit, delete aur listing AJAX requests se handle ki. Form submit par **`preventDefault()`** use karke page reload prevent kiya, form data AJAX ke through controller ko send kiya, backend mein validation aur database operation perform hua aur JSON response return hua. Success response ke basis par table ko dynamically update kiya aur error cases ke liye proper error handling aur loader use kiya."

- Ye **real interview answer** hai aur PHP/CodeIgniter profile ke liye relevant hai.

---

# 🔥 20 Most Important AJAX Questions — Must Prepare

- Agar interviewer ke paas time kam ho, **ye 20 definitely prepare karo:**

1. AJAX kya hai?
2. AJAX kaise work karta hai?
3. Asynchronous ka meaning?
4. XMLHttpRequest kya hai?
5. **`$.ajax()`** kya hai?
6. **`$.get()`** vs **`$.post()`** ?
7. GET vs POST?
8. **`dataType`** vs **`contentType`**?
9. **`success`, `error`, `complete`**?
10. **`beforeSend`**?
11. AJAX form submit?
12. **`preventDefault()`**?
13. **`serialize()`**?
14. FormData?
15. AJAX file upload?
16. JSON response?
17. AJAX CRUD?
18. CORS?
19. CSRF?
20. AJAX debugging using Network tab?
