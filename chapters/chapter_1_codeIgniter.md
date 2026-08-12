# <u>`CodeIgniter 4 Complete Interview Questions & Answers`</u>

## 1. CodeIgniter kya hai?
- CodeIgniter ek PHP framework hai jo MVC architecture follow karta hai. Iska use web applications aur APIs ko structured aur fast way me develop karne ke liye hota hai.

## 2. MVC kya hai?
- **Model** → Database/data logic handle karta hai.
- **View** → UI/HTML handle karta hai.
- **Controller** → Request receive karke Model aur View ke beech coordination karta hai.

**Flow:**

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
- **`$routes->get('/users', 'UserController::index');`**
- **`/users`** open karne par **`index()`** execute hoga.


## 4. GET aur POST route me difference?
- **GET** normally data retrieve/display karne ke liye.
- **`$routes->get('/users', 'UserController::index');`**


- **POST** form data submit/create karne ke liye.
- **`$routes->post('/users/store', 'UserController::store');`**


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
- **`php spark make:controller UserController`**


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
- **`$user = $model->find($id);`**

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
- **`$model->delete($id);`**

# <u>`CRUD — Very Important`</u> 🔥
## 14. CRUD ka full form?

<code><pre>
C = Create
R = Read
U = Update
D = Delete
</pre></code>

**`Typical methods:`**

<code><pre>
index()   → List
create()  → Form
store()   → Insert
edit()    → Edit form
update()  → Update
delete()  → Delete
</pre></code>

## 15. Form data kaise receive karenge?
- **`$name = $this->request->getPost('name');`**

**`Multiple:`**

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

**`Example:`**

- **`'email' => 'required|valid_email|is_unique[users.email]'`**

# <u>`Query Builder`</u> 🔥

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

**`Multiple:`**

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

# <u>`Sessions`</u> 🔥
## 25. Session kya hai?
- Session server side par user-specific data temporarily maintain karta hai.
<code><pre>
$session = session();
$session->set('user_id', 10);
</pre></code>

**`Retrieve:`**

- **`$userId = session()->get('user_id');`**

**`Remove:`**

- **`session()->remove('user_id');`**

## 26. Session destroy?

- **`session()->destroy();`**

- Commonly logout me.

## 27. Flashdata kya hai?
- Sirf next request tak temporary data store karta hai.
<code><pre>
session()->setFlashdata(
    'success',
    'User created successfully'
);
</pre></code>

**`View:`**

- **`<?= session()->getFlashdata('success') ?>`**

# <u>`Authentication`</u> 🔥🔥

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

# <u>`Filters`</u> 🔥

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

## 35. Filter alias kaha define hota hai?

- **`app/Config/Filters.php`**

**Conceptually:**

- **`'auth' => \App\Filters\AuthFilter::class`**

**`Route:`**

<code><pre>
$routes->get(
    '/dashboard',
    'Dashboard::index',
    ['filter' => 'auth']
);

</pre></code>

# <u>`View & Layout`</u>

## 36. Controller se View me data kaise pass karenge?

**`Controller:`**
<code><pre>
$data['users'] = $model->findAll();
return view('users/index', $data);
</pre></code>

**`View:`**
<code><pre>
<?php foreach ($users as $user): ?>

    <?= esc($user['name']) ?>

<?php endforeach; ?>
</pre></code>

## 37. esc() kyun use karte hain?
- Output escape karne aur **XSS risk reduce** karne ke liye.
- **`<?= esc($user['name']) ?>`**

## 38. Layout kaise create hota hai?
<code><pre>
<?= $this->extend('layouts/main') ?>

<?= $this->section('content') ?>

&lt;h1&gt;Dashboard&lt;/h1&gt;

<?= $this->endSection() ?>
</pre></code>

**`Layout:`**

- **`<?= $this->renderSection('content') ?>`**

# <u>`Pagination`</u> 🔥

## 39. Pagination kaise?
<code><pre>
$data = [
    'users' => $model->paginate(10),
    'pager' => $model->pager
];

return view('users/index', $data);
</pre></code>

**`View:`**

- **`<?= $pager->links() ?>`**

# <u>`File Upload`</u>
## 40. Uploaded file kaise retrieve karenge?

- **`$file = $this->request->getFile('image');`**

## 41. File valid hai ya nahi?
<code><pre>
if ($file->isValid() && !$file->hasMoved()) {
    // upload
}
</pre></code>

## 42. Random filename kaise?
- **`$newName = $file->getRandomName();`**

**`Move:`**
<code><pre>
$file->move(
    WRITEPATH . 'uploads',
    $newName
);
</pre></code>

# <u>`Database / Migration`</u>

## 43. Migration kya hai?

- Database schema ko PHP files/code ke through version-control karne ka method hai.
- **`php spark make:migration CreateUsersTable`**

**`Run:`**

- **`php spark migrate`**

## 44. Seeder kya hai?
- Database me sample/default data insert karne ke liye.
- **`php spark make:seeder UserSeeder`**

**`Run:`**
- **`php spark db:seed UserSeeder`**

# <u>`REST API`</u> 🔥🔥
## 45. REST API kya hai?

- HTTP ke through applications ke beech data/resources exchange karne ka architecture style hai.

**`Common methods:`**
<code><pre>
GET     → Read
POST    → Create
PUT     → Update
PATCH   → Partial update
DELETE  → Delete
</pre></code>

## 46. ResourceController kya hai?
- CI4 me RESTful APIs banane ke liye useful base controller.
<code><pre>
use CodeIgniter\RESTful\ResourceController;

class Users extends ResourceController
{
    public function index()
    {
        return $this->respond([
            'status' => true
        ]);
    }
}
</pre></code>

## 47. JSON response kaise return karenge?
<code><pre>
return $this->response->setJSON([
    'status' => true,
    'message' => 'Success'
]);
</pre></code>

# <u>`Security`</u> 🔥🔥
## 48. CSRF kya hai?
- **Cross-Site Request Forgery**
- Attacker authenticated user se unwanted request perform karwane ki koshish karta hai.
- Form me: **`<?= csrf_field() ?>`**
- CI4 me CSRF protection configure/enable ki ja sakti hai.

## 49. XSS kya hai?

- **`Cross-Site Scripting`**
- Malicious script user input ke through page me inject ho sakti hai.
- Output escape karein: **`<?= esc($name) ?>`**

## 50. SQL Injection se kaise protect karenge?

- Query Builder, Model aur parameter binding use karein.

**`Bad:`**

- **`$sql = "SELECT * FROM users WHERE id = $id";`**

**`Better:`**

**`$model->find($id);`**

**`Ya bindings:`**
<code><pre>
$db->query(
    'SELECT * FROM users WHERE id = ?',
    [$id]
);
</pre></code>

# <u>`Important CI4 Questions`</u>

## 51. `.env` file kya hai?

- Environment-specific configuration ke liye.

**`Example:`**

<code><pre>
database.default.hostname = localhost
database.default.database = my_database
database.default.username = root
database.default.password =
</pre></code>

- Secrets ko Git repository me commit nahi karna chahiye.

## 52. Spark kya hai?

- CI4 ka command-line tool.
<code><pre>
php spark serve
php spark routes
php spark migrate
php spark make:controller Users
php spark make:model UserModel
</pre></code>

## 53. `BaseController` kya hai?

- Application ke controllers ke liye common base controller hai.
- Common helpers/services/properties initialize ki ja sakti hain.

## 54. Helper kya hai?

- Reusable procedural functions ka collection.
- Load: **`helper('url');`**
- Multiple: **`helper(['url', 'form']);`**

## 55. base_url() vs site_url()?

- **`base_url()`** generally assets/resources ke base URL banane me useful:

**`base_url('assets/css/style.css');`**
- **`site_url()`** application routes/pages ke URLs banane me useful:

 **`site_url('users')`**

## 56. Redirect kaise?
 - **`return redirect()->to('/users');`**
 - Previous page: **`return redirect()->back();`**

## 57. Named routes kya hain?

- Route ko name de sakte hain:
<code><pre>
$routes->get(
    'users',
    'UserController::index',
    ['as' => 'users']
);

</pre></code>

## 58. Route parameters?
<code><pre>
$routes->get(
    'user/(:num)',
    'UserController::show/$1'
);
</pre></code>

**`Controller:`**

<code><pre>
public function show($id)
{
    // ...
}
</pre></code>

## 59. Route group?
<code><pre>
$routes->group('admin', function ($routes) {

    $routes->get(
        'users',
        'Admin\UserController::index'
    );

});
</pre></code>

- URL **`/admin/users`**

## 60. Auto Routing kya hai?

- Routes automatically controller methods se resolve ho sakte hain. Production applications me explicit routes generally better hote hain because routing behavior aur allowed HTTP methods clear/control me rehte hain.

## Rapid-Fire Interview Questions

- Inke one-line answers yaad hone chahiye:

**62. CI4 kis language me hai? → `PHP`**

**63. MVC? → `Model View Controller`**

**64. CLI tool? → `Spark`**

**65. Routes file? → `app/Config/Routes.php`**

**66. Models folder? → `app/Models`**

**67. Views folder? → `app/Views`**

**68. Controllers folder? → `app/Controllers`**

**69. Database config? → `.env` / `app/Config/Database.php`**

**70. Validation? → `$this->validate()`**

**71. Session access? → `session()`**

**72. Password encryption/hash? → `password_hash()`**

**73. Password checking? → `password_verify()`**

**74. Output escaping? → `esc()`**

**75. CSRF form field? → `csrf_field()`**

**76. All records? →` findAll()`**

**77. One record? → `find()` / `first()`**

**78. Insert? → `insert()`**

**79. Update? → `update()`**

**80. Delete? → `delete()`**
