# Panduan Instalasi Hyperspace Nodes
Panduan ini menjelaskan langkah-langkah untuk menginstal, mengonfigurasi, dan mengelola Hyperspace Nodes di VPS Anda.
For more information, For more information, visit the [official website](https://node.hyper.space).

# Persyaratan
- VPS: Minimal RAM 8GB untuk Tier 3. Jika kurang, gunakan Tier 5.
- Akses SSH: Pastikan Anda memiliki akses SSH ke VPS.
- Pengetahuan Dasar: Pemahaman dasar tentang perintah Linux terminal.

## Langkah-langkah Instalasi dan Konfigurasi
1. Install Hyperspace Nodes
```bash
curl https://download.hyper.space/api/install | bash
```
2. Muat Ulang Bash Profile
```bash
source /root/.bashrc
```
3. Buat File my.pem
```bash
nano my.pem
```
Simpan file dengan menekan CTRL + S lalu keluar dengan CTRL + X.
4. Atur Izin untuk File my.pem
```bash
chmod 600 my.pem
```

5. Buat Screen Baru untuk Hyperspace Nodes
```bash
screen -S Hypernodes
```
- exit Jalankan script berikut, dengan menekan CTRL + A + D:

6. Jalankan Script Hyperspace Nodes
```bash
aios-cli start
```

7. Periksa Model dan Tier yang Tersedia
```bash
aios-cli models available
```
## Pilih Tier sesuai spesifikasi VPS:
- Tier 3: Untuk RAM 8GB atau lebih.
- Tier 5: Untuk RAM kurang dari 8GB.
- Gunakan perintah berikut untuk memilih tier:
```bash
aios-cli hive select-tier 5
```

8. Tambahkan Model Default
```bash
Salin kode
aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
```

9. Jalankan Script Inference
```bash
aios-cli infer --model hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf --prompt "Can you explain the concept of hyperspace and its applications in science fiction?"
```
- Atau gunakan prompt khusus:

```bash
aios-cli hive infer --model hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf --prompt "Hello, Mad.jr Here! Can you explain hyperspace and its connection to modern science?"
```
- Jika gagal, "filed" lanjutkan ke langkah login.

10. Impor PV.key dan Login
## Impor file PV.key lalu login ke Hive:
```bash
aios-cli hive import-keys ./my.pem
aios-cli hive login
```

11. Sambungkan ke Jaringan Hive
```bash
aios-cli hive connect
```

12. Cek Poin Anda
- Cek saldo poin Anda di Hive:
```bash
aios-cli hive points
```

13. Cek PV.key dan Pub.Key
- Verifikasi status kunci publik dan privat Anda:
```bash
aios-cli hive whoami
```

14. Hentikan Node
```bash
aios-cli kill
```

15. Masuk ke Screen Hyperspace
```bash
screen -r Hypernodes
```

16. Mulai Node dan Sambungkan
```bash
aios-cli start --connect
```

> Catatan Tambahan
- Tier 3: Gunakan untuk VPS dengan RAM 8GB atau lebih.
- Tier 5: Gunakan untuk VPS dengan RAM kurang dari 8GB.
- Informasi Lebih Lanjut: Kunjungi node.hyper.space.
