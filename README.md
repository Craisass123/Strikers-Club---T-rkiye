<!DOCTYPE html>
<html lang="tr" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Strikers Club Türkiye Ligi - Resmi Web Portalı</title>

    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        turkred: {
                            DEFAULT: '#e30613',
                            hover: '#c2040f',
                            dark: '#800000',
                            glow: 'rgba(227, 6, 19, 0.4)'
                        },
                        league: {
                            gold: '#f59e0b',
                            darkBg: '#090d16',
                            cardBg: '#111827',
                            border: '#1f2937'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <!-- Fonts & Icons -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #090d16;
            color: #f3f4f6;
        }
        .glow-red {
            box-shadow: 0 0 25px -5px rgba(227, 6, 19, 0.4);
        }
        .glow-gold {
            box-shadow: 0 0 25px -5px rgba(245, 158, 11, 0.3);
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #090d16;
        }
        ::-webkit-scrollbar-thumb {
            background: #1f2937;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #e30613;
        }
    </style>
</head>
<body class="bg-league-darkBg text-gray-100 min-h-screen flex flex-col justify-between selection:bg-turkred selection:text-white">

    <header class="sticky top-0 z-40 bg-league-darkBg/95 backdrop-blur-md border-b border-gray-800/80">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <!-- Logo -->
                <div class="flex items-center space-x-3 cursor-pointer" onclick="switchTab('dashboard')">
                    <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-turkred to-league-gold p-0.5 shadow-lg shadow-turkred/20">
                        <div class="w-full h-full bg-league-darkBg rounded-[10px] flex items-center justify-center">
                            <i class="fa-solid fa-trophy text-xl text-league-gold"></i>
                        </div>
                    </div>
                    <div>
                        <span class="text-xl sm:text-2xl font-black tracking-wider bg-gradient-to-r from-white via-gray-200 to-amber-400 bg-clip-text text-transparent">
                            STRIKERS CLUB
                        </span>
                        <span class="block text-xs font-bold tracking-widest text-turkred uppercase">Türkiye Ligi</span>
                    </div>
                </div>

                <!-- Desktop Navigation Menu -->
                <nav class="hidden md:flex items-center space-x-1 lg:space-x-2">
                    <button onclick="switchTab('dashboard')" id="nav-dashboard" class="nav-btn px-4 py-2 rounded-xl font-medium text-sm transition-all text-turkred bg-league-cardBg border border-turkred/40 shadow-sm">
                        <i class="fa-solid fa-chart-line mr-2"></i>Genel Bakış
                    </button>
                    <button onclick="switchTab('standings')" id="nav-standings" class="nav-btn px-4 py-2 rounded-xl font-medium text-sm text-gray-400 hover:text-white hover:bg-gray-800/80 transition-all">
                        <i class="fa-solid fa-list-ol mr-2"></i>Puan Durumu
                    </button>
                    <button onclick="switchTab('fixtures')" id="nav-fixtures" class="nav-btn px-4 py-2 rounded-xl font-medium text-sm text-gray-400 hover:text-white hover:bg-gray-800/80 transition-all">
                        <i class="fa-solid fa-calendar-days mr-2"></i>Fikstür & Sonuçlar
                    </button>
                    <button onclick="switchTab('stats')" id="nav-stats" class="nav-btn px-4 py-2 rounded-xl font-medium text-sm text-gray-400 hover:text-white hover:bg-gray-800/80 transition-all">
                        <i class="fa-solid fa-fire mr-2"></i>İstatistikler
                    </button>
                    <button onclick="switchTab('teams')" id="nav-teams" class="nav-btn px-4 py-2 rounded-xl font-medium text-sm text-gray-400 hover:text-white hover:bg-gray-800/80 transition-all">
                        <i class="fa-solid fa-shield-halved mr-2"></i>Takımlar
                    </button>
                    <button onclick="switchTab('news')" id="nav-news" class="nav-btn px-4 py-2 rounded-xl font-medium text-sm text-gray-400 hover:text-white hover:bg-gray-800/80 transition-all">
                        <i class="fa-solid fa-newspaper mr-2"></i>Haberler
                    </button>
                </nav>

                <!-- Admin & Mobile Toggle -->
                <div class="flex items-center space-x-3">
                    <button onclick="switchTab('admin')" id="nav-admin" class="flex items-center space-x-2 bg-gradient-to-r from-turkred to-amber-600 hover:from-red-700 hover:to-amber-700 text-white font-extrabold px-4 py-2 rounded-xl text-sm transition-all shadow-lg shadow-turkred/30">
                        <i class="fa-solid fa-sliders"></i>
                        <span class="hidden sm:inline">Lig Yönetimi</span>
                    </button>

                    <!-- Mobile Menu Button -->
                    <button id="mobile-menu-btn" onclick="toggleMobileMenu()" class="md:hidden text-gray-400 hover:text-white p-2 text-xl focus:outline-none">
                        <i class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <div id="mobile-menu" class="hidden md:hidden bg-league-cardBg border-b border-gray-800 px-4 pt-2 pb-4 space-y-1">
            <button onclick="switchTab('dashboard')" class="block w-full text-left px-3 py-2 rounded-lg font-medium text-gray-300 hover:bg-gray-800 hover:text-white"><i class="fa-solid fa-chart-line w-6"></i>Genel Bakış</button>
            <button onclick="switchTab('standings')" class="block w-full text-left px-3 py-2 rounded-lg font-medium text-gray-300 hover:bg-gray-800 hover:text-white"><i class="fa-solid fa-list-ol w-6"></i>Puan Durumu</button>
            <button onclick="switchTab('fixtures')" class="block w-full text-left px-3 py-2 rounded-lg font-medium text-gray-300 hover:bg-gray-800 hover:text-white"><i class="fa-solid fa-calendar-days w-6"></i>Fikstür & Sonuçlar</button>
            <button onclick="switchTab('stats')" class="block w-full text-left px-3 py-2 rounded-lg font-medium text-gray-300 hover:bg-gray-800 hover:text-white"><i class="fa-solid fa-fire w-6"></i>İstatistikler</button>
            <button onclick="switchTab('teams')" class="block w-full text-left px-3 py-2 rounded-lg font-medium text-gray-300 hover:bg-gray-800 hover:text-white"><i class="fa-solid fa-shield-halved w-6"></i>Takımlar</button>
            <button onclick="switchTab('news')" class="block w-full text-left px-3 py-2 rounded-lg font-medium text-gray-300 hover:bg-gray-800 hover:text-white"><i class="fa-solid fa-newspaper w-6"></i>Haberler</button>
        </div>
    </header>

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 flex-grow w-full">

        <!-- TAB 1: DASHBOARD (Genel Bakış) -->
        <section id="tab-dashboard" class="space-y-8">
            <!-- Hero Banner -->
            <div class="relative overflow-hidden rounded-2xl bg-gradient-to-r from-gray-950 via-league-darkBg to-red-950 border border-gray-800 p-6 sm:p-10 shadow-2xl">
                <div class="absolute -right-10 -bottom-10 opacity-10 text-turkred pointer-events-none">
                    <i class="fa-solid fa-trophy text-[250px]"></i>
                </div>
                <div class="relative z-10 max-w-2xl">
                    <span class="inline-block bg-turkred/20 text-turkred border border-turkred/40 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider mb-4">
                        2026 Resmî Sezon
                    </span>
                    <h1 class="text-3xl sm:text-5xl font-black text-white tracking-tight mb-4 leading-tight">
                        STRIKERS CLUB TÜRKİYE LİGİ
                    </h1>
                    <p class="text-gray-400 text-sm sm:text-base mb-6 leading-relaxed">
                        Heyecanın tavan yaptığı resmi turnuva merkezine hoş geldiniz. Skor güncellemelerini anlık takip edin, canlı puan durumunu inceleyin ve krallık yarışına göz atın!
                    </p>
                    <div class="flex flex-wrap gap-3">
                        <button onclick="switchTab('standings')" class="bg-turkred hover:bg-turkred-hover text-white font-extrabold px-6 py-3 rounded-xl transition-all shadow-lg shadow-turkred/30 flex items-center space-x-2">
                            <span>Puan Durumu Tablosu</span>
                            <i class="fa-solid fa-arrow-right"></i>
                        </button>
                        <button onclick="switchTab('fixtures')" class="bg-gray-800 hover:bg-gray-700 text-white font-bold px-6 py-3 rounded-xl border border-gray-700 transition-all">
                            Son Maç Sonuçları
                        </button>
                    </div>
                </div>
            </div>

            <!-- Dashboard Highlights Grid -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <!-- Mini Standings -->
                <div class="bg-league-cardBg rounded-2xl border border-gray-800 p-6 shadow-xl">
                    <div class="flex items-center justify-between mb-4">
                        <h2 class="font-bold text-lg text-white flex items-center">
                            <i class="fa-solid fa-ranking-star text-league-gold mr-2"></i> Liderlik Tablosu
                        </h2>
                        <button onclick="switchTab('standings')" class="text-xs text-turkred hover:underline font-semibold">Tümünü Gör</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="w-full text-sm text-left">
                            <thead class="text-xs text-gray-500 border-b border-gray-800 uppercase">
                                <tr>
                                    <th class="pb-2">#</th>
                                    <th class="pb-2">Takım</th>
                                    <th class="pb-2 text-center">O</th>
                                    <th class="pb-2 text-center">AV</th>
                                    <th class="pb-2 text-right">P</th>
                                </tr>
                            </thead>
                            <tbody id="dash-mini-standings" class="divide-y divide-gray-800/60 font-medium">
                                <!-- JS Populated -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Recent Match Results -->
                <div class="bg-league-cardBg rounded-2xl border border-gray-800 p-6 shadow-xl">
                    <div class="flex items-center justify-between mb-4">
                        <h2 class="font-bold text-lg text-white flex items-center">
                            <i class="fa-solid fa-stopwatch text-sky-400 mr-2"></i> Son Sonuçlar
                        </h2>
                        <button onclick="switchTab('fixtures')" class="text-xs text-sky-400 hover:underline font-semibold">Tüm Fikstür</button>
                    </div>
                    <div id="dash-recent-matches" class="space-y-3">
                        <!-- JS Populated -->
                    </div>
                </div>

                <!-- Top Goal Scorers Summary -->
                <div class="bg-league-cardBg rounded-2xl border border-gray-800 p-6 shadow-xl">
                    <div class="flex items-center justify-between mb-4">
                        <h2 class="font-bold text-lg text-white flex items-center">
                            <i class="fa-solid fa-fire text-amber-500 mr-2"></i> Gol Krallığı Top 3
                        </h2>
                        <button onclick="switchTab('stats')" class="text-xs text-amber-500 hover:underline font-semibold">Tüm Krallıklar</button>
                    </div>
                    <div id="dash-top-scorers" class="space-y-3">
                        <!-- JS Populated -->
                    </div>
                </div>
            </div>
        </section>

        <section id="tab-standings" class="space-y-6 hidden">
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 bg-league-cardBg p-6 rounded-2xl border border-gray-800">
                <div>
                    <h2 class="text-2xl font-black text-white flex items-center">
                        <i class="fa-solid fa-list-ol text-turkred mr-3"></i> Resmî Puan Durumu
                    </h2>
                    <p class="text-sm text-gray-400 mt-1">Strikers Club Türkiye Ligi Canlı Tablosu</p>
                </div>
                <!-- Legend Zone Badges -->
                <div class="flex flex-wrap items-center gap-3 text-xs font-semibold">
                    <span class="flex items-center"><span class="w-3 h-3 rounded-full bg-emerald-500 mr-1.5"></span> Şampiyonlar Ligi</span>
                    <span class="flex items-center"><span class="w-3 h-3 rounded-full bg-sky-500 mr-1.5"></span> Avrupa Ligi</span>
                    <span class="flex items-center"><span class="w-3 h-3 rounded-full bg-red-600 mr-1.5"></span> Düşme Hattı</span>
                </div>
            </div>

            <div class="bg-league-cardBg rounded-2xl border border-gray-800 overflow-hidden shadow-2xl">
                <div class="overflow-x-auto">
                    <table class="w-full text-sm text-left text-gray-300">
                        <thead class="text-xs text-gray-400 uppercase bg-gray-900/90 border-b border-gray-800">
                            <tr>
                                <th scope="col" class="px-4 py-4 text-center">Sıra</th>
                                <th scope="col" class="px-6 py-4">Takım</th>
                                <th scope="col" class="px-3 py-4 text-center">O</th>
                                <th scope="col" class="px-3 py-4 text-center">G</th>
                                <th scope="col" class="px-3 py-4 text-center">B</th>
                                <th scope="col" class="px-3 py-4 text-center">M</th>
                                <th scope="col" class="px-3 py-4 text-center">AG</th>
                                <th scope="col" class="px-3 py-4 text-center">YG</th>
                                <th scope="col" class="px-3 py-4 text-center">AV</th>
                                <th scope="col" class="px-4 py-4 text-center text-white font-extrabold bg-gray-800/80">Puan</th>
                            </tr>
                        </thead>
                        <tbody id="full-standings-body" class="divide-y divide-gray-800/60 font-medium">
                            <!-- JS Populated -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <section id="tab-fixtures" class="space-y-6 hidden">
            <div class="bg-league-cardBg p-6 rounded-2xl border border-gray-800 flex flex-col sm:flex-row justify-between items-center gap-4">
                <div>
                    <h2 class="text-2xl font-black text-white flex items-center">
                        <i class="fa-solid fa-calendar-check text-sky-400 mr-3"></i> Fikstür ve Sonuçlar
                    </h2>
                    <p class="text-sm text-gray-400 mt-1">Haftalık maç takvimi ve skor takibi</p>
                </div>
                
                <!-- Week Switcher -->
                <div class="flex items-center space-x-2 bg-gray-900 p-1.5 rounded-xl border border-gray-800">
                    <button onclick="changeWeek(-1)" class="w-9 h-9 rounded-lg bg-gray-800 hover:bg-gray-700 text-white flex items-center justify-center transition-all">
                        <i class="fa-solid fa-chevron-left text-xs"></i>
                    </button>
                    <select id="week-select" onchange="selectWeek(this.value)" class="bg-transparent text-white font-bold text-sm px-3 focus:outline-none cursor-pointer">
                        <!-- JS Populated Weeks -->
                    </select>
                    <button onclick="changeWeek(1)" class="w-9 h-9 rounded-lg bg-gray-800 hover:bg-gray-700 text-white flex items-center justify-center transition-all">
                        <i class="fa-solid fa-chevron-right text-xs"></i>
                    </button>
                </div>
            </div>

            <!-- Matches List Container -->
            <div id="fixtures-container" class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <!-- JS Populated -->
            </div>
        </section>

        <section id="tab-stats" class="space-y-6 hidden">
            <div class="bg-league-cardBg p-6 rounded-2xl border border-gray-800">
                <h2 class="text-2xl font-black text-white flex items-center">
                    <i class="fa-solid fa-trophy text-amber-500 mr-3"></i> Lig İstatistikleri
                </h2>
                <p class="text-sm text-gray-400 mt-1">Strikers Club Türkiye Ligi Gol ve Asist Krallığı</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <!-- Gol Krallığı -->
                <div class="bg-league-cardBg rounded-2xl border border-gray-800 overflow-hidden shadow-xl">
                    <div class="bg-gradient-to-r from-amber-950/50 to-league-cardBg p-4 border-b border-gray-800 flex items-center justify-between">
                        <h3 class="font-extrabold text-lg text-amber-400 flex items-center">
                            <i class="fa-solid fa-futbol mr-2"></i> Gol Krallığı
                        </h3>
                        <span class="text-xs bg-amber-500/20 text-amber-300 font-bold px-2.5 py-1 rounded-full">En İyiler</span>
                    </div>
                    <div class="p-2">
                        <table class="w-full text-sm text-left">
                            <thead class="text-xs text-gray-500 uppercase border-b border-gray-800">
                                <tr>
                                    <th class="p-3 text-center">#</th>
                                    <th class="p-3">Oyuncu</th>
                                    <th class="p-3">Takım</th>
                                    <th class="p-3 text-right">Gol</th>
                                </tr>
                            </thead>
                            <tbody id="top-goals-body" class="divide-y divide-gray-800/50">
                                <!-- JS Populated -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Asist Krallığı -->
                <div class="bg-league-cardBg rounded-2xl border border-gray-800 overflow-hidden shadow-xl">
                    <div class="bg-gradient-to-r from-sky-950/50 to-league-cardBg p-4 border-b border-gray-800 flex items-center justify-between">
                        <h3 class="font-extrabold text-lg text-sky-400 flex items-center">
                            <i class="fa-solid fa-handshake mr-2"></i> Asist Krallığı
                        </h3>
                        <span class="text-xs bg-sky-500/20 text-sky-300 font-bold px-2.5 py-1 rounded-full">En İyiler</span>
                    </div>
                    <div class="p-2">
                        <table class="w-full text-sm text-left">
                            <thead class="text-xs text-gray-500 uppercase border-b border-gray-800">
                                <tr>
                                    <th class="p-3 text-center">#</th>
                                    <th class="p-3">Oyuncu</th>
                                    <th class="p-3">Takım</th>
                                    <th class="p-3 text-right">Asist</th>
                                </tr>
                            </thead>
                            <tbody id="top-assists-body" class="divide-y divide-gray-800/50">
                                <!-- JS Populated -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </section>

        <section id="tab-teams" class="space-y-6 hidden">
            <div class="bg-league-cardBg p-6 rounded-2xl border border-gray-800">
                <h2 class="text-2xl font-black text-white flex items-center">
                    <i class="fa-solid fa-shield-halved text-turkred mr-3"></i> Lig Takımları ve Kadrolar
                </h2>
                <p class="text-sm text-gray-400 mt-1">Takım detaylarını inceleyin, oyuncu kadrolarını görün</p>
            </div>

            <div id="teams-grid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
                <!-- JS Populated Teams -->
            </div>
        </section>

        <section id="tab-news" class="space-y-6 hidden">
            <div class="bg-league-cardBg p-6 rounded-2xl border border-gray-800">
                <h2 class="text-2xl font-black text-white flex items-center">
                    <i class="fa-solid fa-newspaper text-sky-400 mr-3"></i> Haberler & Duyurular
                </h2>
                <p class="text-sm text-gray-400 mt-1">Strikers Club liginden en son duyurular ve haberler</p>
            </div>

            <div id="news-container" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- JS Populated News -->
            </div>
        </section>

        <section id="tab-admin" class="space-y-8 hidden">
            <!-- Header Banner -->
            <div class="bg-gradient-to-r from-red-950 via-gray-900 to-league-cardBg p-6 sm:p-8 rounded-2xl border border-red-900/50 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                <div>
                    <span class="bg-turkred/20 text-turkred border border-turkred/30 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider">0 TL Ücretsiz Lig Yönetimi</span>
                    <h2 class="text-3xl font-black text-white mt-2 flex items-center">
                        <i class="fa-solid fa-sliders text-turkred mr-3"></i> Lig Yönetim Paneli
                    </h2>
                    <p class="text-sm text-gray-400 mt-1">
                        Maç skorlarını girin, takımları/oyuncuları yönetin, yeni haberler ekleyin. Tüm değişiklikler anında kaydedilir.
                    </p>
                </div>
                <button onclick="resetLeagueData()" class="bg-red-900/40 hover:bg-red-800 text-red-200 border border-red-700 px-4 py-2.5 rounded-xl font-bold text-xs transition-all flex items-center">
                    <i class="fa-solid fa-rotate-left mr-2"></i> Verileri Sıfırla / Örnek Veri Yükle
                </button>
            </div>

            <!-- Admin Action Grid -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <!-- Left Panel: Score Entry -->
                <div class="lg:col-span-2 bg-league-cardBg rounded-2xl border border-gray-800 p-6 space-y-6 shadow-xl">
                    <h3 class="font-bold text-lg text-white border-b border-gray-800 pb-3 flex items-center">
                        <i class="fa-solid fa-pen-to-square text-turkred mr-2"></i> Maç Skoru Gir & Puan Durumunu Güncelle
                    </h3>

                    <form id="admin-score-form" onsubmit="handleScoreSubmit(event)" class="space-y-4">
                        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                            <div>
                                <label class="block text-xs font-bold text-gray-400 uppercase mb-2">Hafta Seç</label>
                                <select id="admin-week-select" onchange="loadAdminMatches(this.value)" class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:border-turkred focus:outline-none">
                                    <!-- JS Populated -->
                                </select>
                            </div>
                            <div class="sm:col-span-2">
                                <label class="block text-xs font-bold text-gray-400 uppercase mb-2">Maç Seç</label>
                                <select id="admin-match-select" onchange="populateAdminMatchDetails()" class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:border-turkred focus:outline-none">
                                    <!-- JS Populated -->
                                </select>
                            </div>
                        </div>

                        <div id="admin-score-inputs" class="p-4 bg-gray-900/90 rounded-xl border border-gray-800 grid grid-cols-5 gap-2 items-center text-center">
                            <div class="col-span-2 text-right font-bold text-gray-200 text-sm sm:text-base" id="admin-home-name">Ev Sahibi</div>
                            <div class="flex items-center justify-center space-x-2">
                                <input type="number" id="admin-home-score" min="0" max="99" class="w-12 h-12 text-center bg-gray-800 border border-gray-700 rounded-xl text-xl font-black text-turkred focus:outline-none focus:border-turkred">
                                <span class="text-gray-500 font-bold">-</span>
                                <input type="number" id="admin-away-score" min="0" max="99" class="w-12 h-12 text-center bg-gray-800 border border-gray-700 rounded-xl text-xl font-black text-turkred focus:outline-none focus:border-turkred">
                            </div>
                            <div class="col-span-2 text-left font-bold text-gray-200 text-sm sm:text-base" id="admin-away-name">Deplasman</div>
                        </div>

                        <button type="submit" class="w-full bg-turkred hover:bg-turkred-hover text-white font-black py-3 rounded-xl transition-all shadow-lg shadow-turkred/30">
                            Skoru Kaydet ve Tabloyu Otomatik Hesapla
                        </button>
                    </form>
                </div>

                <!-- Right Panel: News Creation & Quick Stats Modifiers -->
                <div class="space-y-6">
                    <!-- Add News Form -->
                    <div class="bg-league-cardBg rounded-2xl border border-gray-800 p-6 space-y-4 shadow-xl">
                        <h3 class="font-bold text-lg text-white border-b border-gray-800 pb-3 flex items-center">
                            <i class="fa-solid fa-bullhorn text-sky-400 mr-2"></i> Yeni Duyuru / Haber Ekle
                        </h3>
                        <form onsubmit="handleAddNews(event)" class="space-y-3">
                            <div>
                                <label class="block text-xs font-bold text-gray-400 mb-1">Başlık</label>
                                <input type="text" id="news-title" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-2.5 text-sm text-white focus:border-sky-400 focus:outline-none" placeholder="Haber Başlığı">
                            </div>
                            <div>
                                <label class="block text-xs font-bold text-gray-400 mb-1">Kategori</label>
                                <select id="news-category" class="w-full bg-gray-900 border border-gray-700 rounded-xl p-2.5 text-sm text-white focus:outline-none">
                                    <option value="Duyuru">Duyuru</option>
                                    <option value="Maç Özeti">Maç Özeti</option>
                                    <option value="Transfer">Transfer</option>
                                    <option value="Haftanın Panoraması">Haftanın Panoraması</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-xs font-bold text-gray-400 mb-1">Detay</label>
                                <textarea id="news-content" rows="3" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-2.5 text-sm text-white focus:border-sky-400 focus:outline-none" placeholder="Haber açıklaması..."></textarea>
                            </div>
                            <button type="submit" class="w-full bg-sky-500 hover:bg-sky-400 text-black font-extrabold py-2.5 rounded-xl transition-all">
                                Haberi Yayınla
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-league-cardBg border-t border-gray-800 mt-16 py-8">
        <div class="max-w-7xl mx-auto px-4 text-center sm:flex sm:justify-between sm:items-center">
            <div class="flex items-center justify-center sm:justify-start space-x-2 mb-4 sm:mb-0">
                <i class="fa-solid fa-trophy text-league-gold text-xl"></i>
                <span class="font-extrabold text-white tracking-wider">STRIKERS CLUB TÜRKİYE LİGİ</span>
            </div>
            <p class="text-xs text-gray-500">
                &copy; 2026 Strikers Club Türkiye Ligi. %100 Ücretsiz Yönetim Portalı.
            </p>
        </div>
    </footer>

    <div id="team-modal" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="bg-league-cardBg border border-gray-800 rounded-2xl w-full max-w-2xl overflow-hidden shadow-2xl">
            <div class="p-6 border-b border-gray-800 flex justify-between items-center bg-gray-900/80">
                <div class="flex items-center space-x-4">
                    <div id="modal-team-icon" class="w-12 h-12 rounded-xl bg-gray-800 flex items-center justify-center text-2xl">🛡️</div>
                    <div>
                        <h3 id="modal-team-name" class="text-2xl font-black text-white">Takım Adı</h3>
                        <p id="modal-team-stadium" class="text-xs text-gray-400">Stadyum Bilgisi</p>
                    </div>
                </div>
                <button onclick="closeTeamModal()" class="text-gray-400 hover:text-white p-2 text-xl">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>
            <div class="p-6 space-y-6 max-h-[70vh] overflow-y-auto">
                <div>
                    <h4 class="text-xs font-bold uppercase tracking-wider text-turkred mb-3">Oyuncu Kadrosu</h4>
                    <div id="modal-team-roster" class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                        <!-- JS Populated Roster -->
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Initial Sample League Data Structure
        const DEFAULT_LEAGUE_DATA = {
            teams: [
                { id: "1", name: "İstanbul Strikers", short: "IST", icon: "🦁", stadium: "Strikers Park Arena", squad: ["Ali Yılmaz (GK)", "Mehmet Kaya (DEF)", "Caner Erkin (DEF)", "Ozan Tufan (MID)", "Hakan Çalhanoğlu (MID)", "Burak Yılmaz (FW)"] },
                { id: "2", name: "Ankara Gücü SC", short: "ANK", icon: "🦅", stadium: "Başkent Stadyumu", squad: ["Volkan Demirel (GK)", "Ahmet Yılmaz (DEF)", "Kaan Ayhan (DEF)", "İrfan Can (MID)", "Cengiz Ünder (FW)", "Enes Ünal (FW)"] },
                { id: "3", name: "İzmir Birlik", short: "IZM", icon: "⚓", stadium: "Ege Şehir Parkı", squad: ["Mert Günok (GK)", "Zeki Çelik (DEF)", "Merih Demiral (DEF)", "Orkun Kökçü (MID)", "Kerem Aktürkoğlu (FW)", "Cenk Tosun (FW)"] },
                { id: "4", name: "Bursa Şimşekler", short: "BUR", icon: "⚡", stadium: "Atatürk Kompleksi", squad: ["Uğurcan Çakır (GK)", "Samet Akaydin (DEF)", "Ferdi Kadıoğlu (DEF)", "Salih Özcan (MID)", "Arda Güler (MID)", "Yunus Akgün (FW)"] },
                { id: "5", name: "Trabzon Fırtınası", short: "TRB", icon: "🌊", stadium: "Karadeniz Arena", squad: ["Altay Bayındır (GK)", "Serdar Saatçı (DEF)", "Eren Elmalı (DEF)", "Berat Özdemir (MID)", "Barış Alper Yılmaz (FW)", "Semih Kılıçsoy (FW)"] },
                { id: "6", name: "Antalya Akrep", short: "ANT", icon: "🦂", stadium: "Akdeniz Stadyumu", squad: ["Berke Özer (GK)", "Ozan Kabak (DEF)", "Rıdvan Yılmaz (DEF)", "İsmail Yüksek (MID)", "Yusuf Yazıcı (FW)", "Bertuğ Yıldırım (FW)"] }
            ],
            players: [
                { id: 101, name: "Burak Yılmaz", teamId: "1", goals: 7, assists: 2 },
                { id: 102, name: "Arda Güler", teamId: "4", goals: 5, assists: 6 },
                { id: 103, name: "Cengiz Ünder", teamId: "2", goals: 6, assists: 3 },
                { id: 104, name: "Kerem Aktürkoğlu", teamId: "3", goals: 4, assists: 5 },
                { id: 105, name: "Barış Alper Yılmaz", teamId: "5", goals: 5, assists: 1 },
                { id: 106, name: "Semih Kılıçsoy", teamId: "5", goals: 3, assists: 2 },
                { id: 107, name: "Hakan Çalhanoğlu", teamId: "1", goals: 2, assists: 7 },
                { id: 108, name: "Bertuğ Yıldırım", teamId: "6", goals: 4, assists: 0 }
            ],
            fixtures: [
                {
                    week: 1,
                    matches: [
                        { id: "w1m1", homeId: "1", awayId: "2", homeScore: 3, awayScore: 1, played: true },
                        { id: "w1m2", homeId: "3", awayId: "4", homeScore: 2, awayScore: 2, played: true },
                        { id: "w1m3", homeId: "5", awayId: "6", homeScore: 1, awayScore: 0, played: true }
                    ]
                },
                {
                    week: 2,
                    matches: [
                        { id: "w2m1", homeId: "4", awayId: "1", homeScore: 0, awayScore: 2, played: true },
                        { id: "w2m2", homeId: "6", awayId: "3", homeScore: 1, awayScore: 3, played: true },
                        { id: "w2m3", homeId: "2", awayId: "5", homeScore: 2, awayScore: 2, played: true }
                    ]
                },
                {
                    week: 3,
                    matches: [
                        { id: "w3m1", homeId: "1", awayId: "5", homeScore: null, awayScore: null, played: false },
                        { id: "w3m2", homeId: "3", awayId: "2", homeScore: null, awayScore: null, played: false },
                        { id: "w3m3", homeId: "4", awayId: "6", homeScore: null, awayScore: null, played: false }
                    ]
                }
            ],
            news: [
                {
                    id: 1,
                    title: "Strikers Club Türkiye Ligi Yeni Sezonu Görkemli Başladı!",
                    category: "Duyuru",
                    date: "10 Eylül 2026",
                    content: "Strikers Club lig yönetimi yeni sezonun resmen açıldığını bildirdi. Tüm takımlara ve oyunculara başarılar dileriz."
                },
                {
                    id: 2,
                    title: "İstanbul Strikers Zirvedeki Yürüyüşünü Sürdürüyor",
                    category: "Haftanın Panoraması",
                    date: "08 Eylül 2026",
                    content: "Ligin ilk haftalarında üst üste galibiyetler alan İstanbul Strikers, averaj farkıyla liderlik koltuğunda oturuyor."
                }
            ]
        };

        // Application State Management
        let leagueData = JSON.parse(localStorage.getItem('strikers_league_data')) || DEFAULT_LEAGUE_DATA;
        let selectedWeek = 1;

        // Save State to LocalStorage
        function saveData() {
            localStorage.setItem('strikers_league_data', JSON.stringify(leagueData));
        }

        // Reset All League Data
        function resetLeagueData() {
            localStorage.removeItem('strikers_league_data');
            leagueData = JSON.parse(JSON.stringify(DEFAULT_LEAGUE_DATA));
            saveData();
            initApp();
            showNotice("Lig verileri başarıyla sıfırlandı!");
        }

        // Notification Helper
        function showNotice(msg) {
            const toast = document.createElement('div');
            toast.className = 'fixed bottom-5 right-5 bg-turkred text-white font-bold px-5 py-3 rounded-xl shadow-2xl z-50 transition-all transform translate-y-0';
            toast.innerText = msg;
            document.body.appendChild(toast);
            setTimeout(() => toast.remove(), 3000);
        }

        // Dynamically Calculate Points, Goal Differences and Standings
        function calculateStandings() {
            const stats = {};
            leagueData.teams.forEach(t => {
                stats[t.id] = {
                    id: t.id,
                    name: t.name,
                    icon: t.icon,
                    played: 0,
                    won: 0,
                    drawn: 0,
                    lost: 0,
                    gf: 0,
                    ga: 0,
                    gd: 0,
                    pts: 0
                };
            });

            leagueData.fixtures.forEach(w => {
                w.matches.forEach(m => {
                    if (m.played && m.homeScore !== null && m.awayScore !== null) {
                        const home = stats[m.homeId];
                        const away = stats[m.awayId];

                        if (home && away) {
                            home.played += 1;
                            away.played += 1;
                            home.gf += m.homeScore;
                            home.ga += m.awayScore;
                            away.gf += m.awayScore;
                            away.ga += m.homeScore;

                            if (m.homeScore > m.awayScore) {
                                home.won += 1;
                                home.pts += 3;
                                away.lost += 1;
                            } else if (m.homeScore < m.awayScore) {
                                away.won += 1;
                                away.pts += 3;
                                home.lost += 1;
                            } else {
                                home.drawn += 1;
                                home.pts += 1;
                                away.drawn += 1;
                                away.pts += 1;
                            }
                        }
                    }
                });
            });

            const table = Object.values(stats).map(s => {
                s.gd = s.gf - s.ga;
                return s;
            });

            // Sort: Points -> GD -> Goals For
            table.sort((a, b) => {
                if (b.pts !== a.pts) return b.pts - a.pts;
                if (b.gd !== a.gd) return b.gd - a.gd;
                return b.gf - a.gf;
            });

            return table;
        }

        // Render Dashboard Overview
        function renderDashboard() {
            const table = calculateStandings();
            
            // Mini Standings
            const miniBody = document.getElementById('dash-mini-standings');
            miniBody.innerHTML = table.slice(0, 4).map((t, idx) => `
                <tr class="hover:bg-gray-800/40">
                    <td class="py-2.5 font-bold ${idx === 0 ? 'text-league-gold' : 'text-gray-400'}">${idx + 1}</td>
                    <td class="py-2.5 font-semibold text-white flex items-center space-x-2">
                        <span>${t.icon}</span>
                        <span class="truncate max-w-[120px]">${t.name}</span>
                    </td>
                    <td class="py-2.5 text-center text-gray-400">${t.played}</td>
                    <td class="py-2.5 text-center text-gray-400">${t.gd > 0 ? '+' + t.gd : t.gd}</td>
                    <td class="py-2.5 text-right font-bold text-turkred">${t.pts}</td>
                </tr>
            `).join('');

            // Recent Played Matches
            const recentContainer = document.getElementById('dash-recent-matches');
            const playedMatches = [];
            leagueData.fixtures.forEach(w => {
                w.matches.forEach(m => {
                    if (m.played) playedMatches.push({ ...m, week: w.week });
                });
            });

            if (playedMatches.length === 0) {
                recentContainer.innerHTML = `<p class="text-xs text-gray-500 italic">Henüz oynanmış maç bulunmuyor.</p>`;
            } else {
                recentContainer.innerHTML = playedMatches.slice(-3).reverse().map(m => {
                    const home = leagueData.teams.find(t => t.id === m.homeId);
                    const away = leagueData.teams.find(t => t.id === m.awayId);
                    return `
                        <div class="bg-gray-900/80 p-3 rounded-xl border border-gray-800 flex items-center justify-between text-xs">
                            <div class="flex items-center space-x-2 w-2/5">
                                <span>${home?.icon || ''}</span>
                                <span class="font-bold text-white truncate">${home?.name || 'Takım'}</span>
                            </div>
                            <div class="bg-gray-800 px-3 py-1 rounded-lg font-black text-turkred border border-turkred/20">
                                ${m.homeScore} - ${m.awayScore}
                            </div>
                            <div class="flex items-center justify-end space-x-2 w-2/5 text-right">
                                <span class="font-bold text-white truncate">${away?.name || 'Takım'}</span>
                                <span>${away?.icon || ''}</span>
                            </div>
                        </div>
                    `;
                }).join('');
            }

            // Top Scorers Top 3
            const scorersContainer = document.getElementById('dash-top-scorers');
            const sortedScorers = [...leagueData.players].sort((a, b) => b.goals - a.goals).slice(0, 3);
            scorersContainer.innerHTML = sortedScorers.map((p, idx) => {
                const team = leagueData.teams.find(t => t.id === p.teamId);
                return `
                    <div class="flex items-center justify-between p-2.5 bg-gray-900/60 rounded-xl border border-gray-800">
                        <div class="flex items-center space-x-3">
                            <span class="w-6 h-6 rounded-full bg-amber-500/20 text-amber-400 font-bold text-xs flex items-center justify-center">${idx + 1}</span>
                            <div>
                                <div class="font-bold text-white text-sm">${p.name}</div>
                                <div class="text-xs text-gray-500">${team?.name || ''}</div>
                            </div>
                        </div>
                        <span class="font-black text-amber-400 text-sm">${p.goals} Gol</span>
                    </div>
                `;
            }).join('');
        }

        // Render Full Standings Table
        function renderStandings() {
            const table = calculateStandings();
            const tbody = document.getElementById('full-standings-body');
            tbody.innerHTML = table.map((t, idx) => {
                let statusColor = "";
                if (idx === 0) statusColor = "border-l-4 border-emerald-500";
                else if (idx === 1) statusColor = "border-l-4 border-sky-500";
                else if (idx >= table.length - 1) statusColor = "border-l-4 border-red-600";

                return `
                    <tr class="hover:bg-gray-800/40 transition-colors ${statusColor}">
                        <td class="px-4 py-4 text-center font-bold text-gray-400">${idx + 1}</td>
                        <td class="px-6 py-4 font-bold text-white flex items-center space-x-3">
                            <span class="text-xl">${t.icon}</span>
                            <span>${t.name}</span>
                        </td>
                        <td class="px-3 py-4 text-center">${t.played}</td>
                        <td class="px-3 py-4 text-center text-emerald-400 font-semibold">${t.won}</td>
                        <td class="px-3 py-4 text-center text-amber-400">${t.drawn}</td>
                        <td class="px-3 py-4 text-center text-red-400">${t.lost}</td>
                        <td class="px-3 py-4 text-center text-gray-400">${t.gf}</td>
                        <td class="px-3 py-4 text-center text-gray-400">${t.ga}</td>
                        <td class="px-3 py-4 text-center font-bold ${t.gd > 0 ? 'text-emerald-400' : t.gd < 0 ? 'text-red-400' : 'text-gray-400'}">${t.gd > 0 ? '+' + t.gd : t.gd}</td>
                        <td class="px-4 py-4 text-center text-white font-extrabold bg-gray-800/40 text-base">${t.pts}</td>
                    </tr>
                `;
            }).join('');
        }

        // Render Fixtures Tab
        function renderFixtures() {
            const weekSelect = document.getElementById('week-select');
            weekSelect.innerHTML = leagueData.fixtures.map(f => `
                <option value="${f.week}" ${f.week === selectedWeek ? 'selected' : ''}>Hafta ${f.week}</option>
            `).join('');

            const currentFixture = leagueData.fixtures.find(f => f.week === selectedWeek);
            const container = document.getElementById('fixtures-container');

            if (!currentFixture || currentFixture.matches.length === 0) {
                container.innerHTML = `<div class="col-span-2 text-center text-gray-500 py-8">Bu hafta için maç bulunmuyor.</div>`;
                return;
            }

            container.innerHTML = currentFixture.matches.map(m => {
                const home = leagueData.teams.find(t => t.id === m.homeId);
                const away = leagueData.teams.find(t => t.id === m.awayId);

                return `
                    <div class="bg-league-cardBg border border-gray-800 rounded-2xl p-5 hover:border-gray-700 transition-all flex items-center justify-between shadow-md">
                        <!-- Home Team -->
                        <div class="flex items-center space-x-3 w-5/12">
                            <span class="text-3xl">${home?.icon || '🛡️'}</span>
                            <div>
                                <span class="font-extrabold text-white block text-sm sm:text-base">${home?.name}</span>
                                <span class="text-xs text-gray-500">${home?.short}</span>
                            </div>
                        </div>

                        <!-- Score / Status -->
                        <div class="text-center w-2/12">
                            ${m.played ? `
                                <div class="bg-gray-900 border border-turkred/40 text-turkred font-black text-lg px-3 py-1.5 rounded-xl">
                                    ${m.homeScore} - ${m.awayScore}
                                </div>
                                <span class="text-[10px] text-gray-500 font-bold uppercase mt-1 block">Oynandı</span>
                            ` : `
                                <div class="bg-gray-800 text-gray-400 font-bold text-xs px-2.5 py-1.5 rounded-xl">
                                    VS
                                </div>
                                <span class="text-[10px] text-amber-500 font-bold uppercase mt-1 block">Oynanmadı</span>
                            `}
                        </div>

                        <!-- Away Team -->
                        <div class="flex items-center justify-end space-x-3 w-5/12 text-right">
                            <div>
                                <span class="font-extrabold text-white block text-sm sm:text-base">${away?.name}</span>
                                <span class="text-xs text-gray-500">${away?.short}</span>
                            </div>
                            <span class="text-3xl">${away?.icon || '🛡️'}</span>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function changeWeek(delta) {
            const maxWeek = leagueData.fixtures.length;
            const newWeek = selectedWeek + delta;
            if (newWeek >= 1 && newWeek <= maxWeek) {
                selectedWeek = newWeek;
                renderFixtures();
            }
        }

        function selectWeek(week) {
            selectedWeek = parseInt(week);
            renderFixtures();
        }

        // Render Stats Leaderboards
        function renderStats() {
            // Goals
            const sortedGoals = [...leagueData.players].sort((a, b) => b.goals - a.goals);
            const goalsBody = document.getElementById('top-goals-body');
            goalsBody.innerHTML = sortedGoals.map((p, idx) => {
                const team = leagueData.teams.find(t => t.id === p.teamId);
                return `
                    <tr class="hover:bg-gray-800/30">
                        <td class="p-3 text-center font-bold ${idx < 3 ? 'text-amber-400' : 'text-gray-500'}">${idx + 1}</td>
                        <td class="p-3 font-bold text-white">${p.name}</td>
                        <td class="p-3 text-gray-400 text-xs">${team?.name || ''}</td>
                        <td class="p-3 text-right font-black text-amber-400">${p.goals}</td>
                    </tr>
                `;
            }).join('');

            // Assists
            const sortedAssists = [...leagueData.players].sort((a, b) => b.assists - a.assists);
            const assistsBody = document.getElementById('top-assists-body');
            assistsBody.innerHTML = sortedAssists.map((p, idx) => {
                const team = leagueData.teams.find(t => t.id === p.teamId);
                return `
                    <tr class="hover:bg-gray-800/30">
                        <td class="p-3 text-center font-bold ${idx < 3 ? 'text-sky-400' : 'text-gray-500'}">${idx + 1}</td>
                        <td class="p-3 font-bold text-white">${p.name}</td>
                        <td class="p-3 text-gray-400 text-xs">${team?.name || ''}</td>
                        <td class="p-3 text-right font-black text-sky-400">${p.assists}</td>
                    </tr>
                `;
            }).join('');
        }

        // Render Teams Tab
        function renderTeams() {
            const container = document.getElementById('teams-grid');
            container.innerHTML = leagueData.teams.map(t => `
                <div onclick="openTeamModal('${t.id}')" class="bg-league-cardBg border border-gray-800 hover:border-turkred/50 rounded-2xl p-6 transition-all transform hover:-translate-y-1 cursor-pointer group shadow-lg">
                    <div class="text-4xl mb-4 group-hover:scale-110 transition-transform">${t.icon}</div>
                    <h3 class="text-xl font-black text-white mb-1">${t.name}</h3>
                    <p class="text-xs text-gray-400 mb-4">${t.stadium}</p>
                    <div class="flex items-center justify-between text-xs pt-4 border-t border-gray-800">
                        <span class="text-gray-500">${t.squad?.length || 0} Oyuncu</span>
                        <span class="text-turkred font-bold flex items-center">
                            Kadroyu Gör <i class="fa-solid fa-chevron-right ml-1 text-[10px]"></i>
                        </span>
                    </div>
                </div>
            `).join('');
        }

        // Open Team Modal Detail
        function openTeamModal(teamId) {
            const team = leagueData.teams.find(t => t.id === teamId);
            if (!team) return;

            document.getElementById('modal-team-icon').innerText = team.icon;
            document.getElementById('modal-team-name').innerText = team.name;
            document.getElementById('modal-team-stadium').innerText = `Stadyum: ${team.stadium}`;

            const rosterContainer = document.getElementById('modal-team-roster');
            rosterContainer.innerHTML = team.squad.map(player => `
                <div class="bg-gray-900/80 p-3 rounded-xl border border-gray-800 flex items-center space-x-3">
                    <div class="w-8 h-8 rounded-lg bg-gray-800 flex items-center justify-center text-turkred font-bold text-xs">
                        <i class="fa-solid fa-user"></i>
                    </div>
                    <span class="text-sm font-semibold text-gray-200">${player}</span>
                </div>
            `).join('');

            document.getElementById('team-modal').classList.remove('hidden');
        }

        function closeTeamModal() {
            document.getElementById('team-modal').classList.add('hidden');
        }

        // Render News Tab
        function renderNews() {
            const container = document.getElementById('news-container');
            container.innerHTML = leagueData.news.map(n => `
                <div class="bg-league-cardBg border border-gray-800 rounded-2xl p-6 flex flex-col justify-between hover:border-gray-700 transition-all shadow-md">
                    <div>
                        <div class="flex items-center justify-between mb-3">
                            <span class="bg-sky-500/10 text-sky-400 border border-sky-500/30 text-[10px] font-bold px-2.5 py-1 rounded-full uppercase">${n.category}</span>
                            <span class="text-xs text-gray-500">${n.date}</span>
                        </div>
                        <h3 class="text-lg font-bold text-white mb-3 leading-snug">${n.title}</h3>
                        <p class="text-sm text-gray-400 leading-relaxed">${n.content}</p>
                    </div>
                </div>
            `).join('');
        }

        // Admin Panel Controls
        function renderAdminPanel() {
            const weekSelect = document.getElementById('admin-week-select');
            weekSelect.innerHTML = leagueData.fixtures.map(f => `
                <option value="${f.week}">Hafta ${f.week}</option>
            `).join('');

            loadAdminMatches(weekSelect.value || 1);
        }

        function loadAdminMatches(weekNum) {
            const week = leagueData.fixtures.find(f => f.week === parseInt(weekNum));
            const matchSelect = document.getElementById('admin-match-select');

            if (!week || week.matches.length === 0) {
                matchSelect.innerHTML = `<option value="">Maç Yok</option>`;
                return;
            }

            matchSelect.innerHTML = week.matches.map(m => {
                const home = leagueData.teams.find(t => t.id === m.homeId);
                const away = leagueData.teams.find(t => t.id === m.awayId);
                return `<option value="${m.id}">${home?.name} vs ${away?.name} ${m.played ? `(${m.homeScore}-${m.awayScore})` : '(Oynanmadı)'}</option>`;
            }).join('');

            populateAdminMatchDetails();
        }

        function populateAdminMatchDetails() {
            const weekNum = parseInt(document.getElementById('admin-week-select').value);
            const matchId = document.getElementById('admin-match-select').value;

            const week = leagueData.fixtures.find(f => f.week === weekNum);
            const match = week?.matches.find(m => m.id === matchId);

            if (!match) return;

            const home = leagueData.teams.find(t => t.id === match.homeId);
            const away = leagueData.teams.find(t => t.id === match.awayId);

            document.getElementById('admin-home-name').innerText = home?.name || "Ev Sahibi";
            document.getElementById('admin-away-name').innerText = away?.name || "Deplasman";

            document.getElementById('admin-home-score').value = match.homeScore !== null ? match.homeScore : 0;
            document.getElementById('admin-away-score').value = match.awayScore !== null ? match.awayScore : 0;
        }

        function handleScoreSubmit(e) {
            e.preventDefault();
            const weekNum = parseInt(document.getElementById('admin-week-select').value);
            const matchId = document.getElementById('admin-match-select').value;
            const homeScore = parseInt(document.getElementById('admin-home-score').value);
            const awayScore = parseInt(document.getElementById('admin-away-score').value);

            const week = leagueData.fixtures.find(f => f.week === weekNum);
            const match = week?.matches.find(m => m.id === matchId);

            if (match) {
                match.homeScore = homeScore;
                match.awayScore = awayScore;
                match.played = true;

                saveData();
                initApp();
                showNotice("Skor kaydedildi ve Lig Tablosu güncellendi!");
            }
        }

        function handleAddNews(e) {
            e.preventDefault();
            const title = document.getElementById('news-title').value;
            const category = document.getElementById('news-category').value;
            const content = document.getElementById('news-content').value;

            const newNews = {
                id: Date.now(),
                title,
                category,
                content,
                date: new Date().toLocaleDateString('tr-TR', { day: 'numeric', month: 'long', year: 'numeric' })
            };

            leagueData.news.unshift(newNews);
            saveData();
            renderNews();

            document.getElementById('news-title').value = '';
            document.getElementById('news-content').value = '';

            showNotice("Yeni haber başarıyla eklendi!");
        }

        // Tab Switcher
        function switchTab(tabId) {
            const tabs = ['dashboard', 'standings', 'fixtures', 'stats', 'teams', 'news', 'admin'];
            tabs.forEach(t => {
                const el = document.getElementById(`tab-${t}`);
                if (el) el.classList.add('hidden');

                const navBtn = document.getElementById(`nav-${t}`);
                if (navBtn) {
                    navBtn.classList.remove('text-turkred', 'bg-league-cardBg', 'border', 'border-turkred/40');
                    navBtn.classList.add('text-gray-400');
                }
            });

            const activeTab = document.getElementById(`tab-${tabId}`);
            if (activeTab) activeTab.classList.remove('hidden');

            const activeBtn = document.getElementById(`nav-${tabId}`);
            if (activeBtn) {
                activeBtn.classList.remove('text-gray-400');
                activeBtn.classList.add('text-turkred', 'bg-league-cardBg', 'border', 'border-turkred/40');
            }

            document.getElementById('mobile-menu').classList.add('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        // App Initialization
        function initApp() {
            renderDashboard();
            renderStandings();
            renderFixtures();
            renderStats();
            renderTeams();
            renderNews();
            renderAdminPanel();
        }

        window.onload = function() {
            initApp();
        };
    </script>
</body>
</html>