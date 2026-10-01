<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SSO UNDIP - Sistem Tiket Makan Gratis Kampus</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        undip: {
                            navy: '#002855',
                            blue: '#003366',
                            lightBlue: '#1a4971',
                            gold: '#f39c12',
                            goldHover: '#d38307',
                            accent: '#e67e22',
                            bg: '#f4f6f9'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        .sso-gradient {
            background: linear-gradient(135deg, #001f3f 0%, #003366 60%, #004080 100%);
        }
        .ticket-pattern {
            background-color: #ffffff;
            background-image: radial-gradient(#003366 0.75px, transparent 0.75px);
            background-size: 12px 12px;
        }
    </style>
</head>
<body class="bg-undip-bg font-sans text-gray-800 min-h-screen flex flex-col">

    <!-- Top Undip Brand Bar -->
    <header class="sso-gradient text-white shadow-md border-b-4 border-undip-gold sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3 flex items-center justify-between">
            <div class="flex items-center space-x-3">
                <div class="bg-white p-1.5 rounded-full shadow-inner flex items-center justify-center w-10 h-10 border border-undip-gold">
                    <i class="fa-solid font-bold text-undip-navy text-xl">U</i>
                </div>
                <div>
                    <h1 class="font-bold text-lg sm:text-xl tracking-tight flex items-center gap-2">
                        SSO UNDIP <span class="bg-undip-gold text-undip-navy text-xs px-2 py-0.5 rounded font-semibold uppercase">Meal Pass</span>
                    </h1>
                    <p class="text-xs text-blue-200 hidden sm:block">Sistem Informasi Antrean & Distribusi Makanan Gratis Universitas Diponegoro</p>
                </div>
            </div>

            <div id="user-profile-badge" class="flex items-center space-x-3 bg-white/10 px-3 py-1.5 rounded-lg border border-white/20">
                <div class="text-right hidden sm:block">
                    <p id="nav-user-name" class="text-xs font-semibold text-white">Budi Santoso</p>
                    <p id="nav-user-nim" class="text-[10px] text-blue-200">NIM: 24060121120001 | FTIK</p>
                </div>
                <div class="w-8 h-8 bg-undip-gold text-undip-navy font-bold rounded-full flex items-center justify-center text-sm shadow">
                    BS
                </div>
            </div>
        </div>
    </header>

    <!-- Navigation Tabs -->
    <nav class="bg-white border-b border-gray-200 shadow-sm sticky top-[60px] z-40">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex overflow-x-auto space-x-1 sm:space-x-4 py-2 scrollbar-none">
            <button onclick="switchTab('tab-menu')" id="btn-tab-menu" class="nav-btn px-4 py-2 rounded-md text-sm font-medium flex items-center space-x-2 text-undip-blue bg-blue-50 border-b-2 border-undip-blue">
                <i class="fa-solid fa-utensils"></i>
                <span>Menu & War Tiket</span>
            </button>
            <button onclick="switchTab('tab-tiket')" id="btn-tab-tiket" class="nav-btn px-4 py-2 rounded-md text-sm font-medium flex items-center space-x-2 text-gray-600 hover:text-undip-blue hover:bg-gray-50">
                <i class="fa-solid fa-ticket"></i>
                <span>Tiket Saya</span>
                <span id="ticket-badge" class="hidden bg-red-500 text-white text-xs px-1.5 py-0.5 rounded-full font-bold">1</span>
            </button>
            <button onclick="switchTab('tab-history')" id="btn-tab-history" class="nav-btn px-4 py-2 rounded-md text-sm font-medium flex items-center space-x-2 text-gray-600 hover:text-undip-blue hover:bg-gray-50">
                <i class="fa-solid fa-clock-rotate-left"></i>
                <span>Riwayat Klaim</span>
            </button>
            <button onclick="switchTab('tab-feedback')" id="btn-tab-feedback" class="nav-btn px-4 py-2 rounded-md text-sm font-medium flex items-center space-x-2 text-gray-600 hover:text-undip-blue hover:bg-gray-50">
                <i class="fa-solid fa-star"></i>
                <span>Penilaian & Vote Menu</span>
            </button>
            <button onclick="switchTab('tab-admin')" id="btn-tab-admin" class="nav-btn px-4 py-2 rounded-md text-sm font-medium flex items-center space-x-2 text-amber-700 hover:bg-amber-50 ml-auto border border-amber-200">
                <i class="fa-solid fa-qrcode"></i>
                <span>Loket Pemindaian (Admin)</span>
            </button>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex-grow w-full">

        <!-- Banner Info Undip -->
        <div class="bg-blue-900 text-white p-4 rounded-xl shadow-lg mb-6 flex flex-col md:flex-row items-center justify-between gap-4 sso-gradient border-l-4 border-undip-gold">
            <div class="flex items-center gap-3">
                <div class="bg-white/20 p-3 rounded-lg text-undip-gold text-2xl hidden sm:block">
                    <i class="fa-solid fa-bullhorn"></i>
                </div>
                <div>
                    <h2 class="text-base sm:text-lg font-bold text-white">Program Nutrisi Mahasiswa Undip Sehat</h2>
                    <p class="text-xs sm:text-sm text-blue-100">War Tiket Makan Siang Buka Pukul <b>10.00 WIB</b> setiap hari kerja. Kuota 1.500 porsi/hari.</p>
                </div>
            </div>
            <div class="flex items-center space-x-2 text-xs bg-white/10 px-3 py-2 rounded-lg border border-white/20">
                <i class="fa-solid fa-server text-green-400"></i>
                <span>Status Server: <b class="text-green-300">Optimal (Anti-Crash Active)</b></span>
            </div>
        </div>

        <!-- ================= TAB 1: MENU & WAR TIKET ================= -->
        <section id="tab-menu" class="tab-content block space-y-6">
            
            <!-- Filter & Operational Slots -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                <div class="bg-white p-4 rounded-xl shadow-sm border border-gray-200 flex items-center space-x-4">
                    <div class="p-3 bg-blue-100 text-undip-blue rounded-lg text-xl">
                        <i class="fa-solid fa-calendar-day"></i>
                    </div>
                    <div>
                        <p class="text-xs text-gray-500 font-medium">Tanggal Distribusi</p>
                        <p id="current-date-str" class="text-sm font-bold text-gray-800">Kamis, 15 Oktober 2026</p>
                    </div>
                </div>

                <div class="bg-white p-4 rounded-xl shadow-sm border border-gray-200 flex items-center space-x-4">
                    <div class="p-3 bg-amber-100 text-amber-800 rounded-lg text-xl">
                        <i class="fa-solid fa-clock"></i>
                    </div>
                    <div>
                        <p class="text-xs text-gray-500 font-medium">Sesi Pengambilan Aktif</p>
                        <select id="session-select" onchange="updateSessionInfo()" class="mt-0.5 text-xs font-bold text-gray-800 bg-gray-50 border border-gray-300 rounded px-2 py-1 focus:ring-undip-blue focus:border-undip-blue">
                            <option value="1">Sesi 1: 11:30 - 12:30 WIB (Kantin Student Center)</option>
                            <option value="2">Sesi 2: 12:30 - 13:30 WIB (Kantin GSG Undip)</option>
                            <option value="3">Sesi 3: 13:30 - 14:30 WIB (Kantin Fakultas Teknik)</option>
                        </select>
                    </div>
                </div>

                <div class="bg-white p-4 rounded-xl shadow-sm border border-gray-200 flex items-center space-x-4">
                    <div class="p-3 bg-emerald-100 text-emerald-800 rounded-lg text-xl">
                        <i class="fa-solid fa-cubes-stacked"></i>
                    </div>
                    <div class="w-full">
                        <div class="flex justify-between items-center text-xs">
                            <span class="text-gray-500 font-medium">Total Sisa Stok Sesi Ini</span>
                            <span id="stock-count-total" class="font-bold text-emerald-600">342 / 500 Porsi</span>
                        </div>
                        <div class="w-full bg-gray-200 h-2 rounded-full mt-2 overflow-hidden">
                            <div id="stock-bar-total" class="bg-emerald-500 h-full rounded-full" style="width: 68.4%;"></div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- List Menu Makanan Hari Ini -->
            <div>
                <div class="flex items-center justify-between mb-4">
                    <h3 class="text-lg font-bold text-gray-800 flex items-center gap-2">
                        <i class="fa-solid fa-plate-wheat text-undip-gold"></i> Pilihan Menu Makan Gratis Hari Ini
                    </h3>
                    <span class="text-xs text-gray-500 bg-gray-100 px-3 py-1 rounded-full border">Pilih 1 Menu per Mahasiswa</span>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-6" id="menu-container">
                    <!-- Menu Cards generated dynamically in JS -->
                </div>
            </div>
        </section>

        <!-- ================= MODAL ANTI-BOT & WAR CAPTCHA ================= -->
        <div id="bot-modal" class="fixed inset-0 bg-black/60 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
            <div class="bg-white rounded-2xl shadow-2xl max-w-md w-full overflow-hidden border border-gray-100 transform transition-all">
                <div class="sso-gradient p-4 text-white flex justify-between items-center">
                    <div class="flex items-center space-x-2">
                        <i class="fa-solid fa-shield-halved text-undip-gold"></i>
                        <h3 class="font-bold text-sm">Verifikasi Keamanan Anti-Bot (SSO Guard)</h3>
                    </div>
                    <button onclick="closeBotModal()" class="text-gray-300 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
                </div>
                
                <div class="p-6 space-y-5">
                    <div class="bg-blue-50 border border-blue-200 rounded-lg p-3 text-xs text-blue-900 flex items-start space-x-2">
                        <i class="fa-solid fa-circle-info text-undip-blue mt-0.5"></i>
                        <span>Untuk mencegah kecurangan dan penggunaan bot otomatis, selesaikan verifikasi sebelum tiket diterbitkan.</span>
                    </div>

                    <div class="border rounded-xl p-4 bg-gray-50 text-center space-y-3">
                        <p class="text-xs font-semibold text-gray-600">Selesaikan Soal Matematika Singkat:</p>
                        <div class="text-2xl font-extrabold text-undip-navy tracking-wider bg-white py-2 rounded border border-gray-300 shadow-inner" id="captcha-question">
                            8 + 5 = ?
                        </div>
                        <input type="number" id="captcha-answer" placeholder="Masukkan Jawaban" class="w-full text-center px-4 py-2 border rounded-lg focus:ring-2 focus:ring-undip-blue text-sm font-bold">
                    </div>

                    <div class="bg-gray-100 p-3 rounded-lg text-xs space-y-1">
                        <div class="flex justify-between">
                            <span class="text-gray-500">Menu Dipilih:</span>
                            <span id="modal-menu-title" class="font-bold text-gray-800">-</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-gray-500">NIM Pemesan:</span>
                            <span class="font-mono text-gray-700">24060121120001</span>
                        </div>
                    </div>

                    <div id="captcha-error" class="hidden text-xs text-red-600 bg-red-50 p-2 rounded text-center border border-red-200 font-semibold">
                        Jawaban salah! Silakan coba lagi.
                    </div>

                    <button onclick="processTicketClaim()" id="btn-confirm-claim" class="w-full bg-undip-gold hover:bg-undip-goldHover text-undip-navy font-bold py-3 px-4 rounded-xl shadow-lg transition flex items-center justify-center space-x-2">
                        <i class="fa-solid fa-ticket"></i>
                        <span>Konfirmasi & Ambil Tiket Antrean</span>
                    </button>
                </div>
            </div>
        </div>

        <!-- ================= TAB 2: TIKET SAYA & VIRTUAL QUEUE ================= -->
        <section id="tab-tiket" class="tab-content hidden space-y-6">
            <div id="no-ticket-state" class="bg-white rounded-2xl p-12 text-center border border-gray-200 shadow-sm max-w-lg mx-auto">
                <div class="w-16 h-16 bg-blue-50 text-undip-blue rounded-full flex items-center justify-center mx-auto text-2xl mb-4">
                    <i class="fa-solid fa-ticket-simple"></i>
                </div>
                <h3 class="text-lg font-bold text-gray-800">Belum Ada Tiket Aktif</h3>
                <p class="text-xs text-gray-500 mt-2 mb-6">Anda belum memesan tiket makanan gratis untuk hari ini. Silakan pilih menu di tab Menu Hari Ini.</p>
                <button onclick="switchTab('tab-menu')" class="bg-undip-blue text-white px-5 py-2.5 rounded-lg text-sm font-semibold hover:bg-undip-navy transition shadow">
                    Pilih Menu Makanan
                </button>
            </div>

            <!-- Ticket View Active -->
            <div id="active-ticket-state" class="hidden max-w-xl mx-auto">
                <div class="bg-white rounded-2xl shadow-xl overflow-hidden border border-gray-200 border-t-8 border-t-undip-gold">
                    <!-- Ticket Header -->
                    <div class="sso-gradient text-white p-6 relative">
                        <div class="flex justify-between items-start">
                            <div>
                                <span class="bg-emerald-500/20 border border-emerald-400 text-emerald-300 text-[10px] font-bold px-2 py-0.5 rounded uppercase tracking-wider">
                                    Tiket Aktif - Sah
                                </span>
                                <h3 class="text-xl font-extrabold mt-1 text-white">E-TIKET MEAL PASS UNDIP</h3>
                                <p class="text-xs text-blue-200">Dipersembahkan oleh Direktorat Kemahasiswaan Undip</p>
                            </div>
                            <div class="text-right">
                                <p class="text-[10px] text-blue-200">Nomor Antrean</p>
                                <p id="ticket-queue-no" class="text-3xl font-black text-undip-gold font-mono tracking-tight">A-142</p>
                            </div>
                        </div>
                    </div>

                    <!-- Ticket Details -->
                    <div class="p-6 space-y-6 ticket-pattern">
                        <div class="grid grid-cols-2 gap-4 bg-blue-50/80 p-4 rounded-xl border border-blue-100">
                            <div>
                                <p class="text-[10px] text-gray-500 font-semibold uppercase">Nama Mahasiswa</p>
                                <p class="text-sm font-bold text-gray-800">Budi Santoso</p>
                                <p class="text-[11px] text-gray-600">NIM: 24060121120001</p>
                            </div>
                            <div>
                                <p class="text-[10px] text-gray-500 font-semibold uppercase">Lokasi Pengambilan</p>
                                <p id="ticket-location" class="text-sm font-bold text-undip-blue">Kantin Student Center</p>
                                <p id="ticket-session-str" class="text-[11px] text-gray-600">Sesi 1 (11:30 - 12:30 WIB)</p>
                            </div>
                        </div>

                        <!-- Menu Item Chosen -->
                        <div class="flex items-center space-x-4 bg-white p-3 rounded-xl border shadow-sm">
                            <div id="ticket-menu-icon" class="w-12 h-12 bg-amber-100 text-amber-700 rounded-lg flex items-center justify-center text-xl font-bold">
                                <i class="fa-solid fa-bowl-food"></i>
                            </div>
                            <div class="flex-grow">
                                <p class="text-[10px] text-gray-400 font-semibold uppercase">Menu Pilihan Anda</p>
                                <p id="ticket-menu-name" class="text-base font-bold text-gray-800">Nasi Ayam Geprek Sambal Korek</p>
                                <p id="ticket-calories" class="text-xs text-emerald-600 font-medium"><i class="fa-solid fa-fire"></i> 580 kcal (Gizi Seimbang)</p>
                            </div>
                        </div>

                        <!-- Barcode Simulation -->
                        <div class="text-center pt-2 pb-4 bg-white rounded-xl border border-dashed border-gray-300 p-4">
                            <p class="text-xs text-gray-500 mb-2 font-medium">Tunjukkan QR Code / Barcode ini kepada Petugas Loket:</p>
                            <div class="bg-gray-900 text-white p-3 rounded-lg inline-block font-mono text-xs tracking-widest my-1 shadow">
                                <i class="fa-solid fa-qrcode text-5xl my-2 text-white block"></i>
                                <span id="ticket-code-str">UNDIP-MEAL-20261015-8839</span>
                            </div>
                            <p class="text-[10px] text-gray-400 mt-2">Kode QR berubah dinamis setiap 60 detik untuk keamanan</p>
                        </div>

                        <!-- Queue Status & Estimasi -->
                        <div class="bg-amber-50 border border-amber-200 p-4 rounded-xl flex items-center justify-between">
                            <div class="flex items-center space-x-3">
                                <i class="fa-solid fa-users text-amber-600 text-xl"></i>
                                <div>
                                    <p class="text-xs font-semibold text-amber-900">Estimasi Waktu Tunggu</p>
                                    <p class="text-xs text-amber-700">Ada <b id="queue-ahead-count">12 orang</b> di depan Anda saat ini</p>
                                </div>
                            </div>
                            <span class="text-xs font-bold bg-amber-200 text-amber-900 px-3 py-1 rounded-full">
                                ~ 8 Menit
                            </span>
                        </div>
                    </div>

                    <!-- Ticket Footer Action -->
                    <div class="bg-gray-50 p-4 border-t border-gray-200 flex justify-between items-center text-xs text-gray-500">
                        <span><i class="fa-solid fa-circle-check text-emerald-500"></i> Terverifikasi SSO Undip</span>
                        <button onclick="cancelTicket()" class="text-red-600 hover:text-red-800 font-semibold underline">Batalkan Tiket</button>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= TAB 3: RIWAYAT KLAIM ================= -->
        <section id="tab-history" class="tab-content hidden space-y-6">
            <div class="bg-white rounded-xl p-6 shadow-sm border border-gray-200">
                <div class="flex justify-between items-center mb-6">
                    <div>
                        <h3 class="text-lg font-bold text-gray-800">Riwayat Pengambilan Makanan</h3>
                        <p class="text-xs text-gray-500">Daftar klaim makanan gratis Anda dalam 30 hari terakhir</p>
                    </div>
                    <span class="text-xs bg-blue-50 text-undip-blue font-bold px-3 py-1 rounded-full border border-blue-200">
                        Total Diterima: 14 Porsi
                    </span>
                </div>

                <div class="overflow-x-auto">
                    <table class="w-full text-left text-xs text-gray-600">
                        <thead class="bg-gray-50 text-gray-700 font-semibold uppercase border-b">
                            <tr>
                                <th class="p-3">Tanggal & Sesi</th>
                                <th class="p-3">Menu Makanan</th>
                                <th class="p-3">Lokasi Kantin</th>
                                <th class="p-3">Kode Tiket</th>
                                <th class="p-3">Status</th>
                            </tr>
                        </thead>
                        <tbody id="history-table-body" class="divide-y">
                            <!-- Populated in JS -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- ================= TAB 4: PENILAIAN & VOTE MENU ================= -->
        <section id="tab-feedback" class="tab-content hidden space-y-6">
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Form Penilaian Makanan Hari Ini -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-200 space-y-4">
                    <div class="border-b pb-3">
                        <h3 class="text-base font-bold text-gray-800 flex items-center gap-2">
                            <i class="fa-solid fa-comment-dots text-undip-gold"></i> Penilaian & Feedback Makanan
                        </h3>
                        <p class="text-xs text-gray-500">Masukan Anda digunakan oleh Tim Gizi Undip untuk meningkatkan mutu layanan makanan.</p>
                    </div>

                    <form onsubmit="submitFeedback(event)" class="space-y-4">
                        <div>
                            <label class="block text-xs font-semibold text-gray-700 mb-1">Pilih Menu Yang Baru Dimakan:</label>
                            <select id="review-menu-select" class="w-full text-xs p-2.5 bg-gray-50 border rounded-lg focus:ring-undip-blue">
                                <option value="Nasi Ayam Geprek">Nasi Ayam Geprek Sambal Korek</option>
                                <option value="Nasi Rendang Sapi">Nasi Rendang Sapi & Sayur Kapit</option>
                                <option value="Soto Ayam Kudus">Soto Ayam Kudus & Perkedel</option>
                            </select>
                        </div>

                        <div>
                            <label class="block text-xs font-semibold text-gray-700 mb-1">Rating Cita Rasa & Porsi:</label>
                            <div class="flex space-x-2 text-2xl text-amber-400 cursor-pointer" id="rating-stars">
                                <i class="fa-solid fa-star" onclick="setRating(1)"></i>
                                <i class="fa-solid fa-star" onclick="setRating(2)"></i>
                                <i class="fa-solid fa-star" onclick="setRating(3)"></i>
                                <i class="fa-solid fa-star" onclick="setRating(4)"></i>
                                <i class="fa-regular fa-star" onclick="setRating(5)"></i>
                            </div>
                        </div>

                        <div>
                            <label class="block text-xs font-semibold text-gray-700 mb-1">Komentar / Saran / Apresiasi:</label>
                            <textarea id="review-text" rows="3" placeholder="Contoh: Ayamnya renyah dan gurih, sambalnya cukup pedas. Porsinya pas!" class="w-full text-xs p-2.5 border rounded-lg focus:ring-undip-blue" required></textarea>
                        </div>

                        <button type="submit" class="w-full bg-undip-blue text-white py-2.5 rounded-lg text-xs font-bold hover:bg-undip-navy transition shadow">
                            Kirim Ulasan Makanan
                        </button>
                    </form>
                </div>

                <!-- Voting Menu Hari Esok -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-200 space-y-4">
                    <div class="border-b pb-3">
                        <h3 class="text-base font-bold text-gray-800 flex items-center gap-2">
                            <i class="fa-solid fa-check-to-slot text-emerald-600"></i> Voting Menu Hari Besok
                        </h3>
                        <p class="text-xs text-gray-500">Pilih menu favoritmu! Menu suara terbanyak akan dimasak esok hari.</p>
                    </div>

                    <div id="voting-options" class="space-y-3">
                        <!-- Polling Items JS -->
                    </div>
                </div>
            </div>

            <!-- Feed Komentar Ulasan Mahasiswa -->
            <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-200 space-y-4">
                <h3 class="text-base font-bold text-gray-800">Apresiasi & Komentar Terbaru Mahasiswa</h3>
                <div id="reviews-feed" class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <!-- Feed Generated in JS -->
                </div>
            </div>
        </section>

        <!-- ================= TAB 5: LOKET PEMINDAIAN (ADMIN) ================= -->
        <section id="tab-admin" class="tab-content hidden space-y-6">
            <div class="bg-amber-50 border border-amber-200 rounded-xl p-4 text-xs text-amber-900 flex justify-between items-center">
                <div class="flex items-center space-x-2">
                    <i class="fa-solid fa-user-shield text-amber-600 text-base"></i>
                    <span><b>Mode Simulator Petugas Loket / Catering Kantin</b> (Hanya untuk keperluan pengujian sistem)</span>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Scan Input -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-200 space-y-4">
                    <h3 class="text-sm font-bold text-gray-800">Scan Barcode Tiket Mahasiswa</h3>
                    <div class="space-y-2">
                        <input type="text" id="admin-scan-input" placeholder="Masukkan Kode Tiket (mis: UNDIP-MEAL-...)" class="w-full text-xs p-2.5 border rounded-lg font-mono">
                        <button onclick="adminProcessScan()" class="w-full bg-emerald-600 text-white py-2.5 rounded-lg text-xs font-bold hover:bg-emerald-700 transition">
                            <i class="fa-solid fa-barcode"></i> Process Scan / Ambil Makanan
                        </button>
                    </div>

                    <div id="admin-scan-result" class="hidden p-3 rounded-lg text-xs border"></div>
                </div>

                <!-- Admin Analytics Board -->
                <div class="md:col-span-2 bg-white p-6 rounded-xl shadow-sm border border-gray-200 space-y-4">
                    <h3 class="text-sm font-bold text-gray-800">Dashboard Riset Kepuasan Menu</h3>
                    <div class="grid grid-cols-3 gap-3 text-center">
                        <div class="bg-blue-50 p-3 rounded-lg border border-blue-100">
                            <p class="text-[10px] text-gray-500">Menu Terfavorit</p>
                            <p class="text-xs font-extrabold text-undip-blue mt-1">Ayam Geprek (84%)</p>
                        </div>
                        <div class="bg-emerald-50 p-3 rounded-lg border border-emerald-100">
                            <p class="text-[10px] text-gray-500">Rata-rata Rating Gizi</p>
                            <p class="text-xs font-extrabold text-emerald-700 mt-1">4.8 / 5.0 ★</p>
                        </div>
                        <div class="bg-purple-50 p-3 rounded-lg border border-purple-100">
                            <p class="text-[10px] text-gray-500">Terlayani Hari Ini</p>
                            <p id="admin-served-count" class="text-xs font-extrabold text-purple-700 mt-1">1,158 Porsi</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer SSO Undip -->
    <footer class="bg-undip-navy text-white text-xs py-6 border-t-2 border-undip-gold mt-auto">
        <div class="max-w-7xl mx-auto px-4 text-center space-y-2">
            <p class="font-semibold">© 2026 Universitas Diponegoro (UNDIP) - Diponegoro Smart Campus System</p>
            <p class="text-gray-400">Direktorat Kemahasiswaan & Layanan TI SSO UNDIP Semarang, Jawa Tengah</p>
        </div>
    </footer>

    <script>
        // App State
        let selectedMenuForClaim = null;
        let activeTicket = null;
        let selectedRating = 4;
        let captchaAns = 0;

        // Sample Daily Menus
        const dailyMenus = [
            {
                id: 1,
                name: 'Nasi Ayam Geprek Sambal Korek',
                category: 'Tinggi Protein',
                calories: '580 kcal',
                ingredients: 'Nasi Putih, Daging Ayam Crispy, Sambal Korek, Tahu Tempe, Lalapan',
                stock: 145,
                maxStock: 200,
                rating: 4.8,
                imageIcon: 'fa-drumstick-bite',
                colorBg: 'bg-amber-500'
            },
            {
                id: 2,
                name: 'Nasi Rendang Sapi & Sayur Kapit',
                category: 'Gizi Komplit',
                calories: '620 kcal',
                ingredients: 'Nasi Putih, Daging Sapi Rendang, Sayur Nangka, Kerupuk udang',
                stock: 92,
                maxStock: 150,
                rating: 4.9,
                imageIcon: 'fa-bowl-rice',
                colorBg: 'bg-red-600'
            },
            {
                id: 3,
                name: 'Soto Ayam Kudus & Perkedel',
                category: 'Menu Hangat',
                calories: '490 kcal',
                ingredients: 'Nasi Soto Ayam Suwir, Tauge, Perkedel Kentang, Telur Rebus Setengah',
                stock: 105,
                maxStock: 150,
                rating: 4.7,
                imageIcon: 'fa-bowl-food',
                colorBg: 'bg-emerald-600'
            }
        ];

        // Claim History Mock
        const claimHistoryData = [
            { date: '14 Okt 2026', session: 'Sesi 1 (11.30)', menu: 'Nasi Ayam Penyet Sambal Ijo', canteen: 'Kantin Student Center', code: 'UNDIP-MEAL-9921', status: 'Selesai' },
            { date: '13 Okt 2026', session: 'Sesi 2 (12.30)', menu: 'Nasi Telur Bumbu Bali & Sayur', canteen: 'Kantin GSG Undip', code: 'UNDIP-MEAL-8812', status: 'Selesai' },
            { date: '10 Okt 2026', session: 'Sesi 1 (11.30)', menu: 'Nasi Rendang Sapi', canteen: 'Kantin Student Center', code: 'UNDIP-MEAL-7710', status: 'Kadaluarsa' }
        ];

        // Votes for Tomorrow
        let votingData = [
            { id: 1, menu: 'Nasi Ayam Bakar Madu', votes: 342, percentage: 45 },
            { id: 2, menu: 'Nasi Daging Sapi Yakiniku', votes: 280, percentage: 37 },
            { id: 3, menu: 'Ikan Asam Manis & Capcay', votes: 138, percentage: 18 }
        ];

        // Reviews Feed
        let reviewsFeedData = [
            { name: 'Siti Rahma (FSM)', menu: 'Nasi Ayam Geprek', rating: 5, comment: 'Porsinya sangat kenyang dan ayamnya hangat. Mantap UNDIP!', time: '10 menit lalu' },
            { name: 'Rizky Febrian (FH)', menu: 'Nasi Rendang Sapi', rating: 5, comment: 'Bumbunya meresap sekali. Semoga menu rendang sering ada!', time: '25 menit lalu' }
        ];

        window.onload = function() {
            renderMenus();
            renderHistoryTable();
            renderVotingOptions();
            renderReviewsFeed();
        };

        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.getElementById(tabId).classList.remove('hidden');

            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('bg-blue-50', 'text-undip-blue', 'border-b-2', 'border-undip-blue');
                btn.classList.add('text-gray-600');
            });

            const activeBtn = document.getElementById('btn-' + tabId);
            if(activeBtn) {
                activeBtn.classList.add('bg-blue-50', 'text-undip-blue', 'border-b-2', 'border-undip-blue');
                activeBtn.classList.remove('text-gray-600');
            }
        }

        function renderMenus() {
            const container = document.getElementById('menu-container');
            container.innerHTML = '';

            dailyMenus.forEach(item => {
                const percentage = Math.round((item.stock / item.maxStock) * 100);
                const isOutOfStock = item.stock <= 0;

                const cardHtml = `
                    <div class="bg-white rounded-2xl shadow-sm border border-gray-200 overflow-hidden flex flex-col justify-between hover:shadow-md transition">
                        <div>
                            <div class="${item.colorBg} p-6 text-white text-center relative">
                                <span class="absolute top-3 right-3 bg-black/30 backdrop-blur-sm text-white text-[10px] px-2 py-0.5 rounded-full font-semibold">
                                    ★ ${item.rating}
                                </span>
                                <i class="fa-solid ${item.imageIcon} text-5xl mb-2"></i>
                                <span class="bg-white/20 text-white text-[10px] font-bold px-2.5 py-0.5 rounded-full uppercase tracking-wide block w-max mx-auto">
                                    ${item.category}
                                </span>
                            </div>

                            <div class="p-5 space-y-3">
                                <h4 class="font-bold text-base text-gray-800 leading-snug">${item.name}</h4>
                                <p class="text-xs text-gray-500 leading-relaxed">${item.ingredients}</p>

                                <div class="flex items-center space-x-2 text-xs text-emerald-700 font-semibold bg-emerald-50 p-2 rounded-lg">
                                    <i class="fa-solid fa-leaf"></i>
                                    <span>Estimasi Nutrisi: ${item.calories}</span>
                                </div>

                                <div class="space-y-1 pt-2">
                                    <div class="flex justify-between text-xs font-semibold">
                                        <span class="text-gray-500">Tersedia:</span>
                                        <span class="${item.stock < 20 ? 'text-red-600 font-bold' : 'text-gray-800'}">${item.stock} / ${item.maxStock} Porsi</span>
                                    </div>
                                    <div class="w-full bg-gray-200 h-2 rounded-full overflow-hidden">
                                        <div class="bg-undip-blue h-full rounded-full" style="width: ${percentage}%"></div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="p-5 pt-0">
                            <button onclick="openBotVerification(${item.id})" ${isOutOfStock || activeTicket ? 'disabled' : ''} 
                                class="w-full ${activeTicket ? 'bg-gray-300 text-gray-600 cursor-not-allowed' : isOutOfStock ? 'bg-red-200 text-red-700 cursor-not-allowed' : 'bg-undip-gold hover:bg-undip-goldHover text-undip-navy'} font-bold py-2.5 px-4 rounded-xl shadow transition flex items-center justify-center space-x-2 text-xs">
                                <i class="fa-solid ${activeTicket ? 'fa-check' : 'fa-ticket'}"></i>
                                <span>${activeTicket ? 'Anda Sudah Memiliki Tiket' : isOutOfStock ? 'Stok Habis' : 'Klaim Tiket Makan'}</span>
                            </button>
                        </div>
                    </div>
                `;
                container.innerHTML += cardHtml;
            });
        }

        function openBotVerification(menuId) {
            if (activeTicket) return;

            selectedMenuForClaim = dailyMenus.find(m => m.id === menuId);
            document.getElementById('modal-menu-title').innerText = selectedMenuForClaim.name;

            // Generate Captcha
            const n1 = Math.floor(Math.random() * 10) + 1;
            const n2 = Math.floor(Math.random() * 10) + 1;
            captchaAns = n1 + n2;

            document.getElementById('captcha-question').innerText = `${n1} + ${n2} = ?`;
            document.getElementById('captcha-answer').value = '';
            document.getElementById('captcha-error').classList.add('hidden');

            document.getElementById('bot-modal').classList.remove('hidden');
        }

        function closeBotModal() {
            document.getElementById('bot-modal').classList.add('hidden');
        }

        function processTicketClaim() {
            const inputAns = parseInt(document.getElementById('captcha-answer').value);
            if (inputAns !== captchaAns) {
                document.getElementById('captcha-error').classList.remove('hidden');
                return;
            }

            // Reduce stock
            selectedMenuForClaim.stock -= 1;
            renderMenus();

            // Create Active Ticket
            const sessionSelect = document.getElementById('session-select');
            const sessionText = sessionSelect.options[sessionSelect.selectedIndex].text;

            activeTicket = {
                queueNo: 'A-' + (Math.floor(Math.random() * 80) + 100),
                menuName: selectedMenuForClaim.name,
                calories: selectedMenuForClaim.calories,
                sessionStr: sessionText,
                ticketCode: 'UNDIP-MEAL-20261015-' + Math.floor(1000 + Math.random() * 9000),
                location: 'Kantin Student Center'
            };

            closeBotModal();
            updateTicketUI();
            switchTab('tab-tiket');
        }

        function updateTicketUI() {
            if (activeTicket) {
                document.getElementById('no-ticket-state').classList.add('hidden');
                document.getElementById('active-ticket-state').classList.remove('hidden');

                document.getElementById('ticket-queue-no').innerText = activeTicket.queueNo;
                document.getElementById('ticket-menu-name').innerText = activeTicket.menuName;
                document.getElementById('ticket-calories').innerHTML = `<i class="fa-solid fa-fire"></i> ${activeTicket.calories} (Gizi Seimbang)`;
                document.getElementById('ticket-session-str').innerText = activeTicket.sessionStr;
                document.getElementById('ticket-code-str').innerText = activeTicket.ticketCode;

                document.getElementById('ticket-badge').classList.remove('hidden');
            } else {
                document.getElementById('no-ticket-state').classList.remove('hidden');
                document.getElementById('active-ticket-state').classList.add('hidden');
                document.getElementById('ticket-badge').classList.add('hidden');
            }
        }

        function cancelTicket() {
            if (confirm("Apakah Anda yakin ingin membatalkan tiket ini? Stok akan dikembalikan ke pengguna lain.")) {
                if (selectedMenuForClaim) {
                    selectedMenuForClaim.stock += 1;
                    renderMenus();
                }
                activeTicket = null;
                updateTicketUI();
            }
        }

        function renderHistoryTable() {
            const tbody = document.getElementById('history-table-body');
            tbody.innerHTML = '';

            claimHistoryData.forEach(item => {
                const tr = `
                    <tr class="hover:bg-gray-50">
                        <td class="p-3 font-medium text-gray-800">${item.date}<br><span class="text-[10px] text-gray-400">${item.session}</span></td>
                        <td class="p-3 font-semibold text-undip-blue">${item.menu}</td>
                        <td class="p-3">${item.canteen}</td>
                        <td class="p-3 font-mono text-[11px]">${item.code}</td>
                        <td class="p-3">
                            <span class="px-2 py-0.5 rounded text-[10px] font-bold ${item.status === 'Selesai' ? 'bg-emerald-100 text-emerald-800' : 'bg-red-100 text-red-800'}">
                                ${item.status}
                            </span>
                        </td>
                    </tr>
                `;
                tbody.innerHTML += tr;
            });
        }

        function setRating(r) {
            selectedRating = r;
            const stars = document.getElementById('rating-stars').children;
            for(let i=0; i<5; i++) {
                if(i < r) {
                    stars[i].className = 'fa-solid fa-star';
                } else {
                    stars[i].className = 'fa-regular fa-star';
                }
            }
        }

        function submitFeedback(e) {
            e.preventDefault();
            const menuName = document.getElementById('review-menu-select').value;
            const comment = document.getElementById('review-text').value;

            reviewsFeedData.unshift({
                name: 'Budi Santoso (FTIK)',
                menu: menuName,
                rating: selectedRating,
                comment: comment,
                time: 'Baru saja'
            });

            document.getElementById('review-text').value = '';
            renderReviewsFeed();
            alert("Terima kasih! Ulasan makanan Anda telah direkam.");
        }

        function renderVotingOptions() {
            const container = document.getElementById('voting-options');
            container.innerHTML = '';

            votingData.forEach(item => {
                const html = `
                    <div class="border rounded-lg p-3 bg-gray-50 hover:bg-gray-100 cursor-pointer transition" onclick="castVote(${item.id})">
                        <div class="flex justify-between items-center text-xs font-bold text-gray-800 mb-1">
                            <span>${item.menu}</span>
                            <span class="text-undip-blue">${item.votes} Suara (${item.percentage}%)</span>
                        </div>
                        <div class="w-full bg-gray-200 h-2 rounded-full overflow-hidden">
                            <div class="bg-emerald-500 h-full rounded-full" style="width: ${item.percentage}%"></div>
                        </div>
                    </div>
                `;
                container.innerHTML += html;
            });
        }

        function castVote(id) {
            votingData = votingData.map(item => {
                if(item.id === id) {
                    return { ...item, votes: item.votes + 1 };
                }
                return item;
            });

            const totalVotes = votingData.reduce((acc, curr) => acc + curr.votes, 0);
            votingData.forEach(item => {
                item.percentage = Math.round((item.votes / totalVotes) * 100);
            });

            renderVotingOptions();
        }

        function renderReviewsFeed() {
            const container = document.getElementById('reviews-feed');
            container.innerHTML = '';

            reviewsFeedData.forEach(item => {
                let starHtml = '';
                for(let i=0; i<item.rating; i++) starHtml += '<i class="fa-solid fa-star text-amber-400"></i>';

                const html = `
                    <div class="p-3 bg-gray-50 rounded-xl border border-gray-200 text-xs space-y-1">
                        <div class="flex justify-between items-center">
                            <span class="font-bold text-gray-800">${item.name}</span>
                            <span class="text-[10px] text-gray-400">${item.time}</span>
                        </div>
                        <p class="text-[11px] font-semibold text-undip-blue">${item.menu}</p>
                        <div class="text-[10px] space-x-0.5">${starHtml}</div>
                        <p class="text-gray-600 italic">"${item.comment}"</p>
                    </div>
                `;
                container.innerHTML += html;
            });
        }

        function adminProcessScan() {
            const val = document.getElementById('admin-scan-input').value.trim();
            const res = document.getElementById('admin-scan-result');
            res.classList.remove('hidden');

            if(val === '' || (activeTicket && val === activeTicket.ticketCode)) {
                res.className = 'p-3 rounded-lg text-xs border bg-emerald-50 border-emerald-300 text-emerald-900';
                res.innerHTML = '<b><i class="fa-solid fa-circle-check"></i> VOKASI BERHASIL!</b> Makanan diserahkan ke Budi Santoso (NIM: 24060121120001). Tiket hangus.';
                
                if (activeTicket) {
                    claimHistoryData.unshift({
                        date: 'Hari Ini',
                        session: 'Sesi 1 (11.30)',
                        menu: activeTicket.menuName,
                        canteen: 'Kantin Student Center',
                        code: activeTicket.ticketCode,
                        status: 'Selesai'
                    });
                    renderHistoryTable();
                    activeTicket = null;
                    updateTicketUI();
                }
            } else {
                res.className = 'p-3 rounded-lg text-xs border bg-red-50 border-red-300 text-red-900';
                res.innerHTML = '<b><i class="fa-solid fa-circle-xmark"></i> TIKET TIDAK VALID</b> atau sudah pernah ditukarkan.';
            }
        }

        function updateSessionInfo() {
            // Simulated session change logic
        }
    </script>
</body>
</html>
