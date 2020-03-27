MENGGUNAKAN SENSOR SUHU DS18B20
<br>WIRING LIHAT GAMBAR
<br>VCC 3V
<br>
<br>CARA MENGGUNAKAN PERTAMA KALI
<br>SSH ke Pi Anda. Ketik perintah berikut:
<br>sudo modprobe w1-gpio
<br>sudo modprobe w1-therm
<br>Output dari sensor suhu Anda sekarang sedang ditulis ke file di Pi Anda. Untuk menemukan file yang sama,
<br>cd /sys/bus/w1/devices
<br>ketik ls untuk melihat list file
<br>Dalam direktori ini, akan ada sub-direktori yang dimulai dengan “28-“. Apa yang tertulis setelah “28-“ adalah nomor seri sensor Anda.
<br>masuk ke direktori tersebut dengan perintah cd 28-xxx
<br>Dalam direktori ini, sebuah file bernama w1_slave berisi output sensor Anda.
<br>masuk ke file tersebut dengan perintah nano w1_slave
<br> Isi dari file ini akan terlihat seperti ini:
<br>A2 01 4b 46 7f ff 0e 10 d8: crc = d8 Yes
<br>A2 01 4b 46 7f ff 0e 10 d8 t = 26125
<br>Jumlah setelah “t =” nomor yang kita inginkan. Ini adalah suhu di 1/1000 derajat Celcius 
<br>(dalam contoh di atas, suhu adalah 26.125 C). 
<br>Kita hanya perlu sebuah program sederhana yang membaca file ini dan mem-parsing nomor itu.
<br>isi program ada di file temp.py