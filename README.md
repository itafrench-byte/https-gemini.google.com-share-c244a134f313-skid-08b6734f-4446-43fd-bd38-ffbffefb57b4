[code_artifact.html](https://github.com/user-attachments/files/33489374/code_artifact.html)
<!DOCTYPE html>
<html lang="ko" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>금손만두 - 정성과 손맛으로 빚은 달인의 손만두</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Noto Sans KR, Nanum Myeongjo -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Nanum+Myeongjo:wght@700;800&family=Noto+Sans+KR:wght@300;400;500;700;900&display=swap" rel="stylesheet">
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        goldbrand: {
                            50: '#fffbf0',
                            100: '#fef3c7',
                            500: '#d97706',
                            600: '#b45309',
                            700: '#92400e',
                            800: '#78350f',
                            900: '#451a03',
                        },
                        dumplingRed: '#991b1b',
                        warmBg: '#fbf9f5',
                        darkBg: '#1c1917',
                    },
                    fontFamily: {
                        sans: ['Noto Sans KR', 'sans-serif'],
                        myeongjo: ['Nanum Myeongjo', 'serif'],
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background-color: #fbf9f5;
            color: #292524;
            overflow-x: hidden;
        }
        .myeongjo {
            font-family: 'Nanum Myeongjo', serif;
        }
        /* Custom Steam Animation for Dumplings */
        @keyframes steam {
            0% { transform: translateY(0) scaleX(1); opacity: 0; }
            50% { opacity: 0.6; }
            100% { transform: translateY(-40px) scaleX(1.5); opacity: 0; }
        }
        .steam-effect {
            animation: steam 3s infinite ease-out;
        }
        .steam-delay-1 { animation-delay: 0.8s; }
        .steam-delay-2 { animation-delay: 1.6s; }
        
        /* Glassmorphism */
        .glass-nav {
            background: rgba(251, 249, 245, 0.92);
            backdrop-filter: blur(8px);
        }
    </style>
</head>
<body class="antialiased selection:bg-goldbrand-500 selection:text-white">

<!-- Header & Navigation Bar -->
<header class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 glass-nav border-b border-stone-200/60 shadow-sm" id="mainHeader">
    <div class="max-w-7xl mx-mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between mx-auto">
        <!-- Logo -->
        <a href="#" class="flex items-center gap-3 group">
            <div class="w-11 h-11 bg-stone-900 rounded-full flex items-center justify-center text-amber-400 font-bold text-xl shadow-md border-2 border-amber-500 group-hover:scale-105 transition-transform">
                金
            </div>
            <div class="flex flex-col">
                <span class="myeongjo text-2xl font-extrabold tracking-tight text-stone-900 group-hover:text-goldbrand-600 transition-colors">
                    금손<span class="text-goldbrand-600">만두</span>
                </span>
                <span class="text-[10px] text-stone-500 tracking-widest -mt-1 font-semibold uppercase">Geumson Dumpling</span>
            </div>
        </a>

        <!-- Desktop Navigation -->
        <nav class="hidden md:flex items-center space-x-8 font-medium text-stone-700 text-base">
            <a href="#about" class="hover:text-goldbrand-600 transition-colors py-2 relative after:content-[''] after:absolute after:bottom-0 after:left-0 after:w-0 after:h-0.5 after:bg-goldbrand-600 hover:after:w-full after:transition-all">브랜드소개</a>
            <a href="#menu" class="hover:text-goldbrand-600 transition-colors py-2 relative after:content-[''] after:absolute after:bottom-0 after:left-0 after:w-0 after:h-0.5 after:bg-goldbrand-600 hover:after:w-full after:transition-all">달인 메뉴</a>
            <a href="#secret" class="hover:text-goldbrand-600 transition-colors py-2 relative after:content-[''] after:absolute after:bottom-0 after:left-0 after:w-0 after:h-0.5 after:bg-goldbrand-600 hover:after:w-full after:transition-all">맛의 비밀</a>
        </nav>

        <!-- Call to Actions -->
        <div class="hidden lg:flex items-center space-x-3">
            <button onclick="openModal('cartModal')" class="px-5 py-2.5 rounded-full bg-stone-900 text-amber-400 font-semibold text-sm hover:bg-goldbrand-700 hover:text-white transition shadow-md flex items-center gap-2">
                <i class="fa-solid fa-bag-shopping"></i>
                <span>포장 주문 예약</span>
                <span id="cartCount" class="bg-dumplingRed text-white text-xs px-2 py-0.5 rounded-full font-bold">0</span>
            </button>
        </div>

        <!-- Mobile Menu Toggle Button -->
        <button id="mobileMenuBtn" class="md:hidden p-2 text-stone-700 hover:text-stone-900 focus:outline-none">
            <i class="fa-solid fa-bars text-2xl"></i>
        </button>
    </div>

    <!-- Mobile Dropdown Menu -->
    <div id="mobileMenu" class="hidden md:hidden bg-white border-b border-stone-200 px-6 py-6 space-y-4 shadow-xl">
        <a href="#about" class="block text-stone-800 font-medium py-2 hover:text-goldbrand-600 border-b border-stone-100">브랜드소개</a>
        <a href="#menu" class="block text-stone-800 font-medium py-2 hover:text-goldbrand-600 border-b border-stone-100">달인 메뉴</a>
        <a href="#secret" class="block text-stone-800 font-medium py-2 hover:text-goldbrand-600">맛의 비밀</a>
        
        <div class="pt-4 flex flex-col gap-3">
            <button onclick="openModal('cartModal')" class="w-full py-3 rounded-xl bg-stone-900 text-amber-400 font-bold flex items-center justify-center gap-2 shadow">
                <i class="fa-solid fa-bag-shopping"></i> 포장 주문 담기 (<span id="mobileCartCount">0</span>)
            </button>
        </div>
    </div>
</header>

<!-- Hero Section (Slide Hero) -->
<section class="relative pt-24 min-h-[92vh] flex items-center justify-center bg-stone-900 text-white overflow-hidden">
    <!-- Darkened Layer & Food Background Pattern -->
    <div class="absolute inset-0 bg-cover bg-center opacity-30 scale-105 transition-transform duration-10000" style="background-image: url('https://images.unsplash.com/photo-1541696432-82c6da8ce7bf?q=80&w=1920&auto=format&fit=crop');"></div>
    <div class="absolute inset-0 bg-gradient-to-t from-stone-950 via-stone-900/80 to-transparent"></div>

    <!-- Animated Steam Decor -->
    <div class="absolute bottom-1/3 left-1/2 -translate-x-1/2 flex gap-8 opacity-40 pointer-events-none">
        <div class="w-16 h-32 bg-stone-300 rounded-full blur-xl steam-effect"></div>
        <div class="w-20 h-36 bg-stone-200 rounded-full blur-xl steam-effect steam-delay-1"></div>
        <div class="w-16 h-32 bg-stone-300 rounded-full blur-xl steam-effect steam-delay-2"></div>
    </div>

    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20 text-center z-10 flex flex-col items-center">
        <!-- Badge -->
        <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-amber-500/20 border border-amber-500/40 text-amber-300 text-xs sm:text-sm font-semibold mb-8 backdrop-blur-sm">
            <i class="fa-solid fa-award"></i> 대한민국 대표 수제 손만두의 자부심
        </div>

        <!-- Main Title -->
        <h1 class="myeongjo text-4xl sm:text-6xl md:text-7xl font-extrabold tracking-tight leading-tight sm:leading-none text-stone-100 mb-6">
            매일 아침 얇은 피에 <br class="hidden sm:inline" />
            <span class="text-amber-400 underline underline-offset-8 decoration-amber-600/60">정성을 빚어 넣습니다</span>
        </h1>

        <!-- Subtitle -->
        <p class="text-stone-300 text-base sm:text-xl max-w-2xl font-light leading-relaxed mb-10">
            신선한 국내산 100% 돼지고기와 엄선된 야채, 30년 전통 육수로 빚어낸 깊고 진한 맛.<br class="hidden md:inline"/>
            입안 가득 터지는 풍부한 육즙의 감동을 선사합니다.
        </p>

        <!-- Hero Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 w-full sm:w-auto">
            <a href="#menu" class="px-8 py-4 rounded-full bg-amber-500 hover:bg-amber-600 text-stone-950 font-bold text-lg shadow-lg hover:shadow-amber-500/20 transition-all flex items-center justify-center gap-2">
                <span>인기 메뉴 보기</span>
                <i class="fa-solid fa-arrow-right text-sm"></i>
            </a>
            <button onclick="openModal('cartModal')" class="px-8 py-4 rounded-full bg-stone-800/80 hover:bg-stone-800 border border-stone-600 text-stone-200 font-bold text-lg transition flex items-center justify-center gap-2 backdrop-blur-sm">
                <i class="fa-solid fa-bag-shopping text-amber-400"></i>
                <span>포장 예약 주문</span>
            </button>
        </div>

        <!-- Key Highlights Cards -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 sm:gap-6 mt-16 w-full max-w-4xl text-left">
            <div class="bg-stone-800/50 backdrop-blur-md p-4 rounded-2xl border border-stone-700/60">
                <p class="text-xs text-amber-400 font-bold mb-1">01. 당일 생산 원칙</p>
                <p class="text-stone-200 font-bold text-sm sm:text-base">매일 아침 직송 재료</p>
            </div>
            <div class="bg-stone-800/50 backdrop-blur-md p-4 rounded-2xl border border-stone-700/60">
                <p class="text-xs text-amber-400 font-bold mb-1">02. 0.5mm 초박피</p>
                <p class="text-stone-200 font-bold text-sm sm:text-base">속이 훤히 보이는 피</p>
            </div>
            <div class="bg-stone-800/50 backdrop-blur-md p-4 rounded-2xl border border-stone-700/60">
                <p class="text-xs text-amber-400 font-bold mb-1">03. 100% 한돈 사용</p>
                <p class="text-stone-200 font-bold text-sm sm:text-base">풍부한 육즙과 식감</p>
            </div>
            <div class="bg-stone-800/50 backdrop-blur-md p-4 rounded-2xl border border-stone-700/60">
                <p class="text-xs text-amber-400 font-bold mb-1">04. 무방부제·무색소</p>
                <p class="text-stone-200 font-bold text-sm sm:text-base">온가족 안심 먹거리</p>
            </div>
        </div>
    </div>
</section>

<!-- Brand Story Section -->
<section id="about" class="py-24 bg-warmBg relative overflow-hidden">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-16 items-center">
            
            <!-- Left Image Collage -->
            <div class="relative">
                <div class="relative z-10 rounded-3xl overflow-hidden shadow-2xl border-4 border-white">
                    <img src="https://images.unsplash.com/photo-1541696432-82c6da8ce7bf?q=80&w=900&auto=format&fit=crop" alt="손만두 빚는 과정" class="w-full h-[450px] object-cover hover:scale-105 transition-transform duration-700">
                </div>
                <div class="absolute -bottom-8 -right-6 z-20 w-3/5 rounded-2xl overflow-hidden shadow-2xl border-4 border-white hidden sm:block">
                    <img src="https://images.unsplash.com/photo-1563245372-f21724e3856d?q=80&w=600&auto=format&fit=crop" alt="갓 찐 찜기 만두" class="w-full h-56 object-cover">
                </div>
                <div class="absolute -top-6 -left-6 w-32 h-32 bg-amber-200 rounded-full filter blur-2xl opacity-60"></div>
                <!-- Experience Badge -->
                <div class="absolute top-6 left-6 z-20 bg-stone-900 text-amber-400 px-5 py-3 rounded-2xl shadow-xl flex items-center gap-3 border border-amber-500/30">
                    <i class="fa-solid fa-utensils text-2xl"></i>
                    <div>
                        <p class="text-xs text-stone-400 font-medium">손만두 외길</p>
                        <p class="myeongjo font-bold text-lg text-white">30년 달인의 집념</p>
                    </div>
                </div>
            </div>

            <!-- Right Story Content -->
            <div class="space-y-6">
                <div class="inline-block px-3 py-1 bg-amber-100 text-goldbrand-800 rounded-md text-xs font-bold uppercase tracking-wider">Brand Story</div>
                <h2 class="myeongjo text-3xl sm:text-4xl lg:text-5xl font-extrabold text-stone-900 leading-tight">
                    한 알 한 알,<br/>
                    <span class="text-goldbrand-600">금빛 손길</span>로 완성하는 진심
                </h2>
                <p class="text-stone-600 text-base sm:text-lg leading-relaxed">
                    금손만두는 기계로 찍어내는 흔한 만두와 다릅니다. 
                    수십 년간 만두만을 빚어온 달인의 섬세한 손끝에서 피어나는 진짜 손만두입니다.
                </p>
                <p class="text-stone-600 text-base leading-relaxed">
                    속이 투명하게 비치는 얇은 피 속에는 매일 아침 엄선한 신선한 야채와 국내산 100% 돼지고기가 가득 차 있습니다. 한 입 베어 물 때 느껴지는 풍부한 육즙과 쫄깃한 피의 완벽한 조화를 약속드립니다.
                </p>

                <!-- Points List -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-4 border-t border-stone-200">
                    <div class="flex items-start gap-3">
                        <div class="w-8 h-8 rounded-full bg-amber-500/10 flex items-center justify-center text-amber-600 shrink-0 mt-1">
                            <i class="fa-solid fa-check text-sm"></i>
                        </div>
                        <div>
                            <h4 class="font-bold text-stone-800 text-base">당일 제조 · 당일 판매</h4>
                            <p class="text-xs text-stone-500">신선함을 위해 그날 만든 만두만 판매합니다.</p>
                        </div>
                    </div>
                    <div class="flex items-start gap-3">
                        <div class="w-8 h-8 rounded-full bg-amber-500/10 flex items-center justify-center text-amber-600 shrink-0 mt-1">
                            <i class="fa-solid fa-check text-sm"></i>
                        </div>
                        <div>
                            <h4 class="font-bold text-stone-800 text-base">특제 천연 육수</h4>
                            <p class="text-xs text-stone-500">인공 조미료를 줄이고 깊은 풍미를 더했습니다.</p>
                        </div>
                    </div>
                </div>

            </div>

        </div>
    </div>
</section>

<!-- Menu Showcase Section -->
<section id="menu" class="py-24 bg-stone-100 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        
        <!-- Section Title Header -->
        <div class="text-center max-w-3xl mx-auto mb-12">
            <span class="text-goldbrand-600 font-bold text-sm tracking-widest uppercase">Geumson Delicious Menu</span>
            <h2 class="myeongjo text-3xl sm:text-4xl font-extrabold text-stone-900 mt-2">금손만두 대표 메뉴</h2>
            <p class="text-stone-600 mt-3 text-base">정성과 손맛이 가득 들어간 달인의 메뉴를 확인해 보세요.</p>
        </div>

        <!-- Menu Filter Buttons -->
        <div class="flex flex-wrap justify-center gap-2 sm:gap-3 mb-12">
            <button onclick="filterMenu('all')" class="menu-tab active px-5 py-2.5 rounded-full text-sm font-bold transition-all bg-stone-900 text-amber-400 shadow-md">
                전체보기
            </button>
            <button onclick="filterMenu('tong')" class="menu-tab px-5 py-2.5 rounded-full text-sm font-bold transition-all bg-white text-stone-700 hover:bg-stone-200">
                통만두류
            </button>
            <button onclick="filterMenu('king')" class="menu-tab px-5 py-2.5 rounded-full text-sm font-bold transition-all bg-white text-stone-700 hover:bg-stone-200">
                왕만두/찐빵류
            </button>
            <button onclick="filterMenu('special')" class="menu-tab px-5 py-2.5 rounded-full text-sm font-bold transition-all bg-white text-stone-700 hover:bg-stone-200">
                별미/전골류
            </button>
        </div>

        <!-- Menu Grid (Wonmiga Official Lineup) -->
        <div id="menuGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6 sm:gap-8">
            
            <!-- Menu Item 1: 고기통만두 -->
            <div class="menu-item tong bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1541696432-82c6da8ce7bf?q=80&w=800&auto=format&fit=crop" alt="고기통만두" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                    <span class="absolute top-3 left-3 bg-amber-500 text-stone-950 font-bold text-xs px-2.5 py-1 rounded-md shadow">BEST</span>
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">고기통만두 (8개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">6,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2"> thin 0.5mm 피 속에 100% 국산 한돈 고기와 신선한 야채가 꽉 찬 백남옥 장인의 대표 시그니처 통만두</p>
                    </div>
                    <button onclick="addToCart('고기통만두 (8개)', 6000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 2: 김치통만두 -->
            <div class="menu-item tong bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1498654896293-37aacf113fd9?q=80&w=800&auto=format&fit=crop" alt="김치통만두" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                    <span class="absolute top-3 left-3 bg-dumplingRed text-white font-bold text-xs px-2.5 py-1 rounded-md shadow">인기</span>
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">김치통만두 (8개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">6,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">아삭아삭 씹히는 국산 김치와 감칠맛 나는 매콤한 소로 입맛을 사로잡는 수제 김치통만두</p>
                    </div>
                    <button onclick="addToCart('김치통만두 (8개)', 6000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 3: 새우통만두 -->
            <div class="menu-item tong bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1563245372-f21724e3856d?q=80&w=800&auto=format&fit=crop" alt="새우통만두" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                    <span class="absolute top-3 left-3 bg-stone-900 text-amber-400 font-bold text-xs px-2.5 py-1 rounded-md shadow">강추</span>
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">새우통만두 (5개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">6,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">탱글탱글한 통새우 한 마리가 통째로 얇은 피 속으로 쏙 들어간 고급 스페셜 만두</p>
                    </div>
                    <button onclick="addToCart('새우통만두 (5개)', 6000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 4: 갈비통만두 -->
            <div class="menu-item tong bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1569718212165-3a8278d5f624?q=80&w=800&auto=format&fit=crop" alt="갈비통만두" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">갈비통만두 (10개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">6,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">달콤 짭조름한 숯불 갈비 양념 소가 듬뿍 들어간 남녀노소 최고의 인기 만두</p>
                    </div>
                    <button onclick="addToCart('갈비통만두 (10개)', 6000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 5: 고기왕만두 -->
            <div class="menu-item king bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1625398407796-82650a8c139f?q=80&w=800&auto=format&fit=crop" alt="고기왕만두" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                    <span class="absolute top-3 left-3 bg-amber-500 text-stone-950 font-bold text-xs px-2.5 py-1 rounded-md shadow">인기</span>
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">고기왕만두 (4개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">5,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">폭신폭신 발효 빵피 속에 고기 속이 푸짐하게 담긴 든든한 장인 왕만두</p>
                    </div>
                    <button onclick="addToCart('고기왕만두 (4개)', 5000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 6: 김치왕만두 -->
            <div class="menu-item king bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1585032226651-759b368d7246?q=80&w=800&auto=format&fit=crop" alt="김치왕만두" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">김치왕만두 (4개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">5,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">부드러운 왕만두 피와 매콤달콤 칼칼한 김치소가 만들어내는 가성비 최고 왕만두</p>
                    </div>
                    <button onclick="addToCart('김치왕만두 (4개)', 5000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 7: 우유찐빵 -->
            <div class="menu-item king bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1505253716362-afaea1d3d1af?q=80&w=800&auto=format&fit=crop" alt="우유찐빵" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">우유찐빵 (4개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">5,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">고소하고 촉촉한 우유 반죽에 적당한 단맛의 팥앙금이 듬뿍 들어간 전통 찐빵</p>
                    </div>
                    <button onclick="addToCart('우유찐빵 (4개)', 5000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 8: 굴림고기만두 -->
            <div class="menu-item special bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1547592180-85f173990554?q=80&w=800&auto=format&fit=crop" alt="굴림고기만두" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                    <span class="absolute top-3 left-3 bg-amber-600 text-white font-bold text-xs px-2.5 py-1 rounded-md shadow">별미</span>
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">굴림고기만두 (10개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">6,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">밀가루 피 없이 전분 가루에 살살 굴려 익혀낸 탄수화물 부담 적은 건강 손만두</p>
                    </div>
                    <button onclick="addToCart('굴림고기만두 (10개)', 6000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 9: 원미가 만두전골 세트 -->
            <div class="menu-item special bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1541696432-82c6da8ce7bf?q=80&w=800&auto=format&fit=crop" alt="원미가 만두전골 세트" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                    <span class="absolute top-3 left-3 bg-stone-900 text-amber-400 font-bold text-xs px-2.5 py-1 rounded-md shadow">밀키트</span>
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">원미가 만두전골 세트</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">18,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">수제 만두 10개 + 비법 천연육수 + 신선 야채 + 칼국수 사리가 포함된 풍성한 전골 (2~3인분)</p>
                    </div>
                    <button onclick="addToCart('원미가 만두전골 세트', 18000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

            <!-- Menu Item 10: 바싹군만두 -->
            <div class="menu-item special bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 border border-stone-200 flex flex-col group">
                <div class="relative h-52 overflow-hidden bg-stone-200">
                    <img src="https://images.unsplash.com/photo-1569718212165-3a8278d5f624?q=80&w=800&auto=format&fit=crop" alt="바싹군만두" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                </div>
                <div class="p-5 flex-1 flex flex-col justify-between">
                    <div>
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="font-bold text-stone-900 text-lg group-hover:text-goldbrand-600 transition-colors">바싹군만두 (5개)</h3>
                            <span class="font-extrabold text-goldbrand-700 text-lg">6,000원</span>
                        </div>
                        <p class="text-xs text-stone-500 mb-4 line-clamp-2">겉은 노릇하고 바삭하며 속은 육즙으로 가득 찬 한 손에 들어오는 극상의 바싹 군만두</p>
                    </div>
                    <button onclick="addToCart('바싹군만두 (5개)', 6000)" class="w-full py-2.5 rounded-xl border border-stone-300 hover:bg-stone-900 hover:text-amber-400 font-bold text-xs text-stone-800 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-plus"></i> 포장담기
                    </button>
                </div>
            </div>

        </div>
    </div>
</section>

<!-- Footer -->
<footer class="bg-stone-950 text-stone-400 py-16 border-t border-stone-800">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-12">
            
            <!-- Brand Info -->
            <div class="md:col-span-2">
                <div class="flex items-center gap-2 mb-4">
                    <div class="w-8 h-8 bg-amber-500 rounded-full flex items-center justify-center text-stone-950 font-bold text-sm">金</div>
                    <span class="myeongjo text-xl font-bold text-white">금손만두</span>
                </div>
                <p class="text-xs text-stone-400 leading-relaxed max-w-sm mb-4">
                    (주)금손푸드 | 대표자: 금달인<br>
                    사업자등록번호: 746-08-00742 | 통신판매업신고: 제 2026-경기남양주-0123 호<br>
                    주소: 경기 남양주시 진접읍 금강로 1845번길 16-2 금손만두빌딩 2층
                </p>
                <p class="text-xs text-stone-500">© 2026 GEUMSON DUMPLING. All rights reserved.</p>
            </div>

            <!-- Customer Center -->
            <div>
                <h4 class="text-white font-bold text-sm mb-3">고객센터 & 주문문의</h4>
                <p class="text-2xl font-extrabold text-amber-400 mb-1">031-527-8671</p>
                <p class="text-xs text-stone-400">운영시간: 09:00 ~ 21:00 (연중무휴)</p>
                <p class="text-xs text-stone-400 mt-1">이메일: geumson@dumpling.co.kr</p>
            </div>

            <!-- Navigation Links -->
            <div>
                <h4 class="text-white font-bold text-sm mb-3">바로가기</h4>
                <ul class="space-y-2 text-xs">
                    <li><a href="#about" class="hover:text-amber-400 transition">브랜드 스토리</a></li>
                    <li><a href="#menu" class="hover:text-amber-400 transition">메뉴 안내</a></li>
                    <li><a href="#secret" class="hover:text-amber-400 transition">맛의 비밀</a></li>
                    <li><a href="#" class="hover:text-amber-400 transition">개인정보처리방침</a></li>
                </ul>
            </div>
        </div>
    </div>
</footer>

<!-- Order / Cart Modal -->
<div id="cartModal" class="fixed inset-0 bg-black/70 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-md w-full p-6 shadow-2xl relative border border-stone-200">
        <button onclick="closeModal('cartModal')" class="absolute top-5 right-5 text-stone-400 hover:text-stone-800 text-xl font-bold">
            <i class="fa-solid fa-xmark"></i>
        </button>

        <h3 class="myeongjo text-2xl font-bold text-stone-900 mb-1">포장 주문 목록</h3>
        <p class="text-xs text-stone-500 mb-6">매장 방문 전 미리 포장 주문을 예약하실 수 있습니다.</p>

        <!-- Cart Items List -->
        <div id="cartItems" class="space-y-3 max-h-60 overflow-y-auto mb-6 pr-1">
            <p id="emptyCartMsg" class="text-stone-400 text-xs text-center py-8">담긴 메뉴가 없습니다. 메뉴에서 포장하실 만두를 담아주세요.</p>
        </div>

        <!-- Total Sum -->
        <div class="border-t border-stone-200 pt-4 mb-6">
            <div class="flex justify-between items-center font-bold text-stone-900">
                <span>총 결제 예정 금액</span>
                <span id="cartTotalPrice" class="text-xl text-goldbrand-700">0 원</span>
            </div>
        </div>

        <button onclick="checkoutOrder()" class="w-full py-3.5 bg-amber-500 hover:bg-amber-600 text-stone-950 font-bold rounded-xl shadow-lg transition">
            포장 방문 예약 신청하기
        </button>
    </div>
</div>

<!-- Toast Notice Message -->
<div id="toast" class="fixed bottom-6 right-6 bg-stone-900 text-amber-400 px-6 py-3.5 rounded-2xl shadow-2xl z-50 text-xs sm:text-sm font-bold hidden transition-all flex items-center gap-3 border border-amber-500/30">
    <i class="fa-solid fa-circle-check text-amber-400 text-base"></i>
    <span id="toastMsg">메뉴가 담겼습니다!</span>
</div>

<script>
    // Shopping Cart State
    let cart = [];

    // Navigation Toggle for Mobile
    const mobileBtn = document.getElementById('mobileMenuBtn');
    const mobileMenu = document.getElementById('mobileMenu');

    mobileBtn.addEventListener('click', () => {
        mobileMenu.classList.toggle('hidden');
    });

    // Menu Filtering Logic
    function filterMenu(category) {
        const items = document.querySelectorAll('.menu-item');
        const tabs = document.querySelectorAll('.menu-tab');

        tabs.forEach(tab => {
            tab.classList.remove('bg-stone-900', 'text-amber-400', 'shadow-md');
            tab.classList.add('bg-white', 'text-stone-700');
        });

        event.currentTarget.classList.remove('bg-white', 'text-stone-700');
        event.currentTarget.classList.add('bg-stone-900', 'text-amber-400', 'shadow-md');

        items.forEach(item => {
            if (category === 'all' || item.classList.contains(category)) {
                item.style.display = 'flex';
            } else {
                item.style.display = 'none';
            }
        });
    }

    // Add to Cart
    function addToCart(name, price) {
        const existing = cart.find(item => item.name === name);
        if (existing) {
            existing.qty += 1;
        } else {
            cart.push({ name, price, qty: 1 });
        }
        updateCartUI();
        showToast(`[${name}] 포장 목록에 추가되었습니다!`);
    }

    // Update Cart UI
    function updateCartUI() {
        const cartCount = document.getElementById('cartCount');
        const mobileCartCount = document.getElementById('mobileCartCount');
        const cartItems = document.getElementById('cartItems');
        const emptyCartMsg = document.getElementById('emptyCartMsg');
        const cartTotalPrice = document.getElementById('cartTotalPrice');

        const totalQty = cart.reduce((sum, item) => sum + item.qty, 0);
        const totalPrice = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);

        cartCount.innerText = totalQty;
        mobileCartCount.innerText = totalQty;

        if (cart.length === 0) {
            emptyCartMsg.style.display = 'block';
            cartItems.innerHTML = '<p id="emptyCartMsg" class="text-stone-400 text-xs text-center py-8">담긴 메뉴가 없습니다. 메뉴에서 포장하실 만두를 담아주세요.</p>';
        } else {
            cartItems.innerHTML = '';
            cart.forEach((item, index) => {
                const div = document.createElement('div');
                div.className = 'flex justify-between items-center bg-stone-50 p-3 rounded-xl border border-stone-200 text-xs';
                div.innerHTML = `
                    <div>
                        <p class="font-bold text-stone-800">${item.name}</p>
                        <p class="text-stone-500 text-[11px]">${(item.price * item.qty).toLocaleString()}원</p>
                    </div>
                    <div class="flex items-center gap-2">
                        <button onclick="changeQty(${index}, -1)" class="w-6 h-6 rounded bg-stone-200 text-stone-700 font-bold flex items-center justify-center hover:bg-stone-300">-</button>
                        <span class="font-bold text-stone-800 w-4 text-center">${item.qty}</span>
                        <button onclick="changeQty(${index}, 1)" class="w-6 h-6 rounded bg-stone-200 text-stone-700 font-bold flex items-center justify-center hover:bg-stone-300">+</button>
                    </div>
                `;
                cartItems.appendChild(div);
            });
        }

        cartTotalPrice.innerText = `${totalPrice.toLocaleString()} 원`;
    }

    function changeQty(index, delta) {
        cart[index].qty += delta;
        if (cart[index].qty <= 0) {
            cart.splice(index, 1);
        }
        updateCartUI();
    }

    // Toast Notification
    function showToast(message) {
        const toast = document.getElementById('toast');
        const toastMsg = document.getElementById('toastMsg');
        toastMsg.innerText = message;
        toast.classList.remove('hidden');

        setTimeout(() => {
            toast.classList.add('hidden');
        }, 2500);
    }

    // Modal Operations
    function openModal(id) {
        document.getElementById(id).classList.remove('hidden');
    }

    function closeModal(id) {
        document.getElementById(id).classList.add('hidden');
    }

    function checkoutOrder() {
        if (cart.length === 0) {
            showToast('포장할 메뉴를 먼저 추가해주세요!');
            return;
        }
        closeModal('cartModal');
        showToast('포장 예약 접수가 완료되었습니다. 매장에서 확인 연락을 드립니다!');
        cart = [];
        updateCartUI();
    }
</script>

</body>
</html>
