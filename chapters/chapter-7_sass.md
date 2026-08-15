# <u>`SASS Interview Questions & Answers`</u>

**1. SASS kya hai?**

- SASS ka full form **Syntactically Awesome Style Sheets** hai. Ye ek **CSS preprocessor** hai jo CSS ko powerful banata hai.

- SASS mein hum variables, nesting, mixins, functions, inheritance, modules etc. use kar sakte hain.

```scss
$primary-color: #3498db;

.button {
  background: $primary-color;
}
```

**Compiled CSS:**

```css
.button {
  background: #3498db;
}
```

---

**2. CSS aur SASS mein kya difference hai?**

| CSS | SASS |
|---|---|
| Styling language | CSS preprocessor |
| Variables limited/custom properties | Powerful variables |
| Nesting limited | Proper nesting |
| Mixins nahi | Mixins available |
| Functions limited | Custom functions |
| Inheritance limited | **`@extend`** |
| Large project mein repetitive code ho sakta hai | Code reusable aur maintainable |
| Browser directly read karta hai | Pehle CSS mein compile hota hai |

- **Interview line:** SASS CSS ko replace nahi karta, balki CSS likhne ko easier aur maintainable banata hai.

---

**3. SASS aur SCSS mein difference kya hai?**

- SASS ke mainly **do syntaxes** hain:

**`SASS syntax`**

```sass
$primary: red

.button
  color: $primary
```

- Ismein **`{}`** aur **`;`** use nahi hote.

**SCSS syntax**

```scss
$primary: red;

.button {
  color: $primary;
}
```

- SCSS ka syntax CSS jaisa hi hota hai.

- **Interview point:** SCSS is more commonly used because existing CSS can easily be converted/used as SCSS with minimal syntax changes.

---

**4. SASS file extension kya hoti hai?**

**Two common extensions:**

```text
.scss
.sass
```

**`SCSS:`**

```text
style.scss
```

**`SASS syntax:`**

```text
style.sass
```

---

**5. SASS ko browser directly understand karta hai?**

- **No.** , Browser normally SASS/SCSS ko directly understand nahi karta.

```text
style.scss
    ↓
Sass Compiler
    ↓
style.css
    ↓
Browser
```

---

**6. SASS compiler kya karta hai?**

- Compiler **`.scss`** ya **`.sass`** file ko normal **`.css`** file mein convert karta hai.

```scss
$color: red;

.title {
  color: $color;
}
```

**`Compiled:`**

```css
.title {
  color: red;
}
```

---

**7. SASS variables kya hain?**

- Variables reusable values store karne ke liye use hote hain.

```scss
$primary-color: #3498db;
$font-size: 18px;

.title {
  color: $primary-color;
  font-size: $font-size;
}
```

- Agar color change karna ho to sirf variable change karna padega.

---

**8. SASS variable naming kaise hoti hai?**

- Variable **`$`** se start hota hai.

```scss
$primary-color: blue;
$font-size: 16px;
$container-width: 1200px;
```

---

**9. SASS variables ka scope kya hota hai?**

- Variables ka scope depend karta hai ki variable kahan define hua hai.

```scss
$color: red;

.box {
  color: $color;
}
```

- Yahan **`$color`** global scope mein hai.

**`Nested/local scope:`**

```scss
.box {
  $color: blue;

  color: $color;
}
```

---

**10. `!global` kya hai?**

- **`!global`** local variable ko global scope mein modify/create karne ke liye use hota hai.

```scss
$color: red;

.box {
  $color: blue !global;
}
```

- Generally ise carefully use karna chahiye because global state maintain karna difficult ho sakta hai.

---

**11. SASS nesting kya hai?**

- Nesting se related CSS selectors ko hierarchical structure mein likh sakte hain.

```scss
.nav {
  background: black;

  ul {
    margin: 0;
  }

  li {
    display: inline-block;
  }

  a {
    color: white;
  }
}
```

**Compiled CSS:**

```css
.nav {
  background: black;
}

.nav ul {
  margin: 0;
}

.nav li {
  display: inline-block;
}

.nav a {
  color: white;
}
```
---

**12. **`&`** selector kya hai?**

- **`&`** parent selector ko represent karta hai.

```scss
.button {
  color: white;

  &:hover {
    color: red;
  }
}
```

**`Output:`**

```css
.button {
  color: white;
}

.button:hover {
  color: red;
}
```

---

**13. **`&`** ka use class naming mein kaise karte hain?**

**BEM style naming:**

```scss
.card {
  &__title {
    font-size: 20px;
  }

  &__button {
    padding: 10px;
  }
}
```

**Output:**

```css
.card__title {
  font-size: 20px;
}

.card__button {
  padding: 10px;
}
```

---

**14. SASS nesting ka disadvantage kya hai?**

- Bahut deep nesting se CSS unnecessarily complicated ho sakti hai.

**Bad example:**

```scss
.header {
  .container {
    .nav {
      ul {
        li {
          a {
            span {
              color: red;
            }
          }
        }
      }
    }
  }
}
```

- **Best practice:** nesting ko generally 2–3 levels ke around rakhna better hai.

---

## <u>`Mixins`</u>

**15. SASS mixin kya hai?**

- Mixin reusable CSS code ka block hota hai.

**`Define:`**

```scss
@mixin button {
  padding: 10px 20px;
  border-radius: 5px;
}
```

**`Use:`**

```scss
.btn {
  @include button;
}
```

---

**16. Mixin with parameters kya hota hai?**

- Mixin ko parameters de sakte hain.

```scss
@mixin button($bg, $color) {
  background: $bg;
  color: $color;
  padding: 10px 20px;
}

.primary {
  @include button(blue, white);
}

.danger {
  @include button(red, white);
}
```

---

**17. Mixin aur function mein difference?**

- **Mixin:** CSS rules/properties generate karne ke liye.

- **Function:** Value calculate/return karne ke liye.

**`Mixin:`**

```scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

**`Function:`**

```scss
@function double($value) {
  @return $value * 2;
}
```

---

**18. Default parameter in mixin kya hai?**

```scss
@mixin button($bg: blue, $color: white) {
  background: $bg;
  color: $color;
  padding: 10px 20px;
}
```

**`Ab:`**

```scss
.btn {
  @include button;
}
```

- Default values use hongi.

---

## <u>`Functions`</u>

**19. SASS function kya hai?**

- Function calculation karke value return karta hai.

```scss
@function double($value) {
  @return $value * 2;
}

.box {
  width: double(100px);
}
```

**`Output:`**

```css
.box {
  width: 200px;
}
```

---

**20. Built-in SASS functions kya hain?**

- SASS mein many built-in functions available hain.

**`Examples:`**

```text
darken()
lighten()
mix()
rgba()
rgb()
map-get()
map-merge()
nth()
```

- Modern Dart Sass mein kuch legacy color functions deprecated/obsolete direction mein hain, so new projects mein modern color APIs prefer karna better hai.

---

## <u>`@extend`</u>

**21. `@extend` kya hai?**

- **`@extend`** ek selector ki CSS properties ko doosre selector ke saath share karne ke liye use hota hai.

```scss
.message {
  padding: 10px;
  border: 1px solid;
}

.success {
  @extend .message;
  color: green;
}
```

**`Output conceptually:`**

```css
.message,
.success {
  padding: 10px;
  border: 1px solid;
}

.success {
  color: green;
}
```

---

**22. `@extend` aur `@mixin` mein difference?**

| **`@extend`** | **`@mixin`** |
|---|---|
| Selectors share karta hai | CSS declarations generate karta hai |
| Selector relationships create karta hai | Reusable code block |
| Output sometimes complex ho sakta hai | Parameters easily use kar sakte hain |
| Carefully use karna chahiye | Reusable patterns ke liye useful |

- **Interview answer:** Mixin reusable styles ke liye flexible hota hai, while **`@extend`** selector inheritance/share ke liye use hota hai.

---

**23. Placeholder selector `%` kya hai?**

- Placeholder selector output CSS mein independently generate nahi hota.

```scss
%button {
  padding: 10px;
  border-radius: 5px;
}

.primary {
  @extend %button;
  background: blue;
}
```

- Ye reusable base style ke liye useful hai.

---

## <u>`Modules and Files`</u>

**24. `@import` kya hai?**

- Historically SASS mein files ko combine karne ke liye `@import` use hota tha.

```scss
@import "variables";
@import "buttons";
```

- Lekin **modern Sass mein `@import` deprecated hai**.

- Modern projects mein **`@use`** aur **`@forward`** prefer kiye jaate hain.

---

**25. `@use` kya hai?**

- **`@use`** kisi Sass module ko load karta hai.

**`_variables.scss`:**

```scss
$primary: blue;
```

**Then:**

```scss
@use "variables";

.button {
  color: variables.$primary;
}
```

---

**26. `@use` ka advantage kya hai?**

**`@use`:**

- namespace provide karta hai
- global namespace pollution reduce karta hai
- modern Sass module system ka part hai
- dependencies ko clearer banata hai

---

**27. `@forward` kya hai?**

- **`@forward`** ek Sass module ke members ko doosre module se expose/re-export karne ke liye use hota hai.

```scss
// _index.scss

@forward "variables";
@forward "mixins";
```

**Phir:**

```scss
@use "index";
```

- Isse module organization better ho sakti hai.

---

**28. Partial kya hota hai?**

- SASS partial file usually underscore **`_`** se start hoti hai.

**Examples:**

```text
_variables.scss
_mixins.scss
_buttons.scss
_header.scss
```

- Ye files generally directly standalone CSS output ke liye nahi hoti; inhe modules/files mein use kiya ja sakta hai.

---

**29. SASS partials ka use kyun karte hain?**

- Large project ko small files mein divide karne ke liye.

```text
scss/
├── _variables.scss
├── _mixins.scss
├── _reset.scss
├── _buttons.scss
├── _header.scss
├── _footer.scss
└── main.scss
```

- Isse maintainability improve hoti hai.

---

## <u>`Operators`</u>

**30. SASS operators kya hain?**

- SASS arithmetic operators support karta hai.

```text
+
-
*
/
%
```

**`Example:`**

```scss
.container {
  width: 100% - 20%;
}
```

- Modern Sass mein division ke liye plain **`/`** ke usage par caution chahiye; **`math.div()`** preferred hai where division is intended.

---

**31. `math.div()` kya hai?**

Modern Sass mein division ke liye:

```scss
@use "sass:math";

.box {
  width: math.div(100px, 2);
}
```

**`Output:`**

```css
.box {
  width: 50px;
}
```

---

## <u>`Interpolation`</u>

**32. SASS interpolation kya hai?**

- Interpolation **`#{}`** se hoti hai.

- Variable/value ko selector, property name ya string ke andar insert karne ke liye use hoti hai.

```scss
$name: primary;

.#{$name}-button {
  color: blue;
}
```

**Output:**

```css
.primary-button {
  color: blue;
}
```

---

**33. Interpolation ka practical example?**

```scss
$property: margin;

.box {
  #{$property}-top: 20px;
}
```

**Output:**

```css
.box {
  margin-top: 20px;
}
```

---

## <u>`Maps and Lists`</u>

**34. SASS maps kya hain?**

- Map key-value pairs ka collection hai.

```scss
$colors: (
  primary: blue,
  danger: red,
  success: green
);
```

**`Modern syntax:`**

```scss
@use "sass:map";

.button {
  color: map.get($colors, primary);
}
```

---

**35. SASS lists kya hain?**

- List multiple values ka collection hai.

```scss
$fonts: Arial, Helvetica, sans-serif;
```

**Ya:**

```scss
$spacing: 10px 20px 30px;
```

---

**36. List aur Map mein difference?**

**List:**

```scss
$colors: red, blue, green;
```

- Ordered values.

**Map:**

```scss
$colors: (
  primary: blue,
  danger: red
);
```

- Key-value structure.

---

## <u>`Conditions`</u>

**37. `@if` kya hai?**

- Conditional styling ke liye.

```scss
$theme: dark;

.button {
  @if $theme == dark {
    background: black;
    color: white;
  } @else {
    background: white;
    color: black;
  }
}
```

---

**38. `@else if` kaise use karte hain?**

```scss
$size: medium;

.box {
  @if $size == small {
    width: 100px;
  } @else if $size == medium {
    width: 200px;
  } @else {
    width: 300px;
  }
}
```

---

## <u>`Loops`</u>

**39. `@for` loop kya hai?**

- Repeated CSS generate karne ke liye.

```scss
@for $i from 1 through 3 {
  .margin-#{$i} {
    margin: $i * 10px;
  }
}
```

**Output:**

```css
.margin-1 {
  margin: 10px;
}

.margin-2 {
  margin: 20px;
}

.margin-3 {
  margin: 30px;
}
```

---

**40. `through` aur `to` mein difference?**

```scss
@for $i from 1 through 5
```

- 1 se 5 tak.

```scss
@for $i from 1 to 5
```

- 1 se 4 tak.

**Important interview question.**

---

**41. `@each` loop kya hai?**

- List/map ke items par iterate karne ke liye.

```scss
$colors: red, blue, green;

@each $color in $colors {
  .text-#{$color} {
    color: $color;
  }
}
```

---

**42. Map ke saath `@each`?**

```scss
$colors: (
  primary: blue,
  danger: red,
  success: green
);

@each $name, $color in $colors {
  .btn-#{$name} {
    background: $color;
  }
}
```

---

**43. `@while` loop kya hai?**

- Condition true hone tak code execute hota hai.

```scss
$i: 1;

@while $i <= 3 {
  .box-#{$i} {
    width: $i * 100px;
  }

  $i: $i + 1;
}
```

---

## Comments and Debugging

**44. SASS comments kitne types ke hote hain?**

Two common types:

**`CSS comment`**

```scss
/* This comment appears in CSS */
```

**`Silent comment`**

```scss
// This comment does not appear in CSS
```

---

**45. SASS `@debug` kya hai?**

- Debugging ke liye.

```scss
$color: red;

@debug $color;
```

- Compiler output mein debugging information mil sakti hai.

---

**46. `@warn` kya hai?**

- Warning generate karne ke liye.

```scss
@warn "This value is deprecated";
```

---

**47. `@error` kya hai?**

- Invalid condition mein compilation ko error ke saath stop karne ke liye.

```scss
@error "Invalid theme";
```

---

## <u>`Responsive Design`</u>

**48. SASS mein responsive design kaise implement karte hain?**

- Mixin ke through media queries reusable bana sakte hain.

```scss
@mixin mobile {
  @media (max-width: 768px) {
    @content;
  }
}
```

**`Use:`**

```scss
.container {
  width: 1200px;

  @include mobile {
    width: 100%;
  }
}
```

---

**49. `@content` kya hai?**

- `@content` mixin ke andar caller ka CSS content inject karta hai.

```scss
@mixin mobile {
  @media (max-width: 768px) {
    @content;
  }
}
```

**`Then:`**

```scss
.box {
  @include mobile {
    width: 100%;
  }
}
```

---

**50. `@mixin` ke andar `@content` ka use kyun?**

- Reusable structures ke liye.

```scss
@mixin breakpoint($size) {
  @media (max-width: $size) {
    @content;
  }
}
```

**Use:**

```scss
.card {
  @include breakpoint(768px) {
    width: 100%;
  }
}
```

---

## <u>`Architecture`</u>

**51. SASS architecture kya hoti hai?**

- Large project mein common architecture:

```text
scss/
│
├── abstracts/
│   ├── _variables.scss
│   ├── _mixins.scss
│   └── _functions.scss
│
├── base/
│   ├── _reset.scss
│   └── _typography.scss
│
├── components/
│   ├── _button.scss
│   ├── _card.scss
│   └── _modal.scss
│
├── layout/
│   ├── _header.scss
│   ├── _footer.scss
│   └── _grid.scss
│
├── pages/
│   ├── _home.scss
│   └── _about.scss
│
└── main.scss
```

- Ye large projects mein maintainability improve karta hai.

---

**52. SASS mein DRY principle kya hai?**

- **DRY = Don't Repeat Yourself**

- Repeated CSS ko variables, mixins, functions, modules etc. se reusable banana.

**`Bad:`**

```scss
.btn1 {
  padding: 10px;
  border-radius: 5px;
}

.btn2 {
  padding: 10px;
  border-radius: 5px;
}
```

**`Better:`**

```scss
@mixin button-base {
  padding: 10px;
  border-radius: 5px;
}

.btn1 {
  @include button-base;
}

.btn2 {
  @include button-base;
}
```

---

## <u>`Advantages & Disadvantages`</u>

**53. SASS ke advantages kya hain?**

- Variables
- Nesting
- Mixins
- Functions
- Loops
- Conditions
- Modules
- **`@extend`**
- Better code organization
- Reusability
- Maintainability
- Large CSS projects ko manage karna easier

---

**54. SASS ke disadvantages kya hain?**

- Compilation required
- Beginners ke liye extra concepts
- Over-nesting se CSS complicated ho sakti hai
- **`@extend`** ka improper use complex selectors generate kar sakta hai
- Large architecture ko discipline ke saath maintain karna padta hai

---

## <u>`Comparisons`</u>

**55. SASS vs LESS?**

| SASS | LESS |
|---|---|
| Powerful preprocessor | CSS preprocessor |
| `.scss` / `.sass` | `.less` |
| Rich module/function features | Simpler syntax |
| `@mixin` | Mixins |
| `@use`, `@forward` | Different import model |
| Large projects mein widely used | Many projects mein use hua hai |

---

**56. SASS vs Tailwind CSS?**

- Ye dono same cheez nahi hain.

- **SASS:** CSS likhne ko powerful banata hai.

- **Tailwind:** Utility-first CSS framework hai.

**`SASS:`**

```scss
.card {
  padding: 20px;
  background: white;
}
```

**`Tailwind:`**

```html
<div class="p-5 bg-white"></div>
```

---

**57. SASS vs Bootstrap?**

- **SASS = CSS preprocessor**

- **Bootstrap = CSS/JS framework**

- Bootstrap ko Sass source/customization workflow ke through customize kiya ja sakta hai.

---

**58. Kya Bootstrap mein SASS use hota hai?**

- Yes. Bootstrap ke source CSS ko customize/build karne ke ecosystem mein Sass ka important role hai.

**`Example concept:`**

```scss
$primary: #ff0000;

@import "bootstrap";
```

- Modern Bootstrap versions ke saath exact import/module structure version-specific ho sakta hai, so project version ki documentation follow karni chahiye.

---

## <u>`Installation and Compilation`</u>

**59. SASS ko project mein kaise install karenge?**

**`Node.js project mein:`**

```bash
npm install -D sass
```

**`Then compile:`**

```bash
npx sass src/scss/style.scss dist/css/style.css
```

**`Watch mode:`**

```bash
npx sass --watch src/scss:dist/css
```

---

**60. `--watch` kya karta hai?**

- Sass files mein changes continuously monitor karta hai.

```bash
npx sass --watch src/scss:dist/css
```

- File change hone par CSS automatically compile ho jayegi.

---

**61. SASS aur Node.js ka relation kya hai?**

- Sass khud Node.js nahi hai.

- Lekin Node.js ecosystem mein Sass compiler ko npm package ke through install/use kar sakte hain.

```bash
npm install -D sass
```

---

**62. Dart Sass kya hai?**

- **Dart Sass** Sass ka primary/reference implementation hai.

- Modern Sass development mein generally Dart Sass use kiya jata hai.

---

**63. LibSass kya tha?**

- LibSass Sass ka older C/C++ implementation tha.

- **Important interview point:** LibSass deprecated hai, aur modern Sass development ke liye Dart Sass preferred hai.

---

**64. Sass aur SCSS kaun sa use karna chahiye?**

- Most modern projects mein **SCSS** practical choice hai because syntax CSS ke bahut close hai.

```scss
.card {
  color: red;
}
```

- Existing CSS ko SCSS mein migrate karna relatively easy hota hai.

---

## <u>`Advanced Questions`</u>

**65. SASS mein `!default` kya hai?**

- **`!default`** variable ko tabhi value assign karta hai jab wo pehle defined nahi hai.

```scss
$primary: blue !default;
```

- Agar **`$primary`** already defined hai, to existing value preserve hogi.

- Ye especially libraries/themes ko customize karne mein useful hai.

---

**66. `!important` aur `!default` mein difference?**

**`!important`**

**CSS priority ke liye:**

```scss
color: red !important;
```

**`!default`**

- Sass variable assignment behavior ke liye:

```scss
$primary: blue !default;
```

- Dono completely different hain.

---

**67. SASS mein private members kya hote hain?**

- Sass naming convention mein members jo **`-`** ya **`_`** se start hote hain, unhe private/internal API ke roop mein treat kiya ja sakta hai depending on Sass module context.

**`Example:`**

```scss
$_internal-color: red;
```

---

**68. SASS mein color manipulation kaise karte hain?**

- Modern Sass color module use kar sakte hain:

```scss
@use "sass:color";

.button {
  background: color.adjust(blue, $lightness: 10%);
}
```

- Color APIs ko current Dart Sass version ke according use karna chahiye.

---

**69. SASS mein loops ka practical use kya hai?**

- Utility classes generate karne ke liye.

```scss
@for $i from 1 through 5 {
  .m-#{$i} {
    margin: $i * 5px;
  }
}
```

- Ye automatically multiple classes generate kar sakta hai.

---

**70. SASS mein reusable breakpoints kaise banayenge?**

```scss
$breakpoints: (
  mobile: 576px,
  tablet: 768px,
  desktop: 1200px
);
```

- Map se values retrieve karke media-query mixin banaya ja sakta hai.

---

**71. SASS mein theme system kaise banayenge?**

- Variables/maps use karke:

```scss
$theme: (
  primary: blue,
  secondary: gray,
  danger: red
);
```

**`Then:`**

```scss
@use "sass:map";

.button {
  background: map.get($theme, primary);
}
```

- Large applications mein CSS custom properties + Sass ka combination bhi useful hota hai.

---

**72. Sass variables vs CSS custom properties?**

**`Sass variable`**

```scss
$primary: blue;
```

- Ye compile time par resolve hota hai.

**CSS variable**

```css
:root {
  --primary: blue;
}
```

- Ye browser runtime par available hota hai.

- CSS variables ko JavaScript se dynamically change kar sakte ho.

---

**73. Sass variable runtime par change ho sakta hai?**

- Normally **no**.

- Sass variable compilation ke time resolve hota hai.

```scss
$color: red;
```

- Browser ko final CSS milti hai:

```css
color: red;
```

- Runtime theming ke liye CSS custom properties better hoti hain.

---

**74. Kya Sass JavaScript ka alternative hai?**

- **No.**, Sass styling/CSS generation ke liye hai.

**`JavaScript:`**

- DOM manipulation
- Events
- API calls
- Application logic
- Dynamic behavior

**`Sass:`**

- CSS architecture
- Styling
- Variables
- Mixins
- CSS generation

---

## <u>`Top 10 Most Asked SASS Interview Questions`</u>

**Q1. SASS kya hai?**

- CSS preprocessor jo CSS ko variables, nesting, mixins, functions etc. jaise features ke saath powerful banata hai.

**Q2. SASS aur SCSS mein difference?**

- SCSS CSS-like syntax use karta hai, jabki **`.sass`** indentation-based syntax use karta hai.

**Q3. Variables kaise banate hain?**

```scss
$variable: value;
```

**Q4. Mixin kya hai?**

- Reusable CSS block.

**Q5. `@extend` kya karta hai?**

- Selectors ke styles share/inherit karne deta hai.

**Q6. `@use` kya hai?**

- Modern Sass module loading system.

**Q7. `@import` vs `@use`?**

- **`@import`** legacy/deprecated approach hai; **`@use`** modern module system hai.

**Q8. `&` kya karta hai?**

- Parent selector ko reference karta hai.

**Q9. Sass variable vs CSS variable?**

- Sass variable compile-time par resolve hota hai; CSS custom property browser/runtime level par available hoti hai.

**Q10. SASS ka biggest advantage?**

- Reusable, organized aur maintainable CSS architecture banana easier hota hai.

---

# Quick Cheat Sheet

| Feature | Syntax |
|---|---|
| Variable | `$color: red;` |
| Nesting | `.box { .title {} }` |
| Parent selector | `&` |
| Mixin | `@mixin name {}` |
| Include mixin | `@include name;` |
| Function | `@function name() {}` |
| Return | `@return` |
| Extend | `@extend` |
| Placeholder | `%name` |
| Module | `@use` |
| Re-export | `@forward` |
| Condition | `@if` |
| Loop | `@for` |
| List loop | `@each` |
| While loop | `@while` |
| Interpolation | `#{}` |
| Content block | `@content` |
| Warning | `@warn` |
| Error | `@error` |
| Debug | `@debug` |
| Default variable | `!default` |
| Global variable | `!global` |
| Division | `math.div()` |

