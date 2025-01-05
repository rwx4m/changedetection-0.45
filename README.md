# CHANGEDETECTION.io 0.45.20

# Cara Kerja
ChangeDetection.io bekerja dengan cara mengambil snapshot dari halaman web yang dipantau pada interval waktu tertentu, lalu membandingkannya dengan snapshot sebelumnya untuk mendeteksi perubahan. Pengguna dapat menentukan URL halaman yang ingin dipantau untuk memantau area tertentu saja. Ketika perubahan terdeteksi, sistem akan mengirimkan notifikasi melalui metode yang dipilih, seperti Discord, Email, Slack, Telegram, API calls, dan lainnya. 

# Kerentanan
Kerentanan Server-Side Template Injection (SSTI) pada aplikasi changedetection.io yang menggunakan mesin template Jinja2. Kerentanan ini memungkinkan penyerang melakukan Remote Command Execution (RCE) pada host server, memberikan mereka kemampuan untuk menjalankan perintah sistem tanpa batasan, termasuk kemungkinan penggunaan reverse shell. Dampaknya sangat kritis karena penyerang dapat mengambil alih sepenuhnya mesin server.


Sumber :
CVE Details
Hacktive Security
Cyber Material
