# 🤖 Instalasi ROS 2 Humble Hawksbill (Dari Nol)

Panduan ini dibuat untuk kamu yang ingin **menginstal ROS 2 Humble dari awal sampai siap dipakai**, tanpa asumsi aneh-aneh seperti “pasti sudah pernah install Linux”. Cocok untuk **mahasiswa robotika**, **anggota Motion Amarine**, atau siapa pun yang ingin hidupnya sedikit lebih bermakna dengan robot.

---

## 📌 Apa Itu ROS 2?

**ROS 2 (Robot Operating System 2)** adalah framework open-source untuk membangun sistem robotika modern, mulai dari simulasi hingga robot sungguhan.

Pada panduan ini kita menggunakan:

* **ROS 2 Humble Hawksbill**
* **Ubuntu 22.04 LTS (Jammy Jellyfish)**

Kenapa Humble?

* Versi **LTS**
* Stabil
* Dipakai luas di riset, kompetisi, dan industri

---

## 🧰 Kebutuhan Awal

### 🔧 Hardware Minimum

* Laptop / PC 64-bit
* RAM minimal 8 GB (4 GB masih bisa, tapi sabar)
* Storage kosong minimal 50 GB
* Virtualization aktif di BIOS

### 💻 Software

* **VMware Workstation Player / Pro**
* **File ISO Ubuntu 22.04 LTS**
* Koneksi internet stabil

---

## 💿 Instalasi Ubuntu 22.04 di VMware

### 1️⃣ Install VMware

* Download VMware Workstation dari website resmi
* Install seperti aplikasi biasa
* Restart jika diminta

### 2️⃣ Buat Virtual Machine

1. Buka VMware → **Create a New Virtual Machine**
2. Pilih **Installer disc image file (ISO)**
3. Masukkan file **Ubuntu 22.04 LTS.iso**
4. Guest OS: **Linux – Ubuntu 64-bit**

### 3️⃣ Konfigurasi VM (Disarankan)

* CPU: 2 core atau lebih
* RAM: 4–8 GB
* Storage: 40–50 GB
* Network: NAT

Klik **Finish**, lalu jalankan VM.

### 4️⃣ Install Ubuntu

* Pilih **Normal Installation**
* Centang **Install third-party software**
* Pilih **Erase disk and install Ubuntu** (aman, ini disk virtual)
* Atur username & password

Tunggu hingga selesai dan masuk ke desktop Ubuntu.

---

## 🖥️ Setup Awal Ubuntu

Buka terminal:

```bash
Ctrl + Alt + T
```

Update sistem:

```bash
sudo apt update && sudo apt upgrade -y
```

Ubuntu sekarang siap untuk ROS 2.

---

## 🌍 Konfigurasi Locale (WAJIB)

ROS 2 butuh UTF-8 agar tidak error.

```bash
locale

sudo apt install locales -y
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

---

## 📦 Tambahkan Repository ROS 2

```bash
sudo apt install software-properties-common -y
sudo add-apt-repository universe -y

sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key \
-o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] \
http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" \
| sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

---

## 🤖 Instalasi ROS 2 Humble

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install ros-humble-desktop -y
```

⏳ Proses ini cukup lama. Jangan panik, jangan ditutup.

---

## 🌱 Setup Environment ROS 2

Agar perintah `ros2` otomatis aktif setiap buka terminal:

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

Cek:

```bash
ros2 --help
```

---

## 🐢 Verifikasi Instalasi (Turtlesim)

### Terminal 1

```bash
ros2 run turtlesim turtlesim_node
```

### Terminal 2

```bash
ros2 run turtlesim turtle_teleop_key
```

Gunakan tombol panah untuk menggerakkan kura-kura.

Jika kura-kura bergerak, **instalasi berhasil** 🎉

---

## ✅ Checklist Berhasil

* `ros2` dikenali di terminal
* Tidak ada error merah
* Turtlesim berjalan normal

---

## 🚀 Next Step

* Buat workspace ROS 2
* Buat package sendiri
* Integrasi dengan robot atau simulasi

---

## 🏁 Penutup

Selamat. Kamu sekarang resmi punya environment ROS 2 yang layak dipakai untuk belajar, riset, dan kompetisi.

Robot mungkin belum pintar, tapi kamu selangkah lebih dekat.
