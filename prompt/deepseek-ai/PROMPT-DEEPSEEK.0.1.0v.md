# 🐧 🖥️ Panduan Lengkap: Linux, Git, MCP, Bahasa Pengaturcaraan & Codespaces

<!-- Simple Icons (monochrome, bagus untuk icon) -->
<img src="https://cdn.jsdelivr.net/npm/simple-icons@v16/icons/linux.svg" alt="Linux" width="32" height="32">

<!-- Dengan warna rasmi -->
<img src="https://cdn.simpleicons.org/linux" alt="Linux" width="32" height="32">
<!-- Logo Light (untuk background gelap) -->
<img src="https://opencode.ai/brand/files/opencode-logo-light.svg" alt="OpenCode" width="32" height="32">

<!-- Logo Dark (untuk background cerah) -->
<img src="https://opencode.ai/brand/files/opencode-logo-dark.svg" alt="OpenCode" width="32" height="32">

<!-- Square version -->
<img src="https://opencode.ai/brand/files/opencode-logo-light-square.svg" alt="OpenCode" width="32" height="32">

**DEEPSEEK AI**
<!-- Simple Icons -->
<img src="https://cdn.jsdelivr.net/npm/simple-icons@v16/icons/deepseek.svg" alt="DeepSeek" width="32" height="32">

<!-- Dengan warna rasmi -->
<img src="https://cdn.simpleicons.org/deepseek" alt="DeepSeek" width="32" height="32">

**LLAMA AI**
<!-- Icon rasmi dari llama.brand -->
<img src="https://raw.githubusercontent.com/ggml-org/llama.brand/master/logo/svg/icon/icon-light.svg" alt="Llama" width="32" height="32">

<!-- Versi dark -->
<img src="https://raw.githubusercontent.com/ggml-org/llama.brand/master/logo/svg/icon/icon-dark.svg" alt="Llama" width="32" height="32">

<!-- Dari repo llama.cpp -->
<img src="https://raw.githubusercontent.com/ggml-org/llama.cpp/master/media/llama1-icon.svg" alt="Llama" width="32" height="32">

> **Nota penting:**  
> Dokumen ini menggabungkan cheat sheet Linux, Git, pemasangan MCP, pengurusan bahasa (Node.js, Java, Bash), **openSUSE**, dan aliran kerja GitHub Codespaces.  
> Sesetengah arahan (contohnya `systemctl`, `reboot`, GRUB, EFI) **tidak berfungsi** dalam Codespaces kerana ia berjalan dalam container, bukan mesin Linux penuh.

**Ikon yang digunakan:**  
🐧 Linux · 🖥️ Terminal · 🦎 openSUSE · 🤖 DeepSeek AI · ⚙️ OpenCode / MCP

---

## Kandungan

1. [Arahan Asas Linux & Bila Guna](#1-arahan-asas-linux--bila-guna)
2. [Pengurusan Fail & Direktori](#2-pengurusan-fail--direktori)
3. [Kebenaran Fail](#3-kebenaran-fail)
4. [Pengurusan Proses & Sistem](#4-pengurusan-proses--sistem)
5. [Rangkaian & Pemantauan](#5-rangkaian--pemantauan)
6. [Pengurusan Pakej (apt, dnf, zypper, pacman)](#6-pengurusan-pakej)
7. [openSUSE: Pemasangan Bahasa & Alat](#7-opensuse-pemasangan-bahasa--alat)
8. [Node.js, npm & pnpm (JavaScript)](#8-nodejs-npm--pnpm-javascript)
9. [Java (OpenJDK)](#9-java-openjdk)
10. [Bash & Bahasa Sistem](#10-bash--bahasa-sistem)
11. [Pemasangan MCP (Model Context Protocol)](#11-pemasangan-mcp-model-context-protocol)
12. [Semua Arahan Git](#12-semua-arahan-git)
13. [Cipta Repositori Baharu dalam Codespaces & Terminal](#13-cipta-repositori-baharu-dalam-codespaces--terminal)
14. [Had Sistem dalam Codespaces](#14-had-sistem-dalam-codespaces)

---

## 1. Arahan Asas Linux & Bila Guna 🐧 🖥️

| Perintah              | Kegunaan                  | Bila Guna                              |
|-----------------------|---------------------------|----------------------------------------|
| `pwd`                 | Papar direktori semasa    | Semak lokasi anda dalam terminal       |
| `ls`                  | Senarai fail              | Lihat kandungan direktori              |
| `cd <dir>`            | Tukar direktori           | Navigasi sistem fail                   |
| `whoami`              | Papar pengguna semasa     | Semak identiti pengguna                |
| `echo <teks>`         | Cetak teks                | Uji output atau papar mesej            |
| `history`             | Sejarah perintah          | Ulang perintah lama                    |
| `man <perintah>`      | Manual perintah           | Fahami pilihan perintah                |
| `clear`               | Kosongkan skrin           | Bersihkan terminal                     |

**Contoh:**

```bash
pwd
ls -la
cd /home/user/projek
```

---

## 2. Pengurusan Fail & Direktori 🖥️

| Perintah                    | Kegunaan                          | Bila Guna                                      |
|-----------------------------|-----------------------------------|------------------------------------------------|
| `mkdir <dir>`               | Cipta direktori                   | Buat folder projek                             |
| `rmdir <dir>`               | Buang direktori kosong            | Bersihkan folder kosong                        |
| `rm <fail>`                 | Padam fail                        | Buang fail tidak diperlukan                    |
| `rm -rf <dir>`              | Padam paksa direktori             | **Hati-hati:** buang folder dan kandungannya   |
| `cp <sumber> <dest>`        | Salin fail                        | Sandaran atau duplikasi                        |
| `mv <sumber> <dest>`        | Pindah / namakan semula           | Susun atur fail                                |
| `touch <fail>`              | Cipta fail kosong                 | Mulakan fail baharu                            |
| `cat <fail>`                | Papar kandungan                   | Baca fail teks pendek                          |
| `less <fail>`               | Baca halaman demi halaman         | Fail teks panjang                              |
| `head <fail>`               | 10 baris pertama                  | Semak permulaan fail                           |
| `tail -f <fail>`            | Ikut fail secara langsung         | Pantau log masa nyata                          |
| `find <dir> -name <nama>`   | Cari fail                         | Cari fail mengikut nama                        |
| `grep "<corak>" <fail>`     | Cari teks                         | Tapis kandungan fail                           |

**Contoh:**

```bash
mkdir projek-baharu
cp -r sumber/ destinasi/
tail -f /var/log/syslog
grep "error" log.txt
```

---

## 3. Kebenaran Fail 🐧

| Perintah                              | Kegunaan              | Bila Guna                        |
|---------------------------------------|-----------------------|----------------------------------|
| `ls -l`                               | Lihat kebenaran       | Semak akses fail                 |
| `chmod <mod> <fail>`                  | Ubah kebenaran        | Beri akses baca/tulis/laksana    |
| `chown <pemilik>:<kumpulan> <fail>`   | Tukar pemilik         | Pindah hak milik                 |
| `chgrp <kumpulan> <fail>`             | Tukar kumpulan        | Urus akses kumpulan              |

**Contoh:**

```bash
chmod 755 skrip.sh
chown user:group data.txt
```

---

## 4. Pengurusan Proses & Sistem 🖥️

| Perintah                          | Kegunaan                    | Bila Guna                                      |
|-----------------------------------|-----------------------------|------------------------------------------------|
| `ps aux`                          | Senarai proses              | Lihat semua proses berjalan                    |
| `top` / `htop`                    | Pemantauan masa nyata       | Semak beban CPU/memori                         |
| `kill <PID>`                      | Hentikan proses             | Tamatkan proses tersangkut                     |
| `kill -9 <PID>`                   | Bunuh paksa                 | Proses enggan berhenti                         |
| `pgrep <nama>`                    | Cari PID                    | Dapatkan ID proses                             |
| `pkill <nama>`                    | Hentikan ikut nama          | Tamatkan semua proses sama nama                |
| `nice -n <nilai> <perintah>`      | Jalankan dengan keutamaan   | Kawal penggunaan CPU                           |
| `renice <nilai> <PID>`            | Ubah keutamaan              | Laraskan proses sedia ada                      |
| `systemctl status <servis>`       | Status perkhidmatan         | Semak servis systemd (**Codespaces: tidak berfungsi**) |
| `journalctl -u <servis>`          | Log servis                  | Diagnostik servis (**Codespaces: tidak berfungsi**) |

**Contoh:**

```bash
ps aux | grep nginx
kill -9 1234
nice -n 10 make
```

---

## 5. Rangkaian & Pemantauan 🖥️

| Perintah              | Kegunaan                  | Bila Guna                          |
|-----------------------|---------------------------|------------------------------------|
| `ip addr`             | Alamat IP                 | Semak antara muka rangkaian        |
| `ping <hos>`          | Uji sambungan             | Diagnostik rangkaian               |
| `curl <URL>`          | HTTP request              | Uji API atau muat turun            |
| `wget <URL>`          | Muat turun fail           | Muat turun dari web                |
| `ss -tuln`            | Port mendengar            | Semak port terbuka                 |
| `netstat -tuln`       | Port (lama)               | Alternatif `ss`                    |
| `dig <domain>`        | DNS query                 | Selesaikan masalah DNS             |
| `traceroute <hos>`    | Jejak laluan              | Cari titik gangguan                |
| `df -h`               | Ruang cakera              | Semak kapasiti                     |
| `du -sh <dir>`        | Saiz direktori            | Cari folder besar                  |
| `free -h`             | Penggunaan memori         | Semak RAM                          |
| `vmstat`              | Statistik maya            | Analisis prestasi                  |

**Contoh:**

```bash
ip addr show
curl -I https://example.com
df -h
```

---

## 6. Pengurusan Pakej 🐧

| Sistem            | Perintah                                              | Kegunaan          |
|-------------------|-------------------------------------------------------|-------------------|
| Debian / Ubuntu   | `sudo apt update && sudo apt upgrade`                 | Kemas kini pakej  |
| Debian / Ubuntu   | `sudo apt install <pakej>`                            | Pasang pakej      |
| Red Hat / CentOS  | `sudo dnf install <pakej>`                            | Pasang pakej      |
| **openSUSE**      | `sudo zypper refresh && sudo zypper install <pakej>`  | Pasang pakej      |
| Arch              | `sudo pacman -S <pakej>`                              | Pasang pakej      |

> **Bila guna:** Apabila perlu memasang alat baharu, mengemas kini sistem, atau membuang pakej.

---

## 7. openSUSE: Pemasangan Bahasa & Alat 🦎

openSUSE menggunakan **zypper** sebagai pengurus pakej utama.

### Node.js & npm

```bash
sudo zypper refresh
sudo zypper install nodejs npm
```

Untuk versi Node.js terkini melalui NodeSource:

```bash
sudo zypper install -y curl
curl -fsSL https://rpm.nodesource.com/setup_20.x | sudo bash -
sudo zypper install -y nodejs
node -v && npm -v
```

### pnpm

```bash
sudo npm install -g pnpm
```

Atau melalui zypper (jika tersedia dalam repo):

```bash
sudo zypper install pnpm
```

### Java (OpenJDK)

```bash
sudo zypper refresh
sudo zypper install java-11-openjdk-devel   # atau java-17-openjdk-devel, java-21-openjdk-devel
java --version
```

### Alat pembangunan asas

```bash
sudo zypper install -t pattern devel_basis
```

---

## 8. Node.js, npm & pnpm (JavaScript) ⚙️

JavaScript dijalankan melalui Node.js. Disyorkan guna **nvm** untuk urus versi.

### Pasang nvm & Node.js (Linux / Codespaces)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
source ~/.bashrc
nvm install 20
nvm use 20
node -v && npm -v
```

### Pasang pnpm

```bash
npm install -g pnpm
```

**Bila guna**
- `nvm` → Apabila perlu tukar versi Node.js antara projek
- `npm` / `pnpm` → Pasang kebergantungan projek (`npm install`, `pnpm install`)

---

## 9. Java (OpenJDK) ⚙️

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install openjdk-17-jdk
java --version
```

### openSUSE 🦎

```bash
sudo zypper install java-17-openjdk-devel
java --version
```

> **Bila guna:** Apabila membangunkan aplikasi Java, menjalankan `.jar`, atau menggunakan alat seperti Maven / Gradle.

---

## 10. Bash & Bahasa Sistem 🖥️

Bash ialah shell lalai dalam kebanyakan Linux dan Codespaces. Anda boleh menulis skrip `.sh`.

### Asas skrip Bash

```bash
#!/bin/bash
echo "Hello, World!"
nama="Ali"
echo "Hai, $nama"
```

**Bila guna**
- Automasi tugasan berulang
- Menjalankan urutan perintah Linux
- Menulis skrip pemasangan atau deployment

---

## 11. Pemasangan MCP (Model Context Protocol) 🤖 DeepSeek AI

MCP membolehkan pembantu AI (termasuk DeepSeek AI) menyambung ke alat luaran (GitHub, pangkalan data, sistem fail, dll.).

### Kaedah 1: `npx add-mcp` (paling mudah)

Memerlukan **Node.js 18+**.

```bash
# Pasang server MCP jauh
npx add-mcp https://mcp.context7.com/mcp

# Pasang server MCP daripada pakej npm
npx add-mcp @modelcontextprotocol/server-postgres

# Dengan pemboleh ubah persekitaran
npx add-mcp @modelcontextprotocol/server-filesystem --env "API_KEY=secret"

# Pasang secara global (user-level)
npx add-mcp https://mcp.example.com/mcp -g
```

### Kaedah 2: Pasang pakej npm secara global

```bash
npm install -g @modelcontextprotocol/server-filesystem
npx -y @modelcontextprotocol/server-filesystem
```

### Kaedah 3: Python (uv)

```bash
uv init mcp-client
cd mcp-client
uv venv
source .venv/bin/activate
uv add mcp anthropic python-dotenv
```

**Bila guna**
- Apabila anda ingin memberikan keupayaan tambahan kepada pembantu AI (akses fail, carian web, pangkalan data, dsb.)
- Dalam projek yang menggunakan klien MCP seperti Cursor, Claude Code, atau VS Code

---

## 12. Semua Arahan Git ⚙️

### Persediaan awal

```bash
git config --global user.name "Nama Anda"
git config --global user.email "emel@example.com"
```

### Cipta & klon repositori

```bash
git init                     # Mulakan repo baharu
git clone <url>              # Klon repo sedia ada
git clone <url> <folder>     # Klon ke folder tertentu
```

### Status & perubahan

```bash
git status                   # Status fail
git diff                     # Perubahan belum di-stage
git add <fail>               # Stage fail
git add .                    # Stage semua
git commit -m "mesej"        # Commit
```

### Log & sejarah

```bash
git log                      # Sejarah commit
git log --oneline --graph    # Sejarah ringkas dengan graf
```

### Cawangan (Branch)

```bash
git branch                   # Senarai cawangan
git branch <nama>            # Cipta cawangan
git switch <nama>            # Tukar cawangan
git switch -c <nama>         # Cipta & tukar
git merge <nama>             # Gabung cawangan
git branch -d <nama>         # Padam cawangan
```

### Rebase

```bash
git rebase main              # Rebase ke main
git rebase -i HEAD~3         # Rebase interaktif 3 commit terakhir
```

### Stash (simpan sementara)

```bash
git stash                    # Simpan perubahan
git stash save "mesej"       # Stash dengan mesej
git stash list               # Senarai stash
git stash apply              # Guna stash terakhir
git stash pop                # Guna & buang stash
```

### Remote

```bash
git remote add origin <url>  # Tambah remote
git remote -v                # Semak remote
git push -u origin main      # Push pertama
git push                     # Push seterusnya
git pull                     # Tarik perubahan
```

### Undo & reset

```bash
git reset <fail>             # Unstage fail
git reset --hard <commit>    # Reset paksa (hati-hati)
git revert <commit>          # Buat commit baru untuk undo
```

### Tag

```bash
git tag                      # Senarai tag
git tag v1.0.0               # Cipta tag
git push origin v1.0.0       # Push tag
```

**Bila guna setiap kategori:**
- `init` / `clone` → mula projek
- `add` / `commit` → simpan perubahan
- `branch` / `merge` / `rebase` → kolaborasi & sejarah bersih
- `stash` → tukar cawangan tanpa commit
- `remote` / `push` / `pull` → segerak dengan GitHub

---

## 13. Cipta Repositori Baharu dalam Codespaces & Terminal 🖥️

### Dalam Codespaces (melalui terminal)

Codespaces menggunakan `GITHUB_TOKEN` yang **tidak boleh** mencipta repo. Anda perlu authenticate `gh` atau cipta repo di web dahulu.

```bash
# 1. Log keluar & buang token sementara
gh auth logout -h github.com
unset GITHUB_TOKEN

# 2. Log masuk semula
gh auth login -h github.com -p https -w

# 3. Semak status
gh auth status

# 4. Cipta repo & push
git init
git add .
git commit -m "init"
gh repo create nama-repo --private --source . --remote origin --push
```

### Di terminal biasa (tanpa Codespaces)

```bash
mkdir projek-baharu && cd projek-baharu
git init
echo "# projek-baharu" >> README.md
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/username/projek-baharu.git
git push -u origin main
```

**Bila guna**
- **Codespaces** → Apabila memulakan projek dalam persekitaran awan
- **Terminal biasa** → Apabila membangun secara lokal

---

## 14. Had Sistem dalam Codespaces 🐧

Codespaces ialah **container**, bukan mesin Linux penuh. Arahan berikut **tidak berfungsi** atau tidak dibenarkan:

```plaintext
systemctl, journalctl, reboot, shutdown, halt, poweroff
grub-install, update-grub, efibootmgr, mokutil
modprobe, insmod, rmmod, lsmod
iptables, firewall-cmd, ufw
mount, fdisk, parted, hdparm
sysctl -w (kebanyakan parameter kernel)
```

**Arahan yang selamat & berfungsi:**  
Fail, teks, rangkaian asas, proses, pemantauan, pakej dengan `sudo` (bergantung kepada container).

---

> **Sumber digabungkan:**  
> Cheat sheet Linux umum · Pemasangan MCP · Git & Codespaces · openSUSE & Node.js/Java · nvm & pnpm

---

**Simpan sebagai:** `panduan-lengkap.md`

Jika anda mahu saya tambah bahagian lain (contohnya Docker, Python, atau contoh projek penuh), beritahu sahaja.
