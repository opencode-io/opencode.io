Helaian Rujukan Perintah Linux

Koleksi perintah Linux biasa untuk navigasi sistem, pengurusan fail, rangkaian dan lagi.

Kandungan

1. Perintah Asas
2. Pengoperasi
3. Pengurusan Fail dan Direktori
4. Kebenaran Fail
5. Screen
6. Penutupan dan Tidur
7. Pengurusan Pengguna
8. Pengurusan Pakej
9. Kerja Cron dan Penjadualan
10. Pengurusan Proses
11. Pemantauan Sistem
12. Pengurusan Systemd
13. Rangkaian
14. Pengurusan SSH
15. Pengurusan Mel
16. Pengurusan Kernel dan Modul
17. Boot, Bootloader (GRUB), dan Firmware EFI

___
Perintah Asas

Perintah Keterangan
pwd Cetak direktori kerja semasa
ls Senaraikan fail dalam direktori
cd <directory> Tukar direktori
whoami Paparkan pengguna semasa
echo <text> Cetak teks ke terminal
history Tunjukkan sejarah perintah

---

Maklumat Sistem

Perintah Keterangan
uname -a Paparkan maklumat sistem terperinci (kernel, nama hos, dll.)
uname -r Tunjukkan versi kernel
hostname Tunjukkan atau tetapkan nama hos sistem
hostnamectl Paparkan atau tetapkan nama hos sistem dan tetapan berkaitan
uptime Tunjukkan berapa lama sistem berjalan dan beban sistem
whoami Paparkan pengguna semasa
id Tunjukkan ID pengguna semasa dan maklumat kumpulan
who Tunjukkan siapa yang sedang log masuk ke sistem
w Paparkan siapa yang log masuk dan apa yang mereka lakukan
date Tunjukkan atau tetapkan tarikh dan masa sistem
cal Paparkan kalendar untuk bulan semasa
df -h Tunjukkan penggunaan ruang cakera dalam format mudah dibaca
du -h <directory> Paparkan penggunaan cakera fail dan direktori dalam format mudah dibaca
du -sh <directory> Paparkan jumlah saiz direktori
top Paparkan penggunaan sumber sistem dan proses secara masa nyata
free -h Tunjukkan penggunaan memori dalam format mudah dibaca
lscpu Paparkan maklumat seni bina CPU
lsblk Senaraikan maklumat tentang peranti blok (cakera, partition)
dmesg Paparkan mesej daripada penampan gelang kernel
lsusb Senaraikan maklumat tentang peranti USB
lspci Senaraikan maklumat tentang peranti PCI
uptime Paparkan masa hidup sistem dan purata beban
last Tunjukkan log masuk terakhir pengguna
uname -m Tunjukkan nama perkakasan mesin (cth., x86_64)

---

Pengoperasi

Pengoperasi Keterangan
` ` (Pipe)
> Ubah hala output ke fail, menimpa fail jika wujud (echo "Hello" > file.txt)
>> Ubah hala output ke fail, menambah jika fail wujud (echo "Hello" >> file.txt)
< Ubah hala input daripada fail ke perintah (sort < file.txt)
2> Ubah hala output ralat ke fail (command 2> error.log)
2>&1 Ubah hala output ralat ke output standard (command > file.txt 2>&1)
& Jalankan perintah di latar belakang (command &)
&& Jalankan perintah seterusnya hanya jika perintah sebelumnya berjaya (command1 && command2)
` 
; Jalankan berbilang perintah secara berturutan (command1; command2; command3)
$(command) Penggantian perintah: gunakan output perintah sebagai argumen (echo $(date))
&> Ubah hala kedua-dua output standard dan output ralat ke fail (command &> output.log)

---

Pengurusan Fail dan Direktori

Perintah Keterangan
ls Senaraikan fail dan direktori dalam direktori semasa
ls -l Senaraikan fail dan direktori dengan maklumat terperinci
ls -a Senaraikan semua fail, termasuk fail tersembunyi
cd <directory> Tukar ke direktori tertentu
cd .. Naik satu tahap direktori
pwd Paparkan direktori kerja semasa
mkdir <directory> Cipta direktori baharu
rmdir <directory> Buang direktori kosong
rm <file> Padam fail
rm -r <directory> Buang direktori dan kandungannya secara rekursif
rm -rf <directory> Padam secara paksa direktori dan kandungannya
cp <source> <destination> Salin fail atau direktori
cp -r <source-directory> <destination> Salin direktori secara rekursif
mv <source> <destination> Pindah atau namakan semula fail dan direktori
touch <file> Cipta fail kosong atau kemas kini cap masa fail sedia ada
ln -s <target> <link> Cipta pautan simbolik (pautan lembut)
ln <target> <link> Cipta pautan keras
cat <file> Paparkan kandungan fail
less <file> Lihat kandungan fail halaman demi halaman
more <file> Lihat kandungan fail halaman demi halaman (lebih lama daripada less)
head <file> Paparkan 10 baris pertama fail
tail <file> Paparkan 10 baris terakhir fail
tail -f <file> Paparkan kandungan fail secara masa nyata (ikuti fail semasa ia membesar)
find <directory> -name <filename> Cari fail atau direktori mengikut nama
find <directory> -type d -name <dirname> Cari direktori yang sepadan dengan nama tertentu
find <directory> -type f -name <filename> Cari fail yang sepadan dengan nama tertentu
grep "<pattern>" <file> Cari corak tertentu dalam fail
grep -r "<pattern>" <directory> Cari corak secara rekursif dalam direktori

---

Kebenaran Fail

Perintah Keterangan
ls -l Senaraikan fail dan tunjukkan kebenaran, pemilik dan kumpulan
chmod <permissions> <file> Ubah kebenaran fail atau direktori
chmod 644 <file> Tetapkan baca/tulis untuk pemilik dan baca sahaja untuk kumpulan dan lain-lain
chmod 755 <directory> Tetapkan baca/tulis/laksana untuk pemilik, baca/laksana untuk kumpulan dan lain-lain
chown <owner>:<group> <file> Ubah pemilik dan kumpulan fail atau direktori
chown <owner> <file> Ubah pemilik fail
chgrp <group> <file> Ubah kumpulan fail

---

Screen

Perintah Keterangan
screen Mulakan sesi screen baharu
screen -S <session_name> Mulakan sesi screen baharu dengan nama tersuai
screen -ls Senaraikan semua sesi screen aktif
screen -r <session_id> Sambung semula ke sesi screen yang terlepas
Ctrl + a + d Lepaskan daripada sesi screen semasa
screen -X -S <session_id> quit Paksa keluar sesi screen
Ctrl + a + k Hentikan screen semasa
screen -x <session_id> Sambung ke sesi yang sedang berjalan dikongsi oleh berbilang pengguna
Ctrl + a + n Tukar ke tetingkap seterusnya dalam sesi screen
Ctrl + a + p Tukar ke tetingkap sebelumnya dalam sesi screen
Ctrl + a + c Cipta tetingkap baharu dalam sesi screen semasa
Ctrl + a + " Senaraikan semua tetingkap dalam sesi semasa

---

Penutupan dan Tidur

Perintah Keterangan
shutdown now Tutup sistem serta-merta
shutdown -h now Hentikan sistem serta-merta
shutdown -r now Mulakan semula sistem serta-merta
shutdown -h +<time> Jadualkan penutupan selepas masa tertentu (cth., +10 untuk 10 minit)
shutdown -c Batal penutupan berjadual
reboot But semula sistem
halt Hentikan sistem tanpa mematikan kuasa
systemctl poweroff Matikan kuasa sistem
systemctl reboot But semula sistem
systemctl suspend Gantung sistem (mod tidur)
systemctl hibernate Hibernasi sistem
systemctl hybrid-sleep Hibernasi dan gantung sistem
pm-suspend Gantung sistem (jika pm-utils dipasang)
pm-hibernate Hibernasi sistem (jika pm-utils dipasang)
pm-suspend-hybrid Hibernasi dan gantung sistem (jika pm-utils dipasang)

---

Pengurusan Pengguna

Perintah Keterangan
adduser <username> Cipta pengguna baharu dengan direktori home dan shell lalai
useradd <username> Cipta pengguna baharu (persediaan minimum, tiada direktori home secara lalai)
userdel <username> Padam akaun pengguna
userdel -r <username> Padam akaun pengguna dan direktori home mereka
passwd <username> Tukar kata laluan untuk pengguna
chage -l <username> Paparkan maklumat tempoh luput kata laluan untuk pengguna
usermod -aG <groupname> <username> Tambah pengguna ke kumpulan
groups <username> Senaraikan kumpulan yang pengguna sertai
id <username> Tunjukkan ID pengguna (UID), ID kumpulan (GID), dan keahlian kumpulan lain
deluser <username> Buang pengguna daripada sistem
deluser <username> <groupname> Buang pengguna daripada kumpulan tertentu
sudo <command> Laksanakan perintah sebagai superuser
su <username> Tukar ke akaun pengguna lain (memerlukan kata laluan pengguna itu)
who Tunjukkan siapa yang log masuk
whoami Paparkan pengguna yang sedang log masuk
last Tunjukkan log masuk terakhir pengguna
w Paparkan siapa yang log masuk dan apa yang mereka lakukan
finger <username> Paparkan maklumat terperinci tentang pengguna
getent passwd Paparkan semua pengguna dalam sistem
vipw Sunting /etc/passwd dengan selamat (akaun pengguna)
visudo Sunting /etc/sudoers dengan selamat
chown <owner>:<group> <file> Ubah pemilikan fail
chmod <permissions> <file> Ubah kebenaran fail

---

Pengurusan Kumpulan

Perintah Keterangan
groupadd <groupname> Cipta kumpulan baharu
groupdel <groupname> Padam kumpulan
gpasswd -a <username> <groupname> Tambah pengguna ke kumpulan (alternatif kepada usermod -aG)
gpasswd -d <username> <groupname> Buang pengguna daripada kumpulan
newgrp <groupname> Tukar ke kumpulan baharu untuk sesi semasa
groups <username> Paparkan kumpulan yang pengguna sertai
getent group <groupname> Tunjukkan entri kumpulan dalam /etc/group

---

Pengurusan Akaun dan Sesi

Perintah Keterangan
chage -E <date> <username> Tetapkan tarikh luput akaun untuk pengguna
chage -M <days> <username> Tetapkan bilangan maksimum hari kata laluan kekal sah
chage -m <days> <username> Tetapkan bilangan minimum hari sebelum kata laluan boleh ditukar
chage -I <days> <username> Tetapkan bilangan hari selepas kata laluan luput sebelum akaun dilumpuhkan
faillog -u <username> Tunjukkan statistik kegagalan log masuk untuk pengguna
faillog -r <username> Tetapkan semula kiraan log masuk gagal untuk pengguna
lastlog Tunjukkan log masuk terakhir semua pengguna
pkill -u <username> Tamatkan semua proses milik pengguna
passwd -l <username> Kunci akaun pengguna (tidak dibenarkan log masuk)
passwd -u <username> Buka kunci akaun pengguna
nologin Halang pengguna daripada log masuk dengan menetapkan shell mereka kepada /sbin/nologin

---

Pengurusan Pakej

Debian/Ubuntu

Perintah Keterangan
apt-get update Kemas kini senarai pakej
apt-get upgrade Tingkatkan semua pakej yang dipasang
apt-get install <package> Pasang pakej
apt-get remove <package> Buang pakej

Red Hat/CentOS

Perintah Keterangan
yum update Kemas kini senarai pakej
yum install <package> Pasang pakej
yum remove <package> Buang pakej

---

Kerja Cron dan Penjadualan

Mengurus Kerja Cron

Perintah Keterangan
crontab -e Sunting fail crontab pengguna semasa
crontab -l Senaraikan kerja cron pengguna semasa
crontab -r Buang fail crontab pengguna semasa
sudo crontab -e -u <username> Sunting crontab untuk pengguna tertentu
sudo crontab -l -u <username> Senaraikan crontab untuk pengguna tertentu
sudo crontab -r -u <username> Buang crontab untuk pengguna tertentu

---

Sintaks Kerja Cron

Kerja cron ditakrifkan menggunakan sintaks berikut:

<p>* * * * * command_to_run</p>

Contoh Entri Kerja Cron

Entri Keterangan
0 5 * * * /path/to/script.sh Jalankan skrip setiap hari pada 5:00 pagi
*/15 * * * * /path/to/backup.sh Jalankan skrip sandaran setiap 15 minit
0 0 1 * * /path/to/report.sh Jalankan skrip laporan pada tengah malam hari pertama setiap bulan
30 2 * * 1 /path/to/cleanup.sh Jalankan skrip pembersihan setiap Isnin pada 2:30 pagi

---

Kerja Cron Seluruh Sistem

Kerja cron seluruh sistem dikonfigurasikan dalam /etc/crontab dan juga boleh ditemui dalam direktori /etc/cron.d/.

Penjadualan dengan at

Perintah at digunakan untuk menjadualkan tugas sekali sahaja.

Perintah Keterangan
at 10:00 Jadualkan perintah untuk dijalankan pada 10:00 pagi (minta perintah)
`echo "command_to_run" at 10:00`
atq Senaraikan kerja berjadual untuk pengguna semasa
atrm <job_number> Buang kerja berjadual mengikut nombor kerja

---

Pengurusan Proses:

Melihat Proses

Perintah Keterangan
ps aux Senaraikan semua proses yang berjalan secara terperinci
ps -ef Senaraikan proses dengan output format penuh
top Tunjukkan penggunaan sumber sistem masa nyata (CPU, memori, proses)
htop Pelihat proses interaktif dipertingkat (htop perlu dipasang secara berasingan)
pgrep <name> Cari PID proses mengikut nama
pidof <process> Cari PID proses yang berjalan
pstree Paparkan proses dalam format seperti pokok

Mengurus Proses

Perintah Keterangan
kill <PID> Tamatkan proses mengikut PID
kill -9 <PID> Bunuh proses secara paksa
killall <name> Bunuh semua proses mengikut nama
pkill <name> Bunuh proses mengikut nama (menyokong ungkapan nalar)
bg Sambung kerja yang digantung di latar belakang
fg Bawa kerja latar belakang ke hadapan
jobs Senaraikan semua kerja latar belakang dalam shell semasa
nice -n <priority> <command> Mulakan proses dengan keutamaan tertentu (nilai lebih rendah = keutamaan lebih tinggi)
renice <priority> <PID> Ubah keutamaan proses yang berjalan

Memantau Proses

Perintah Keterangan
top Paparkan maklumat masa nyata tentang proses berjalan dan penggunaan sumber
htop Versi interaktif top (pasang berasingan dengan sudo apt-get install htop)
uptime Tunjukkan berapa lama sistem berjalan
free -m Paparkan penggunaan memori sistem dalam megabait
vmstat Laporkan statistik memori maya
lsof Senaraikan fail terbuka oleh proses
strace -p <PID> Jejaki panggilan sistem yang dibuat oleh proses
watch <command> Laksanakan perintah berulang kali dan pantau output secara masa nyata

Isyarat

Proses Linux boleh dihantar pelbagai isyarat untuk mengawal tingkah laku mereka.

Isyarat Nombor Keterangan
SIGHUP 1 Gantung, muat semula konfigurasi
SIGINT 2 Gangguan daripada papan kekunci (Ctrl + C)
SIGKILL 9 Isyarat bunuh, tidak boleh diabaikan
SIGTERM 15 Isyarat penamatan
SIGSTOP 19 Hentikan proses (tidak boleh diabaikan)
SIGCONT 18 Sambung proses yang dihentikan

---

Pengurusan Proses Latar Belakang & Hadapan

Perintah Keterangan
command & Jalankan perintah di latar belakang
bg Sambung kerja yang digantung di latar belakang
fg Bawa kerja latar belakang ke hadapan
jobs Senaraikan kerja semasa dan statusnya
nohup <command> & Jalankan perintah kebal terhadap gantung, di latar belakang
disown <job> Buang kerja daripada jadual kerja, biarkan ia berjalan

---

Pemilikan Proses dan Keselamatan

Perintah Keterangan
ps -u <username> Senaraikan semua proses milik pengguna
sudo -u <username> <command> Jalankan perintah sebagai pengguna lain
chown <owner>:<group> <file> Ubah pemilikan fail atau direktori
chmod <permissions> <file> Ubah suai kebenaran untuk fail atau direktori
setfacl -m u:<user>:rwx <file> Tetapkan senarai kawalan akses fail (ACL) untuk pengguna pada fail
getfacl <file> Lihat kebenaran ACL fail

---

Memantau Penggunaan CPU dan Memori oleh Proses

Perintah Keterangan
top Paparkan proses disusun mengikut penggunaan CPU
htop Pelihat proses interaktif masa nyata
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu Senaraikan proses disusun mengikut penggunaan CPU
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem Senaraikan proses disusun mengikut penggunaan memori

---

Pengurusan Systemd

systemd ialah pengurus sistem dan perkhidmatan untuk sistem pengendalian Linux. Ia bertanggungjawab mengurus perkhidmatan, proses dan pelbagai unit.

Perintah Keterangan
systemctl Perintah utama untuk mengurus perkhidmatan dan unit systemd
systemctl status <service> Semak status perkhidmatan
systemctl start <service> Mulakan perkhidmatan
systemctl stop <service> Hentikan perkhidmatan yang berjalan
systemctl restart <service> Mulakan semula perkhidmatan
systemctl reload <service> Muat semula konfigurasi perkhidmatan tanpa memulakan semula
systemctl enable <service> Dayakan perkhidmatan untuk bermula semasa boot
systemctl disable <service> Lumpuhkan perkhidmatan daripada bermula semasa boot
systemctl is-enabled <service> Semak sama ada perkhidmatan didayakan untuk bermula semasa boot
systemctl daemon-reload Muat semula fail konfigurasi pengurus systemd selepas perubahan
systemctl list-units --type=service Senaraikan semua perkhidmatan systemd
systemctl list-units --failed Senaraikan perkhidmatan gagal
journalctl -u <service> Lihat log untuk perkhidmatan tertentu
journalctl -xe Lihat log systemd dengan lebih terperinci tentang ralat
systemctl mask <service> Lumpuhkan perkhidmatan sepenuhnya, walaupun perkhidmatan lain cuba memulakannya
systemctl unmask <service> Dayakan semula perkhidmatan yang dimask
systemctl show <service> Tunjukkan sifat terperinci perkhidmatan
systemctl cat <service> Lihat fail unit untuk perkhidmatan
systemctl isolate <target> Tukar ke sasaran sistem tertentu (cth., multi-user.target, rescue.target)

Jenis Unit Systemd

Systemd mengurus pelbagai jenis unit, bukan hanya perkhidmatan.

Jenis Unit Keterangan
.service Perkhidmatan sistem (cth., pelayan web, pangkalan data)
.socket Soket untuk komunikasi antara proses
.device Unit peranti yang didedahkan oleh kernel Linux
.mount Titik lekap sistem fail
.automount Titik lekap yang dilekap secara automatik apabila diakses
.swap Peranti atau fail swap
.target Kumpulan unit systemd (cth., multi-user.target)
.timer Unit penjadualan serupa dengan kerja cron

Sasaran Biasa

Perintah Keterangan
systemctl get-default Tunjukkan sasaran lalai semasa (cth., multi-user, graphical)
systemctl set-default <target> Tetapkan sasaran lalai (cth., multi-user.target, graphical.target)
systemctl isolate <target> Tukar sistem ke sasaran yang ditentukan (cth., rescue.target)

---

Rangkaian

Pengurusan Antara Muka Rangkaian

Perintah Keterangan
ip addr Tunjukkan semua antara muka rangkaian dan alamat IP mereka
ip -a Tunjukkan semua antara muka rangkaian dan alamat IP mereka
ip addr show <interface> Paparkan maklumat tentang antara muka rangkaian tertentu
ip link set <interface> up Hidupkan antara muka rangkaian
ip link set <interface> down Matikan antara muka rangkaian
ifconfig Paparkan atau konfigurasi antara muka rangkaian (perintah lama, gunakan ip untuk sistem baharu)
ifconfig <interface> Tunjukkan butiran tentang antara muka rangkaian tertentu
ifdown <interface> Matikan antara muka rangkaian (sistem berasaskan Debian)
ifup <interface> Hidupkan antara muka rangkaian (sistem berasaskan Debian)
ethtool <interface> Paparkan atau ubah tetapan peranti Ethernet
ip route Paparkan atau ubah suai jadual penghalaan
ip route add <destination> via <gateway> Tambah laluan baharu ke jadual penghalaan
ip route del <destination> Buang laluan daripada jadual penghalaan
hostname Tunjukkan atau tetapkan nama hos sistem
hostname -I Paparkan semua alamat IP hos
nmcli dev show <interface> Paparkan status sambungan antara muka rangkaian tertentu (NetworkManager)
nmcli device status Tunjukkan status semua antara muka rangkaian (NetworkManager)
nmcli connection show Paparkan sambungan rangkaian tersimpan (NetworkManager)
nmcli connection up <connection-name> Hidupkan sambungan rangkaian tertentu (NetworkManager)
nmcli connection down <connection-name> Matikan sambungan rangkaian tertentu (NetworkManager)
sudo nmcli connection reload Muat semula sambungan
nmtui Antara muka pengguna berasaskan teks untuk mengurus sambungan rangkaian
sudo systemctl restart NetworkManager Terapkan konfigurasi
sudo nmtui UI untuk mengurus rangkaian dalam RHEL
cat /etc/sysconfig/network-scripts/ifcfg-eth160 konfigurasi IP dalam Red Hat

---

Pengurusan DNS

Perintah Keterangan
dig <domain> Tanya maklumat DNS untuk domain
dig +short <domain> Dapatkan output pendek (cth., hanya alamat IP)
dig @<nameserver> <domain> Tanya pelayan DNS tertentu untuk resolusi domain
nslookup <domain> Tanya maklumat DNS untuk domain
host <domain> Lakukan carian DNS dan carian songsang
systemd-resolve --status Tunjukkan status resolusi DNS (systemd-resolved)
resolvectl query <domain> Tanya DNS menggunakan systemd-resolved
cat /etc/resolv.conf Paparkan konfigurasi pelayan DNS

---

Penyelesaian Masalah Rangkaian

Perintah Keterangan
ping <host> Semak ketersambungan ke hos
ping -c <count> <host> Hantar bilangan permintaan gema ICMP tertentu ke hos
ping6 <host> Hantar permintaan gema ICMP ke hos menggunakan IPv6
traceroute <host> Jejaki laluan paket untuk sampai ke hos
tracepath <host> Serupa dengan traceroute, tetapi tidak memerlukan keistimewaan superuser
mtr <host> Menggabungkan ping dan traceroute untuk analisis rangkaian berterusan
netstat -tuln Tunjukkan port dan perkhidmatan yang mendengar
ss -tuln Tunjukkan soket yang mendengar (lebih moden daripada netstat)
nc -zv <host> <port> Semak sama ada port tertentu terbuka pada hos (ujian sambungan TCP/UDP)
nc -l <port> Buka port dan dengar sambungan masuk
telnet <host> <port> Semak ketersambungan TCP ke hos dan port
curl <url> Lakukan permintaan HTTP asas dan paparkan respons
curl -I <url> Paparkan pengepala HTTP untuk URL
curl -O <url> Muat turun fail daripada URL
wget <url> Muat turun fail daripada web menggunakan HTTP, HTTPS atau FTP
arp -a Paparkan jadual ARP sistem (menunjukkan pemetaan MAC ke IP)
tcpdump Tangkap dan analisis trafik rangkaian
tcpdump -i <interface> Tangkap paket pada antara muka rangkaian tertentu
tcpdump -nn -X port <port> Tangkap paket pada port dan paparkan kandungan paket dalam heksadesimal

---

Pengurusan Firewall (iptables dan firewalld)

Perintah Keterangan
iptables -L Senaraikan semua peraturan firewall
iptables -A <chain> -p <protocol> --dport <port> -j <target> Tambah peraturan pada rantai (cth., ACCEPT, DROP)
iptables -D <chain> <rule-number> Padam peraturan tertentu daripada rantai
iptables -F Kosongkan (padam) semua peraturan firewall
firewall-cmd --list-all Senaraikan semua peraturan firewalld aktif (CentOS, Fedora)
firewall-cmd --add-service=<service> Benarkan perkhidmatan melalui firewall sementara
firewall-cmd --permanent --add-service=<service> Benarkan perkhidmatan melalui firewall secara kekal
firewall-cmd --remove-service=<service> Buang perkhidmatan daripada firewall
ufw status Paparkan status UFW (Uncomplicated Firewall) (Ubuntu)
ufw enable Dayakan UFW
ufw disable Lumpuhkan UFW
ufw allow <port>/<protocol> Benarkan trafik pada port (cth., ufw allow 22/tcp)
ufw deny <port>/<protocol> Tolak trafik pada port

---

Pemindahan Fail Rangkaian

Perintah Keterangan
scp <source> <user>@<host>:<destination> Salin fail ke hos jauh dengan selamat
scp <user>@<host>:<source> <destination> Salin fail daripada hos jauh dengan selamat
rsync -avz <source> <user>@<host>:<destination> Segerakkan fail antara hos tempatan dan jauh
rsync -avz <user>@<host>:<source> <destination> Segerakkan fail daripada jauh ke tempatan
sftp <user>@<host> Mulakan sesi pemindahan fail selamat
ftp <host> Mulakan sesi FTP (tidak disulitkan)

---

SSH dan Sambungan Jauh

Perintah Keterangan
ssh <user>@<host> Sambung ke hos jauh melalui SSH
ssh -i <keyfile> <user>@<host> Sambung ke hos jauh menggunakan kunci peribadi tertentu
ssh -L <local-port>:<remote-host>:<remote-port> <user>@<host> Cipta terowong SSH dengan pemajuan port
ssh-copy-id <user>@<host> Salin kunci SSH tempatan ke hos jauh untuk mendayakan log masuk tanpa kata laluan
scp <user>@<host>:<source> <destination> Salin fail antara hos tempatan dan jauh dengan selamat
sftp <user>@<host> Pindahkan fail ke/daripada hos jauh dengan selamat menggunakan SFTP
tmux Mulakan sesi multiplekser terminal (kekalkan sesi SSH)
screen Mulakan sesi screen (kekalkan sesi SSH)

Pemantauan Sistem

Bahagian ini menyediakan perintah untuk memantau prestasi sistem, proses, CPU, memori, I/O cakera dan aktiviti rangkaian.

Pemantauan Sistem Am

Perintah Keterangan
top Paparan masa nyata penggunaan CPU dan memori oleh proses
htop Versi top interaktif dipertingkat dengan ciri tambahan (mungkin perlu dipasang)
vmstat Laporkan statistik memori maya, termasuk proses, memori, penukaran halaman, I/O blok dan aktiviti CPU
glances Alat pemantauan sistem menyeluruh (perlu dipasang)
uptime Tunjukkan berapa lama sistem berjalan dan beban sistem
watch <command> Jalankan perintah berulang kali pada selang tetap dan paparkan output secara langsung

---

Pemantauan CPU

Perintah Keterangan
mpstat Paparkan penggunaan CPU setiap teras (daripada pakej sysstat)
sar Kumpul, laporkan dan simpan maklumat aktiviti sistem (termasuk CPU, memori, I/O, dll.)
lscpu Paparkan maklumat seni bina CPU (model, teras, kelajuan)
cat /proc/cpuinfo Paparkan maklumat CPU terperinci
iostat Statistik CPU dan I/O, sebahagian daripada pakej sysstat

---

Pemantauan Memori

Perintah Keterangan
free -h Paparkan penggunaan memori dalam format mudah dibaca (jumlah, digunakan, bebas, swap)
vmstat -s Statistik memori dan swap dalam format terperinci
cat /proc/meminfo Lihat statistik memori terperinci
watch free -h Pantau penggunaan memori secara masa nyata
dmidecode --type memory Paparkan maklumat terperinci tentang memori yang dipasang (memerlukan root)

---

Penggunaan Cakera dan Pemantauan I/O

Perintah Keterangan
df -h Paparkan penggunaan ruang cakera dalam format mudah dibaca
du -sh <directory> Paparkan jumlah saiz direktori dalam format mudah dibaca
iostat Tunjukkan statistik I/O cakera dan penggunaan CPU (daripada pakej sysstat)
iotop Paparkan penggunaan I/O cakera masa nyata oleh proses (perlu dipasang)
dstat Statistik sumber menyeluruh (termasuk I/O cakera)
lsblk Senaraikan peranti blok, partition dan sistem fail
blkid Paparkan atribut peranti blok seperti UUID dan jenis sistem fail
df -i Tunjukkan penggunaan inod untuk sistem fail
du -ah <directory> Tunjukkan penggunaan cakera untuk semua fail dan direktori
hdparm -t /dev/sda Uji kelajuan baca cakera (mungkin perlu dipasang)

---

Pemantauan Proses

Perintah Keterangan
ps aux Senaraikan semua proses berjalan dengan maklumat terperinci
pgrep <process-name> Cari proses berjalan mengikut nama
pidof <process-name> Cari ID proses (PID) bagi proses yang berjalan
pstree Tunjukkan proses dalam format seperti pokok
kill <PID> Hantar isyarat untuk menamatkan proses menggunakan PID
killall <process-name> Tamatkan semua proses yang sepadan dengan nama tertentu
pkill <process-name> Hantar isyarat kepada proses berdasarkan nama dan atribut lain
renice <priority> <PID> Ubah keutamaan proses yang berjalan
strace -p <PID> Jejaki panggilan sistem dan isyarat untuk proses tertentu
lsof Senaraikan fail terbuka oleh proses
lsof -i :<port> Senaraikan proses yang menggunakan port rangkaian tertentu
nice -n <priority> <command> Mulakan perintah dengan keutamaan tertentu

---

Pemantauan Rangkaian

Perintah Keterangan
netstat -tuln Tunjukkan port yang mendengar dan perkhidmatan berkaitan
ss -tuln Versi lebih moden netstat, menunjukkan port yang mendengar
iftop Paparkan penggunaan jalur lebar rangkaian masa nyata (perlu dipasang)
nload Tunjukkan trafik rangkaian masuk dan keluar (perlu dipasang)
tcpdump -i <interface> Tangkap dan paparkan paket rangkaian pada antara muka tertentu
iptraf-ng Pemantauan trafik rangkaian masa nyata (perlu dipasang)
ping <hostname/IP> Uji ketersambungan rangkaian dengan menghantar permintaan gema ICMP
traceroute <hostname/IP> Jejaki laluan paket untuk sampai ke hos rangkaian
ss -s Tunjukkan statistik soket terperinci
arp -a Paparkan jadual ARP sistem (protokol resolusi alamat)
dig <hostname> Tanya pelayan DNS untuk maklumat tentang nama hos
host <hostname> Lakukan carian DNS untuk domain atau alamat IP
nslookup <hostname> Tanya DNS untuk menyelesaikan nama hos kepada alamat IP
mtr <hostname> Alat diagnostik rangkaian menggabungkan ping dan traceroute (perlu dipasang)

---

Pemantauan Sistem Lain-lain

Perintah Keterangan
uptime Tunjukkan berapa lama sistem berjalan dan purata beban semasa
last Tunjukkan log masuk terakhir pengguna pada sistem
sar Kumpul dan paparkan statistik aktiviti sistem (CPU, memori, I/O, rangkaian)
dstat Alat untuk menghasilkan statistik prestasi dan sumber terperinci
vmstat Laporkan maklumat tentang proses, memori, penukaran halaman dan I/O
iostat -x Tunjukkan statistik I/O lanjutan, termasuk penggunaan cakera
tload Tunjukkan perwakilan grafik beban sistem dalam terminal
uptime Paparkan masa hidup sistem dan purata beban
w Tunjukkan siapa yang log masuk dan apa yang mereka lakukan
who Tunjukkan siapa yang log masuk ke sistem

Pengurusan SSH

SSH (Secure Shell) ialah protokol yang digunakan untuk mengakses mesin jauh dengan selamat melalui rangkaian. Bahagian ini merangkumi perintah untuk mengurus sambungan SSH, kunci dan konfigurasi.

Perintah SSH Asas

Perintah Keterangan
ssh <user>@<host> Sambung ke hos jauh sebagai pengguna yang ditentukan
ssh -p <port> <user>@<host> Sambung ke hos jauh pada port tertentu
ssh -i <keyfile> <user>@<host> Sambung menggunakan fail kunci peribadi tertentu
ssh -L <local_port>:<remote_host>:<remote_port> <user>@<host> Cipta terowong SSH untuk pemajuan port tempatan
ssh -R <remote_port>:<local_host>:<local_port> <user>@<host> Cipta terowong SSH untuk pemajuan port jauh
ssh -D <local_port> <user>@<host> Sediakan proksi SOCKS pada port tempatan yang ditentukan
scp <file> <user>@<host>:<remote_path> Salin fail ke hos jauh menggunakan SSH
scp <user>@<host>:<remote_path> <local_path> Salin fail daripada hos jauh ke mesin tempatan
rsync -avz -e "ssh -p <port>" <source> <user>@<host>:<destination> Segerakkan fail dengan hos jauh melalui SSH

---

Pengurusan Kunci SSH

Kunci SSH menyediakan cara selamat untuk pengesahan tanpa menggunakan kata laluan.

Perintah Keterangan
ssh-keygen -t rsa -b 4096 -C "your_email@example.com" Jana pasangan kunci SSH baharu (RSA, 4096 bit)
ssh-add <keyfile> Tambah kunci peribadi ke ejen pengesahan SSH
ssh-copy-id <user>@<host> Pasang kunci awam anda pada hos jauh untuk pengesahan tanpa kata laluan
cat ~/.ssh/id_rsa.pub Paparkan kunci awam anda untuk dikongsi
ssh-agent bash Mulakan shell baharu dengan ejen SSH berjalan
ssh-keygen -R <host> Buang hos yang ditentukan daripada fail known_hosts
ssh -Q key Senaraikan jenis kunci yang disokong

---

Pilihan Konfigurasi SSH Biasa

Pilihan Keterangan
Host <name> Alias untuk konfigurasi hos
HostName <hostname> Nama hos sebenar atau alamat IP untuk disambung
User <username> Nama pengguna lalai untuk log masuk
Port <port_number> Port untuk disambung (lalai ialah 22)
IdentityFile <path> Laluan ke fail kunci peribadi untuk pengesahan
ForwardAgent yes Dayakan pemajuan ejen SSH
StrictHostKeyChecking no Lumpuhkan pengesahan kunci hos (tidak disyorkan untuk keselamatan)

---

Pengurusan Kunci SSH untuk Pengguna

Perintah Keterangan
ssh-keygen Jana pasangan kunci SSH baharu
ssh-copy-id <username>@<host> Salin kunci SSH ke hos jauh untuk log masuk tanpa kata laluan
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys Tambah kunci awam SSH secara manual untuk pengesahan pengguna
chmod 600 ~/.ssh/authorized_keys Tetapkan kebenaran yang betul untuk kunci dibenarkan SSH

---

Amalan Terbaik Keselamatan SSH

Amalan Terbaik Keterangan
Gunakan kunci SSH dan bukannya kata laluan Kunci SSH memberikan keselamatan lebih baik daripada kata laluan.
Lumpuhkan log masuk root Halang log masuk SSH langsung sebagai root dengan menyunting /etc/ssh/sshd_config:
 ```plaintext
PermitRootLogin no 
``` 
Gunakan frasa laluan yang kukuh untuk kunci SSH Lindungi kunci peribadi dengan frasa laluan yang kukuh.
Tukar port SSH lalai Sunting /etc/ssh/sshd_config dan tukar Port 22 kepada port lain.
Dayakan pengesahan dua faktor Tambah lapisan keselamatan tambahan dengan 2FA menggunakan alat seperti Google Authenticator.

---

Konfigurasi SSH

Klien SSH boleh dikonfigurasikan menggunakan fail ~/.ssh/config untuk kemudahan dan kegunaan.

Contoh Konfigurasi SSH

```plaintext
# Tetapan lalai
Host *
    User your_username
    Port 22
    IdentityFile ~/.ssh/id_rsa

# Konfigurasi hos khusus
Host myserver
    HostName myserver.example.com
    User myuser
    Port 2222
    IdentityFile ~/.ssh/myserver_id_rsa
```

Pengurusan Mel

Menghantar Mel

Perintah Keterangan
mail <recipient> Buka klien mel untuk menghantar e-mel
`echo "Email body" mail -s "Subject" <recipient>`
sendmail <recipient> Hantar e-mel menggunakan perintah sendmail
mailx -s "Subject" <recipient> < <file> Hantar kandungan fail sebagai badan e-mel
mutt -s "Subject" <recipient> < <file> Hantar e-mel dengan subjek menggunakan mutt
ssmtp <recipient> Hantar e-mel menggunakan ssmtp (klien SMTP ringkas)
mail -c <cc_recipient> Hantar salinan karbon (CC) kepada penerima lain
mail -b <bcc_recipient> Hantar salinan karbon buta (BCC) kepada penerima lain

---

Perkhidmatan Mel Biasa

Perkhidmatan Keterangan
postfix Ejen pemindahan mel (MTA) yang digunakan secara meluas
sendmail Ejen pemindahan mel tradisional, sering digunakan untuk menghantar mel
exim Satu lagi ejen pemindahan mel popular
ssmtp Utiliti ringkas untuk menghantar e-mel melalui SMTP
mutt Klien e-mel berasaskan teks untuk Unix
mailx Versi dipertingkat perintah mail

---

Penyelesaian Masalah Mel

Perintah Keterangan
tail -f /var/log/mail.log Pantau log mel untuk isu penghantaran (Debian/Ubuntu)
grep "error" /var/log/mail.log Cari ralat dalam log mel
mailq Lihat baris gilir mel
sendmail -bv <recipient> Sahkan sama ada e-mel boleh dihantar kepada penerima

Konfigurasi Mel

Fail konfigurasi untuk perkhidmatan mel biasanya boleh ditemui dalam /etc/mail/ atau /etc/.

Contoh Konfigurasi /etc/ssmtp/ssmtp.conf

```plaintext
root=postmaster
mailhub=smtp.example.com:587
AuthUser=username
AuthPass=password
UseSTARTTLS=YES
```

Pengurusan Kernel dan Modul

Bahagian ini menyediakan perintah untuk mengurus kernel Linux dan modulnya, termasuk memuat, memunggah dan menanyakan modul kernel.

Maklumat Kernel

Perintah Keterangan
uname -r Paparkan versi kernel semasa
uname -a Paparkan semua maklumat sistem, termasuk versi kernel
hostnamectl Tunjukkan maklumat tentang hos, termasuk versi kernel
cat /proc/version Paparkan maklumat versi kernel daripada sistem fail /proc
dmesg Paparkan mesej log boot dan kernel
`dmesg grep <keyword>`
ls /boot/ Senaraikan fail berkaitan kernel, termasuk imej kernel

---

Pengurusan Modul Kernel

Perintah Keterangan
lsmod Senaraikan modul kernel yang dimuatkan semasa
modinfo <module_name> Paparkan maklumat terperinci tentang modul kernel tertentu
modprobe <module_name> Muat modul kernel ke dalam kernel yang berjalan
modprobe -r <module_name> Buang modul kernel daripada kernel yang berjalan
insmod <path_to_module> Masukkan modul ke dalam kernel (memerlukan laluan penuh ke fail modul)
rmmod <module_name> Buang modul kernel
depmod -a Jana senarai kebergantungan modul
modprobe --show-depends <module_name> Tunjukkan kebergantungan modul sebelum memuatkannya
ls /lib/modules/$(uname -r)/kernel/ Senaraikan modul kernel yang tersedia untuk kernel semasa

---

Pengurusan Parameter Kernel

Perintah Keterangan
sysctl -a Paparkan semua parameter kernel (tetapan sysctl)
sysctl <parameter> Lihat nilai semasa parameter kernel tertentu
sysctl -w <parameter>=<value> Tetapkan nilai parameter kernel semasa runtime
cat /proc/sys/<parameter> Lihat nilai semasa parameter kernel terus daripada sistem fail /proc
echo <value> > /proc/sys/<parameter> Ubah parameter kernel sementara (sehingga but semula)
nano /etc/sysctl.conf Sunting fail konfigurasi sysctl untuk menggunakan perubahan parameter kernel secara kekal
sysctl -p Muat semula tetapan sysctl daripada fail konfigurasi

---

Parameter Boot Kernel

Perintah Keterangan
cat /proc/cmdline Tunjukkan parameter kernel yang dihantar semasa boot
nano /etc/default/grub Sunting konfigurasi GRUB untuk mengubah parameter boot kernel secara kekal
grub-mkconfig -o /boot/grub/grub.cfg Bina semula fail konfigurasi GRUB selepas membuat perubahan
update-grub Kemas kini GRUB untuk menggunakan perubahan konfigurasi boot

---

Membina Semula Initramfs

Perintah Keterangan
mkinitcpio -p linux Bina semula initramfs untuk sistem berasaskan Arch
update-initramfs -u Kemas kini initramfs untuk kernel semasa (Debian/Ubuntu)
dracut -f Jana semula initramfs pada sistem yang menggunakan Dracut

---

Naik Taraf dan Pengurusan Kernel

Perintah Keterangan
apt-cache search linux-image Cari versi kernel tersedia (Debian/Ubuntu)
apt install linux-image-<version> Pasang versi kernel tertentu (Debian/Ubuntu)
dnf list kernel Senaraikan versi kernel tersedia (Fedora)
dnf install kernel-<version> Pasang versi kernel tertentu (Fedora)
yum update kernel Kemas kini kernel ke versi terkini (CentOS/Red Hat)
grubby --default-kernel Tunjukkan kernel lalai yang digunakan semasa boot
grubby --set-default /boot/vmlinuz-<version> Tetapkan kernel tertentu sebagai lalai untuk boot (RHEL/CentOS)
reboot But semula sistem untuk memuat kernel yang baru dipasang

---

Penyusunan Kernel (Lanjutan)

Perintah Keterangan
make menuconfig Konfigurasi pilihan kernel sebelum menyusun
make -j$(nproc) Susun kernel menggunakan semua teras CPU yang tersedia
make modules_install Pasang modul kernel yang disusun
make install Pasang kernel yang disusun
make mrproper Bersihkan semua fail binaan dan konfigurasi kernel
cp /boot/config-$(uname -r) .config Salin fail konfigurasi kernel semasa sebagai asas untuk menyusun

---

Boot, Bootloader (GRUB), dan Firmware EFI

Bahagian ini merangkumi perintah berkaitan boot sistem, mengurus bootloader GRUB, dan bekerja dengan firmware EFI/UEFI.

---

Pengurusan Bootloader GRUB

GRUB (GRand Unified Bootloader) ialah bootloader lalai bagi banyak distribusi Linux, dan ia mengurus kernel atau sistem pengendalian mana yang hendak diboot.

Perintah GRUB Biasa

Perintah Keterangan
grub-install /dev/sda Pasang bootloader GRUB pada cakera yang ditentukan (cth., /dev/sda)
grub-mkconfig -o /boot/grub/grub.cfg Jana fail konfigurasi GRUB (jalankan selepas memasang atau mengemas kini GRUB)
update-grub Kemas kini konfigurasi GRUB (Debian/Ubuntu)
grub-set-default <entry> Tetapkan entri boot lalai dengan menyatakan indeks atau tajuk entri menu
grub-reboot <entry> But semula sistem ke entri GRUB tertentu sekali
grub-editenv list Senaraikan pemboleh ubah persekitaran GRUB yang disimpan
grub2-mkconfig -o /boot/grub2/grub.cfg Jana konfigurasi GRUB (Red Hat/CentOS/Fedora)
grub2-install /dev/sda Pasang GRUB pada sistem berasaskan Red Hat (RHEL/CentOS/Fedora)
nano /etc/default/grub Sunting fail konfigurasi GRUB untuk menetapkan timeout, OS lalai, dll.

Contoh Konfigurasi GRUB

Anda boleh menyunting /etc/default/grub secara manual untuk mengubah pilihan boot, seperti kernel lalai, timeout atau menambah parameter boot kernel.

```bash
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_CMDLINE_LINUX="quiet splash"
GRUB_GFXMODE=1920x1080
```

Selepas membuat perubahan, kemas kini konfigurasi GRUB:

```bash
sudo update-grub
```

Pengurusan Firmware EFI/UEFI

EFI (Extensible Firmware Interface) atau UEFI (Unified Extensible Firmware Interface) ialah pengganti moden kepada BIOS tradisional. Ia mengurus proses boot sistem dan menawarkan ciri lanjutan seperti secure boot, pengurusan entri boot dan kawalan susunan boot.

Perintah EFI/UEFI

Perintah Keterangan
efibootmgr Urus entri dan tetapan boot UEFI
efibootmgr -v Senaraikan semua entri boot UEFI dalam mod verbose
efibootmgr -n <boot-number> Tetapkan entri boot seterusnya untuk sistem boot sekali
efibootmgr -o 0001,0002 Ubah susunan boot untuk mengutamakan entri boot 0001 diikuti 0002
efibootmgr -b 0003 -B Buang entri boot UEFI nombor 0003
efibootmgr -c -d /dev/sda -p 1 -L "Linux" -l /vmlinuz Cipta entri boot baharu untuk Linux pada partition EFI di /dev/sda1
efibootmgr -t 5 Tetapkan timeout 5 saat untuk menu boot UEFI
efibootmgr -a <boot-number> Aktifkan entri boot tertentu

---

Melihat dan Mengubah Pemboleh Ubah EFI

Pemboleh ubah EFI mengandungi maklumat tentang tetapan dan konfigurasi sistem.

Perintah Keterangan
ls /sys/firmware/efi/efivars/ Senaraikan semua pemboleh ubah EFI pada sistem
cat /sys/firmware/efi/fw_platform_size Paparkan sama ada platform ialah UEFI 32-bit atau 64-bit
efivar --list Senaraikan semua pemboleh ubah UEFI dalam format mudah dibaca
efivar --print <variable> Paparkan maklumat terperinci tentang pemboleh ubah EFI tertentu
modprobe efivars Muat modul efivars untuk mengakses pemboleh ubah UEFI

---

Pengurusan Secure Boot

Secure Boot ialah ciri UEFI yang hanya membenarkan perisian bertandatangan (seperti bootloader dan sistem pengendalian) untuk boot.

Perintah Keterangan
mokutil --sb-state Semak keadaan semasa Secure Boot
mokutil --enable-validation Dayakan pengesahan Secure Boot
mokutil --disable-validation Lumpuhkan pengesahan Secure Boot
mokutil --list-enrolled Senaraikan kunci yang didaftarkan dalam Secure Boot
mokutil --import <keyfile> Import kunci baharu untuk digunakan bagi Secure Boot
mokutil --reset Tetapkan semula semua kunci Secure Boot ke keadaan lalai

---

Boot ke Firmware UEFI

Untuk masuk ke tetapan firmware UEFI daripada Linux:

1. Distribusi berasaskan systemd:
   ```bash
   systemctl reboot --firmware-setup
