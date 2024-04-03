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
- [fuzz](#soal10)

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

**A. PEMBAHASAN**

**B. HASIL**

**C. REVISI**

- Setelah direvisi

---

### **malwaew<a name="soal10"></a>**
> Ini adalah network traffic dari salah satu komputer di DPSSI yang terkena malware. Pak Sunhi, memintamu untuk membantu menganalisisnya. Bantulah Pak Sunhi untuk menemukan malware tersebut. Hint: decrypt tls first

**A. PEMBAHASAN**

1. Download attachment file yang disediakan pada soal (infected.zip), kemudian ekstrak file .zipnya. Maka akan terdapat 2 file yaitu capture.pcap dan keylog.txt

2. Sebelum itu, kita coba cek filter http, untuk mengetahui apakah ada traffic network berdasarkan web service

3. Kemudian buka file capture.pcap lalu akan diarahkan ke wireshark. Mengingat terdapat hint untuk decrypt TLS terlebih dahulu, maka klik Edit > Preferences > Protocols > TLS. Lalu pada (Pre)-Master-Secret.log filename klik Browse... lalu pilih file keylog.txt

4. Setelah decrypt TLS, coba cek filter dengan protocol http lagi, maka beberapa file yang sebelumnya tidak ada/ sembunyi akan muncul. Jika dianalisis ada beberapa respon dan request yang terjadi. Di situ terdapat request GET yang berbeda sendiri yaitu pada sebuah file .dll. File .dll merupakan file yang bisa dieksekusi, kemungkinan ini adalah malware yang dimaksud.

5. Lalu coba follow stream dan muncul data-data biner yang tidak jelas. Namun di situ terselipkan data bertuliskan

```
This program cannot be run in DOS mode.
```

artinya bahwa Ini adalah pesan yang umumnya ditemukan dalam berkas PE (Portable Executable) Windows, dan bisa menandakan bahwa ini adalah file biner Windows. Beberapa jenis malware mengirimkan pesan semacam ini untuk membingungkan analis keamanan. 

6. Ketika sudah dipastikan itu merupakan file malware, selanjutnya kita matikan antivirus laptop terlebih dahulu, agar ketika file diexport maka masih terjaga.
  
8. Jika antivirus windows sudah mati, maka klik File > Export Object > FTP-DATA , lalu save file export agar dapat masuk ke local device kita

9. Kemudian cek SHA-256 hash dari file invest_20.dll pada terminal linux

```
┌──(keyfee㉿ikiadfi)-[~/download]
└─$ shasum -a 256 invest_20.dll
31cf42b2a7c5c558f44cfc67684cc344c17d4946d3a1e0b2cecb8eb58173cb2f  invest_20.dll
```

10. Copy hash tersebut dan jawab pertanyaan pada `nc 10.15.40.20 10003` dan flag berhasil ditemukan

**B. HASIL**

