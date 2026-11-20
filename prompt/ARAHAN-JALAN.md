# Panduan Arahan Command Line & Git

> Panduan ringkas untuk terminal Linux, GitHub Codespaces dan pembangunan JavaScript/Node.js, Java serta Python.

---

## 1. Arahan asas terminal

```bash
pwd                 # Papar folder semasa
ls                  # Senarai fail dan folder
ls -la              # Senarai lengkap termasuk fail tersembunyi
cd nama-folder      # Masuk ke dalam folder
cd ..               # Kembali ke folder sebelumnya
cd ~                # Pergi ke folder utama pengguna
mkdir nama-folder   # Bina folder baharu
touch nama-file.txt # Cipta fail kosong
cp sumber destinasi # Salin fail atau folder
mv lama baharu      # Tukar nama atau pindahkan fail/folder
rm nama-file        # Padam fail
rm -r nama-folder   # Padam folder beserta kandungannya
rm -rf nama-folder  # Paksa padam folder; gunakan dengan berhati-hati
cat nama-file       # Papar kandungan fail
less nama-file      # Baca fail satu skrin pada satu masa
clear               # Bersihkan paparan terminal
history             # Papar sejarah arahan
!!                  # Jalankan arahan terakhir semula
```

Gunakan `sudo` hanya untuk arahan yang memerlukan kebenaran pentadbir:

```bash
sudo apt update
sudo apt upgrade
sudo apt install nama-pakej
sudo nama-perintah
```

Untuk memastikan arahan itu selamat sebelum dijalankan, gunakan:

```bash
<command> --help
man <command>
which nama-perintah
command -v nama-perintah
```

---

## 2. Pemasangan sistem Linux

### Ubuntu/Debian

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install -y curl wget git unzip zip build-essential
```

`build-essential` mengandungi GCC, G++, make dan pembangun asas Linux.

### Fedora

```bash
sudo dnf update -y
sudo dnf install -y curl wget git unzip zip gcc gcc-c++ make
```

### openSUSE

```bash
sudo zypper refresh
sudo zypper update
sudo zypper install curl wget git unzip zip gcc gcc-c++ make
```

Untuk mencari atau memasang pakej:

```bash
sudo apt search nama-pakej       # Ubuntu/Debian
sudo dnf search nama-pakej       # Fedora
sudo zypper search nama-pakej    # openSUSE
```

Untuk memadam pakej:

```bash
sudo apt remove nama-pakej       # Ubuntu/Debian
sudo apt purge nama-pakej        # Buang pakej dan konfigurasi
sudo dnf remove nama-pakej       # Fedora
sudo zypper remove nama-pakej    # openSUSE
```

---

## 3. Pasang Node.js dan npm

Semak sama ada Node.js dan npm telah dipasang:

```bash
node --version
npm --version
npx --version
```

### Ubuntu/Debian

Lalai repositori OS mungkin mempunyai versi lama. Untuk Node.js aktif semasa, gunakan NodeSource atau NVM.

#### Pilihan A: NVM

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
source ~/.bashrc
nvm install --lts
nvm use --lts
nvm alias default --lts
node --version
npm --version
```

Untuk melangkau definisi shell yang menggunakan zsh:

```bash
source ~/.zshrc
```

#### Pilihan B: NodeSource

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
node --version
npm --version
```

### Fedora

```bash
sudo dnf install -y nodejs npm
```

### openSUSE

```bash
sudo zypper install nodejs npm
```

### Pasang pnpm

```bash
corepack enable
corepack prepare pnpm@latest --activate
pnpm --version
```

Jika Corepack tidak tersedia:

```bash
npm install -g pnpm
```

---

## 4. Arahan npm

Cipta projek Node.js baharu:

```bash
npm init -y
npm create vite@latest
npm create next-app@latest
```

Pasang dependency projek:

```bash
npm install
npm install nama-pakej
npm install nama-pakej --save-dev
npm install -g nama-pakej
```

Nyahpasang:

```bash
npm uninstall nama-pakej
npm uninstall -g nama-pakej
npm uninstall nama-pakej --save-dev
```

Kemaskini:

```bash
npm update
npm update nama-pakej
npm outdated
npm audit
npm audit fix
npm audit fix --force
npm run script-name
npm start
npm test
npm run build
npm run dev
npm list
npm list --depth=0
npm cache verify
npm cache clean --force
```

Jangan guna `npm audit fix --force` tanpa memahami perubahan utama yang mungkin berlaku.

### Arahan pnpm

```bash
pnpm install
pnpm add nama-pakej
pnpm add -D nama-pakej
pnpm remove nama-pakej
pnpm update
pnpm run dev
pnpm build
pnpm test
pnpm dlx nama-pakej
```

---

## 5. Java

Semak sama ada Java dipasang:

```bash
java --version
javac --version
which java
```

Ubuntu/Debian:

```bash
sudo apt install -y openjdk-21-jdk
```

Fedora:

```bash
sudo dnf install -y java-21-openjdk-devel
```

openSUSE:

```bash
sudo zypper install java-21-openjdk-devel
```

Semak dan tetapkan `JAVA_HOME`:

```bash
readlink -f $(which java)
sudo update-alternatives --config java
export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
export PATH=$JAVA_HOME/bin:$PATH
```

Tambah ke `.bashrc` atau `.zshrc`:

```bash
echo 'export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

Kompil dan jalankan Java:

```bash
javac Main.java
java Main
java -jar aplikasi.jar
```

Maven:

```bash
sudo apt install -y maven
mvn --version
mvn compile
mvn test
mvn package
mvn spring-boot:run
```

Gradle:

```bash
sudo apt install -y gradle
gradle --version
./gradlew build
./gradlew test
./gradlew bootRun
```

---

## 6. Python

Semak Python:

```bash
python --version
python3 --version
pip --version
pip3 --version
```

Ubuntu/Debian:

```bash
sudo apt install -y python3 python3-pip python3-venv
```

Fedora:

```bash
sudo dnf install -y python3 python3-pip
```

openSUSE:

```bash
sudo zypper install python3 python3-pip python3-venv
```

Bina dan guna virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install nama-pakej
python -m pip install -r requirements.txt
python main.py
python -m pytest
deactivate
```

Windows Git Bash/PowerShell berbeza:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

Arahan pip:

```bash
pip install nama-pakej
pip uninstall nama-pakej
pip freeze > requirements.txt
pip install -r requirements.txt
pip show nama-pakej
pip check
```

---

## 7. Mengetahui jenis projek

Senarai fail utama projek:

```bash
ls -la
find . -maxdepth 2 -type f | sort
```

### Ciri projek JavaScript/Node.js

```text
package.json
package-lock.json / pnpm-lock.yaml / yarn.lock
node_modules/
src/
```

```bash
cat package.json
node --version
npm --version
```

### Ciri projek Java

```text
pom.xml
build.gradle / build.gradle.kts
src/main/java/
src/test/java/
gradlew atau mvnw
```

```bash
file Main.java
ls pom.xml build.gradle 2>/dev/null
java --version
mvn --version
gradle --version
```

`pom.xml` bermaksud Maven dan `build.gradle` bermaksud Gradle.

### Ciri projek Python

```text
requirements.txt
pyproject.toml
Pipfile
setup.py
src/
.venv/
```

```bash
python3 --version
ls requirements.txt pyproject.toml setup.py 2>/dev/null
cat requirements.txt
cat pyproject.toml
```

Kira jenis fail secara automatik:

```bash
find . -type f | sed 's/.*\.//' | sort | uniq -c | sort -nr | head -20
```

Semak bahasa yang wujud:

```bash
find . -type f -name '*.js' -o -name '*.ts' | head
find . -type f -name '*.java' | head
find . -type f -name '*.py' | head
```

---

## 8. Git asas

Semak atau tetapkan konfigurasi:

```bash
git --version
git config --global --list
git config --global user.name "Nama Anda"
git config --global user.email "email@example.com"
git config --local user.name "Nama Anda"
git config --local user.email "email@example.com"
```

Inisialisasi repository baharu:

```bash
mkdir nama-projek
cd nama-projek
git init
echo "# Nama Projek" > README.md
git add README.md
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/USERNAME/nama-projek.git
git push -u origin main
```

Jika GitHub CLI tersedia:

```bash
gh auth login
gh repo create nama-projek --public --source=. --remote=origin --push
gh repo create nama-projek --private --source=. --remote=origin --push
gh repo view
```

### Clone repository

```bash
git clone https://github.com/USERNAME/nama-projek.git
git clone https://github.com/USERNAME/nama-projek.git nama-folder
cd nama-folder
git status
```

### Status dan perubahan

```bash
git status
git status --short
git diff
git diff --stat
git diff -- nama-file
git add nama-file
git add .
git add -A
git reset nama-file
git reset
git restore nama-file
git restore --source=HEAD nama-file
git restore --staged nama-file
git commit -m "Penerangan perubahan"
git commit --amend -m "Penerangan baharu"
```

Gunakan `git restore` untuk memulihkan fail. Gunakan `git reset` atau `git restore --staged` untuk membuang fail daripada staging sahaja; ia tidak selalu memadam kandungan fail.

### Branch

```bash
git branch
git branch -a
git branch nama-cabang
git switch nama-cabang
git switch -c nama-cabang
git checkout nama-cabang
git checkout -b nama-cabang
git branch -m nama-baharu
git branch -d nama-cabang
git branch -D nama-cabang
git push origin --delete nama-cabang
```

Untuk repo yang masih menggunakan nama default `master`:

```bash
git branch -M main
```

### Fetch, pull dan push

```bash
git remote -v
git remote add origin URL
git remote set-url origin URL-BAHARU
git remote remove origin
git fetch origin
git pull origin main
git pull --rebase origin main
git push
git push -u origin main
git push origin nama-cabang
git push --force-with-lease
```

Jangan gunakan `git push --force`; lebih selamat ialah `git push --force-with-lease` apabila benar-benar perlu menulis semula sejarah, dan pastikan tiada kerja rakan akan hilang.

### Merge dan rebase

```bash
git merge nama-cabang
git merge --abort
git rebase nama-cabang
git rebase --continue
git rebase --abort
git rebase -i HEAD~3
git cherry-pick <commit-id>
git cherry-pick --abort
```

### Sejarah dan inspect

```bash
git log
git log --oneline --decorate --graph --all
git log -n 10
git show <commit-id>
git blame nama-file
git grep "teks-yang-dicari"
git reflog
```

---

## 9. Membatalkan kesalahan dan memadam

### Buang perubahan yang belum commit

Untuk satu fail:

```bash
git restore nama-file
```

Untuk semua fail:

```bash
git restore .
```

Jangan gunakan jika perubahan dalam fail itu memang mahu disimpan.

### Buang fail daripada staging

```bash
git restore --staged nama-file
git restore --staged .
```

Ini tidak memadam fail daripada komputer.

### Padam fail

Dengan terminal biasa:

```bash
rm nama-file
rm -r nama-folder
```

Kemudian rekodkan pengubahsusan pada Git:

```bash
git rm nama-file
git rm -r nama-folder
git commit -m "Padam nama-file"
git push origin main
```

Untuk fail di workspace tetapi belum ditambah ke Git:

```bash
rm -rf nama-folder
```

Untuk file `.gitignore` yang tersalah dikepilkan:

```bash
git rm --cached nama-file
git rm -r --cached nama-folder
echo "nama-file" >> .gitignore
git add .gitignore
git commit -m "Tambah nama-file ke gitignore"
```

### Buang commit terakhir

Simpan perubahan sebagai commit baharu yang membalikkan commit terakhir:

```bash
git revert HEAD
git revert <commit-id>
```

Buang commit secara setempat dengan reset:

```bash
git reset --soft HEAD~1   # Kekalkan perubahan dalam staging
git reset HEAD~1          # Kekalkan perubahan sebagai unstaged
git reset --hard HEAD~1   # Buang perubahan; berbahaya
```

Untuk kembali sepenuhnya ke commit tertentu:

```bash
git reflog
git reset --hard <commit-id>
```

Selepas menulis semula sejarah yang telah dihantar:

```bash
git push --force-with-lease origin main
```

### Pulih fail atau commit selepas tersalah padam

```bash
git reflog
git fsck --lost-found
git log --all --oneline
git restore --source=<commit-id> nama-file
git switch -c recovery/<commit-id> <commit-id>
```

### Padam tag

```bash
git tag
git tag nama-tag
git tag -d nama-tag
git push origin --delete nama-tag
git push origin nama-tag
```

### Padam remote

```bash
git remote remove origin
git remote -v
```

### Padam stash

```bash
git stash
git stash push -m "Penerangan"
git stash list
git stash apply stash@{0}
git stash pop
git stash show -p stash@{0}
git stash drop stash@{0}
git stash clear
```

---

## 10. GitHub CLI

Pasang GitHub CLI:

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install -y gh
```

openSUSE:

```bash
sudo zypper install gh
```

Fedora:

```bash
sudo dnf install -y gh
```

Semak dan login:

```bash
gh --version
gh auth login
gh auth status
```

Arahan repo:

```bash
gh repo create
gh repo create nama-repo --public
gh repo create nama-repo --private
gh repo clone OWNER/nama-repo
gh repo view
gh repo view OWNER/nama-repo --web
```

Arahan pull request:

```bash
gh pr create
gh pr list
gh pr status
gh pr view
gh pr checkout <nomber-pr>
gh pr merge
gh pr close <nomber-pr>
```

Arahan issue:

```bash
gh issue create
gh issue list
gh issue view <nomber>
```

---

## 11. GitHub Codespaces

Buka terminal dalam Codespace, kemudian semak repo:

```bash
pwd
git status
git remote -v
node --version
python3 --version
java --version
```

Bina repo baharu dengan GitHub CLI:

```bash
mkdir nama-repo
cd nama-repo
git init
echo "# Nama Repo" > README.md
git add -A
git commit -m "Initial commit"
git branch -M main
gh auth login
gh repo create nama-repo --public --source=. --remote=origin --push
```

Untuk Codespace dari GitHub CLI:

```bash
gh codespace list
gh codespace create --repo OWNER/nama-repo --branch main
gh codespace ssh --codespace <nama-codespace>
gh codespace delete --codespace <nama-codespace>
```

Di terminal lokal:

```bash
git clone https://github.com/OWNER/nama-repo.git
cd nama-repo
code .
```

Arahan devcontainer:

```bash
ls -la .devcontainer
docker --version
code --list-extensions
```

---

## 12. Pasang dan gunakan Docker

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install -y ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

Kemudian tambah repositori rasmi Docker mengikut distro Ubuntu/Debian yang digunakan, atau gunakan Docker Desktop pada Windows/macOS.

Arahan Docker:

```bash
docker --version
docker ps
docker ps -a
docker images
docker pull nama-imej
docker run --rm nama-imej
docker build -t nama-imej .
docker stop nama-container
docker rm nama-container
docker rmi nama-imej
docker compose up
docker compose up -d
docker compose down
docker compose logs -f
```

---

## 13. MCP (Model Context Protocol)

MCP membolehkan klien AI berhubung dengan alat luaran seperti repository, pangkalan data atau API.

### Semak fail konfigurasi pelbagai klien

Kodex/OpenCode/VSCodium/VS Code:

```bash
ls -la ~/.config
ls -la ~/.config/opencode
ls -la .vscode
```

Contoh konfigurasi MCP JSON di dalam OpenCode:

```json
{
  "mcp": {
    "github": {
      "type": "remote",
      "url": "https://api.githubcopilot.com/mcp/",
      "enabled": true
    }
  }
}
```

### Contoh MCP local menggunakan npm

```bash
npm install -g @modelcontextprotocol/server-filesystem
npm install -g @modelcontextprotocol/server-github
```

Contoh konfigurasi lokal:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/workspaces"
      ]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "TOKEN_ANDA"
      }
    }
  }
}

```

Jangan commit token, PAT atau secret ke dalam Git. Gunakan environment variable atau rahsia Codespaces.

### Tetapkan secret untuk MCP

```bash
export GITHUB_PERSONAL_ACCESS_TOKEN="ghp_xxx"
printenv GITHUB_PERSONAL_ACCESS_TOKEN
unset GITHUB_PERSONAL_ACCESS_TOKEN
```

Untuk menyimpan secara kekal dalam shell:

```bash
chmod 600 ~/.bashrc
printf '\nexport GITHUB_PERSONAL_ACCESS_TOKEN="ghp_xxx"\n' >> ~/.bashrc
source ~/.bashrc
```

Daripada menulis rahsia terus ke `~/.bashrc`, lebih baik guna GitHub Codespaces Secrets atau secret manager klien MCP.

### Pasang MCP semasa menggunakan VS Code/Codespaces

1. Buka Command Palette: `Ctrl+Shift+P`.
2. Cari `MCP: Add Server` atau arahan MCP yang disokong versi VS Code.
3. Pilih sama ada STDIO atau HTTP/Remote.
4. Masukkan arahan `npx`, server package atau URL MCP.
5. Restart MCP server.
6. Semak log MCP jika gagal.

### Debug MCP

```bash
node --version
npx --version
npx -y @modelcontextprotocol/inspector
npm view @modelcontextprotocol/server-github version
curl -I https://api.github.com
```

---

## 14. Editor dan alatan pembangunan

VS Code:

```bash
code --version
code .
code nama-file
code --install-extension ms-python.python
code --install-extension redhat.java
code --install-extension dbaeumer.vscode-eslint
code --uninstall-extension nama-extension
code --list-extensions
code --disable-extensions
```

GitHub CLI:

```bash
sudo apt install -y gh
gh auth login
```

Vim/Neovim:

```bash
sudo apt install -y vim neovim
vim nama-file
nvim nama-file
```

Arahan asas Vim:

```text
i       masuk mod insert
Esc     keluar mod insert
:w      simpan
:q      keluar
:wq     simpan dan keluar
:q!     keluar tanpa simpan
u       undo
:paste  tampal teks
```

---

## 15. SSH untuk GitHub

Semak atau bina SSH key:

```bash
ls -la ~/.ssh
ssh-keygen -t ed25519 -C "email@example.com"
cat ~/.ssh/id_ed25519.pub
```

Salin public key kepada GitHub:

```text
GitHub → Settings → SSH and GPG keys → New SSH key
```

Uji sambungan:

```bash
ssh -T git@github.com
```

Clone melalui SSH:

```bash
git clone git@github.com:OWNER/nama-repo.git
```

---

## 16. Environment variable

```bash
printenv
printenv NAMA_VARIABLE
export NAMA_VARIABLE="nilai"
unset NAMA_VARIABLE
echo $NAMA_VARIABLE
```

Tambah kekal untuk bash:

```bash
echo 'export NAMA_VARIABLE="nilai"' >> ~/.bashrc
source ~/.bashrc
```

Untuk zsh:

```bash
echo 'export NAMA_VARIABLE="nilai"' >> ~/.zshrc
source ~/.zshrc
```

Untuk projek Node.js:

```text
.env
.env.local
.env.example
```

Jangan commit `.env`. Contoh:

```text
DATABASE_URL=
API_KEY=
```

`.gitignore` juga mesti mengandungi:

```text
.env
.env.*
!.env.example
node_modules/
dist/
build/
.venv/
```

---

## 17. Arahan berguna untuk debug

```bash
uname -a
lsb_release -a
cat /etc/os-release
whoami
hostname
df -h
free -h
du -sh *
du -sh nama-folder
top
htop
ps aux
ps aux | grep node
kill <PID>
kill -9 <PID>
```

Semak port:

```bash
lsof -i :3000
ss -ltnp | grep 3000
kill $(lsof -t -i:3000)
```

Untuk DNS dan internet:

```bash
ping github.com
curl -I https://github.com
curl -I https://api.github.com
wget https://example.com/file.zip
```

---

## 18. Aliran kerja Git yang disarankan

```bash
git switch main
git pull origin main
git switch -c feature/nama-fitur
git status
git add -A
git commit -m "Tambah nama fitur"
git push -u origin feature/nama-fitur
gh pr create --title "Tambah nama fitur" --body "Penerangan perubahan"
```

Selepas PR diluluskan:

```bash
git switch main
git pull origin main
git branch -d feature/nama-fitur
```

---

## 19. Arahan repo ini

Untuk repo `opencode-io/opencode.io`:

```bash
git clone https://github.com/opencode-io/opencode.io.git
cd opencode.io
cat package.json
npm install
npm run dev
```

Jika nama versi atau skrip berbeza, semak dahulu:

```bash
cat package.json
npm run
```

Untuk membuat cabang baharu dalam repo ini:

```bash
git switch main
git pull origin main
git switch -c feature/nama-saya
git add prompt/ARAHAN-JALAN.md
git commit -m "docs: tambah panduan arahan terminal"
git push -u origin feature/nama-saya
gh pr create --title "Tambah panduan arahan terminal"
```

---

## 20. Amaran keselamatan

- Gunakan `sudo` hanya jika arahan itu benar-benar memerlukan akses pentadbir.
- Jangan jalankan `rm -rf /`, `rm -rf ~`, `chmod -R 777` atau arahan yang tidak difahami.
- Jangan pamerkan `GITHUB_TOKEN`, SSH private key atau password dalam terminal atau commit.
- Semak `git status` dan `git diff` sebelum commit.
- Gunakan `--force-with-lease`, bukan `--force`.
- Simpan salinan projek sebelum menjalankan `git reset --hard`.
- Semak setiap skrip yang dipasang melalui `curl | bash` terlebih dahulu.
- Gunakan persekitaran Maya Python dan Node version manager untuk mengelakkan konflik versi.
