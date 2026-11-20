# 🐧 🖥️ Panduan Lengkap Command Line untuk Developer

> Dokumen ini mengandungi **command yang paling kerap digunakan** oleh developer, lengkap dengan:
> - **Penerangan** (command ini untuk apa)
> - **Bila perlu guna**
> - **Cara penggunaan**

**Ikon:** 🐧 Linux · 🖥️ Terminal · 📦 Node.js/npm · 🐍 Python · 🐳 Docker · 🗄️ Database

---

<!-- Dengan warna rasmi -->
<img src="https://cdn.simpleicons.org/linux" alt="Linux" width="280" height="280">

![Linux](https://cdn.jsdelivr.net/npm/simple-icons@v16/icons/linux.svg)
![DeepSeek](https://cdn.jsdelivr.net/npm/simple-icons@v16/icons/deepseek.svg)

## **Pertama** 
<img src="https://cdn.simpleicons.org/linux" alt="Linux" width="100" height="100">

1. [Linux Asas](#1-linux-asas)
2. [Pengurusan Fail & Direktori](#2-pengurusan-fail--direktori)
3. [Kebenaran Fail & Pengguna](#3-kebenaran-fail--pengguna)
4. [Proses & Monitoring](#4-proses--monitoring)
5. [Rangkaian, SSH & Muat Turun](#5-rangkaian-ssh--muat-turun)
6. [Archive & Compression](#6-archive--compression)
7. [Teks Processing](#7-teks-processing)
8. [Environment & Alias](#8-environment--alias)
9. [Package Manager (apt / zypper)](#9-package-manager)
10. [Node.js, npm, pnpm & Yarn](#10-nodejs-npm-pnpm--yarn)
11. [Python & pip](#11-python--pip)
12. [Git](#12-git)
13. [Docker](#13-docker)
14. [Database (MySQL, PostgreSQL, Prisma)](#14-database)
15. [Frontend (Next.js, Vite, React)](#15-frontend)
16. [Tools Moden](#16-tools-moden)

---

## 1. Linux Asas

### `pwd`
**Penerangan:** Papar direktori semasa (Print Working Directory).  
**Bila guna:** Bila anda hilang arah dalam terminal dan nak tahu di folder mana anda berada.  
**Cara guna:**
```bash
pwd
```

### `ls`
**Penerangan:** Senarai fail dan folder dalam direktori semasa.  
**Bila guna:** Setiap kali mahu lihat kandungan folder.  
**Cara guna:**
```bash
ls              # Senarai biasa
ls -l           # Format panjang (kebenaran, saiz, tarikh)
ls -la          # Termasuk fail tersembunyi (yang bermula dengan .)
ls -lh          # Saiz dalam format manusia (KB, MB)
ls -lt          # Susun mengikut masa diubah
```

### `cd`
**Penerangan:** Tukar direktori (Change Directory).  
**Bila guna:** Navigasi antara folder.  
**Cara guna:**
```bash
cd nama-folder          # Masuk ke folder
cd ..                   # Naik satu tahap
cd ~                    # Balik ke home directory
cd /                    # Ke root
cd -                    # Balik ke direktori sebelumnya
```

### `clear` / `Ctrl + L`
**Penerangan:** Kosongkan skrin terminal.  
**Bila guna:** Terminal penuh dengan output lama dan nak bersih.  
**Cara guna:**
```bash
clear
```

### `history`
**Penerangan:** Papar sejarah command yang pernah dijalankan.  
**Bila guna:** Nak ulang command lama atau cari command yang pernah digunakan.  
**Cara guna:**
```bash
history
history | grep npm      # Cari command berkaitan npm
!123                    # Jalankan semula command nombor 123
```

### `whoami`
**Penerangan:** Papar nama pengguna semasa.  
**Bila guna:** Semak identiti user (terutama selepas `sudo` atau `su`).  
**Cara guna:**
```bash
whoami
```

### `date` & `uptime`
**Penerangan:**  
- `date` → Tarikh dan masa sistem  
- `uptime` → Berapa lama sistem telah hidup + load average  
**Bila guna:** Semak masa sistem atau status kesihatan server.  
**Cara guna:**
```bash
date
uptime
```

---

## 2. Pengurusan Fail & Direktori

### `mkdir`
**Penerangan:** Cipta folder baru.  
**Bila guna:** Buat struktur projek.  
**Cara guna:**
```bash
mkdir nama-folder
mkdir -p parent/child/grandchild   # Cipta nested folder sekaligus
```

### `touch`
**Penerangan:** Cipta fail kosong atau kemas kini timestamp fail.  
**Bila guna:** Mulakan fail baru dengan cepat.  
**Cara guna:**
```bash
touch index.js
touch file1.txt file2.txt
```

### `cp`
**Penerangan:** Salin fail atau folder.  
**Bila guna:** Backup atau duplikasi fail.  
**Cara guna:**
```bash
cp fail.txt backup.txt
cp -r folder-asal/ folder-baru/     # Salin folder beserta isi
```

### `mv`
**Penerangan:** Pindah fail/folder ATAU tukar nama.  
**Bila guna:** Susun fail atau rename.  
**Cara guna:**
```bash
mv lama.txt baru.txt                # Rename
mv fail.txt /path/ke/folder/        # Pindah
```

### `rm`
**Penerangan:** Padam fail atau folder.  
**Bila guna:** Buang fail yang tidak diperlukan.  
**Amaran:** Sangat berbahaya. Tiada recycle bin.  
**Cara guna:**
```bash
rm fail.txt
rm -r folder/                       # Padam folder + isi
rm -rf folder/                      # Paksa padam (tiada confirmation)
```

### `ln -s`
**Penerangan:** Cipta symbolic link (pintasan).  
**Bila guna:** Buat shortcut ke fail/folder tanpa salin.  
**Cara guna:**
```bash
ln -s /path/asal/fail.js ./fail.js
ln -s /var/www/project ~/project
```

### `cat`
**Penerangan:** Papar keseluruhan kandungan fail.  
**Bila guna:** Baca fail teks pendek.  
**Cara guna:**
```bash
cat fail.txt
cat file1.txt file2.txt             # Gabung beberapa fail
```

### `less` / `more`
**Penerangan:** Baca fail panjang halaman demi halaman.  
**Bila guna:** Log fail atau fail besar.  
**Cara guna:**
```bash
less log.txt
# Tekan q untuk keluar, / untuk search
```

### `head` & `tail`
**Penerangan:**  
- `head` → 10 baris pertama  
- `tail` → 10 baris terakhir  
**Bila guna:** Semak permulaan atau akhir fail (sangat berguna untuk log).  
**Cara guna:**
```bash
head -n 20 fail.txt
tail -n 50 fail.txt
tail -f /var/log/syslog             # Ikut log secara live
```

### `find`
**Penerangan:** Cari fail berdasarkan nama, jenis, saiz, tarikh, dll.  
**Bila guna:** Cari fail dalam projek besar.  
**Cara guna:**
```bash
find . -name "*.js"
find . -name "*.txt" -type f
find . -size +10M                   # Fail lebih besar dari 10MB
find . -mtime -7                    # Diubah dalam 7 hari lepas
```

### `rsync`
**Penerangan:** Sync fail/folder dengan cekap (hanya salin yang berubah).  
**Bila guna:** Backup, deploy, atau sync antara server.  
**Cara guna:**
```bash
rsync -av folder-asal/ folder-tujuan/
rsync -avz --progress sumber/ user@server:/path/
```

---

## 3. Kebenaran Fail & Pengguna

### `chmod`
**Penerangan:** Ubah kebenaran baca/tulis/laksana.  
**Bila guna:** Beri kebenaran execute pada skrip, atau kawal akses fail.  
**Cara guna:**
```bash
chmod +x skrip.sh                   # Beri execute
chmod 755 skrip.sh                  # rwxr-xr-x
chmod 644 fail.txt                  # rw-r--r--
chmod -R 755 folder/                # Recursive
```

### `chown`
**Penerangan:** Tukar pemilik fail/folder.  
**Bila guna:** Selepas salin fail sebagai root, atau urus permission.  
**Cara guna:**
```bash
chown user:group fail.txt
chown -R user:group folder/
```

### `sudo`
**Penerangan:** Jalankan command sebagai superuser (root).  
**Bila guna:** Install pakej, ubah fail sistem, restart servis.  
**Cara guna:**
```bash
sudo apt update
sudo systemctl restart nginx
```

### `su`
**Penerangan:** Tukar ke user lain (biasanya root).  
**Bila guna:** Bila perlu session root yang panjang.  
**Cara guna:**
```bash
su -
su nama-user
```

### `id`, `groups`, `whoami`
**Penerangan:** Semak identiti dan kumpulan user.  
**Bila guna:** Debug masalah permission.  
**Cara guna:**
```bash
id
groups
whoami
```

### `passwd`
**Penerangan:** Tukar password user.  
**Bila guna:** Reset atau tukar kata laluan.  
**Cara guna:**
```bash
passwd                  # Tukar password sendiri
sudo passwd username    # Tukar password user lain
```

---

## 4. Proses & Monitoring

### `ps aux`
**Penerangan:** Senarai semua proses yang sedang berjalan.  
**Bila guna:** Cari PID proses untuk di-kill atau semak resource.  
**Cara guna:**
```bash
ps aux
ps aux | grep node
ps aux | grep nginx
```

### `top` / `htop`
**Penerangan:** Monitor CPU, RAM, dan proses secara real-time.  
**Bila guna:** Sistem lambat, nak tahu apa yang makan resource.  
**Cara guna:**
```bash
top
htop          # Versi lebih cantik (perlu install)
```

### `kill` / `killall` / `pkill`
**Penerangan:** Hentikan proses.  
**Bila guna:** Proses hang atau tak mahu berhenti.  
**Cara guna:**
```bash
kill 1234                 # Hantar SIGTERM
kill -9 1234              # Paksa bunuh (SIGKILL)
killall node
pkill -f "node app.js"
```

### `df -h`
**Penerangan:** Semak ruang storan (disk free).  
**Bila guna:** Disk penuh atau nak tahu baki ruang.  
**Cara guna:**
```bash
df -h
```

### `du -sh`
**Penerangan:** Semak saiz folder.  
**Bila guna:** Cari folder mana yang besar.  
**Cara guna:**
```bash
du -sh *
du -sh node_modules/
du -h --max-depth=1
```

### `free -h`
**Penerangan:** Semak penggunaan RAM.  
**Bila guna:** Sistem lambat, semak sama ada RAM mencukupi.  
**Cara guna:**
```bash
free -h
```

### `lsof`
**Penerangan:** Senarai fail yang dibuka oleh proses.  
**Bila guna:** Port sudah digunakan, atau cari proses yang hold fail.  
**Cara guna:**
```bash
lsof -i :3000             # Siapa guna port 3000
lsof /path/ke/fail
```

---

## 5. Rangkaian, SSH & Muat Turun

### `ping`
**Penerangan:** Uji sambungan ke host.  
**Bila guna:** Semak internet atau server hidup ke tidak.  
**Cara guna:**
```bash
ping google.com
ping -c 4 8.8.8.8
```

### `curl`
**Penerangan:** Hantar HTTP request (sangat berkuasa).  
**Bila guna:** Test API, muat turun, debug request.  
**Cara guna:**
```bash
curl https://api.example.com
curl -I https://example.com                    # Header sahaja
curl -X POST -H "Content-Type: application/json" -d '{"name":"Ali"}' https://api.example.com
curl -o fail.zip https://example.com/fail.zip  # Muat turun
```

### `wget`
**Penerangan:** Muat turun fail dari internet.  
**Bila guna:** Download fail besar atau recursive.  
**Cara guna:**
```bash
wget https://example.com/fail.zip
wget -c https://example.com/fail.zip           # Resume download
```

### `ssh`
**Penerangan:** Sambung ke server jauh secara selamat.  
**Bila guna:** Urus server remote.  
**Cara guna:**
```bash
ssh user@ip-address
ssh -p 2222 user@ip
ssh -i ~/.ssh/id_rsa user@ip
```

### `scp`
**Penerangan:** Salin fail antara lokal dan remote melalui SSH.  
**Bila guna:** Upload/download fail ke server.  
**Cara guna:**
```bash
scp fail.txt user@server:/path/
scp -r folder/ user@server:/path/
scp user@server:/path/fail.txt .
```

### `ssh-keygen` & `ssh-copy-id`
**Penerangan:** Jana dan salin SSH key (login tanpa password).  
**Bila guna:** Setup akses server yang selamat dan mudah.  
**Cara guna:**
```bash
ssh-keygen -t ed25519 -C "email@example.com"
ssh-copy-id user@server
```

### `ip addr` / `ss`
**Penerangan:**  
- `ip addr` → Alamat IP  
- `ss -tuln` → Port yang sedang listen  
**Bila guna:** Debug rangkaian dan port.  
**Cara guna:**
```bash
ip addr
ss -tuln
```

---

## 6. Archive & Compression

### `tar`
**Penerangan:** Archive dan compress fail/folder (paling standard di Linux).  
**Bila guna:** Backup projek, hantar folder, extract source code.  
**Cara guna:**
```bash
tar -czvf projek.tar.gz folder/     # Compress
tar -xzvf projek.tar.gz             # Extract
tar -tzvf projek.tar.gz             # Senarai isi tanpa extract
```

### `zip` / `unzip`
**Penerangan:** Compress/extract format ZIP (serasi Windows).  
**Bila guna:** Hantar fail kepada pengguna Windows.  
**Cara guna:**
```bash
zip -r projek.zip folder/
unzip projek.zip
unzip -l projek.zip                 # Senarai isi
```

---

## 7. Teks Processing

### `grep`
**Penerangan:** Cari teks dalam fail.  
**Bila guna:** Cari error dalam log, cari function dalam kod.  
**Cara guna:**
```bash
grep "error" log.txt
grep -r "TODO" .                    # Recursive
grep -i "error" log.txt             # Case insensitive
grep -n "function" app.js           # Dengan nombor baris
```

### `awk`
**Penerangan:** Proses teks berasaskan kolum (sangat berkuasa).  
**Bila guna:** Extract data dari log atau CSV.  
**Cara guna:**
```bash
awk '{print $1}' fail.txt           # Cetak kolum pertama
awk -F: '{print $1}' /etc/passwd
```

### `sed`
**Penerangan:** Stream editor – cari dan ganti teks.  
**Bila guna:** Replace teks dalam banyak fail sekaligus.  
**Cara guna:**
```bash
sed 's/lama/baru/' fail.txt
sed -i 's/lama/baru/g' fail.txt     # Edit terus dalam fail
```

### `cut`, `sort`, `uniq`, `wc`, `tr`
**Penerangan:** Alat kecil tapi sangat berguna untuk manipulasi teks.  
**Bila guna:** Bersihkan dan analisis data teks.  
**Cara guna:**
```bash
cut -d',' -f1 data.csv
sort fail.txt
sort fail.txt | uniq
wc -l fail.txt                      # Kira bilangan baris
tr 'a-z' 'A-Z' < fail.txt           # Tukar kepada huruf besar
```

---

## 8. Environment & Alias

### `export` & `env`
**Penerangan:** Set dan lihat environment variable.  
**Bila guna:** Set PATH, API key, NODE_ENV, dll.  
**Cara guna:**
```bash
export NODE_ENV=production
export PATH="$PATH:/new/path"
env                                 # Lihat semua variable
echo $HOME
echo $PATH
```

### `alias`
**Penerangan:** Cipta shortcut untuk command panjang.  
**Bila guna:** Jimat masa menaip command berulang.  
**Cara guna:**
```bash
alias ll='ls -la'
alias gs='git status'
alias ..='cd ..'
# Simpan dalam ~/.bashrc atau ~/.zshrc supaya kekal
```

### `which` / `type`
**Penerangan:** Cari lokasi binary sesuatu command.  
**Bila guna:** Semak sama ada tool sudah dipasang dan dari mana.  
**Cara guna:**
```bash
which node
which python3
type npm
```

---

## 9. Package Manager

### Ubuntu / Debian (`apt`)
```bash
sudo apt update                     # Kemas kini senarai pakej
sudo apt upgrade                    # Upgrade semua pakej
sudo apt install nama-pakej         # Install
sudo apt remove nama-pakej          # Buang
sudo apt autoremove                 # Buang dependency yang tak digunakan
sudo apt search keyword             # Cari pakej
```

**Bila guna:** Setiap kali nak install software di Ubuntu/Debian/Codespaces.

### openSUSE (`zypper`)
```bash
sudo zypper refresh
sudo zypper install nama-pakej
sudo zypper search keyword
sudo zypper remove nama-pakej
sudo zypper update
```

---

## 10. Node.js, npm, pnpm & Yarn

### Semak Versi
```bash
node -v
npm -v
```

### Mulakan Projek
```bash
npm init                            # Interaktif
npm init -y                         # Terus buat package.json
```

### Install Pakej
```bash
npm install express                 # Dependencies biasa
npm i express                       # Shortcut
npm install -D typescript           # Dev dependencies
npm install -g nodemon              # Global
npm install                         # Install semua dari package.json
npm uninstall express
npm update
```

### Script
```bash
npm run dev
npm run build
npm run start
npm run test
```

### Cache & Audit
```bash
npm cache clean --force
npm audit
npm audit fix
npm list                            # Senarai pakej terpasang
```

### npx (jalankan package tanpa install global)
```bash
npx create-react-app my-app
npx create-next-app@latest
npx create-vite@latest
npx vite
npx prisma migrate dev
npx tailwindcss init
npx tailwindcss init -p
npx eslint .
npx tsc
npx nodemon app.js
```

### pnpm (lebih pantas & jimat disk)
```bash
npm install -g pnpm

pnpm install
pnpm add express
pnpm add -D typescript
pnpm remove express

pnpm dev
pnpm build
pnpm start
```

### Yarn
```bash
npm install -g yarn

yarn install
yarn add express
yarn add -D typescript
yarn remove express

yarn dev
yarn build
yarn start
```

---

## 11. Python & pip

### Semak Versi
```bash
python --version
python3 --version
```

### Jalankan Fail
```bash
python app.py
python3 app.py
```

### Virtual Environment (sangat disyorkan)
```bash
python3 -m venv .venv
source .venv/bin/activate           # Linux/macOS
# .venv\Scripts\activate            # Windows

deactivate                          # Keluar dari venv
```

### pip
```bash
pip install requests
pip install -r requirements.txt
pip uninstall requests
pip list
pip freeze > requirements.txt
```

### pipx (install CLI tools secara terasing)
```bash
pipx install poetry
pipx install black
```

---

## 12. Git

### Setup Awal
```bash
git config --global user.name "Nama Anda"
git config --global user.email "emel@example.com"
```

### Mulakan & Klon
```bash
git init
git clone https://github.com/user/repo.git
git clone https://github.com/user/repo.git nama-folder
```

### Status & Perubahan
```bash
git status
git diff
git add .
git add fail.js
git commit -m "Initial commit"
git commit -m "update: tambah feature login"
```

### Remote
```bash
git remote add origin https://github.com/user/repo.git
git remote -v
git push -u origin main
git push
git pull
git fetch
git pull origin main
```

### Branch
```bash
git branch
git branch nama-branch
git checkout nama-branch
git checkout -b feature-login
git switch nama-branch
git switch -c feature-login
git merge dev
git branch -d nama-branch
```

### Undo & Clean
```bash
git restore fail.js                 # Buang perubahan yang belum di-stage
git restore --staged fail.js        # Unstage
git reset --soft HEAD~1             # Undo commit, kekalkan perubahan
git reset --hard HEAD~1             # Undo commit + buang perubahan (bahaya)
git clean -fd                       # Buang fail untracked
git stash
git stash pop
git stash -u                        # Termasuk untracked files
```

### Lain-lain Berguna
```bash
git log --oneline --graph
git blame fail.js
git cherry-pick <commit-hash>
git show <commit-hash>
```

---

## 13. Docker

### Asas
```bash
docker --version
docker pull nginx
docker images
docker run nginx
docker run -d -p 3000:3000 --name myapp image-name
docker ps                           # Container yang sedang berjalan
docker ps -a                        # Semua container
docker stop container_id
docker rm container_id
docker rmi image_id
docker logs container_id
docker exec -it container_id bash
```

### Docker Compose
```bash
docker compose up
docker compose up -d                # Background
docker compose down
docker compose down -v              # Buang volume juga
docker compose logs -f
docker compose ps
```

**Bila guna:**  
- Development environment yang konsisten  
- Jalankan database + app sekali gus  
- Deploy aplikasi

---

## 14. Database

### MySQL
```bash
mysql -u root -p
```

### PostgreSQL
```bash
psql -U postgres
psql -U username -d nama_database
```

### Prisma (ORM popular untuk Node.js)
```bash
npx prisma init
npx prisma generate
npx prisma migrate dev
npx prisma migrate dev --name init
npx prisma db push
npx prisma studio                   # GUI untuk lihat data
npx prisma format
```

**Bila guna Prisma:**  
Bila menggunakan Node.js/TypeScript dan mahu type-safe database access.

---

## 15. Frontend (Next.js, Vite, React)

### Next.js
```bash
npx create-next-app@latest
npx create-next-app@latest my-app
# Ikut wizard (TypeScript, Tailwind, App Router, dll)

cd my-app
npm run dev                         # Development (localhost:3000)
npm run build
npm run start                       # Production
```

### Vite (React / Vue / Svelte)
```bash
npm create vite@latest
npm create vite@latest my-app
npm create vite@latest my-app -- --template react
npm create vite@latest my-app -- --template react-ts

cd my-app
npm install
npm run dev
npm run build
npm run preview
```

### Create React App (lama, kurang disyorkan sekarang)
```bash
npx create-react-app myapp
npx create-react-app myapp --template typescript
```

### Tailwind CSS
```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
npx tailwindcss init -p             # Dengan postcss.config
```

---

## 16. Tools Moden (Disyorkan)

| Tool       | Ganti          | Penerangan                          | Cara Install                  |
|------------|----------------|-------------------------------------|-------------------------------|
| `eza`      | `ls`           | `ls` yang cantik + icon + git       | `sudo apt install eza`        |
| `bat`      | `cat`          | `cat` dengan syntax highlight       | `sudo apt install bat`        |
| `fd`       | `find`         | Cari fail jauh lebih pantas         | `sudo apt install fd-find`    |
| `rg`       | `grep`         | ripgrep – sangat pantas             | `sudo apt install ripgrep`    |
| `fzf`      | -              | Fuzzy finder (sangat berguna)       | `sudo apt install fzf`        |
| `delta`    | `git diff`     | Git diff yang cantik                | `cargo install git-delta`     |
| `lazygit`  | Git manual     | TUI untuk Git                       | `sudo apt install lazygit`    |
| `htop`     | `top`          | Monitor proses yang lebih baik      | `sudo apt install htop`       |
| `jq`       | -              | Process JSON di terminal            | `sudo apt install jq`         |

**Contoh penggunaan tools moden:**
```bash
eza -la
bat app.js
fd "*.ts"
rg "TODO"
fzf
git diff | delta
lazygit
```

---

## Tip Cepat Harian Developer

```bash
# 1. Update sistem
sudo apt update && sudo apt upgrade -y

# 2. Semak status projek
git status
npm run dev

# 3. Bila disk penuh
du -sh * | sort -h
docker system prune -a

# 4. Bila port 3000 sudah digunakan
lsof -i :3000
kill -9 <PID>

# 5. Clean node_modules & reinstall
rm -rf node_modules package-lock.json
npm install
```

---

**Fail ini disimpan sebagai:** `panduan-command-developer.md`

Jika anda mahu saya tambah bahagian tertentu (contoh: Nginx, PM2, Redis, atau contoh workflow penuh), beritahu sahaja.
