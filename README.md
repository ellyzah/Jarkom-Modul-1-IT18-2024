# **LAPORAN RESMI PRAKTIKUM KOMUNIKASI DATA & JARINGAN KOMPUTER MODUL 1**

Berikut adalah Laporan Resmi Praktikum Komunikasi FData & Jaringan Komputer Modul 1 oleh Kelompok IT18.

---

## **TABLE OF CONTENT**

- [ATM or ATP or FTP ? 🤔](#soal1)
- [evidence](#soal2)
- [How Many packets?](#soal3)
- [trace him](#soal4)
- [creds](#soal5)
- [malwleowleo](#soal6)
- [whoami](#soal7)
- [secret](#soal8)
- [fuzz](#soal9)
- [malwaew](#soal10)

---

### **ATM or ATP or FTP ? 🤔<a name="soal1"></a>**

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **evidence<a name="soal2"></a>**

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **How Many packets?<a name="soal3"></a>**

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **trace him<a name="soal4"></a>**

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **creds<a name="soal5"></a>**

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **malwleowleo<a name="soal6"></a>**

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **whoami<a name="soal7"></a>**

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **secret<a name="soal8"></a>**

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **fuzz<a name="soal9"></a>**
>My website got hacked. Can you analyze this network traffic to help me track the attacker?

**A. PEMBAHASAN**

1. Filter protocol berdasarkan `http`. Lalu ketika dilihat pada info, terdapat response `HTTP/1.1 200 OK (text/htm)` respons ini menunjukkan bahwa server telah berhasil menemukan dan mengirimkan dokumen HTML yang diminta oleh klien, dan klien dapat menampilkan halaman web yang sesuai dengan konten HTML tersebut. Kemungkinan IP attacker merupakan IP destinasi yang mehasilkan info `HTTP/1.1 200 OK (text/htm)`

2. Kemudian follow salah satu IP addres yang memiliki info `HTTP/1.1 200 OK (text/htm)` , setelah itu muncul tools, port, dan source IP attacker. Jika dilihat terdapat endpoint berupa `/`, lalu user-agent `ffuf-v2.0.0dev`, untuk port bisa dilihat pada bagian Transmission Control Protocol yaitu `80`
  
3. Setelah dilihat, banyak IP yang didominasi Username & Password incorrect ketika memiliki info  `HTTP/1.1 200 OK (text/htm)`. Kemudian untuk mencoba mencari Username & Password yang correct, berarti kita filter IP yang tidak mengandung info `HTTP/1.1 200 OK (text/htm)` pada IP destination milik attacker dan source milik klien. Jadi yang memungkinkan bisa menggunakan display filter `http and ip.src eq 172.20.0.2 and ip.dst eq 10.33.1.154 and not (http contains "OK")`


4. Ternyata pada info terdapat kata kunci `Found`. Maka selanjutnya follow stream, kemudian find kata `Found` dalam stream tersebut. Hingga ditemukan Username & Password yang berhasil digunakan oleh attacker


**B. HASIL**

---

### **malwaew<a name="soal10"></a>**
> Ini adalah network traffic dari salah satu komputer di DPSSI yang terkena malware. Pak Sunhi, memintamu untuk membantu menganalisisnya. Bantulah Pak Sunhi untuk menemukan malware tersebut. Hint: decrypt tls first

**A. PEMBAHASAN**

1. Download attachment file yang disediakan pada soal (infected.zip), kemudian ekstrak file .zipnya. Maka akan terdapat 2 file yaitu capture.pcap dan keylog.txt

![a](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/61a0d504-2701-4d33-92a7-979d46760f19)

2. Sebelum itu, kita coba cek filter http, untuk mengetahui apakah ada traffic network berdasarkan web service

![a1](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/0b362563-99c7-4b02-b369-40eb24e593b4)

3. Kemudian buka file capture.pcap lalu akan diarahkan ke wireshark. Mengingat terdapat hint untuk decrypt TLS terlebih dahulu, maka klik Edit > Preferences > Protocols > TLS. Lalu pada (Pre)-Master-Secret.log filename klik Browse... lalu pilih file keylog.txt

![b](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/1236c18e-71cb-48c6-be33-6e6b98411294)

4. Setelah decrypt TLS, coba cek filter dengan protocol http lagi, maka beberapa file yang sebelumnya tidak ada/ sembunyi akan muncul. Jika dianalisis ada beberapa respon dan request yang terjadi. Di situ terdapat request GET yang berbeda sendiri yaitu pada sebuah file .dll. File .dll merupakan file yang bisa dieksekusi, kemungkinan ini adalah malware yang dimaksud.

![c](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/5b015123-f0a5-4c85-8a8e-daf6ea6bb670)

5. Lalu coba follow stream dan muncul data-data biner yang tidak jelas. Namun di situ terselipkan data bertuliskan `This program cannot be run in DOS mode.` artinya bahwa Ini adalah pesan yang umumnya ditemukan dalam berkas PE (Portable Executable) Windows, dan bisa menandakan bahwa ini adalah file biner Windows. Beberapa jenis malware mengirimkan pesan semacam ini untuk membingungkan analis keamanan. 

![d](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/cc4882bb-3215-45ba-9637-ced32a126310)

6. Ketika sudah dipastikan itu merupakan file malware, selanjutnya kita matikan antivirus laptop terlebih dahulu, agar ketika file diexport maka masih terjaga.

![d1](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/729b0078-8d09-4917-87dd-ae9cd123e566)
  
8. Jika antivirus windows sudah mati, maka klik File > Export Object > FTP-DATA , lalu save file export agar dapat masuk ke local device kita

![e](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/3025d414-2257-40f6-ae94-c8e6e55556b7)

9. Kemudian cek SHA-256 hash dari file invest_20.dll pada terminal linux

```
┌──(keyfee㉿ikiadfi)-[~/download]
└─$ shasum -a 256 invest_20.dll
31cf42b2a7c5c558f44cfc67684cc344c17d4946d3a1e0b2cecb8eb58173cb2f  invest_20.dll
```
![e1](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/f4a979ba-f36c-4e09-8ce5-b92743359f22)

10. Copy hash tersebut dan jawab pertanyaan pada `nc 10.15.40.20 10003` dan flag berhasil ditemukan

**B. HASIL**

![f](https://github.com/ellyzah/Jarkom-Modul-1-IT18-2024/assets/120791817/4dc7824d-b869-4d01-98cf-a99faf836fa8)

