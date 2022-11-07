# Rangkuman Week 6

## React Lanjutan

### React JS Hooks

#### Apa itu Hooks?

Hooks merupakan fitur baru di React 16.8. Fitur ini memungkinkan Anda menggunakan state dan fitur React lainnya tanpa menuliskan sebuah kelas. Hook adalah fungsi spesial yang memungkinkan Anda “terhubung” dengan fitur-fitur di React. Sebagai contoh, useState adalah sebuah Hook yang memungkinkan Anda memberi state pada function components.
React Hooks diperkenalkan oleh React Team untuk melakukan state management dan side effects di dalam function component. Dengan Hooks kita bisa menggunakan state dan lifecycle methods tanpa harus menulis class di React.

#### Cara menggunakan React Hooks

**Menggunakan UseState**

```js
import React, { useState } from "react";

function ListUser() {
  // Deklarasi variabel state baru yang kita sebut "count"
  const [user, setUser] = useState("Aldi");

  return (
    <div>
      <h1>Nama anda adalah {user}</h1>
    </div>
  );
}
```

useState adalah sebuah Hook, dan akan mengembalikan nilai dari state dan fungsi yang bisa kita gunakan untuk mengubah nilai tersebut. Fungsi `setName` disini mirip dengan cara kerja `this.setState`. Berbeda dengan this.state, state di dalam useState tidak harus berbentuk object. Dan kita bisa menggunakan lebih dari satu useState di dalam satu component. Seperti contoh diatas, untuk menggunakan useState kita harus melakukan import `useState` dari react, kemudian kita deklarasikan state yang akan kita buat. Dengan menggunakan state data nya bersifat dinamis dan dapat diubah, untuk mengubah data pada useState kita menggunakan `setUser` untuk mengubahnya, seperti contoh diatas. Untuk memanggil state yang sudah kita buat agarbisa tamppil cukup mudah, kita hanya perlu memanggil variable staete yang sudah kita buat, seperti pada contoh diatas, kita hanya cukup memanggil variable `user` dengan menggunakan curly braces `{user}`.

**Menggunakan UseEffect**
useEffect, menambahkan kemampuan untuk melakukan `side-effect/efek samping` dari sebuah function component. Hook ini memiliki fungsi yang sama dengan componentDidMount, componentDidUpdate, dan componentWillUnmount pada kelas React, tetapi disatukan menjadi satu API.

```js
import React, { useState, useEffect } from "react";

function CountNumber() {
  const [count, setCount] = useState(0);

  // Sama seperti componentDidMount dan componentDidUpdate:
  useEffect(() => {
    // Memperbarui judul dokumen menggunakan API browser
    document.title = `Anda klik sebanyak ${count} kali`;
  });

  return (
    <div>
      <p>Anda klik sebanyak {count} kali</p>
      <button onClick={() => setCount(count + 1)}>Click</button>
    </div>
  );
}
```

Pada saat memanggil useEffect, Anda memerintah React untuk menjalankan fungsi yang akan memberikan `efek-samping` setelah membersihkan perubahan pada DOM. Efek dideklarasikan di dalam komponen sehingga mereka akan mendapat akses pada prop dan state komponen tersebut. Nantinya, apa yang sudah kita tuliskan didalam useEffect akan dijalankan setiap component baru akan dimount `componentDidMount`, terjadi perubahan `componenDidUpdate`, dan pada saat component akan ditinggalkan `componentWillUnmount`.

Seperti pada contoh diatas, biasanya useEffect berada dibawah useState. Agar dapat menggunakan useEffect kita harus melakukan import `useEffect` terlebih dahulu sebelum menggunakannya, untuk contoh kode nya diatas ini. Disini kita menggunakan useEffect untuk melakukan perubahan data yang ada pada state yang sudah dideklarasikan di atas ini, untuk useState nya memiliki nilai awalnya 0, kemudian kita melakukan trigger perubahan data pada button dan di set untuk perubahan datanya.

#### Prop-Types

PropTypes merupakan library untuk menvalidasi props. Pada React JS kita dapat mengirimkan sebuah data dalam bentuk (tipe data) apapun sebagai props. Misalkan kita ingin data yang akan kita kirim harus bertipe data string, maka kita harus memberikan data yang berisikan string, jika kita mengirimkan data nya selain string maka akan muncul pesan error. Dengan adanya `prop-types` sangat membantu developer untuk memvalidasi data yang dikirim itu sesuai.

Untuk dapat menggunakan prop-types cukup mudah, pertama kita harus install library nya terlebih dahulu dengan menggunakan perintah `npm install prop-types`

**Penggunaan PropTypes**

```js
import PropTypes from "prop-types";

function DataMhs({ nama, nim, umur }) {
  return (
    <>
      <h1>Nama : {nama}</h1>
      <h1>NIM : {nim}</h1>
      <h1>Umur : {umur}</h1>
    </>
  );
}

DataMhs.propTypes = {
  nama: PropTypes.string,
  nim: PropTypes.string,
  umur: PropTypes.number,
};
```

Setelah selesai install `prop-types` kita dapat menggunakan PropTypes untuk melakukan validasi data yang kita kirim. Pertama, kita harus import PropTypes terlebih dahulu, kemudian kita set PropTypes pada keluaran data yang kita inginkan. Seperti contoh diatas, untuk data `nama` dan `nim` kita buat dalam bentuk string dan data `umur` dalam bentuk number, maka kita harus mengirimkan data yang sesuai.

### React Router

React Router merupakan suatu library yang ada pada React JS. Routing sendiri adalah proses pemetaan antara sebuah URL ke dalam sebuah halaman yang terdapat konten / UI (User Interface) sesuai dengan URL yang dituju. Untuk dapat melakukan routing pada web yang kita build, kita harus mengintal library `react-router-dom`

**Install Library**

```js
npm install react-router-dom
```

**Contoh Penggunaan**

```js
import React from "react";
import { BrowserRouter, Route, Routes } from "react-router-dom";

import Notfound from "./pages/NotFound";
import Home from "./pages/Home";
import Profil from "./pages/Profil";
import ProfilDetail from "./pages/ProfilDetail";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" exact component={Home} />
        <Route path="/profil" exact component={Profil} />
        <Route path="/profil/:name" exact component={ProfilDetail} />
        <Route component={Notfound} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

Untuk penggunaan React Router kita harus import beberapa hal yang dibutuhkan seperti Browser Router, Route, dan Routes. Setiap routingan kita harus memberikan `path` sebagai alamat yang ingin di tuju, untuk contoh diatas pada halaman home memiliki path `/` yang artinya halaman home menjadi halaman utamanya. Biasanya setiap routingan kita dibungkus oleh `Routes` kemudian dibungkus kembali oleh `Browser Router`

### Redux

#### Apa itu Redux

Redux adalah salah satu state management yang sangat hype pada waktunya dan masih relevan sampai sekarang. Redux juga menawarkan tools untuk masing-masing browser contoh chrome redux devtools untuk memonitor keadaan state kita saat ini. Package middleware-nya juga sudah banyak di kembangkan gratis dan siap digunakan untuk memudahkan kita mengembangkan aplikasi yang kita sedang kerjakan.

### Setup Redux

Untuk bisa menggunakan redux pada project yang akan kita bangun, pertama kita harus menginstall library nya terlebih dahulu dengan menggunakan perintah :

```js
npm i redux
```

Untuk mengatur project kita supaya lebih terorganisir, kita bisa membuat folder redux untuk file yang berisikan terkait redux. Hal yang diperlukan untuk membuat redux, kita harus membuat store nya terlebih dahulu

```js
import { createStore } from "redux";
import rootReducer from "./reducers";

export default createStore(rootReducer);
```

**Types**
Ada yang menyebut sebagai constants atau types dimana kita mendeklarasi setiap kegiatan yang akan terjadi pada reducer counter agar tidak ada salah sebut nama variable ketika digunakan.

```js
export const INCREMENT = "INCREMENT";
export const DECREMENT = "DECREMENT";
```

**Action**
Pada folder ini kita harus setuju bahwa semua action atau kegiatan atau juga bisa disebut kejadian akan kita letakkan pada folder ini.

```js
import { INCREMENT, DECREMENT } from "../types/counter";

export const increment = () => ({
  type: INCREMENT,
});

export const decrement = () => ({
  type: DECREMENT,
});
```

**Reducer**

```js
import { combineReducers } from "redux";
import counter from "./counter";

export default combineReducers({ counter });
```

counter.js

```js
import { INCREMENT, DECREMENT } from "../types/counter";

const initialState = {
  value: 1,
};

function reducer(state = initialState, action) {
  switch (action.type) {
    case INCREMENT:
      return { value: state.value + 1 };
    case DECREMENT:
      return { value: state.value - 1 };
    default:
      return state;
  }
}

export default reducer;
```

**Provider**
Kini reducer counter kita siap digunakan, kita bisa implementasi store kita dengan cara berikut. Untuk menggunakan redux kita harus bungkus dengan menggunakan Provider

```js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'

import { Provider } from 'react-redux'
import store from 'redux/store'

ReactDOM.render(
    <Provider store={store}>
        <App />
    </Provider>
    document.getElementById('root)
)
```

**App.js**

```js
import { useSelector, useDispatch } from "react-redux";
import { increment, decrement } from "redux/action/counter";

function App() {
  const counter = useSelector((state) => state.counter);
  const disp = useDispatch();

  return (
    <>
      <button onClick={() => dispatch(increment())}></button>
      <button onClick={() => dispatch(increment())}></button>
    </>
  );
}
```
