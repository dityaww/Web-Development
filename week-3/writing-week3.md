# Rangkuman Week 3

## Javascript Lanjutan

- ### Array & Multidimensional Array

  Array adalah tipe data list order yang dapat menyimpan tipe data apapun di dalamnya, Array biasanya dideklarasikan dengan bentuk `[]`. Array dapat menyimpan tipe data String, Number, Boolean, dan lainnya.
  **Contoh Array**

  ```
  let buah = [
      'anggur',
      'melon',
      'semangka',
      'rambutan'
  ]
  console.log(buah)
  ```

  **Cara Akses Array**
  Kita dapat mengambil/mengakses data pada suatu array dengan menggunakan index, Array biasanya dimulai dengan index 0. contohnya pada array di atas ini, jika kita ingin mengambil data `semangka` pada array `buah`, cara aksesnya yaitu `console.log(buah[2])`
  **Manipulasi Array**
  Kita dapat memanipulasi/mengubah suatu array, seperti menghapus data array, menambahkan data array, dan lainnya.
  contoh :

  ```
  let minuman = ['kopi', 'teh']

  // ubah nilai pada index ke-0
  minuman[0] = 'jus jambu'

  console.log(minuman)
  ```

  **Array Properties**
  Array memiliki 5 properti yang sering digunakan yaitu constructor, length, index, input, dan prototype. Properties adalah fitur yang sudah disediakan oleh Javascript untuk memudahkan developer. Ada banyak properties yang sudah tersedia pada javascript. contohnya `length`

  ```
  let minuman = ['kopi', 'teh']

  // cek panjang array
  console.log(minuman)
  ```

  **Array Method**
  Array memiliki method atau biasa disebut built-in methods. Artinya Javascript sudah memudahkan kita dengan menyediakan function/method umum yang bisa kita gunakan. Kita tidak perlu membuat function lagi jika method yang kita butuhkan sudah tersedia.
  contoh :

  - **push()**
    untuk menambahkan data array pada elemen terakhir
  - **pop()**  
    untuk menghapus data array pada elemen terakhir
  - **unshift()**
    menambahkan item array pada index pertama
  - **shift()**  
    menghapus item array pada index pertama
  - **sort()**
    untuk mengurutkan data secara ascending/descending

  **Array Looping**
  Array memiliki built in methods untuk melakukan looping yaitu .map() dan .forEach()

  - **ForEach**
    method untuk melakukan looping pada setiap elemen array.
    contoh :
    ```
    let motor = ['yamaha', 'suzuki']
    motor.forEach((res) => {
        console.log(res)
    })
    ```
  - **Map**  
    melakukan perulangan/looping dengan membuat array baru.
    contoh :

    ```
    let motor = ['yamaha', 'suzuki']

    let duplicate = motor.map(res => {
        return res
    })
    console.log(res)
    ```

    Kita bisa lihat bahwa **.map()** dan **forEach()** sama-sama melakukan looping dan mengembalikan nilai baru dari operasi yang dilakukan, Perbedaannya adalah `.forEach` tidak dapat membuat Array baru dari hasil operasi yang ada dalam looping Lalu dari segi performance juga sangat jauh.

    Jadi, gunakan `.forEach()` jika hanya memerlukan looping untuk menampilkan saja atau menyimpan ke database. Gunakan `.map()` jika akan melakukan operasi pada array seperti yang dapat mengubah nilai array sebelumnya.

  **Multidimensional Array**
  Mutidimensional Array yaitu `terdapat array didalam array`  
  contoh :

  ```
  let cloth = [
    ['hoodie', 10],
    ['crewneck', 20],
    ['jacket', 15],
  ]

  // Cara Akses
  console.log(cloth[1][0])
  // output : crewneck
  ```

  Sama seperti array satu dimensi, multidimensional array juga dapat menggunakan Property dan Method built-in Array.

- ### Object

  - **Apa itu object?**
    Object adalah sebuah tipe data pada variabel yang menyimpan properti dan fungsi (method).
    Properti adalah data lengkap dari sebuah object. Method adalah action dari sebuah object. Apa saja yang dapat dilakukan dari suatu object. Object sama seperti tipe data yang lain, kita bisa assign value pada object ke dalam suatu variabel.
    contoh :

    ```
    let mahasiswa = {
        nama : 'Aditya Widyatmoko'
        nim : 12739
        jurusan : 'Teknik Informatika'
    }

    // akses seluruh objek
    console.log(mahasiswa)

    // akses nama
    // cara 1
    console.log(mahasiswa.nama)
    // cara 2
    console.log(mahasiswa['nama'])
    ```

    Sama seperti array, didalam object kita dapat menyimpan properti dengan tipe data apapun.

  - **Update data object**
    Kita dapat melakukan update pada variabel dengan tipe data Object.
    contoh :

    ```
    let mahasiswa = {
        nama : 'Aditya Widyatmoko',
        nim : 12739,
        jurusan : 'Teknik Informatika'
    }
    // ubah nim
    mahasiswa.nim = 127419

    // ubah jurusan
    mahasiswa.jurusan = 'DKV'

    console.log(mahasiswa)
    ```

    Selain itu kita juga bisa menghapus suatu data pada sebuah object menggunakan delete operator, misal kita ingin hapus data `nim` pada object `mahasiswa`, maka gunakan `delete mahasiswa.nim`

  - **Method**
    Jika value yang kita masukkan pada property berupa function. Maka itu disebut method. Di dalam object kita bisa memberikan suatu function
    ```
    const greeting = {
        welcome : () => {
            return 'helo world'
        }
    }
    console.log(greeting.welcome)
    ```
  - **Nested Object**
    Terdapat Objek di dalam objek.
    contoh :
    ```
    let buku = {
        judul: 'Helo Dunia',
        desc: 'this is description',
        author: {
           people:{
            nama: 'Aditya',
            umur: 20,
            city: 'Magelang'
           }
        }
    }
    ```
  - **Looping Object**
    Jika kita ingin menampilkan seluruh object properti. Kita bisa menggunakan looping. Jadi tidak perlu mengakses secara manual memanggil setiap propertinya.
    ```
    for(let key in object){
        // code
    }
    ```
  - **Array of Object**
    Object sama seperti Array yang bisa menyimpan banyak data. Kita dapat menggunakan array of object untuk data yang lebih dari satu.
    contoh :
    ```
    let siswa = [
        {
            nama: 'Aditya',
            umur: 20,
            kota: 'Magelang'
        },
        {
            nama: 'Dewa',
            umur: 16,
            kota: 'Magelang'
        },
    ]
    ```

- ### Rekursif

  Recursive adalah function yang memanggil dirinya sendiri sampai kondisi tertentu. Recursive kebanyakan digunakan untuk case matematika, fisika, kimia, dan yang berhubungan dengan calculation. Recursive biasanya memiliki base case dimana akan selalu terjadi perulangan jika base case belum terpenuhi.

  ```
  function rekursif(){
    if(condition){
        // base case
    } else{
        // recursive
    }
  }
  ```

  **Ciri Rekursif**

  - Fungsi rekursif selalu memiliki kondisi yang menyatakan kapan fungsi tersebut berhenti.
  - Fungsi rekursif selalu memanggil dirinya sendiri sambil mengurangi atau memecahkan data masukan setiap panggilannya.

  **Contoh kasus rekursif**

  ```
  // Hitung Faktorial

  function rekursif(x){
      if(x==1){
          return 1
      }else {
          return x * rekursif(x-1)
      }
  }
  ```

- ### Web Storage

  Web storage adalah salah satu Web API yang dapat menyimpan data secara lokal pada sisi client. Berbeda dengan objek atau array, data yang disimpan pada objek atau array JavaScript bersifat sementara, dan akan hilang jika terjadi reload atau pergantian URL pada browser. Sedangkan data yang disimpan pada Web Storage akan bertahan lebih lama karena data akan disimpan pada storage browser.
  Untuk menyimpan dan mengakses data pada storage, metode yang digunakan adalah key-value. Di sini key menjadi sebuah kunci untuk mengakses data pada storage.

  ```
  // create data
  let key = 'Item 1';
  localStorage.setItem(key, 'Value');

  // get data
  let myItem = localStorage.getItem(key);

  // delete data
  localStorage.removeItem(key);

  ```

- ### Asynchronous

  Proses asynchronous sering digunakan untuk komunikasi data, karena data menjadi bagian inti dari sebuah aplikasi maka konsep asynchronous sangat penting untuk dipahami.
  Selain termasuk Interpreted Language dan Dynamic-Typed Language, JavaScript juga termasuk Single Threaded Programming Language. Yaitu JavaScript hanya bisa melakukan satu operasi di satu waktu. Pada konsep `asynchronous`, code akan dieksekusi tanpa menunggu eksekusi code lain selesai sehingga seakan-akan dieksekusi secara bersamaan.
  Ada 3 teknik untuk menghandle proses asynchronous :

  - **Callback**
    Callback adalah function yang menjadi argument untuk function lain dan akan dieksekusi pada poin tertentu, bisa jadi saat ini atau nanti.

  ```
  const notify = () => {
  console.log('Download complete!');
  };

  const download = (url, callback) => {
  console.log(`Downloading from ${url}....`);

  callback();
  };

  const url = 'https://brachio.site/download';
  download(url, notify);
  ```

  - **Promise**
    Promise bisa dikatakan sebagai object yang menyimpan hasil dari sebuah operasi asynchronous baik itu hasil yang diinginkan (resolved value) atau alasan kenapa operasi itu gagal (failure reason).
    Ada 3 kondisi pada promise :

    - pending, operasi sedang berlangsung
    - fulfilled, operasi selesai dan berhasil
    - rejected, operasi selesai namun gagal

    ```
    let progress = 100;

        const download = new Promise((resolve, reject) => {
        if (progress === 100) {
            resolve('Download complete');
        } else {
            reject('Download failed');
        }
        });

        download
        .then((result) => {
            console.log(result); // Download complete
        })
        .catch((error) => {
            console.log(error); // Download failed atau tidak ditampilkan jika tidak ada error
        });
    ```

  - **Async Await**
    untuk menghandle operasi asynchronous dengan syntax yang lebih mirip dengan synchronous.

    ```
        const getStatus = (url) => {
        console.log(`Downloading from ${url}...`);

        return new Promise((resolve, reject) => {
            setTimeout(() => {
            resolve('Download Complete');
            }, 3000);
        });
        };

        async function download(url) {
        let status = await getStatus(url); // tunggu sampai promise selesai
        console.log(status);
        }

        const url = 'https://brachio.site/download';

        download(url);
    ```
