# **Tic-Tac-Toe dengan Agen Cerdas BFS dan Dataset**

---

## **Deskripsi Proyek**

Proyek ini adalah implementasi permainan Tic-Tac-Toe interaktif yang dijalankan di dalam Jupyter Notebook menggunakan **IPyWidgets**. Permainan ini dilengkapi dengan agen cerdas yang menggunakan algoritma **Breadth-First Search (BFS)** dan memanfaatkan dataset historis untuk memandu keputusannya. Agen cerdas ini akan menjadi lawan pemain dan berusaha untuk menang atau minimal menghindari kekalahan.

---

## **Fitur Utama**

- **Antarmuka Interaktif**: Menggunakan **IPyWidgets** untuk menciptakan antarmuka permainan yang interaktif langsung di dalam Jupyter Notebook.
- **Agen Cerdas dengan BFS**: Agen menggunakan algoritma BFS yang dipandu oleh dataset untuk memilih langkah terbaik.
- **Dataset Historis**: Menggunakan dataset `Tic tac initial results.csv` yang berisi riwayat permainan Tic-Tac-Toe sebelumnya untuk memandu agen.
- **Feedback Real-time**: Permainan memberikan pesan status secara real-time, termasuk giliran pemain, kemenangan, kekalahan, atau seri.
- **Reset Permainan**: Fitur untuk mereset permainan dan memulai kembali tanpa harus menjalankan ulang seluruh notebook.

---

## **Persyaratan Sistem**

- **Python 3.x**
- **Jupyter Notebook atau Google Colab**
- **Library Python:**
  - `pandas`
  - `numpy`
  - `ipywidgets`

---

## **Instalasi dan Persiapan**

### **1. Instalasi Python dan Jupyter Notebook**

Jika Anda belum menginstal Python dan Jupyter Notebook, Anda dapat mengunduh dan menginstal **Anaconda Distribution** yang sudah mencakup keduanya:

- **Anaconda Distribution**: [https://www.anaconda.com/products/individual](https://www.anaconda.com/products/individual)

Atau, Anda dapat menggunakan **Google Colab** yang tidak memerlukan instalasi dan dapat dijalankan langsung di browser.

### **2. Instalasi Library Python yang Dibutuhkan**

Jika Anda menggunakan Jupyter Notebook lokal, buka terminal atau command prompt dan jalankan perintah berikut untuk menginstal library yang dibutuhkan:

```bash
pip install pandas numpy ipywidgets
```

Aktifkan ekstensi widgetsnbextension:

```bash
jupyter nbextension enable --py widgetsnbextension
```

Jika Anda menggunakan Google Colab, library ini sudah terinstal, tetapi Anda perlu mengaktifkan `ipywidgets` dengan menjalankan beberapa perintah tambahan (akan dijelaskan di bagian berikutnya).

### **3. Mendapatkan Dataset**

Pastikan Anda memiliki file dataset `Tic tac initial results.csv` dan letakkan di direktori yang sama dengan notebook Anda. Dataset ini digunakan oleh agen cerdas untuk memandu keputusannya.

---

## **Menjalankan Permainan**

Anda dapat menjalankan permainan ini dengan mudah menggunakan Google Colab. Silakan klik link berikut untuk membuka notebook dan menjalankannya secara langsung:

[**Jalankan Tic-Tac-Toe dengan Agen Cerdas di Colab**](https://colab.research.google.com/drive/1l8rUFVuK1Z_fd3WpgCsAuimgvRU5_h-H?usp=sharing)

### **Langkah-langkah:**

1. **Buka Link Colab**

   Klik link di atas untuk membuka notebook di Google Colab.

2. **Mengunggah Dataset**

   - Di Colab, Anda perlu mengunggah file dataset `Tic tac initial results.csv`.
   - Di panel kiri, klik ikon **Folder** untuk membuka file explorer.
   - Klik tombol **Upload** (ikon dengan tanda panah ke atas), dan unggah file `Tic tac initial results.csv`.
   - Pastikan file tersebut ada di direktori root (langsung di bawah `/content`).

3. **Menjalankan Sel Kode**

   - Jalankan sel-sel kode secara berurutan dari atas ke bawah.
   - Beberapa sel mungkin memerlukan izin untuk menginstal atau mengaktifkan ekstensi; ikuti instruksi yang diberikan.

4. **Mengaktifkan IPyWidgets di Colab**

   - Jalankan perintah berikut di sel terpisah untuk mengaktifkan `ipywidgets` di Colab:

     ```python
     !pip install ipywidgets
     from google.colab import output
     output.enable_custom_widget_manager()
     ```

5. **Memulai Permainan**

   - Setelah semua sel dijalankan, Anda akan melihat pesan "Permainan dimulai. Giliran Anda." dan papan permainan.
   - Klik pada sel kosong untuk melakukan gerakan Anda.

6. **Bermain**

   - Nikmati permainan melawan agen cerdas!
   - Gunakan tombol **"Reset Permainan"** jika Anda ingin memulai ulang.

---

## **Cara Bermain**

1. **Memulai Permainan**

   - Pesan "Permainan dimulai. Giliran Anda." akan ditampilkan.
   - Papan permainan kosong akan ditampilkan dengan tombol interaktif.

2. **Melakukan Gerakan**

   - Klik pada salah satu sel kosong untuk melakukan gerakan Anda.
   - Anda adalah pemain 'X', dan agen cerdas adalah pemain 'O'.

3. **Giliran Agen**

   - Setelah Anda melakukan gerakan, agen cerdas akan otomatis melakukan gerakannya.
   - Pesan status akan diperbarui untuk memberi tahu Anda giliran siapa atau hasil permainan.

4. **Mengakhiri Permainan**

   - Permainan akan berakhir jika salah satu pemain menang atau jika permainan berakhir seri.
   - Pesan akan ditampilkan sesuai dengan hasil permainan:
     - "Selamat! Anda menang!"
     - "Maaf, Anda kalah. Agen menang."
     - "Permainan berakhir seri!"

5. **Mereset Permainan**

   - Untuk memulai permainan baru, klik tombol **"Reset Permainan"**.
   - Papan permainan dan pesan akan direset, dan Anda dapat bermain kembali.

---

## **Struktur Kode**

### **1. Memuat dan Memproses Dataset**

- **Memuat dataset** menggunakan `pandas` dan mengganti nilai `'?'` dengan `NaN`.
- **Mengonversi kolom MOVE** menjadi tipe numerik dan memproses jalur kemenangan dari data historis.

### **2. Fungsi Game Logic**

- **`is_winner(board, player)`**: Mengecek apakah pemain tertentu telah menang.
- **`is_draw(board)`**: Mengecek apakah permainan berakhir seri.
- **`get_available_moves(board)`**: Mendapatkan daftar gerakan yang tersedia.
- **`apply_move(board, move, player)`**: Menerapkan gerakan pada papan.

### **3. Implementasi Agen Cerdas dengan BFS**

- **`bfs_agent_with_dataset(board, player, winning_paths)`**: Agen cerdas menggunakan BFS dan dataset untuk menentukan langkah terbaik.

### **4. Antarmuka dengan IPyWidgets**

- **State Permainan**: Variabel global digunakan untuk melacak state permainan.
- **Fungsi `render_board()`**: Menampilkan papan permainan interaktif.
- **Fungsi `player_move(cell_index)`**: Menghandle gerakan pemain dan agen.
- **Fungsi `reset_game(b)`**: Mereset permainan ke state awal.
- **Output Widgets**: Menggunakan `widgets.Output` untuk menampilkan pesan dan papan permainan secara interaktif tanpa menumpuk output.

---

## **Catatan Penting**

- **Interaktivitas dalam Colab**

  - Google Colab mendukung IPyWidgets, tetapi Anda perlu mengaktifkannya dengan menjalankan perintah:

    ```python
    !pip install ipywidgets
    from google.colab import output
    output.enable_custom_widget_manager()
    ```

- **Versi Library**

  - Pastikan library yang diinstal adalah versi terbaru untuk kompatibilitas terbaik.

- **Dataset**

  - Dataset `Tic tac initial results.csv` harus memiliki format yang benar dan diunggah ke Colab setiap kali Anda menjalankan notebook.

- **Manajemen State**

  - State permainan dikelola melalui variabel global. Pastikan untuk tidak mengubahnya secara manual selama permainan berlangsung.

---

## **Peningkatan yang Dapat Dilakukan**

- **Desain Antarmuka**

  - Menyesuaikan tampilan papan permainan dengan CSS atau menambahkan elemen visual lainnya untuk pengalaman bermain yang lebih baik.

- **Strategi Agen**

  - Mengembangkan strategi agen lebih lanjut atau menggunakan algoritma lain untuk meningkatkan kemampuan agen.

- **Analisis Permainan**

  - Menambahkan fitur untuk merekam dan menganalisis riwayat permainan.

- **Ekstensi Permainan**

  - Mengubah ukuran papan atau aturan permainan untuk variasi yang lebih menantang.

---
