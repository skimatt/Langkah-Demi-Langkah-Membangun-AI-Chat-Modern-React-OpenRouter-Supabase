# AI Chat App: Panduan Membangun dari Nol 🌟

Selamat datang di panduan **super lengkap** untuk membuat aplikasi AI Chat menggunakan **React**, **Vite**, **Tailwind CSS**, **OpenRouter API (Gemini 2.0 Flash)**, dan **Supabase**! Panduan ini dibuat untuk **pemula total**, jadi setiap langkah dijelaskan dengan sangat jelas, seperti mengajari bayi berjalan. Kamu akan belajar membuat aplikasi chat interaktif, menyimpan data, dan mendeploy-nya ke internet. Yuk mulai! 🚀

## 📋 Daftar Isi

* [Apa yang Akan Kita Buat?](#apa-yang-akan-kita-buat)
* [Persiapan Awal](#persiapan-awal)
* [Instalasi React dengan Vite](#instalasi-react-dengan-vite)
* [Setup Tailwind CSS](#setup-tailwind-css)
* [Integrasi OpenRouter API](#integrasi-openrouter-api)
* [Setup Database dengan Supabase](#setup-database-dengan-supabase)
* [Deployment ke GitHub & Vercel](#deployment-ke-github--vercel)
* [Fitur Tambahan: Voice-to-Text](#fitur-tambahan-voice-to-text)
* [Struktur Folder Proyek](#struktur-folder-proyek)
* [Troubleshooting](#troubleshooting)
* [Penutup](#penutup)

## 🌟 Apa yang Akan Kita Buat?

Kita akan membangun aplikasi web di mana kamu bisa:
* Mengetik pertanyaan dan mendapatkan jawaban dari AI (Gemini 2.0 Flash via OpenRouter).
* Menyimpan riwayat chat di database (Supabase).
* Menggunakan suara untuk input teks (opsional, dengan Web Speech API).
* Men-deploy aplikasi ke internet agar bisa diakses semua orang!

Aplikasi ini akan punya tampilan modern, cepat, dan mudah digunakan.

## 🛠️ Persiapan Awal

Sebelum mulai, pastikan kamu punya:
* **Komputer** dengan koneksi internet stabil.
* **Text Editor**: Gunakan [Visual Studio Code](https://code.visualstudio.com/) (gratis dan ramah pemula).
* **Terminal**: Ada di dalam VS Code (klik Terminal > New Terminal).
* **Akun Gratis**:
  * [OpenRouter](https://openrouter.ai) untuk API AI.
  * [Supabase](https://supabase.com) untuk database.
  * [GitHub](https://github.com) untuk menyimpan kode.
  * [Vercel](https://vercel.com) untuk hosting.

### Langkah Persiapan

1. **Install Visual Studio Code**:
   * Buka [code.visualstudio.com](https://code.visualstudio.com).
   * Unduh untuk Windows/Mac/Linux, lalu instal.
   * Buka VS Code.

2. **Buat Folder Proyek**:
   * Buat folder bernama `ai-chat-app` di Desktop atau tempat lain.
   * Buka folder di VS Code: File > Open Folder > Pilih `ai-chat-app`.

3. **Cek Koneksi Internet**:
   * Pastikan internet stabil karena kita akan mengunduh alat dan menghubungkan API.

## 🚀 Instalasi React dengan Vite

### Apa Itu React dan Vite?

* **React**: Pustaka JavaScript untuk membuat antarmuka web interaktif (misal: tombol yang berubah saat diklik).
* **Vite**: Alat cepat untuk membuat proyek React, dengan reload otomatis saat kamu edit kode.

### Langkah-langkah

1. **Install Node.js**:
   * Buka [nodejs.org](https://nodejs.org).
   * Unduh versi **LTS** (stabil) dan instal.
   * Buka terminal di VS Code (Terminal > New Terminal) dan cek:
     ```bash
     node -v
     npm -v
     ```
   * Kamu akan melihat versi, misalnya `v16.13.0`. Jika tidak, instal ulang Node.js.

2. **Buat Proyek React**:
   * Di terminal, pastikan kamu di folder `ai-chat-app`. Ketik:
     ```bash
     npm create vite@latest . -- --template react
     ```
   * Pilih `React` dan `JavaScript` saat diminta.
   * Perintah ini membuat proyek React di folder saat ini.

3. **Install Dependensi**:
   * Ketik:
     ```bash
     npm install
     ```
   * Ini mengunduh file yang dibutuhkan React dan Vite.

4. **Jalankan Aplikasi**:
   * Ketik:
     ```bash
     npm run dev
     ```
   * Buka browser di `http://localhost:5173`. Kamu akan melihat halaman Vite + React.
   * Tekan `Ctrl+C` di terminal untuk menghentikan.

5. **Struktur Folder Awal**:
   ```
   ai-chat-app/
   ├── node_modules/        # Dependensi (jangan ubah)
   ├── public/             # File statis (gambar, dll)
   │   └── vite.svg
   ├── src/                # Kode utama
   │   ├── assets/         # Gambar atau file lain
   │   ├── App.jsx         # Komponen utama
   │   ├── index.css       # File CSS
   │   └── main.jsx        # Titik masuk aplikasi
   ├── .gitignore          # File yang diabaikan Git
   ├── index.html          # Halaman utama
   ├── package.json        # Daftar dependensi
   ├── vite.config.js      # Konfigurasi Vite
   ```

## 🎨 Setup Tailwind CSS

### Apa Itu Tailwind CSS?

Tailwind CSS memungkinkanmu mendesain web dengan cepat menggunakan kelas seperti `bg-blue-500` (latar biru) atau `p-4` (padding). Ini sangat cocok untuk pemula karena tidak perlu menulis CSS manual.

### Langkah-langkah

1. **Install Tailwind**:
   * Di terminal, ketik:
     ```bash
     npm install -D tailwindcss postcss autoprefixer
     ```

2. **Buat File Konfigurasi**:
   * Ketik:
     ```bash
     npx tailwindcss init -p
     ```
   * Ini membuat `tailwind.config.js` dan `postcss.config.js`.

3. **Konfigurasi `tailwind.config.js`**:
   * Buka `tailwind.config.js` dan ubah jadi:
     ```javascript
     /** @type {import('tailwindcss').Config} */
     export default {
       content: [
         "./index.html",
         "./src/**/*.{js,ts,jsx,tsx}",
       ],
       theme: {
         extend: {},
       },
       plugins: [],
     }
     ```

4. **Tambahkan Tailwind ke CSS**:
   * Buka `src/index.css` dan ganti isinya:
     ```css
     @tailwind base;
     @tailwind components;
     @tailwind utilities;
     ```

5. **Uji Tailwind**:
   * Buka `src/App.jsx` dan ubah:
     ```jsx
     function App() {
       return (
         <div className="bg-blue-500 text-white p-4">
           <h1>Halo, ini aplikasi AI Chat!</h1>
         </div>
       );
     }
     export default App;
     ```
   * Jalankan `npm run dev` dan buka `http://localhost:5173`. Lihat teks putih dengan latar biru.

## 🤖 Integrasi OpenRouter API

### Apa Itu OpenRouter dan Gemini 2.0 Flash?

* **OpenRouter**: Platform untuk mengakses model AI seperti Gemini 2.0 Flash.
* **Gemini 2.0 Flash**: Model AI cepat dari Google untuk menjawab pertanyaan.

### Langkah-langkah

1. **Daftar di OpenRouter**:
   * Buka [openrouter.ai](https://openrouter.ai).
   * Klik "Sign Up", masukkan email, dan buat kata sandi.
   * Verifikasi email.

2. **Dapatkan API Key**:
   * Login, lalu klik "API Keys" di dashboard.
   * Klik "Generate Key", beri nama (misal: `ai-chat`), dan salin kunci (contoh: `sk-or-v1-xxxx`).
   * Simpan kunci di tempat aman.

3. **Buat Komponen Chat**:
   * Buat folder `src/components` dan file `Chat.jsx`:
     ```jsx
     import { useState } from 'react';

     function Chat() {
       const [prompt, setPrompt] = useState('');
       const [response, setResponse] = useState('');

       const handleSubmit = async (e) => {
         e.preventDefault();
         try {
           const res = await fetch('https://openrouter.ai/api/v1/chat/completions', {
             method: 'POST',
             headers: {
               'Authorization': 'Bearer YOUR_API_KEY',
               'Content-Type': 'application/json',
             },
             body: JSON.stringify({
               model: 'google/gemini-flash-2-0',
               messages: [{ role: 'user', content: prompt }],
             }),
           });
           const data = await res.json();
           setResponse(data.choices[0].message.content);
         } catch (error) {
           console.error('Error:', error);
         }
       };

       return (
         <div className="p-4">
           <form onSubmit={handleSubmit}>
             <input
               type="text"
               value={prompt}
               onChange={(e) => setPrompt(e.target.value)}
               className="border p-2 mr-2 w-64"
               placeholder="Ketik pertanyaan..."
             />
             <button type="submit" className="bg-blue-500 text-white p-2">
               Kirim
             </button>
           </form>
           {response && <p className="mt-4">Respon: {response}</p>}
         </div>
       );
     }

     export default Chat;
     ```
   * Ganti `YOUR_API_KEY` dengan kunci API OpenRouter-mu.

4. **Tambahkan Komponen ke App**:
   * Buka `src/App.jsx` dan ubah:
     ```jsx
     import Chat from './components/Chat';

     function App() {
       return (
         <div className="min-h-screen bg-gray-100 flex items-center justify-center">
           <div className="bg-white p-6 rounded-lg shadow-lg w-full max-w-md">
             <h1 className="text-2xl font-bold mb-4">AI Chat</h1>
             <Chat />
           </div>
         </div>
       );
     }

     export default App;
     ```

5. **Uji API**:
   * Jalankan `npm run dev`.
   * Ketik pertanyaan di input, klik "Kirim", dan lihat respons AI.

## 🗄️ Setup Database dengan Supabase

### Apa Itu Supabase?

Supabase adalah database open-source (mirip Firebase) untuk menyimpan data seperti riwayat chat.

### Langkah-langkah

1. **Daftar di Supabase**:
   * Buka [supabase.com](https://supabase.com) dan klik "Sign Up".
   * Masuk dengan email atau GitHub, lalu buat proyek baru (misal: `ai-chat`).

2. **Buat Tabel**:
   * Di dashboard Supabase, klik "Table Editor" dan buat:
     * **users**:
       ```sql
       id (uuid, primary key, auto-generated)
       email (text, unique)
       created_at (timestamptz, default now())
       ```
     * **chats**:
       ```sql
       id (uuid, primary key, auto-generated)
       user_id (uuid, foreign key to users.id)
       title (text)
       created_at (timestamptz, default now())
       ```
     * **messages**:
       ```sql
       id (uuid, primary key, auto-generated)
       chat_id (uuid, foreign key to chats.id)
       content (text)
       role (text, 'user' or 'assistant')
       created_at (timestamptz, default now())
       ```

3. **Install Supabase**:
   * Di terminal, ketik:
     ```bash
     npm install @supabase/supabase-js
     ```

4. **Konfigurasi Supabase**:
   * Buat file `src/supabase.js`:
     ```javascript
     import { createClient } from '@supabase/supabase-js';

     const supabaseUrl = 'YOUR_SUPABASE_URL';
     const supabaseKey = 'YOUR_SUPABASE_KEY';
     const supabase = createClient(supabaseUrl, supabaseKey);

     export default supabase;
     ```
   * Dapatkan `supabaseUrl` dan `supabaseKey` dari Supabase dashboard > Settings > API.

5. **Simpan Pesan ke Supabase**:
   * Edit `src/components/Chat.jsx`:
     ```jsx
     import { useState } from 'react';
     import supabase from '../supabase';

     function Chat() {
       const [prompt, setPrompt] = useState('');
       const [response, setResponse] = useState('');

       const saveMessage = async (chatId, content, role) => {
         const { error } = await supabase
           .from('messages')
           .insert([{ chat_id: chatId, content, role }]);
         if (error) console.error('Error saving message:', error);
       };

       const handleSubmit = async (e) => {
         e.preventDefault();
         try {
           const chatId = 'YOUR_CHAT_ID'; // Ganti dengan ID chat
           await saveMessage(chatId, prompt, 'user');
           const res = await fetch('https://openrouter.ai/api/v1/chat/completions', {
             method: 'POST',
             headers: {
               'Authorization': 'Bearer YOUR_API_KEY',
               'Content-Type': 'application/json',
             },
             body: JSON.stringify({
               model: 'google/gemini-flash-2-0',
               messages: [{ role: 'user', content: prompt }],
             }),
           });
           const data = await res.json();
           const aiResponse = data.choices[0].message.content;
           setResponse(aiResponse);
           await saveMessage(chatId, aiResponse, 'assistant');
         } catch (error) {
           console.error('Error:', error);
         }
       };

       return (
         <div className="p-4">
           <form onSubmit={handleSubmit}>
             <input
               type="text"
               value={prompt}
               onChange={(e) => setPrompt(e.target.value)}
               className="border p-2 mr-2 w-64"
               placeholder="Ketik pertanyaan..."
             />
             <button type="submit" className="bg-blue-500 text-white p-2">
               Kirim
             </button>
           </form>
           {response && <p className="mt-4">Respon: {response}</p>}
         </div>
       );
     }

     export default Chat;
     ```

6. **Gunakan Environment Variables**:
   * Buat file `.env`:
     ```env
     VITE_SUPABASE_URL=YOUR_SUPABASE_URL
     VITE_SUPABASE_KEY=YOUR_SUPABASE_KEY
     VITE_OPENROUTER_API_KEY=YOUR_API_KEY
     ```
   * Edit `src/supabase.js`:
     ```javascript
     import { createClient } from '@supabase/supabase-js';

     const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
     const supabaseKey = import.meta.env.VITE_SUPABASE_KEY;
     const supabase = createClient(supabaseUrl, supabaseKey);

     export default supabase;
     ```

## 🌍 Deployment ke GitHub & Vercel

### Upload ke GitHub

1. **Install Git**:
   * Unduh dari [git-scm.com](https://git-scm.com) dan instal.
   * Cek versi:
     ```bash
     git --version
     ```

2. **Inisialisasi Git**:
   * Di terminal, ketik:
     ```bash
     git init
     git add .
     git commit -m "Initial commit"
     ```

3. **Buat Repo di GitHub**:
   * Buka [github.com](https://github.com), login, dan klik "New Repository".
   * Beri nama `ai-chat-app` dan klik "Create Repository".
   * Salin URL repo (misal: `https://github.com/username/ai-chat-app.git`).

4. **Push ke GitHub**:
   * Ketik:
     ```bash
     git remote add origin https://github.com/username/ai-chat-app.git
     git branch -M main
     git push -u origin main
     ```

### Hosting di Vercel

1. **Daftar di Vercel**:
   * Buka [vercel.com](https://vercel.com) dan klik "Sign Up".
   * Login dengan GitHub.

2. **Import Proyek**:
   * Di dashboard Vercel, klik "New Project".
   * Pilih repo `ai-chat-app` dan klik "Import".

3. **Atur Environment Variables**:
   * Di pengaturan proyek, tambahkan:
     ```env
     VITE164_SUPABASE_URL=YOUR_SUPABASE_URL
     VITE_SUPABASE_KEY=YOUR_SUPABASE_KEY
     VITE_OPENROUTER_API_KEY=YOUR_API_KEY
     ```

4. **Deploy**:
   * Klik "Deploy". Setelah selesai, kamu akan mendapatkan URL (misal: `https://ai-chat-app.vercel.app`).

## 🎙️ Fitur Tambahan: Voice-to-Text

Tambahkan fitur input suara di `src/components/Chat.jsx`:

```jsx
import { useState } from 'react';
import supabase from '../supabase';

function Chat() {
  const [prompt, setPrompt] = useState('');
  const [response, setResponse] = useState('');
  const [isListening, setIsListening] = useState(false);

  const startListening = () => {
    const recognition = new window.webkitSpeechRecognition();
    recognition.lang = 'id-ID';
    recognition.onresult = (event) => {
      setPrompt(event.results[0][0].transcript);
    };
    recognition.start();
    setIsListening(true);
    recognition.onend = () => setIsListening(false);
  };

  const saveMessage = async (chatId, content, role) => {
    const { error } = await supabase
      .from('messages')
      .insert([{ chat_id: chatId, content, role }]);
    if (error) console.error('Error saving message:', error);
  };

  const handleSubmit = async (e) => {
    e.preventDefault();
    try {
      const chatId = 'YOUR_CHAT_ID';
      await saveMessage(chatId, prompt, 'user');
      const res = await fetch('https://openrouter.ai/api/v1/chat/completions', {
        method: 'POST',
        headers: {
          'Authorization': 'Bearer YOUR_API_KEY',
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          model: 'google/gemini-flash-2-0',
          messages: [{ role: 'user', content: prompt }],
        }),
      });
      const data = await res.json();
      const aiResponse = data.choices[0].message.content;
      setResponse(aiResponse);
      await saveMessage(chatId, aiResponse, 'assistant');
    } catch (error) {
      console.error('Error:', error);
    }
  };

  return (
    <div className="p-4">
      <form onSubmit={handleSubmit}>
        <input
          type="text"
          value={prompt}
          onChange={(e) => setPrompt(e.target.value)}
          className="border p-2 mr-2 w-64"
          placeholder="Ketik pertanyaan..."
        />
        <button
          type="button"
          onClick={startListening}
          className={`p-2 mr-2 ${isListening ? 'bg-red-500' : 'bg-green-500'} text-white`}
        >
          {isListening ? 'Berhenti' : 'Mikrofon'}
        </button>
        <button type="submit" className="bg-blue-500 text-white p-2">
          Kirim
        </button>
      </form>
      {response && <p className="mt-4">Respon: {response}</p>}
    </div>
  );
}

export default Chat;
```

* **Cara Kerja**: Klik "Mikrofon" untuk merekam suara, ucapkan pertanyaan, dan teks akan muncul di input.

## 📂 Struktur Folder Proyek

```
ai-chat-app/
├── node_modules/        # Dependensi
├── public/             # File statis
│   └── vite.svg
├── src/                # Kode utama
│   ├── assets/         # Gambar
│   ├── components/     # Komponen React
│   │   └── Chat.jsx
│   ├── App.jsx
│   ├── index.css
│   ├── main.jsx
│   └── supabase.js
├── .env                # Environment variables
├── .gitignore          # File yang diabaikan Git
├── index.html          # Halaman utama
├── package.json        # Daftar dependensi
├── tailwind.config.js  # Konfigurasi Tailwind
├── vite.config.js      # Konfigurasi Vite
```

## ⚠️ Troubleshooting

* **Node.js tidak terdeteksi**:
  * Cek `node -v` dan instal ulang jika perlu.
* **Tailwind tidak berfungsi**:
  * Pastikan `tailwind.config.js` punya path benar.
  * Cek `index.css` punya direktif `@tailwind`.
* **OpenRouter error**:
  * **401**: Periksa API key.
  * **429**: Tunggu (kuota terbatas).
* **Supabase gagal**:
  * Pastikan `supabaseUrl` dan `supabaseKey` benar.
* **Vercel gagal deploy**:
  * Cek environment variables di Vercel.

## 🎉 Penutup

Selamat! Kamu telah membangun aplikasi AI Chat dari nol. Sekarang kamu punya aplikasi yang:
* Menggunakan React untuk antarmuka.
* Didesain dengan Tailwind CSS.
* Terhubung ke AI via OpenRouter.
* Menyimpan data di Supabase.
* Support input suara.

### Langkah Selanjutnya
* Tambahkan login dengan Supabase Auth.
* Tampilkan riwayat chat dari Supabase.
* Tambahkan animasi dengan [Framer Motion](https://www.framer.com/motion/).
* Pelajari lebih lanjut di:
  * [React](https://react.dev)
  * [Vite](https://vitejs.dev)
  * [Tailwind CSS](https://tailwindcss.com)
  * [OpenRouter](https://openrouter.ai/docs)
  * [Supabase](https://supabase.com/docs)
  * [Vercel](https://vercel.com/docs)

Selamat coding! 🚀
