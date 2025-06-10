README: Panduan Membangun Aplikasi AI Chat dari Nol
Selamat datang di panduan langkah demi langkah untuk membangun aplikasi AI Chat menggunakan React, Vite, Tailwind CSS, OpenRouter API (Gemini 2.0 Flash), dan Supabase! Panduan ini dirancang untuk pemula yang benar-benar baru, jadi setiap langkah dijelaskan dengan sangat detail, seperti menuntun bayi belajar berjalan. Tidak perlu khawatir jika kamu belum pernah coding sebelumnya—kita akan melalui semua proses bersama-sama!
📋 Daftar Isi

Apa yang Akan Kita Buat?
Persiapan Awal
Instalasi React dengan Vite
Setup Tailwind CSS
Integrasi OpenRouter API (Gemini 2.0 Flash)
Setup Database dengan Supabase
Deployment ke GitHub & Vercel
Struktur Folder & Fitur Tambahan
Troubleshooting & Tips
Penutup & Langkah Selanjutnya


1. Apa yang Akan Kita Buat?
Kita akan membuat aplikasi web sederhana di mana pengguna bisa:

Mengetik pertanyaan atau pesan.
Mendapatkan respons dari AI (menggunakan Gemini 2.0 Flash via OpenRouter).
Menyimpan riwayat chat di database (menggunakan Supabase).
Menggunakan fitur suara untuk input teks (opsional).
Men-deploy aplikasi ke internet agar bisa diakses semua orang!

Aplikasi ini akan punya tampilan modern (terima kasih kepada Tailwind CSS), cepat dibuat (terima kasih kepada Vite), dan interaktif (terima kasih kepada React).

2. Persiapan Awal
Sebelum mulai, pastikan kamu punya:

Komputer dengan akses internet.
Text editor: Saya sarankan Visual Studio Code (gratis dan mudah digunakan).
Terminal: VS Code punya terminal bawaan, atau gunakan Command Prompt (Windows) atau Terminal (Mac/Linux).
Akun gratis di OpenRouter, Supabase, GitHub, dan Vercel.

Langkah Persiapan

Unduh VS Code:

Buka code.visualstudio.com.
Klik "Download" sesuai sistem operasi (Windows/Mac/Linux).
Instal dan buka aplikasi.


Buat Folder Proyek:

Buat folder di komputer, misalnya ai-chat-app, di Desktop atau lokasi lain.
Buka folder ini di VS Code: File > Open Folder > Pilih ai-chat-app.


Pastikan Internet Stabil:

Kita akan mengunduh banyak alat dan mengakses API online.




3. Instalasi React dengan Vite
Apa Itu React dan Vite?

React: Pustaka JavaScript untuk membuat antarmuka web interaktif, seperti tombol atau input yang langsung merespons.
Vite: Alat untuk membuat proyek React dengan cepat, ringan, dan mendukung reload otomatis saat kamu mengedit kode.

Langkah-langkah

Instal Node.js:

Buka nodejs.org.
Unduh versi LTS (versi stabil) dan instal.
Buka terminal di VS Code (Terminal > New Terminal) dan ketik:node -v

Kamu akan melihat versi, misalnya v16.13.0. Jika tidak, instal ulang Node.js.
Cek juga npm (alat untuk mengelola paket):npm -v




Buat Proyek React dengan Vite:

Di terminal, pastikan kamu berada di folder ai-chat-app. Ketik:npm create vite@latest . -- --template react


Penjelasan: Perintah ini membuat proyek React di folder saat ini (. berarti folder saat ini).
Pilih React jika diminta, lalu JavaScript (bukan TypeScript).


Tunggu hingga selesai.


Instal Dependensi:

Ketik:npm install


Ini mengunduh semua file yang dibutuhkan React dan Vite.
Jika ada error seperti "command not found", pastikan Node.js terinstal benar.




Jalankan Aplikasi:

Ketik:npm run dev


Buka browser dan kunjungi http://localhost:5173. Kamu akan melihat halaman selamat datang Vite + React.
Tekan Ctrl+C di terminal untuk menghentikan aplikasi.


Kenali Struktur Folder:Setelah instalasi, folder proyekmu akan seperti ini:
ai-chat-app/
├── node_modules/        # Folder dependensi (jangan ubah)
├── public/             # File statis seperti gambar
│   └── vite.svg
├── src/                # Kode utama aplikasi
│   ├── assets/         # Gambar atau file lain
│   ├── App.jsx         # Komponen utama
│   ├── index.css       # File CSS
│   └── main.jsx        # Titik masuk aplikasi
├── .gitignore          # File yang diabaikan Git
├── index.html          # Halaman utama
├── package.json        # Daftar dependensi
├── vite.config.js      # Konfigurasi Vite




4. Setup Tailwind CSS
Apa Itu Tailwind CSS?
Tailwind CSS adalah cara cepat mendesain web dengan menambahkan kelas seperti bg-blue-500 (latar biru) atau p-4 (padding). Ini sangat cocok untuk pemula karena kamu tidak perlu menulis CSS dari nol.
Langkah-langkah

Instal Tailwind CSS:

Di terminal, ketik:npm install -D tailwindcss postcss autoprefixer


-D berarti dependensi untuk pengembangan.




Buat File Konfigurasi:

Ketik:npx tailwindcss init -p


Ini membuat dua file: tailwind.config.js dan postcss.config.js.




Konfigurasi tailwind.config.js:

Buka tailwind.config.js di VS Code dan ubah jadi:/** @type {import('tailwindcss').Config} */
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


Penjelasan: Baris content memberi tahu Tailwind file mana yang menggunakan kelasnya.




Tambahkan Tailwind ke CSS:

Buka src/index.css dan ganti isinya dengan:@tailwind base;
@tailwind components;
@tailwind utilities;




Uji Tailwind:

Buka src/App.jsx dan ubah jadi:function App() {
  return (
    <div className="bg-blue-500 text-white p-4">
      <h1>Halo, ini aplikasi AI Chat!</h1>
    </div>
  );
}
export default App;


Jalankan npm run dev dan buka http://localhost:5173. Kamu akan melihat teks putih dengan latar biru.
Jika tidak berfungsi, pastikan semua langkah diikuti dan terminal tidak menunjukkan error.




5. Integrasi OpenRouter API (Gemini 2.0 Flash)
Apa Itu OpenRouter dan Gemini 2.0 Flash?

OpenRouter: Platform yang menyediakan akses ke model AI seperti Gemini 2.0 Flash (model AI cepat dari Google).
Gemini 2.0 Flash: Model AI yang bisa menjawab pertanyaanmu, cocok untuk aplikasi chat.

Langkah-langkah

Daftar di OpenRouter:

Buka openrouter.ai.
Klik "Sign Up", masukkan email, dan buat kata sandi.
Verifikasi email jika diminta.


Dapatkan API Key:

Login ke OpenRouter.
Klik "API Keys" di dashboard.
Klik "Generate Key", beri nama (misal: ai-chat), lalu salin kunci (contoh: sk-or-v1-xxxx).
Simpan kunci ini di tempat aman (jangan dibagikan!).


Buat Komponen Chat:

Buat folder src/components dan file baru Chat.jsx:import { useState } from 'react';

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


Ganti YOUR_API_KEY dengan kunci API OpenRouter-mu.


Tambahkan Komponen ke App:

Buka src/App.jsx dan ubah:import Chat from './components/Chat';

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




Uji API:

Jalankan npm run dev.
Ketik pertanyaan seperti "Halo, apa kabar?" di input, klik "Kirim", dan lihat respons AI.
Jika tidak berhasil, periksa:
API key benar (tidak ada spasi).
Koneksi internet stabil.
Baca error di console browser (tekan F12 > Console).






6. Setup Database dengan Supabase
Apa Itu Supabase?
Supabase adalah database online gratis yang mirip Firebase, tapi open-source. Kita akan menggunakannya untuk menyimpan data pengguna, chat, dan pesan.
Langkah-langkah

Daftar di Supabase:

Buka supabase.com dan klik "Sign Up".
Masuk dengan email atau GitHub, lalu buat proyek baru di dashboard.
Beri nama proyek, misalnya ai-chat.


Buat Tabel:

Di dashboard Supabase, klik "Table Editor".
Buat tiga tabel:
users:id (uuid, primary key, auto-generated)
email (text, unique)
created_at (timestamptz, default now())


chats:id (uuid, primary key, auto-generated)
user_id (uuid, foreign key to users.id)
title (text)
created_at (timestamptz, default now())


messages:id (uuid, primary key, auto-generated)
chat_id (uuid, foreign key to chats.id)
content (text)
role (text, 'user' or 'assistant')
created_at (timestamptz, default now())






Instal Supabase di Proyek:

Di terminal, ketik:npm install @supabase/supabase-js




Konfigurasi Supabase:

Buat file src/supabase.js:import { createClient } from '@supabase/supabase-js';

const supabaseUrl = 'YOUR_SUPABASE_URL';
const supabaseKey = 'YOUR_SUPABASE_KEY';
const supabase = createClient(supabaseUrl, supabaseKey);

export default supabase;


Dapatkan supabaseUrl dan supabaseKey dari Supabase dashboard > Settings > API.


Simpan Pesan ke Supabase:

Edit src/components/Chat.jsx, tambahkan fungsi untuk menyimpan pesan:import { useState } from 'react';
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
      const chatId = 'YOUR_CHAT_ID'; // Ganti dengan ID chat yang valid
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


Ganti YOUR_CHAT_ID dengan ID chat dari tabel chats (bisa dibuat manual di Supabase).


Gunakan Environment Variables:

Buat file .env di root proyek:VITE_SUPABASE_URL=YOUR_SUPABASE_URL
VITE_SUPABASE_KEY=YOUR_SUPABASE_KEY
VITE_OPENROUTER_API_KEY=YOUR_API_KEY


Edit src/supabase.js untuk menggunakan .env:import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseKey = import.meta.env.VITE_SUPABASE_KEY;
const supabase = createClient(supabaseUrl, supabaseKey);

export default supabase;






7. Deployment ke GitHub & Vercel
Upload ke GitHub

Instal Git:

Unduh dari git-scm.com dan instal.
Cek versi:git --version




Inisialisasi Git:

Di terminal, di folder ai-chat-app, ketik:git init
git add .
git commit -m "Initial commit"




Buat Repo di GitHub:

Buka github.com dan login.
Klik "New Repository", beri nama ai-chat-app, lalu klik "Create Repository".
Salin URL repo (misal: https://github.com/username/ai-chat-app.git).


Push ke GitHub:

Kembali ke terminal:git remote add origin https://github.com/username/ai-chat-app.git
git branch -M main
git push -u origin main





Hosting di Vercel

Daftar di Vercel:

Buka vercel.com dan klik "Sign Up".
Login dengan akun GitHub.


Import Proyek:

Di dashboard Vercel, klik "New Project".
Pilih repo ai-chat-app dari GitHub dan klik "Import".


Atur Environment Variables:

Di pengaturan proyek Vercel, masuk ke tab "Environment Variables".
Tambahkan:VITE_SUPABASE_URL=YOUR_SUPABASE_URL
VITE_SUPABASE_KEY=YOUR_SUPABASE_KEY
VITE_OPENROUTER_API_KEY=YOUR_API_KEY




Deploy:

Klik "Deploy". Tunggu beberapa menit, lalu klik URL yang diberikan (misal: https://ai-chat-app.vercel.app).
Aplikasi sekarang live di internet!




8. Struktur Folder & Fitur Tambahan
Struktur Folder
Setelah semua langkah, folder proyekmu seharusnya seperti ini:
ai-chat-app/
├── node_modules/
├── public/
│   └── vite.svg
├── src/
│   ├── assets/
│   ├── components/
│   │   └── Chat.jsx
│   ├── App.jsx
│   ├── index.css
│   ├── main.jsx
│   └── supabase.js
├── .env
├── .gitignore
├── index.html
├── package.json
├── tailwind.config.js
├── vite.config.js

Fitur Voice-to-Text
Tambahkan fitur input suara menggunakan Web Speech API di Chat.jsx:
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


Cara Kerja: Klik tombol "Mikrofon" untuk mulai merekam suara. Ucapkan pertanyaan, dan teks akan muncul di input. Klik "Kirim" untuk mendapatkan respons AI.


9. Troubleshooting & Tips

Node.js tidak terdeteksi:
Pastikan Node.js terinstal (node -v).
Restart terminal atau komputer setelah instalasi.


Tailwind tidak berfungsi:
Periksa tailwind.config.js dan pastikan path content benar.
Pastikan index.css punya direktif @tailwind.


API OpenRouter error:
401: Cek API key.
429: Tunggu beberapa menit (kuota terbatas).
Baca dokumentasi di openrouter.ai/docs.


Supabase tidak tersambung:
Pastikan supabaseUrl dan supabaseKey benar di .env.
Cek tabel di dashboard Supabase.


Vercel gagal deploy:
Pastikan .env diunggah ke Vercel sebagai environment variables.
Periksa log di dashboard Vercel.



Tips Umum:

Simpan kode sering-sering (Ctrl+S).
Gunakan console.log untuk debugging.
Selalu baca pesan error di terminal atau console browser.


10. Penutup & Langkah Selanjutnya
Selamat! Kamu telah membangun aplikasi AI Chat yang berfungsi penuh, dari nol hingga live di internet. Sekarang kamu punya aplikasi yang:

Menggunakan React untuk antarmuka interaktif.
Didesain dengan Tailwind CSS.
Terhubung ke AI via OpenRouter.
Menyimpan data di Supabase.
Bisa menerima input suara.

Langkah Selanjutnya

Autentikasi: Tambahkan login dengan Supabase Auth.
Riwayat Chat: Tampilkan daftar pesan dari tabel messages.
UI Lebih Keren: Gunakan Framer Motion untuk animasi.
Fitur Lain: Tambahkan tema gelap/terang atau notifikasi real-time dengan Supabase Realtime.

Referensi resmi:

React
Vite
Tailwind CSS
OpenRouter
Supabase
Vercel

Jika ada pertanyaan, cari di Stack Overflow atau tanya komunitas di @skimatt_. Selamat coding!
