KAMEN RIDER - PC
================
Port PC oleh Indra Sundanese.
Dua game PS4 berjalan di Windows dengan Vulkan, dari satu launcher:
  KAMEN RIDER memory of heroez   (CUSA17374)  1 pemain           bisa dimainkan
  KAMEN RIDER Climax Fighters    (CUSA09534)  1-4 pemain (lokal) baru sampai menu, belum bisa gameplay
Perangkat lunak bebas, GNU GPL v2 atau lebih baru. Kredit: NOTICE.md. Tidak ada file game yang disertakan.

Cara bermain
  1. Gunakan dump game milikmu sendiri (folder yang berisi eboot.bin, base game + update sudah digabung).
     Taruh masing-masing di foldernya sendiri di dalam "game\" (misalnya game\KMOH dan game\KRCF),
     atau pilih lewat "Browse..." di launcher.
  2. Buka "KAMEN RIDER Launcher.exe", pilih game di bagian atas, atur pengaturanmu, lalu tekan PLAY.
  Saat pertama kali dijalankan, game meng-compile shader dan akan patah-patah untuk sementara; shader disimpan di shader cache.

Persyaratan
  Windows 10 atau 11, 64-bit. CPU yang mendukung AVX2. Kartu grafis dengan Vulkan 1.3 dan driver terbaru.

Isi folder
  KAMEN RIDER Launcher.exe   pilih game, pengaturan dan tombol mulai
  bin\                       runtime (kmoh-core.exe)
  game\                      dump game milikmu (lokasi opsional)
  user\                      save, shader cache (kecuali dipindah), log, kontrol, pengaturan

Opsi launcher (disimpan terpisah untuk setiap game)
  Mode jendela        Windowed, Borderless fullscreen, Exclusive fullscreen
  Ukuran jendela      720p, 900p, 1080p, 1440p, 4K
  Resolusi render     720p atau 1080p (maksimum PS4)
  Upscaling           Mati atau AMD FSR 1, dengan opsi penajaman RCAS
  Frame rate          memory of heroez: 30 FPS (asli) atau 60 FPS (eksperimental)
                      Climax Fighters: 60 FPS (asli)
  VSync, penghitung FPS, bahasa (Inggris, Jepang, Mandarin Tradisional, Korea), tombol konfirmasi
  Controls...         pemetaan keyboard (dua tombol per aksi, per pemain) dan controller
  Shader cache        folder untuk shader yang sudah di-compile (bawaan user\cache); Clear untuk membangun ulang

Multiplayer lokal (Climax Fighters)
  Controller (XInput, DualShock 4, DualSense) masuk sebagai Player 1-4 sesuai urutan saat dicolokkan.
  "Players at start" memungkinkan pemain tanpa controller ikut pakai keyboard: atur tombolnya di
  Controls... (pilih pemainnya di kanan atas). "Players..." untuk mengatur nama pemain.
  Di dalam game: F5 menambah pemain, F4 mengeluarkan pemain terakhir.

Kontrol
  Setiap game punya file kontrolnya sendiri: user\input_config\<TITLE_ID>.ini.

Masalah
  Lampirkan user\log\shad_log.txt di laporanmu dan sebutkan game yang mana.
