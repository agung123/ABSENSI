# SIMPEG Ciamis - Android WebView App

Aplikasi Android sederhana yang membuka **https://simpeg3.ciamiskab.go.id/** di dalam tampilan native (WebView), lengkap dengan:

- **Toolbar** bertema hijau (bisa diganti warnanya di `res/values/colors.xml`)
- **Progress bar** tipis saat halaman sedang dimuat
- **Swipe-to-refresh** (tarik ke bawah untuk memuat ulang)
- **Tampilan "tidak ada koneksi"** otomatis + tombol "Coba Lagi" saat internet mati atau gagal load
- **Tombol back** perangkat akan mundur ke halaman sebelumnya di dalam web (bukan langsung keluar app)
- Support **dark/light** mengikuti tema sistem (Material Components DayNight)
- Ukuran layar otomatis menyesuaikan (viewport & zoom sudah diatur agar tampilan web tetap rapi di HP)

## Cara Membuka & Menjalankan

1. Ekstrak file zip ini.
2. Buka folder hasil ekstrak dengan **Android Studio** (File → Open → pilih folder `simpeg-app`).
3. Tunggu Gradle sync selesai (Android Studio akan otomatis mengunduh dependency).
4. Klik tombol **Run ▶** untuk menjalankan di emulator atau HP Android yang terhubung (aktifkan USB Debugging).

## Cara Build APK Sendiri (tanpa Android Studio)

Jika sudah punya Android SDK & Gradle terpasang, dari dalam folder proyek jalankan:

```bash
./gradlew assembleDebug
```

APK hasil build akan ada di:
```
app/build/outputs/apk/debug/app-debug.apk
```

## Kustomisasi Cepat

| Yang ingin diubah        | File                                                    |
|---------------------------|----------------------------------------------------------|
| URL website                | `MainActivity.kt` → variabel `siteUrl`                  |
| Nama aplikasi              | `res/values/strings.xml` → `app_name`                   |
| Warna tema                 | `res/values/colors.xml`                                 |
| Ikon aplikasi              | `res/drawable/ic_launcher_foreground.xml` + `colors.xml` → `ic_launcher_background` |
| Package/applicationId      | `app/build.gradle` (`namespace`, `applicationId`) & path folder `java/com/ciamiskab/simpeg` |

## Catatan

- Aplikasi ini butuh izin **Internet** (sudah ditambahkan otomatis di `AndroidManifest.xml`).
- Konten ditampilkan sebagaimana adanya dari website resmi SIMPEG Kabupaten Ciamis — tampilan "simple & dinamis" di sini mengacu pada wrapper aplikasinya (WebView + UI native minimalis); tampilan responsif halaman itu sendiri tetap mengikuti desain situs aslinya.
- Jika situs menggunakan login/session, cookie akan otomatis tersimpan selama aplikasi berjalan berkat `domStorageEnabled`.
