
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Satu Atap Tenang ☕</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #0f172a; /* Biru navy gelap, sangat menenangkan mata */
            color: #f1f5f9; 
            font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, Roboto, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            line-height: 1.6;
        }

        .container {
            max-width: 550px;
            width: 88%;
            padding: 30px 20px;
        }

        h1 {
            font-size: 1.6rem;
            color: #38bdf8; /* Biru muda cerah tapi lembut */
            text-align: center;
            margin-bottom: 15px;
        }

        p {
            font-size: 1rem;
            opacity: 0.9;
        }

        .opening-text {
            text-align: justify;
            margin-bottom: 30px;
        }

        /* Kotak Quotes Tokoh mengenai Zona Nyaman */
        .quote-box {
            background-color: #1e293b; /* Biru keabuan */
            border-left: 4px solid #0284c7; /* Aksen biru langit */
            padding: 15px;
            border-radius: 4px;
            margin: 25px 0;
            font-style: italic;
        }

        .quote-author {
            display: block;
            text-align: right;
            font-style: normal;
            font-size: 0.85rem;
            color: #7dd3fc;
            margin-top: 5px;
        }

        /* Bagian Akordion/Tombol */
        .box-container {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-top: 20px;
        }

        .secret-box {
            background-color: #1e293b;
            border: 1px solid #334155;
            border-radius: 8px;
            padding: 15px;
            cursor: pointer;
            transition: background 0.2s, border-color 0.2s;
        }

        .secret-box:hover {
            background-color: #24344d;
        }

        .box-title {
            margin: 0;
            font-size: 0.95rem;
            color: #7dd3fc;
            font-weight: 600;
        }

        .box-content {
            display: none;
            margin-top: 10px;
            font-size: 0.95rem;
            color: #ffffff;
            border-top: 1px dashed #334155;
            padding-top: 10px;
            text-align: left;
        }

        /* Penutup */
        .closing {
            margin-top: 40px;
            text-align: center;
            border-top: 1px solid #1e293b;
            padding-top: 20px;
        }

        .wa-button {
            display: inline-block;
            background-color: #0284c7;
            color: white;
            text-decoration: none;
            padding: 10px 20px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: bold;
            margin-top: 10px;
            box-shadow: 0 4px 10px rgba(2, 132, 199, 0.3);
            transition: background 0.2s;
        }

        .wa-button:hover {
            background-color: #0369a1;
        }
    </style>
</head>
<body>

    <div class="container">

        <h1>Napas dulu, santai... ✨</h1>
        
        <p class="opening-text">
            Hari ini hari H pengumuman ya? Wajar banget kalau lu lagi deg-degan atau overthinking sekarang. Kuliah sambil curi-curi waktu buat belajar UTBK lagi lewat jalur <em>semi-gapyear</em> itu capeknya double, dan lu udah berhasil ngelewatin itu sampai titik ini. Lu keren, beneran.
        </p>

        <!-- Quotes Tokoh Dunia tentang Keluar dari Zona Nyaman -->
        <div class="quote-box">
            "Life begins at the end of your comfort zone."
            <span class="quote-author">— Neale Donald Walsch</span>
        </div>

        <p style="color: #7dd3fc; font-size: 0.9rem; text-align: center; margin-bottom: 15px;">
            (Klik kotak di bawah buat buka pesan)
        </p>

        <div class="box-container">
            <!-- Kotak 1 -->
            <div class="secret-box" onclick="toggleBox(this)">
                <p class="box-title">🎯 Separuh Langkah Perjuangan...</p>
                <div class="box-content">
                    Lu milih Teknik Industri atau Sekolah Bisnis karena lu emang punya minat di sana. Pilihan kampus lu emang tinggi dan kompetitif, tapi itu bukti kalau lu berani menantang diri buat keluar dari zona nyaman. Apapun hasilnya nanti jam 3 sore, ambisi dan isi kepala lu gak bakal hilang cuma karena hasil satu ujian. Dan Alhamdulliah kalau memang rezeki dan takdir elu, Pliss jangan sia-sia in kesempatan ini, karna perjalan lu yang sebenernya baru dimulai
                </div>
            </div>

            <!-- Kotak 2 -->
            <div class="secret-box" onclick="toggleBox(this)">
                <p class="box-title">👥 Mereka Gak Penting...</p>
                <div class="box-content">
                    Orang lain cuma bisa ngomong atau berkomentar, tapi mereka gak tahu gimana perjuangan lu bagi waktu setahun ini. Gak usah dengerin yang bikin lu drop. Keberanian lu buat mencoba lagi di tahun ini udah membuktikan kalau mental lu jauh di atas mereka yang cuma bisa komentar, Azeeek. Temen-Temen dan Orang tua lu cuman peduli lu doang bukan kampus-kampus itu.
                </div>
            </div>

            <!-- Kotak 3 -->
            <div class="secret-box" onclick="toggleBox(this)">
                <p class="box-title">🚪 Apapun warnanya nanti...</p>
                <div class="box-content">
                    Kalau hijau, kita selebrasi bareng. Kalau ternyata belum rezeki, lu harus ingat kalau ini bukan akhir dari segalanya. Langkah lu keluar dari zona aman dengan mengambil rute <em>semi-gapyear</em> udah ngebentuk mental lu jadi jauh lebih kuat. Masih banyak jalur lain (jalur mandiri, dll) dan lu gak bakal mulai dari nol lagi.
                </div>
            </div>
        </div>

        <!-- Bagian Akhir -->
        <div class="closing">
            <p>Nanti sore setelah lihat pengumuman, Apapun hasilnya, <em>I've got your back.</em></p>
            <!-- Ganti nomor di bawah ini dengan nomor WA-mu -->
            <a href="https://wa.me/62895402920321?text=Gue%20udah%20buka%20webnya,%20thanks%20ya..." class="wa-button" target="_blank">
                Pencet di sini kalau butuh temen ngobrol ☕
            </a>
        </div>
    </div>

    <script>
        function toggleBox(element) {
            var content = element.querySelector('.box-content');
            
            // Perbaikan Bug Toggle: Menggunakan getComputedStyle agar deteksi display lebih akurat
            var currentDisplay = window.getComputedStyle(content).display;

            if (currentDisplay === "block") {
                content.style.display = "none";
                element.style.borderColor = "#334155"; // Kembali ke warna border awal
            } else {
                content.style.display = "block";
                element.style.borderColor = "#0284c7"; // Mengubah border jadi biru terang saat aktif
            }
        }
    </script>

</body>
</html>
