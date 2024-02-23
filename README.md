# Jobsheet 2
> Nama: Fahridana Ahmad Rayyansyah <br/>
> Absen: 11 <br/>
> Kelas: TI-2F

## Praktikum 1 : Basic Routing
1. **Route /hello**
    ```php
    Route::get('/hello', function () {
        return 'Hello World';
    });
    ```
    > ![hello](screenshot/01.png)
   > 
   > dalam file web.php, kita membuat sebuah route untuk /hello yang akan mereturn "Hello World", 
   > jadi jika mengakses /hello akan memunculkan tulisan "Hello World"
2. **Route /world**
    ```php
    Route::get('/world', function () {
        return 'World';
    });
    ```
    > ![world](screenshot/02.png)
   > 
   > Hal yang sama juga terjadi di sini, sama seperti /hello diatas, kita membuat untuk /world, 
   > jadi jika kita mengakses /world akan menampilkan "World"
3. **Route /**
    ```php
    Route::get('/', function () {
        return 'Selamat Datang';
    });
    ```
    > ![home](screenshot/03.png)
4. **Route /about**
    ```php
    Route::get('/about', function () {
        return '2241720158-Fahridana Ahmad Rayyansyah';
    });
    ```
    > ![about](screenshot/04.png)


## Praktikum 2 : Route Parameter
1. **Route /user/fahri**
    ```php
    Route::get('/user/{name}', function ($name) {
        return 'Nama saya '.$name;
    });
    ``` 
    > ![fahri](screenshot/05.png)
   > 
   > disini terdapat parameter untuk $name jadi content yang ada 
   > di web akan berubah sesuai dengan parameter yang ada di url
2. **Route /user**
    > ![user](screenshot/06.png)
   >
   > terjadi 404 not found karena memang belum dibuat routing untuk /user,
   > kita membuat untuk /user/{name} namun tidak membuat /user sehingga
   > jika memuat /user akan terjadi 404 not found
   > 
3. **Route /posts/1/comments/5**
    ```php
    Route::get('/posts/{post}/comments/{comment}', function($postId, $commentId) {
        return 'Pos ke-'.$postId." Komentar ke-: ".$commentId;
    });
    ```
    > ![posts](screenshot/07.png)
   > 
   > sama seperti no 1, content akan berubah sesuai dengan url yang diketikkan
   > disini post = 1 dan comment = 5, maka akan menampilkan 
   > "Pos ke-1 Komentar ke-: 5", semisal post dan commentnya berubah
   > maka angka pos dan komentar di comment juga akan berubah

4. **Route articles/1**
    ```php
    Route::get('/articles/{id}', function($id) {
        return 'Halaman Artikel dengan ID ' . $id;
   })
    ```
    > ![article](screenshot/08.png)

## Praktikum 3 : Optional Parameter
1. **Route /user**
    ```php
    Route::get('/user/{name?}', function ($name=null) {
        return 'Nama saya '.$name;
    });
    ```
   > ![user](screenshot/09.png)
   >
   > Pada kode diatas terdapat optional parameter, dimana tidak wajib untuk menambahkan
sebuah parameter, jadi gambar diatas dengan route /user saja tidak masalah, karena $name
   jika tidak diisi nilainya otomatis secara default akan null

2. **Route /user/Fahri**
   > ![fahri](screenshot/05.png)
   >
   > Pada gambar diatas kodenya sama dengan no 1, namun pada url ditambahkan /Fahri,
   > dimana itu akan memberikan parameter ke dalam routenya, sehingga terdapat Fahri
   > di dalam page tersebut

3. **Route /user**
    ```php
    Route::get('/user/{name?}', function ($name='John') {
        return 'Nama saya '.$name;  
    });
    ```
   > ![user](screenshot/10.png)
   > 
   > Pada kode diatas kita menambahkan nilai default pada name bernilai John, jadi ketika
   > nilai name tidak diisi, otomatis variabel name akan menjadi John


## Praktikum 4 : Membuat Controller
1. **WelcomeController class**
    ```php
    <?php
    namespace App\Http\Controllers;
    use Illuminate\Http\Request;
   
    class WelcomeController extends Controller{
        public function hello() {
            return 'Hello World';
        }
    }
    ```
   **web.php**
    ```php
   use App\Http\Controllers\WelcomeController;
   
    Route::get(‘/hello’, [WelcomeController::class,’hello’]);
    ```
   **Route /hello**
    > ![hello](screenshot/01.png)
   > 
   > Pertama kita membuat sebuah class WelcomeController.php dimana merupakan sebuah child
   > dari Controller, di dalam class tersebut kita buat sebuah function hello() yang akan
   > mengembalikan nilai 'Hello World'. Pada web.php kita memanggil class tersebut, lalu 
   > kita mengatur route /hello agar ketika user membuka /hello akan memanggil function
   > hello() yang ada di class WelcomeController.php

2. **HomeController class**
    ```php
    <?php
    namespace App\Http\Controllers;
    use Illuminate\Http\Request;
    
    class HomeController extends Controller{
        public function index() {   
            return 'Selamat Datang';
        }
    }
    ```
   **Route /**
   > ![home](screenshot/03.png)

3. **AboutController class**
    ```php
    <?php
    namespace App\Http\Controllers;
    use Illuminate\Http\Request;
    
    class AboutController extends Controller {
        public function about() {
            return '2241720158-Fahridana Ahmad Rayyansyah';
        }
    }
    ```
   **Route /about**
   > ![home](screenshot/04.png)

4. **AboutController class**
    ```php
    <?php
    namespace App\Http\Controllers;
    use Illuminate\Http\Request;
    
    class ArticleController extends Controller {
        public function articles($articleId) {
            return 'Halaman Artikel dengan ID '.$articleId;
        }
    }
    ```
   **Route /articles/1**
   > ![home](screenshot/08.png)
 

## Praktikum 5 : Resource Controller
1. **PhotoController class**
    ```php
    <?php
    
    namespace App\Http\Controllers;
    
    use Illuminate\Http\Request;
    
    class PhotoController extends Controller
    {
        /**
         * Display a listing of the resource.
         */
        public function index()
        {
            //
        }
    
        /**
         * Show the form for creating a new resource.
         */
        public function create()
        {
            //
        }
    
        /**
         * Store a newly created resource in storage.
         */
        public function store(Request $request)
        {
            //
        }
    
        /**
         * Display the specified resource.
         */
        public function show(string $id)
        {
            //
        }
    
        /**
         * Show the form for editing the specified resource.
         */
        public function edit(string $id)
        {
            //
        }
    
        /**
         * Update the specified resource in storage.
         */
        public function update(Request $request, string $id)
        {
            //
        }
    
        /**
         * Remove the specified resource from storage.
         */
        public function destroy(string $id)
        {
            //
        }
    }
    ```
   **web.php**
    ```php
   use App\Http\Controllers\PhotoController;
   
    Route::resource('photos', PhotoController::class)->only([
        'index', 'show'
    ]);
   
    Route::resource('photos', PhotoController::class)->except([
        'create', 'store', 'update', 'destroy'
    ]);
    ```
   **list route**
    > ![home](screenshot/11.png)
