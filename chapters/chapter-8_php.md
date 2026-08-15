# <u>`PHP Array & String Functions`</u>

## <u>`1. PHP Array Functions`</u>

**A. Basic Array Information**

| Function             | Use                           |
| -------------------- | ----------------------------- |
| **`count()`**            | Array me elements count       |
| **`sizeof()`**          | **`count()`** ka alias            |
| **`is_array()`**         | Check array hai ya nahi       |
| **`empty()`**            | Array/value empty hai ya nahi |
| **`isset()`**            | Variable/key set hai ya nahi  |
| **`array_key_exists()`** | Key exist karti hai ya nahi   |


``` php
$arr = ["PHP", "JavaScript", "React"];

count($arr);                 // 3
is_array($arr);              // true
isset($arr[0]);              // true
array_key_exists(0, $arr);   // true
```

------------------------------------------------------------------------

## 2. Array Add / Remove Functions

 | Function          | Use                     |
| ----------------- | ----------------------- |
| **`array_push()`**    | End me element add      |
| **`array_pop()`**     | End se element remove   |
| **`array_unshift()`** | Beginning me add        |
| **`array_shift()`**   | Beginning se remove     |
| **`unset()`**         | Specific element remove |


``` php
$arr = [10, 20, 30];

array_push($arr, 40);
// [10,20,30,40]

array_pop($arr);
// [10,20,30]

array_unshift($arr, 5);
// [5,10,20,30]

array_shift($arr);
// [10,20,30]

unset($arr[1]);
// [10,30]
```

**`Interview Question: array_push() vs $arr[]`**

``` php
$arr[] = 40;
```

- For adding a single element, **`$arr[]`** is generally simpler.

------------------------------------------------------------------------

## 3. Search / Check Array

**`Important Functions`**

| Function             | Use                     |
| -------------------- | ----------------------- |
| **`in_array()`**         | Value exist karti hai?  |
| **`array_search()`**     | Value ki key/index find |
| **`array_key_exists()`** | Key exist karti hai?    |


``` php
$arr = ["PHP", "Laravel", "React"];

in_array("PHP", $arr);
// true

array_search("Laravel", $arr);
// 1
```

**`Strict Search`**

``` php
in_array(10, ["10"], true);
```

- The third argument **`true`** checks both value and type.

------------------------------------------------------------------------

## 4. Array Sorting Functions

**`Basic Sorting`**

 | Function   | Meaning                   |
| ---------- | ------------------------- |
| **`sort()`**   | Ascending values          |
| **`rsort()`**  | Descending values         |
| **`asort()`**  | Ascending, keys preserve  |
| **`arsort()`** | Descending, keys preserve |
| **`ksort()`**  | Key ascending             |
| **`krsort()`** | Key descending            |


**`Example:`**

``` php
$arr = [
    "a" => 30,
    "b" => 10,
    "c" => 20
];

asort($arr);
```

**`Result:`**

``` text
b => 10
c => 20
a => 30
```

**`Key Difference`**

``` text
sort()  -> value sort + keys reset
asort() -> value sort + keys preserved
ksort() -> key sort
```

------------------------------------------------------------------------

## 5. Reverse / Shuffle

 | Function          | Use           |
| ----------------- | ------------- |
| **`array_reverse()`** | Array reverse |
| **`shuffle()`**       | Random order  |


``` php
$arr = [1, 2, 3, 4];

array_reverse($arr);
// [4,3,2,1]

shuffle($arr);
```

------------------------------------------------------------------------

## 6. Array Merge / Combine / Replace

  | Function                    | Use                             |
| --------------------------- | ------------------------------- |
| **`array_merge()`**             | Arrays merge                    |
| **`array_merge_recursive()`**   | Recursive merge                 |
| **`array_combine()`**           | One array keys + another values |
| **`array_replace()`**           | Values replace                  |
| **`array_replace_recursive()`** | Recursive replacement           |


**`array_merge()`**

``` php
$a = ["PHP", "Laravel"];
$b = ["React", "Node"];

$result = array_merge($a, $b);
```

**`Result:`**

``` text
["PHP", "Laravel", "React", "Node"]
```

**`array_combine()`**

``` php
$keys = ["name", "age"];
$values = ["Jyoti", 28];

$result = array_combine($keys, $values);
```

**`Result:`**

``` text
[
    "name" => "Jyoti",
    "age" => 28
]
```

------------------------------------------------------------------------

## 7. Array Unique / Duplicate Handling

**`array_unique()`**

``` php
$arr = [10, 20, 20, 30, 30, 40];

array_unique($arr);
```

**`Result:`**

``` text
[10, 20, 30, 40]
```

**`array_count_values()`**

- Counts occurrences of values.

``` php
$arr = ["PHP", "JS", "PHP", "CSS"];

array_count_values($arr);
```

**`Result:`**

``` text
PHP => 2
JS  => 1
CSS => 1
```

------------------------------------------------------------------------

## 8. `array_slice()` vs `array_splice()`

**`array_slice()`**

- Returns a portion without modifying the original array.

``` php
$arr = [10,20,30,40,50];

array_slice($arr, 1, 3);
```

**`Result:`**

``` text
[20,30,40]
```

**`array_splice()`**

- Removes/replaces a portion and modifies the original array.

``` php
$arr = [10,20,30,40];

array_splice($arr, 1, 2);
```

**`Result:`**

``` text
[10,40]
```

## Interview Difference

``` text
array_slice()  -> returns a portion
array_splice() -> modifies the original array
```

------------------------------------------------------------------------

## 9. Array Keys / Values

  | Function                    | Use                             |
| --------------------------- | ------------------------------- |
| **`array_keys()`**             | Get all keys                    |
| **`array_values()`**   | Get all values                 |
| **`array_key_first()`**           | Get first key |
| **`array_key_last()`**           | Get last key                  |
| **`array_flip()`** | Exchange keys and values           |

``` php
$arr = [
    "name" => "Jyoti",
    "age" => 28
];

array_keys($arr);
// ["name", "age"]

array_values($arr);
// ["Jyoti", 28]
```

------------------------------------------------------------------------

## 10. `array_map()`, `array_filter()`, `array_reduce()`

**`array_map()`**

- Transforms every element.

``` php
$numbers = [1,2,3,4];

$result = array_map(function($n) {
    return $n * 2;
}, $numbers);
```

**`Result:`**

``` text
[2,4,6,8]
```

**`array_filter()`**

- Filters elements based on a condition.

``` php
$numbers = [1,2,3,4,5,6];

$result = array_filter($numbers, function($n) {
    return $n % 2 == 0;
});
```

**`Result:`**

``` text
[2,4,6]
```

**`array_reduce()`**

- Reduces an array to a single result.

``` php
$numbers = [1,2,3,4];

$total = array_reduce($numbers, function($carry, $item) {
    return $carry + $item;
}, 0);
```

**`Result:`**

``` text
10
```

**Interview Difference**

``` text
array_map()    -> transform
array_filter() -> filter
array_reduce() -> one final result
```

------------------------------------------------------------------------

## 11. `array_chunk()`

- Splits an array into chunks.

``` php
$arr = [1,2,3,4,5,6];

array_chunk($arr, 2);
```

**`Result:`**

``` text
[
    [1,2],
    [3,4],
    [5,6]
]
```

- Useful for batch processing and pagination-related logic.

------------------------------------------------------------------------

## 12. `array_column()`

- Very useful for PHP/Laravel interviews.

``` php
$users = [
    ["id"=>1, "name"=>"A"],
    ["id"=>2, "name"=>"B"],
    ["id"=>3, "name"=>"C"]
];

array_column($users, "name");
```

**`Result:`**

``` text
["A", "B", "C"]
```

**`With keys:`**

``` php
array_column($users, "name", "id");
```

**`Result:`**

``` text
[
    1 => "A",
    2 => "B",
    3 => "C"
]
```

------------------------------------------------------------------------

## 13. Sum / Min / Max / Product

``` php
$arr = [10,20,30,40];

array_sum($arr);      // 100
min($arr);            // 10
max($arr);            // 40
array_product($arr);  // 240000
```

------------------------------------------------------------------------

## 14. Array Intersection / Difference

## `array_intersect()`

``` php
$a = [1,2,3,4];
$b = [3,4,5,6];

array_intersect($a, $b);
// [3,4]
```

## `array_diff()`

``` php
array_diff($a, $b);
// [1,2]
```

**`Related functions:`**

``` php
array_intersect_key()
array_intersect_assoc()
array_diff_key()
array_diff_assoc()
```

## Difference

``` text
array_intersect()       -> compare values
array_intersect_key()   -> compare keys
array_intersect_assoc() -> compare keys + values
```

------------------------------------------------------------------------

## 15. `range()` and `array_fill()`

## `range()`

``` php
range(1, 5);
```

**`Result:`**

``` text
[1,2,3,4,5]
```

## `array_fill()`

``` php
array_fill(0, 5, "PHP");
```

**`Result:`**

``` text
["PHP","PHP","PHP","PHP","PHP"]
```

------------------------------------------------------------------------

## PHP String Functions

## 16. String Length

``` php
strlen("Hello");
// 5
```

**`Important:`**

``` php
strlen()
mb_strlen()
```

- Use **`mb_strlen()`** when working with multibyte/Unicode strings.

------------------------------------------------------------------------

## 17. String Search

**`Important Functions`**

``` php
strpos()
stripos()
strrpos()
strripos()
```

**`Example:`**

``` php
strpos("Hello PHP", "PHP");
// 6
```

## Difference

``` text
strpos()  -> case-sensitive
stripos() -> case-insensitive
strrpos() -> last occurrence
strripos() -> last occurrence, case-insensitive
```

## Classic Interview Trap

**`Do not write:`**

``` php
if (strpos($str, "PHP")) {
}
```

- If the match occurs at position **`0`**, this evaluates incorrectly.

**`Correct:`**

``` php
if (strpos($str, "PHP") !== false) {
}
```

------------------------------------------------------------------------

## 18. Substring Functions

## `substr()`

``` php
substr("Hello World", 0, 5);
// Hello
```

**`Related:`**

``` php
substr()
substr_replace()
substr_count()
```

**`Example:`**

``` php
substr_count("PHP PHP PHP", "PHP");
// 3
```

------------------------------------------------------------------------

## 19. String Replace

## Very Important

``` php
str_replace("PHP", "Laravel", "I love PHP");
// I love Laravel
```

Case-insensitive version:

``` php
str_ireplace()
```

Related:

``` php
str_replace()
str_ireplace()
substr_replace()
```

------------------------------------------------------------------------

## 20. `explode()` and `implode()`

## `explode()`

String -\> Array

``` php
$str = "PHP,Laravel,React";

explode(",", $str);
```

Result:

``` text
["PHP", "Laravel", "React"]
```

## `implode()`

Array -\> String

``` php
$arr = ["PHP", "Laravel", "React"];

implode(",", $arr);
```

Result:

``` text
PHP,Laravel,React
```

## Interview Difference

``` text
explode() -> String to Array
implode() -> Array to String
```

------------------------------------------------------------------------

## 21. Trim Functions

``` php
trim()
ltrim()
rtrim()
```

Example:

``` php
trim("  Hello  ");
// "Hello"
```

Difference:

``` text
trim()  -> both sides
ltrim() -> left side
rtrim() -> right side
```

------------------------------------------------------------------------

## 22. String Case Functions

``` php
strtolower()
strtoupper()
ucfirst()
lcfirst()
ucwords()
```

Examples:

``` php
strtolower("HELLO");
// hello

strtoupper("hello");
// HELLO

ucfirst("hello world");
// Hello world

ucwords("hello world");
// Hello World
```

------------------------------------------------------------------------

## 23. String Comparison

**`Important functions:`**

``` php
strcmp()
strcasecmp()
strncmp()
strncasecmp()
```

Example:

``` php
strcmp("abc", "abc");
// 0
```

`strcasecmp()` performs case-insensitive comparison.

------------------------------------------------------------------------

## 24. String Formatting

``` php
sprintf()
printf()
vsprintf()
```

Example:

``` php
$name = "Jyoti";
$age = 28;

echo sprintf(
    "My name is %s and I am %d",
    $name,
    $age
);
```

------------------------------------------------------------------------

## 25. Repeat / Reverse / Shuffle

## `str_repeat()`

``` php
str_repeat("PHP ", 3);
// PHP PHP PHP
```

## `strrev()`

``` php
strrev("Hello");
// olleH
```

## `str_shuffle()`

``` php
str_shuffle("Hello");
```

- Returns the characters in a random order.

------------------------------------------------------------------------

## 26. String Padding

``` php
str_pad("123", 5, "0", STR_PAD_LEFT);
// 00123
```

Padding types:

``` php
STR_PAD_LEFT
STR_PAD_RIGHT
STR_PAD_BOTH
```

------------------------------------------------------------------------

## 27. Character / Word Functions

``` php
str_split()
str_word_count()
str_getcsv()
```

Example:

``` php
str_split("Hello");
// ["H","e","l","l","o"]
```

``` php
str_word_count("I love PHP");
// 3
```

------------------------------------------------------------------------

## 28. HTML Related String Functions

Important for PHP web development:

``` php
htmlspecialchars()
htmlentities()
html_entity_decode()
htmlspecialchars_decode()
strip_tags()
```

Example:

``` php
htmlspecialchars($input);
```

Useful when safely displaying user-provided content in HTML.

``` php
strip_tags("<p>Hello</p>");
// Hello
```

------------------------------------------------------------------------

## 29. URL / Encoding Functions

``` php
urlencode()
urldecode()

rawurlencode()
rawurldecode()

base64_encode()
base64_decode()
```

Example:

``` php
$encoded = base64_encode("Hello PHP");

base64_decode($encoded);
// Hello PHP
```

------------------------------------------------------------------------

## 30. Newline / Formatting

``` php
nl2br()
wordwrap()
```

Example:

``` php
nl2br("Hello\nWorld");
```

In HTML:

``` html
Hello<br>
World
```

------------------------------------------------------------------------

## 31. Regex Functions

Important for interviews:

``` php
preg_match()
preg_match_all()
preg_replace()
preg_split()
```

Example:

``` php
preg_match("/php/i", "I love PHP");
```

------------------------------------------------------------------------

## 32. PHP 8+ String Functions

Modern PHP interviews me important:

``` php
str_contains()
str_starts_with()
str_ends_with()
```

Examples:

``` php
str_contains("I love PHP", "PHP");
// true

str_starts_with("Hello World", "Hello");
// true

str_ends_with("Hello.php", ".php");
// true
```

------------------------------------------------------------------------

## Top Array Functions for Interviews

If time is limited, first master these:

``` text
count()
is_array()
in_array()
array_search()

array_push()
array_pop()
array_shift()
array_unshift()

sort()
rsort()
asort()
arsort()
ksort()
krsort()

array_merge()
array_combine()
array_unique()

array_slice()
array_splice()

array_keys()
array_values()

array_map()
array_filter()
array_reduce()

array_column()
array_chunk()

array_sum()
array_diff()
array_intersect()
```

## Top String Functions for Interviews

``` text
strlen()

strpos()
stripos()
strrpos()

substr()
substr_count()

str_replace()
str_ireplace()

explode()
implode()

trim()
ltrim()
rtrim()

strtolower()
strtoupper()
ucfirst()
ucwords()

strcmp()
strcasecmp()

sprintf()

str_repeat()
strrev()
str_pad()

htmlspecialchars()
strip_tags()

base64_encode()
base64_decode()

preg_match()
preg_replace()

str_contains()
str_starts_with()
str_ends_with()
```

## Most Common Interview Differences

Be especially strong in these:

1.  `array_map()` vs `array_filter()`
2.  `array_slice()` vs `array_splice()`
3.  `sort()` vs `asort()`
4.  `in_array()` vs `array_search()`
5.  `isset()` vs `array_key_exists()`
6.  `array_merge()` vs `array_combine()`
7.  `explode()` vs `implode()`
8.  `strpos()` vs `stripos()`
9.  `substr()` vs `str_replace()`
10. `strcmp()` vs `strcasecmp()`
11. `==` vs `===`
12. `array_map()` with associative arrays
13. Remove duplicate values from an array
14. Find the second-highest value in an array
15. Reverse a string
16. Check whether a string is a palindrome
17. Count character/word frequency
18. Find/remove duplicate array values
19. Find common values between two arrays
20. Split a string into words and count them

------------------------------------------------------------------------

## Practical Coding Questions to Practice

## Array

-   Find the largest number
-   Find the second-largest number
-   Remove duplicate values
-   Count duplicate values
-   Find common elements in two arrays
-   Find difference between two arrays
-   Sort associative array by value
-   Sort associative array by key
-   Convert array to string
-   Convert string to array
-   Find a value's key
-   Filter even/odd numbers
-   Sum all array values
-   Find missing number
-   Merge two arrays
-   Find unique values
-   Group data using `array_column()`

## String

-   Reverse a string
-   Check palindrome
-   Count characters
-   Count words
-   Find duplicate characters
-   Remove duplicate characters
-   Find first non-repeating character
-   Reverse words in a sentence
-   Check whether a string contains a word
-   Replace a word
-   Count occurrence of a word
-   Convert string to uppercase/lowercase
-   Remove whitespace
-   Check whether a string starts/ends with a value
-   Validate patterns using regex

------------------------------------------------------------------------

## Interview Priority

## 🔴 Must Know

`count`, `in_array`, `array_search`, `array_merge`, `array_unique`,
`array_slice`, `array_splice`, `array_map`, `array_filter`,
`array_column`, `sort`, `asort`, `ksort`, `strlen`, `strpos`, `substr`,
`str_replace`, `explode`, `implode`, `trim`, `strtolower`, `strtoupper`,
`htmlspecialchars`, `preg_match`

## 🟡 Should Know

`array_reduce`, `array_chunk`, `array_combine`, `array_diff`,
`array_intersect`, `array_flip`, `array_reverse`, `shuffle`, `sprintf`,
`str_pad`, `str_split`, `str_word_count`

## 🟢 Good to Know

`array_replace_recursive`, `array_intersect_assoc`, `array_diff_assoc`,
`vsprintf`, `rawurlencode`, `htmlentities`, `preg_split`,
`preg_match_all`, `mb_strlen`

------------------------------------------------------------------------

## Quick Revision

``` text
ARRAY:
count
search
add/remove
sort
merge
unique
slice/splice
keys/values
map/filter/reduce
column
chunk
sum/diff/intersect

STRING:
length
search
substring
replace
explode/implode
trim
case conversion
comparison
formatting
reverse/repeat/padding
HTML escaping
encoding
regex
PHP 8 string helpers
```
