# Rangkuman Week 7

## React Context

### Apa itu Context API

Context API merupakan sebuah cara untuk membuat global state yang nanti bisa digunakan di semua level komponen tanpa harus mengirim props ke lower level component secara manual. Context API ini merupakan alternatif dari props drilling. Props drilling sendiri adalah cara mempassing props dari grandparent ke parent ke child ke grandchild dan seterusnya.

### Kapan harus menggunakan Context

Jika ingin membangun aplikasi dengan membutuhkan data dalam skala besar, maka tidak disarankan untuk menggunakan context.
Context ini biasanya digunakan untuk aplikasi yang hanya berskala kecil hingga menengah, jika aplikasi membutuhkan data dalam
skala besar maka disarankan menggunakan redux.

### Penggunaan React Context

**Struktur Awal**
App.jsx

```js
import { useContext } from "react";
import Keranjang from "./components/Keranjang";
import ListProduct from "./components/ListProduct";
import SummaryPembelian from "./components/SummaryPembelian";

function App() {
  const { user } = useContext(UserContext);

  return (
    <div className="App">
      <Keranjang />
      <br />

      <ListProduct />
      <SummaryPembelian />
    </div>
  );
}

export default App;
```

KeranjangCountProvider.jsx

```js
import React, { createContext, useState } from "react";

export const KeranjangCountContext = createContext();

function KeranjangCountProvider({ children }) {
  const [keranjangCount, setKeranjangCount] = useState(0);

  return (
    <KeranjangCountContext.Provider
      value={{ keranjangCount, setKeranjangCount }}
    >
      {children}
    </KeranjangCountContext.Provider>
  );
}

export default KeranjangCountProvider;
```

Kita dapat membuat sebuah context baru dengan menggunakan perintah `createContext()`,
kemudian jangan lupa untuk di import terlebih dahulu dan juga jangan lupa memberikan `.Provider`.

Counter.jsx

```js
import React, { useContext, useState } from "react";
import { KeranjangCountContext } from "../KeranjangCountProvider";

function Counter() {
  const { keranjangCount, setKeranjangCount } = useContext(
    KeranjangCountContext
  );
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
    setKeranjangCount(keranjangCount + 1);
  };

  const decrement = () => {
    setCount(count - 1);
    setKeranjangCount(keranjangCount - 1);
  };

  return (
    <>
      <button onClick={decrement}>-</button>
      <span>{count}</span>
      <button onClick={increment}>+</button>
    </>
  );
}

export default Counter;
```

Disini kita menggunakan context yang tadi sudah dibuat `KeranjangCountContext`.
Pada file Counter.jsx ini kita akan melakukan proses increment dan decrement,
untuk penggunaan context nya dengan `useContext`

Keranjang.jsx

```js
import React, { useContext } from "react";
import { KeranjangCountContext } from "../KeranjangCountProvider";

function Keranjang() {
  const stateKeranjang = useContext(KeranjangCountContext);
  const totalKeranjang = stateKeranjang.keranjangCount;

  // console.log(tes)

  return (
    <div>
      <span>Keranjang</span>
      <span> {totalKeranjang}</span>
    </div>
  );
}

export default Keranjang;
```

ListProduct.jsx

```js
import React, { useState } from "react";
import Counter from "./Counter";

function ListProduct() {
  const [products, setProducts] = useState([
    { id: 1, nama: "buku" },
    { id: 2, nama: "pulpen" },
  ]);

  return (
    <div>
      {products.map((item) => (
        <div key={item.id}>
          <span>{item.nama}</span>
          <Counter />
        </div>
      ))}
    </div>
  );
}

export default ListProduct;
```

SummaryPembelian.jsx

```js
import React, { useContext } from "react";
import { KeranjangCountContext } from "../KeranjangCountProvider";

function SummaryPembelian() {
  const { keranjangCount } = useContext(KeranjangCountContext);

  return (
    <div>
      <h1>Summary Pembelian</h1>

      <h2>jumlah barang yg dibeli ada {keranjangCount}</h2>
    </div>
  );
}

export default SummaryPembelian;
```

## React Testing

### Unit Testing

Unit testing merupakan salah satu metode testing terhadap fungsi ataupun usecase yang ada pada aplikasi kita. Dengan dilakukannya unit test ini, akan mudah bagi kita menentukan apakah fungsi tersebut sudah sesuai dengan apa yang diharapkan. Karena kita menguji sebuah fungsi satu persatu maka, fungsi yang kita test tidak akan menyenggol fungsi lainnya, sehingga hal ini akan mempermudah kita dalam melakukan debugging.

**Keuntungan melakukan Unit Test**

- Lebih mudah dalam mencari bug
- Meningkatkan kemampuan re-usable kode
- Waktu dalam pengujian relatif singkat

### Unit Testing with Jest

Jest merupakan sebuah framework testing yang dikembangkan oleh Facebook. Framework ini khusus dikembangkan untuk melakukan unit testing pada javascript, sehingga tidak hanya React.js yang dapat menggunakan Jest, namun framework lain seperti Angular.js dan Vue.js juga dapat menggunakan Jest untuk melakukan unit testing.

**Keuntungan menggunakan Jest untuk Testing**

- Konfigurasi pada Jest cukup mudah
- Adanya fitur snapshot testing, dimana fitur ini memungkinkan kita untuk melakukan suatu perbandingan terhadap hasil render suatu komponen yang baru, dengan hasil render yang lama.

### Penggunaan Jest

Untuk menggunakan Jest pada aplikasi kita, kita terlebih dahulu memasukan library Jest ke dalam proyek kita

```js
npm install --save-dev jest
```

Kita akan membuat fungsi penjumlahan sederhana untuk nantinya akan dicoba testing menggunakan jest.

```js
export const jumlahkan = (x, y) => {
  return x + y;
};
```

Fungsi tersebut menambahkan nilai dari parameter x dan y yang nanti hasilnya akan kita cek apakah fungsi sudah berjalan dengan benar. Selanjutnya untuk melakukan sebuah testing, kita harus membuat sebuah file baru, yang biasanya memiliki format nama sama dengan nama file yang akan diuji, contohnya kita akan menguji Calculator.js maka kita akan membuat sebuah file dengan nama Calculator.test.js

```js
import {fungsiTambah} from ‘./Calculator’

test("Unit Test Penjumlahan", () => {
const nilai = jumlahkan(2,3)
expect(nilai).toEqual(2+3);
})
```
