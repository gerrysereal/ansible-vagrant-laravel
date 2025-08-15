## Deskripsi Proyek
Proyek ini berisi skrip **Ansible** untuk mengotomatisasi proses penyiapan (*provisioning*) server pengembangan Laravel.  
Tujuannya adalah membuat setup server yang **standar**, **cepat**, dan **konsisten** untuk semua developer.  

Lingkungan ini dijalankan menggunakan **Vagrant** dan **VirtualBox**, sehingga Anda bisa bekerja secara lokal tanpa harus menyewa server di **GCP**, **AWS**, atau penyedia *cloud* lainnya.  
Selain itu, *playbook* Ansible di sini **portabel** – artinya, Anda bisa menggunakannya di server manapun dengan sedikit atau tanpa perubahan sama sekali.  

### Stack yang Diinstal
- **Apache** 2.4.56  
- **PHP** 8.2 + module `fpm`, `curl`, `xml`, `mbstring`, `gd`, `imagick`, `imap`, `intl`, `mysqli`, `pgsql`, `zip`  
- **Node.js** v20.13.1 & **NPM** 10.5.2  
- **Composer** (PHP dependency manager)  
- **Laravel** 11 (sesuai dokumentasi resmi **https://laravel.com/docs/11.x**)  

---

## Requirement
Sebelum mulai, pastikan Anda sudah menginstal:
1. **Vagrant** → [Download](https://www.vagrantup.com/downloads)  
2. **VirtualBox** → [Download](https://www.virtualbox.org/wiki/Downloads)  
3. **Ansible**  
   - Instal via `pip`:
     ```bash
     pip install ansible
     ```
   - Atau ikuti [Panduan Resmi](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)  

---

## Langkah Instalasi
1. **Clone repositori**
   git clone <https://github.com/gerrysereal/ansible-vagrant-laravel.git
   cd <ansible-vagrant-laravel>
2. **Jalankan VM & provisioning**
    <vagrant up>
    Perintah ini akan:

    **Membuat VM baru dari Vagrantfile**
    **Menyalakan VM**
    **Menjalankan Ansible untuk menginstal semua stack di atas**
3. **Akses Laravel**
    setelah selesai, buka browser:
    **http://192.168.56.10**
    


## Structure Folder
    ansible-vagrant-laravel/
├── .gitignore
├── Vagrantfile         # Konfigurasi utama untuk Vagrant (VM, Jaringan, Ansible)
├── inventory.ini       # Inventory Ansible untuk mendefinisikan host (VM)
├── provision.yml       # Playbook utama Ansible yang memanggil semua task
└── provisioning/
    ├── handlers/
    │   └── main.yml    # Handler untuk service (contoh: restart apache)
    ├── tasks/          # Direktori berisi semua file task Ansible
    │   ├── apache.yml
    │   ├── composer.yml
    │   ├── laravel.yml
    │   ├── node.yml
    │   ├── php.yml
    │   └── verify.yml
    └── vars/
        └── main.yml     # Semua variabel yang digunakan dalam playbook

## Cara menjalankan
1. Provisioning ulang (kalau ada perubahan skrip)
    **vagrant provision**
2. Masuk ke VM
    **vagrant ssh**
3. Matikan VM
    **vagrant halt**
4. Hapus VM
    **vagrant destroy --force**

## Hasil Screnshoot
    (https://www.notion.so/Screnshoot-Hasil-25019f6a565f803b823dcbbb33b34d50?source=copy_link)


## Hasil Logs
    (https://www.notion.so/Hasil-Logs-25019f6a565f80c2af64c9e84047862e?source=copy_link)