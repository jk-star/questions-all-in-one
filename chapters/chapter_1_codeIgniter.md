# CodeIgniter 4 Complete Interview Questions & Answers

## 1. CodeIgniter kya hai?
- CodeIgniter ek PHP framework hai jo MVC architecture follow karta hai. Iska use web applications aur APIs ko structured aur fast way me develop karne ke liye hota hai.

## 2. MVC kya hai?
- **Model** → Database/data logic handle karta hai.
- **View** → UI/HTML handle karta hai.
- **Controller** → Request receive karke Model aur View ke beech coordination karta hai.

Flow:

<code><pre>
Browser Request
      ↓
Route
      ↓
Controller
      ↓
Model → Database
      ↓
Controller
      ↓
View
      ↓
Browser Response
</pre></code>

## 3. CI4 me route kya hota hai?
- Route URL ko kisi Controller method se map karta hai.
- `$routes->get('/users', 'UserController::index');`
- `/users` open karne par `index()` execute hoga.


## 4. GET aur POST route me difference?
- **GET** normally data retrieve/display karne ke liye.
- `$routes->get('/users', 'UserController::index');`


- **POST** form data submit/create karne ke liye.
- `$routes->post('/users/store', 'UserController::store');`


## 5. Controller kya hai?
- Controller incoming request ko handle karta hai.

<code><pre>
namespace App\Controllers;

class UserController extends BaseController
{
    public function index()
    {
        return view('users/index');
    }
}
</pre></code>


## 6. Controller create karne ki command?
- `php spark make:controller UserController`


## 7. Model kya hai?
- Model database operations handle karta hai.
<code><pre>
namespace App\Models;

use CodeIgniter\Model;

class UserModel extends Model
{
    protected $table = 'users';
    protected $primaryKey = 'id';

    protected $allowedFields = [
        'name',
        'email'
    ];
}
</pre></code>

## 8. $allowedFields kya hai?

- Ye define karta hai ki Model ke through kaunse fields insert/update kiye ja sakte hain.
<code><pre>
protected $allowedFields = [
    'name',
    'email'
];
</pre></code>

- Ye mass-assignment protection me important hai.

## 9. Database se saare records kaise nikalenge?
<code><pre>
$model = new UserModel();
$users = $model->findAll();
</pre></code>

## 10. Single record kaise retrieve karenge?
- `$user = $model->find($id);`

## 11. Record insert kaise karenge?
<code><pre>
$model->insert([
    'name'  => 'Rahul',
    'email' => 'rahul@example.com'
]);

</pre></code>

## 12. Record update kaise karenge?
<code><pre>
$model->update($id, [
    'name' => 'Amit'
]);
</pre></code>

## 13. Record delete?
- `$model->delete($id);`

# CRUD — Very Important 🔥
## 14. CRUD ka full form?

<code><pre>
C = Create
R = Read
U = Update
D = Delete
</pre></code>

**Typical methods:**

<code><pre>
index()   → List
create()  → Form
store()   → Insert
edit()    → Edit form
update()  → Update
delete()  → Delete
</pre></code>

## 15. Form data kaise receive karenge?
- `$name = $this->request->getPost('name');`

**Multiple:**

<code><pre>
$data = [
    'name'  => $this->request->getPost('name'),
    'email' => $this->request->getPost('email')
];
</pre></code>

## 16. Validation kaise lagate hain?
<code><pre>
$rules = [
    'name'  => 'required|min_length[3]',
    'email' => 'required|valid_email'
];

if (!$this->validate($rules)) {
    return redirect()
        ->back()
        ->withInput()
        ->with('errors', $this->validator->getErrors());
}
</pre></code>

## 17. Common validation rules?
<code><pre>
required
valid_email
min_length[]
max_length[]
is_unique[]
matches[]
integer
numeric
</pre></code>

**Example:**

- `'email' => 'required|valid_email|is_unique[users.email]'`

# Query Builder 🔥

## 18. Query Builder kya hai?

- CI4 ka database abstraction interface hai jisse SQL manually likhe bina queries build kar sakte hain.
<code><pre>
$db = \Config\Database::connect();

$builder = $db->table('users');

$users = $builder->get()->getResult();
</pre></code>

## 19. WHERE query?
<code><pre>
$model ->where('status', 1) ->findAll();

</pre></code>

**Multiple:**

<code><pre>
$model ->where('status', 1) ->where('role', 'admin') ->findAll();

</pre></code>

## 20. `where()` + `first()` ?
<code><pre>
$user = $model ->where('email', $email) ->first();
</pre></code>

- Commonly login me use hota hai.

## 21. LIKE search?
<code><pre>
$users = $model ->like('name', $keyword) ->findAll();
</pre></code>

## 22. Order By?
<code><pre>
$users = $model ->orderBy('id', 'DESC') ->findAll();
</pre></code>

## 23. Limit?
<code><pre>
$users = $model ->limit(10) ->findAll();
</pre></code>

## 24. JOIN kaise karenge?
<code><pre>
$builder = $db->table('users');

$builder->select('users.*, orders.total');

$builder->join(
    'orders',
    'orders.user_id = users.id',
    'left'
);

$result = $builder->get()->getResult();
</pre></code>

# Sessions 🔥
## 25. Session kya hai?
- Session server side par user-specific data temporarily maintain karta hai.
<code><pre>
$session = session();
$session->set('user_id', 10);
</pre></code>

**Retrieve:**

- `$userId = session()->get('user_id');`

**Remove:**

- `session()->remove('user_id');`

## 26. Session destroy?

- `session()->destroy();`

- Commonly logout me.

## 27. Flashdata kya hai?
- Sirf next request tak temporary data store karta hai.
<code><pre>
session()->setFlashdata(
    'success',
    'User created successfully'
);
</pre></code>

**View:**

- `<?= session()->getFlashdata('success') ?>`

## Authentication 🔥🔥

## 28. Login ka basic flow?
<code><pre>
Email/password form
        ↓
Validation
        ↓
Email se user find
        ↓
Password verify
        ↓
Session create
        ↓
Dashboard redirect
</pre></code>

## 29. Password database me kaise store karna chahiye?
- Plain password nahi.
<code><pre>
$password = password_hash(
    $this->request->getPost('password'),
    PASSWORD_DEFAULT
);
</pre></code>

## 30. Password verify?

<code><pre>
if (password_verify($password, $user['password'])) {
    // login successful
}
</pre></code>

## 31. Login session?

<code><pre>
session()->set([
    'user_id'   => $user['id'],
    'user_name' => $user['name'],
    'logged_in' => true
]);
</pre></code>

## 32. Logout?
<code><pre>
public function logout()
{
    session()->destroy();

    return redirect()->to('/login');
}
</pre></code>

# Filters 🔥

## 33. Filter kya hai?

- Controller execute hone ke before/after request ko process kar sakta hai.
- Authentication ke liye commonly use hota hai.
<code><pre>
Request
   ↓
Auth Filter
   ↓
Controller
</pre></code>

## 34. Authentication filter ka example?
<code><pre>
public function before(
    \CodeIgniter\HTTP\RequestInterface $request,
    $arguments = null
) {
    if (!session()->get('logged_in')) {
        return redirect()->to('/login');
    }
}

</pre></code>

<code><pre>
</pre></code>

<code><pre>
</pre></code>