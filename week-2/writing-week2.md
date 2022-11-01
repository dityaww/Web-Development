# Rangkuman Week 2

## Javascript Dasar

- ### Definisi & Peran

  JavaScript adalah bahasa pemrograman populer yang digunakan untuk membuat situs dengan konten website yang dinamis. JavaScript biasanya dikolaborasikan dengan HTML dan CSS. Di mana HTML digunakan untuk membuat struktur website dan CSS untuk merancang style halaman website. Lalu, JavaScript berperan menambahkan elemen interaktif.

- ### Penggunaan

  Cara menggunakan javascript yaitu dengan membuat sebuah file javascript kemudian dihubungkan dengan file html yang sudah dibuat, cara menghubungkan nya bisa lewat tag head/body pada html, dengan memberikan tag script lalu dihubungkan dengan file javascript yang sudah dibuat.

- ### Tipe Data

  Macam-macam tipe data pada javascript :

  - **Null**
    Pada tipe data ini variabel sudah dideklarasi tapi tidak ada value/nilainya
  - **Undifined**
    Pada tipe data ini variabel sudah dideklarasikan tetapi belum dipanggil variabel tersebut
  - **Number**
    Tipe data ini berisikan nilai yang berupa angka
  - **String**
    Tipe data ini berisikan nilai yang berupa string/karakter
  - **Boolean**
    Tipe data ini memberikan dua nilai yaitu **true** atau **false**

- ### Operator

  Macam-macam operator pada javascript :

  - **Operator Aritmatika**
    Operator aritmatika merupakan operator untuk melakukan operasi aritmatika seperti penjumlahan, pengurangan, pembagian, perkalian, dsb.
    ```javascript
    let a = 10;
    let b = 20;
    let result = a + b;
    console.log(result);
    ```
  - **Operator Perbandingan**
    Operator yang digunakan untuk membandingkan dua nilai. operator ini akan menghasilkan nilai boolean `true` atau `false`
    ```javascript
    let a = 20;
    let b = 20;
    let result = a == b;
    // true
    ```
  - **Operator Assignment**
    Operator yang digunakan untuk memberikan tugas kepada variabel. Biasanya digunakan untuk mengisi variabel. misal nya memberikan tanda `=` untuk memberikan value pada varibel yang sudah dideklarasikan.
    ```javascript
    let a = "Hello guys";
    ```
  - **Operator Logika**
    Operator logika digunakan untuk melakukan operasi terhadap dua nilai `boolean`
    ```javascript
    AND (&&)
    OR (||)
    NEGATION (!)
    ```
  - **Operator Bitwise**
    Operator bitwise merupakan operator yang digunakan untuk operasi berdasarkan bit (biner).
  - **Operator Ternary**
    Operator ternary biasanya digunakan untuk membuat conditional dengan cara yang lebih ringkas dan efisien
    Untuk bentuknya seperti ini :
    ```javascript
    <kodisi> ? "benar" : "salah"
    ```

- ### Conditional

  Conditional merupakan statement percabangan yang menggambarkan suatu kondisi. Conditional statement akan mengecek kondisi spesifik dan menjalankan perintah berdasarkan kondisi tersebut, yang dicek adalah yang bernilai true, jika true maka kondisi tersebut akan dijalankan jika tidak akan lanjut ke kondisi lainnya.

  **Contoh Conditional**

  - **If Else Statement**

    ```javascript
    let a = 12;
    if (a == 12) {
      console.log("ini angka 12");
    } else {
      console.log("ini bukan angka 12");
    }
    ```

    **Penjelasan**
    Disini akan dicek dahulu jika nilai a = 12 , maka kondisi tersebut akan dijalankan, jika a tidak sama dengan 12 maka akan dijalankan kondisi yang lain.

  - **Switch Case**
    Switch Case digunakan apabila kondisi dan percabangan nya terlalu banyak
    ```javascript
    let x = 0;
    switch (x) {
      case 0:
        console.log("Ini angka 0");
        break;
      default:
        console.log("Bukan angka 0");
    }
    ```

- ### Scope & Function

  - #### Scope

    Scope adalah konsep dalam flow data variabel. Menentukan suatu variabel bisa diakses pada scope tertentu atau tidak

    - **Global Scope**
      Global scope berarti variabel yang kita buat dapat diakses dimanapun dalam suatu file. Agar menjadi Global Scope, suatu variabel harus dideklarasikan diluar Blocks. Blocks adalah code yang berada didalam curly braces `{}`

      ```javascript
      let name = "Aditya";
      function Myname() {
        return name;
      }

      console.log(name);
      ```

    - **Local Scope**
      Local scope berarti kita mendeklarasikan variabel didalam blocks seperti function, conditional, dan looping. Maka variabel hanya bisa diakses didalam blocks saja.

      ```javascript
      function Myname() {
        let name = "Aditya";
        return name;
      }

      console.log(name);
      // error
      ```

    - #### Function

      Function adalah sebuah blok kode dalam sebuah grup untuk menyelesaikan 1 task/1 fitur. Function memiliki kelebihan yaitu dapat digunakan berulang kali.

      ```javascript
      // deklarasi fungsi
      function sayHello() {
        console.log("Hello World");
      }

      // cara panggil
      sayHello();
      ```

      **Parameter Function**
      Dengan parameter, function dapat menerima sebuah inputan data dan menggunakannya untuk melakukan task/tugas. Misal kita membuat function dengan 2 parameter, maka kita harus memberikan 2 nilai pada function tersebut.

      ```javascript
      function jumlahkan(a, b) {
        return a + b;
      }

      // panggil function
      console.log(jumlahkan(5, 10));
      ```

      **Penulisan function**

      ```javascript
      // function biasa
      function jumlah(a, b) {
        return a + b;
      }

      // arrow function
      let jumlah = (a, b) => {
        return a + b;
      };
      ```

- ### DOM (Document Object Model)

  Javascript DOM (Document Object Model) adalah interface yang memungkinkan developer untuk memanipulasi konten, struktur, dan style situs web.
  **Akses Elemen dengan DOM**

  - **GetElemenById()**
    Memilih elemen berdasarkan atribut `id`
  - **GetElemenName()**
    Memilih elemen berdasarkan atribut `name`
  - **GetElemenClassName()**
    Memilih elemen berdasarkan atribut `class`
  - **GetElemenTagName()**
    Memilih elemen berdasarkan nama `Tag`
  - **QuerySelector()**
    Memilih elemen berdasarkan `query`
  - **QuerySelectorAll()**
    Memilih elemen berdasarkan `query`

  **Mengubah Konten Elemen**

  - Elemen.innerHTML
    Dengan menggunakan innerHTML kita dapat memanipulasi elemen yang sudah kita seleksi dengan DOM dan dapat menyisipkan script HTML
  - Elemen.innerText
    Dengan innerText kita hanya bisa memanipulasi elemen HTML berupa string saja.

  **Membuat Elemen HTML**
  Dengan menggunakan DOM kita juga dapat membuat elemen pada HTML

  ```javascript
  // skrip HTML
  <div id="header"></div>
  ```

  ```javascript
  // skrip js
  let header = document.GetElementById("header");

  const headertitle = document.createElement("h1");
  headertitle.textContent = "Ini Heading 1";

  header.append(headertitle);
  ```

  **DOM Event Listener**
  Macam-macam event :

  - click
    Event untuk memberikan interaksi kepada user dengan klik suatu elemen

    ```javascript
    let btn = document.getElementById('mybtn')

    btn.addEventListener(“click”, function() {
      alert("Hello")
    })
    ```

  - blur
    Event di mana sebuah element kehilangan fokus dari user (misal user klk mouse di luar element tersebut atau user klik tab untuk berpindah element

    ```javascript
    const input = document.getElementById(“username”)

    input.addEventListener(“blur”, () => {
      if(input.value.length < 6) alert(“Panjang username minimal 6”)
    })
    ```

  - form submission
    Event yang digunakan pada suatu form untuk mengambil data inputan atau untuk memberikan form validation

    ```javascript
    const form = document.getElementById(“form”)

    form.addEventListener(“submit”, function(event) {

        // preventDefault untuk mencegah agar page tidak refresh
        event.preventDefault()

        const formData = new FormData(form)
        const values = Object.fromEntries(formData) // { email: ... }
    })

    ```
