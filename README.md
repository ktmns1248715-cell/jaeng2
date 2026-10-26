<!DOCTYPE html>
<html lang="ko" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PalmAura - 금쪽이를 위한</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        mystic: {
                            900: '#0b0c16',
                            800: '#131527',
                            700: '#1e223f',
                            600: '#2d335c',
                        },
                        gold: {
                            400: '#facc15',
                            500: '#eab308',
                            600: '#ca8a04',
                            accent: '#fde047'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <!-- FontAwesome & Google Fonts -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500;700&family=Noto+Sans+KR:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background-color: #0b0c16;
            color: #e2e8f0;
            overflow-x: hidden;
        }
        .cinzel-font {
            font-family: 'Cinzel', serif;
        }
        .glow-gold {
            box-shadow: 0 0 25px rgba(234, 179, 8, 0.25);
        }
        .glow-purple {
            box-shadow: 0 0 30px rgba(147, 51, 234, 0.2);
        }
        .glass-panel {
            background: rgba(19, 21, 39, 0.75);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(234, 179, 8, 0.2);
        }
        @keyframes scanline {
            0% { transform: translateY(-100%); }
            100% { transform: translateY(100%); }
        }
        .scanner-line {
            animation: scanline 2.5s infinite linear;
        }
        @keyframes pulseGlow {
            0%, 100% { opacity: 0.4; }
            50% { opacity: 0.9; }
        }
        .pulse-slow {
            animation: pulseGlow 3s infinite ease-in-out;
        }
    </style>
</head>
<body class="min-h-screen bg-mystic-900 flex flex-col justify-between selection:bg-gold-500 selection:text-mystic-900">

    <!-- Header -->
    <header class="w-full border-b border-gold-500/20 bg-mystic-900/80 backdrop-blur-md sticky top-0 z-50">
        <div class="max-w-5xl mx-auto px-4 py-4 flex items-center justify-between">
            <div class="flex items-center space-x-3 cursor-pointer" onclick="resetApp()">
                <div class="w-10 h-10 rounded-full bg-gradient-to-tr from-gold-600 to-amber-300 flex items-center justify-center glow-gold text-mystic-900 font-bold text-xl">
                    <i class="fa-solid fa-hand-sparkles"></i>
                </div>
                <div>
                    <h1 class="cinzel-font text-xl font-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-amber-200 via-gold-400 to-amber-100">PALMAURA</h1>
                    <p class="text-xs text-gold-400/70 tracking-widest uppercase">AI Mystical Palmistry</p>
                </div>
            </div>
            <div class="flex items-center space-x-2">
                <span class="inline-flex items-center px-3 py-1 rounded-full text-xs font-medium bg-gold-500/15 text-gold-400 border border-gold-500/30">
                    <span class="w-2 h-2 mr-1.5 bg-gold-400 rounded-full animate-pulse"></span>
                    Gemini AI Active
                </span>
            </div>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="flex-grow max-w-4xl w-full mx-auto p-4 sm:p-6 my-auto">

        <!-- STEP 1: Upload / Capture Screen -->
        <section id="upload-section" class="transition-all duration-500 space-y-6">
            <div class="text-center space-y-3 max-w-2xl mx-auto py-4">
                <h2 class="cinzel-font text-3xl sm:text-4xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-amber-100 via-gold-400 to-amber-200">
                   똥강아지야 믿을걸 믿어야지이~~~ 손금은 손금일뿐이란다 ~~~ 너는 내 손안에 있다아~
                </h2>
                <p class="text-gray-300 text-sm sm:text-base leading-relaxed">
                   똥강아지야 믿을걸 믿어야지이~~~ 손금은 손금일뿐이란다 ~~~ 너는 내 손안에 있다아~
                </p>
            </div>

            <!-- Upload Box Container -->
            <div class="glass-panel rounded-3xl p-6 sm:p-10 glow-gold relative overflow-hidden">
                <div class="absolute -top-24 -right-24 w-48 h-48 bg-gold-500/10 rounded-full blur-3xl pointer-events-none"></div>
                <div class="absolute -bottom-24 -left-24 w-48 h-48 bg-purple-600/10 rounded-full blur-3xl pointer-events-none"></div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-center">
                    
                    <!-- Drag & Drop / File Input Area -->
                    <div id="drop-zone" class="border-2 border-dashed border-gold-500/40 hover:border-gold-400 rounded-2xl p-8 text-center cursor-pointer transition-all bg-mystic-800/40 hover:bg-mystic-800/70 flex flex-col items-center justify-center min-h-[260px] group relative">
                        <input type="file" id="file-input" accept="image/*" class="absolute inset-0 opacity-0 cursor-pointer w-full h-full z-10">
                        <div class="w-16 h-16 rounded-2xl bg-gold-500/10 text-gold-400 flex items-center justify-center text-2xl mb-4 group-hover:scale-110 transition-transform duration-300 border border-gold-500/20">
                            <i class="fa-solid fa-cloud-arrow-up"></i>
                        </div>
                        <h3 class="font-semibold text-white text-lg mb-1">손바닥 사진 파일 업로드</h3>
                        <p class="text-xs text-gray-400 mb-4">선명하고 밝은 곳에서 촬영된 오른손 바닥 권장</p>
                        <span class="px-4 py-2 rounded-xl bg-gold-500/20 text-gold-400 text-xs font-semibold border border-gold-500/30">파일 선택하기</span>
                    </div>

                    <!-- Camera Capture & Guide Area -->
                    <div class="flex flex-col justify-center space-y-4 bg-mystic-800/60 p-6 rounded-2xl border border-gold-500/20 min-h-[260px]">
                        <div class="flex items-center space-x-3 text-gold-400">
                            <i class="fa-solid fa-camera-retro text-xl"></i>
                            <h3 class="font-semibold text-white text-base">실시간 카메라 촬영</h3>
                        </div>
                        <p class="text-xs text-gray-300 leading-relaxed">
                            웹캠 또는 모바일 카메라를 사용하여 지금 바로 손바닥을 촬영하고 실시간 분석을 시작할 수 있습니다.
                        </p>
                        <div class="pt-2">
                            <button id="camera-btn" onclick="openCameraModal()" class="w-full py-3 px-4 bg-gradient-to-r from-gold-600 to-amber-500 hover:from-gold-500 hover:to-amber-400 text-mystic-900 font-bold rounded-xl transition-all shadow-lg flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-video"></i>
                                <span>카메라로 촬영하기</span>
                            </button>
                        </div>
                        <div class="bg-mystic-900/50 p-3 rounded-xl border border-gray-800 text-[11px] text-gray-400 space-y-1">
                            <div class="text-gold-400 font-medium"><i class="fa-solid fa-lightbulb mr-1"></i> 촬영 팁</div>
                            <div>• 손바닥 전체가 정면으로 나오도록 해주세요.</div>
                            <div>• 주름과 선이 선명하게 보이도록 조명이 밝은 곳이 좋습니다.</div>
                        </div>
                    </div>

                </div>

                <!-- Preview Selected Image Container (Hidden initially) -->
                <div id="preview-container" class="hidden mt-6 pt-6 border-t border-gold-500/20 flex flex-col sm:flex-row items-center justify-between gap-4">
                    <div class="flex items-center space-x-4">
                        <div class="relative w-20 h-20 rounded-xl overflow-hidden border-2 border-gold-500 glow-gold">
                            <img id="preview-img" src="" alt="Selected Palm" class="w-full h-full object-cover">
                        </div>
                        <div>
                            <h4 id="file-name" class="font-semibold text-white text-sm truncate max-w-[200px] sm:max-w-xs">손바닥_사진.jpg</h4>
                            <p class="text-xs text-emerald-400"><i class="fa-solid fa-check-circle mr-1"></i> 이미지 준비 완료</p>
                        </div>
                    </div>
                    <div class="flex items-center space-x-3 w-full sm:w-auto">
                        <button onclick="clearSelectedImage()" class="px-4 py-2 rounded-xl bg-mystic-700 hover:bg-mystic-600 text-gray-300 text-xs font-semibold transition-all">
                            다시 선택
                        </button>
                        <button onclick="startAnalysis()" class="flex-grow sm:flex-grow-0 px-6 py-2.5 rounded-xl bg-gradient-to-r from-amber-400 to-gold-500 text-mystic-900 font-bold text-sm shadow-lg hover:brightness-110 transition-all">
                            <i class="fa-solid fa-wand-magic-sparkles mr-1.5"></i> 손금 분석 시작
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- STEP 2: Loading & Scanning Animation Screen (Hidden initially) -->
        <section id="loading-section" class="hidden py-16 text-center space-y-8">
            <div class="relative w-48 h-48 mx-auto rounded-3xl overflow-hidden glass-panel glow-gold p-2 flex items-center justify-center">
                <img id="scanning-img" src="" alt="Scanning Palm" class="w-full h-full object-cover rounded-2xl opacity-60 filter contrast-125">
                <!-- Scanner Grid overlay -->
                <div class="absolute inset-0 bg-gradient-to-b from-transparent via-gold-500/20 to-transparent scanner-line"></div>
                <div class="absolute inset-0 border border-gold-500/50 rounded-2xl pointer-events-none"></div>
                <div class="absolute inset-4 border border-dashed border-gold-400/30 rounded-xl pointer-events-none"></div>
                <div class="absolute inset-0 flex items-center justify-center">
                    <div class="w-12 h-12 rounded-full bg-mystic-900/80 border border-gold-400 flex items-center justify-center text-gold-400 animate-spin">
                        <i class="fa-solid fa-crosshairs"></i>
                    </div>
                </div>
            </div>

            <div class="space-y-3 max-w-md mx-auto">
                <h3 id="loading-status-title" class="cinzel-font text-2xl font-bold text-gold-400">손금 및 지문 패턴 스캔 중...</h3>
                <p id="loading-status-desc" class="text-sm text-gray-300">생명선, 두뇌선, 감정선 및 운명선 위치를 정밀 매핑하고 있습니다.</p>
                <div class="w-full bg-mystic-800 rounded-full h-2.5 overflow-hidden border border-gold-500/30 mt-4">
                    <div id="loading-progress" class="bg-gradient-to-r from-gold-600 to-amber-300 h-2.5 rounded-full transition-all duration-300" style="width: 0%"></div>
                </div>
            </div>
        </section>

        <!-- STEP 3: Analysis Report Result Screen (Hidden initially) -->
        <section id="result-section" class="hidden space-y-8">
            
            <!-- Report Header Card -->
            <div class="glass-panel rounded-3xl p-6 sm:p-8 glow-gold relative overflow-hidden flex flex-col md:flex-row items-center justify-between gap-6">
                <div class="absolute top-0 right-0 w-64 h-64 bg-gold-500/10 rounded-full blur-3xl pointer-events-none"></div>
                
                <div class="flex items-center space-x-5">
                    <div class="relative w-24 h-24 sm:w-28 sm:h-28 rounded-2xl overflow-hidden border-2 border-gold-400 glow-gold flex-shrink-0">
                        <img id="result-img" src="" alt="Analyzed Palm" class="w-full h-full object-cover">
                        <div class="absolute inset-0 bg-gold-500/15 mix-blend-overlay"></div>
                    </div>
                    <div class="space-y-1.5">
                        <div class="inline-flex items-center px-2.5 py-0.5 rounded-md text-[11px] font-semibold bg-gold-500/20 text-gold-400 border border-gold-500/30">
                            <i class="fa-solid fa-star mr-1"></i> 종합 운세 등급
                        </div>
                        <h2 id="report-title" class="cinzel-font text-2xl sm:text-3xl font-bold text-white">천생운기(天生運氣)형 손금</h2>
                        <p id="report-subtitle" class="text-xs sm:text-sm text-gray-300">균형 잡힌 4대 주선과 강인한 생명력을 지닌 길상(吉相)</p>
                    </div>
                </div>

                <div class="flex flex-row md:flex-col gap-2 w-full md:w-auto">
                    <button onclick="shareReport()" class="flex-1 md:flex-none px-5 py-2.5 bg-mystic-800 hover:bg-mystic-700 border border-gold-500/40 text-gold-400 text-xs font-bold rounded-xl transition-all flex items-center justify-center space-x-2">
                        <i class="fa-solid fa-share-nodes"></i>
                        <span>리포트 공유</span>
                    </button>
                    <button onclick="resetApp()" class="flex-1 md:flex-none px-5 py-2.5 bg-gradient-to-r from-gold-600 to-amber-500 hover:brightness-110 text-mystic-900 text-xs font-bold rounded-xl transition-all flex items-center justify-center space-x-2 shadow-lg">
                        <i class="fa-solid fa-rotate-right"></i>
                        <span>다른 손금 보기</span>
                    </button>
                </div>
            </div>

            <!-- Summary Badges Grid -->
            <div class="grid grid-cols-2 sm:grid-cols-4 gap-4">
                <div class="glass-panel rounded-2xl p-4 text-center space-y-1 border-gold-500/20">
                    <div class="text-xs text-gray-400">기본 체질</div>
                    <div id="badge-vitality" class="text-sm font-bold text-amber-300">강건 활력형</div>
                </div>
                <div class="glass-panel rounded-2xl p-4 text-center space-y-1 border-gold-500/20">
                    <div class="text-xs text-gray-400">지능 및 성향</div>
                    <div id="badge-mind" class="text-sm font-bold text-amber-300">직관 통찰형</div>
                </div>
                <div class="glass-panel rounded-2xl p-4 text-center space-y-1 border-gold-500/20">
                    <div class="text-xs text-gray-400">애정 및 대인</div>
                    <div id="badge-heart" class="text-sm font-bold text-amber-300">깊은 공감형</div>
                </div>
                <div class="glass-panel rounded-2xl p-4 text-center space-y-1 border-gold-500/20">
                    <div class="text-xs text-gray-400">성취 및 재물</div>
                    <div id="badge-fate" class="text-sm font-bold text-amber-300">대기만성형</div>
                </div>
            </div>

            <!-- Detailed Cards Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                
                <!-- Life Line Card -->
                <div class="glass-panel rounded-3xl p-6 space-y-4 border-gold-500/20 relative overflow-hidden group hover:border-gold-500/40 transition-all">
                    <div class="flex items-center justify-between">
                        <div class="flex items-center space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-red-500/15 text-red-400 flex items-center justify-center border border-red-500/30">
                                <i class="fa-solid fa-heart-pulse"></i>
                            </div>
                            <div>
                                <h4 class="font-bold text-white text-base">생명선 (Life Line)</h4>
                                <p class="text-xs text-red-400 font-medium">활력, 건강, 체력 지수</p>
                            </div>
                        </div>
                        <span id="score-life" class="text-xs font-bold px-2.5 py-1 rounded-full bg-red-500/20 text-red-300 border border-red-500/30">92점</span>
                    </div>
                    <p id="desc-life" class="text-xs sm:text-sm text-gray-300 leading-relaxed">
                        엄지손가락과 검지 사이에서 시작해 손바닥 아래로 곡선을 그리며 뻗어가는 선입니다. 깊고 선명하게 이어져 있어 강인한 면역력과 지치지 않는 체력을 상징합니다. 스트레스 관리에 유의하면 평생 활기찬 삶을 누릴 수 있습니다.
                    </p>
                </div>

                <!-- Head Line Card -->
                <div class="glass-panel rounded-3xl p-6 space-y-4 border-gold-500/20 relative overflow-hidden group hover:border-gold-500/40 transition-all">
                    <div class="flex items-center justify-between">
                        <div class="flex items-center space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-blue-500/15 text-blue-400 flex items-center justify-center border border-blue-500/30">
                                <i class="fa-solid fa-brain"></i>
                            </div>
                            <div>
                                <h4 class="font-bold text-white text-base">두뇌선 (Head Line)</h4>
                                <p class="text-xs text-blue-400 font-medium">지적 능력, 사고방식, 적성</p>
                            </div>
                        </div>
                        <span id="score-head" class="text-xs font-bold px-2.5 py-1 rounded-full bg-blue-500/20 text-blue-300 border border-blue-500/30">88점</span>
                    </div>
                    <p id="desc-head" class="text-xs sm:text-sm text-gray-300 leading-relaxed">
                        논리적 사고와 창의력을 관장하는 선입니다. 약간 아래쪽으로 부드럽게 뻗어 있어 예술적 감각과 현실적 분석력을 동시에 지니고 있습니다. 기획, 연구, 컨설팅 분야에서 뛰어난 두각을 나타낼 수 있습니다.
                    </p>
                </div>

                <!-- Heart Line Card -->
                <div class="glass-panel rounded-3xl p-6 space-y-4 border-gold-500/20 relative overflow-hidden group hover:border-gold-500/40 transition-all">
                    <div class="flex items-center justify-between">
                        <div class="flex items-center space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-pink-500/15 text-pink-400 flex items-center justify-center border border-pink-500/30">
                                <i class="fa-solid fa-heart"></i>
                            </div>
                            <div>
                                <h4 class="font-bold text-white text-base">감정선 (Heart Line)</h4>
                                <p class="text-xs text-pink-400 font-medium">애정운, 대인관계, 감성</p>
                            </div>
                        </div>
                        <span id="score-heart" class="text-xs font-bold px-2.5 py-1 rounded-full bg-pink-500/20 text-pink-300 border border-pink-500/30">90점</span>
                    </div>
                    <p id="desc-heart" class="text-xs sm:text-sm text-gray-300 leading-relaxed">
                        새끼손가락 아래에서 시작해 검지나 중지 방향으로 향하는 선입니다. 타인에 대한 공감 능력이 매우 뛰어나며, 깊고 진실한 인간관계를 형성합니다. 로맨틱하면서도 이성적인 판단력을 함께 겸비한 상입니다.
                    </p>
                </div>

                <!-- Fate Line Card -->
                <div class="glass-panel rounded-3xl p-6 space-y-4 border-gold-500/20 relative overflow-hidden group hover:border-gold-500/40 transition-all">
                    <div class="flex items-center justify-between">
                        <div class="flex items-center space-x-3">
                            <div class="w-10 h-10 rounded-xl bg-amber-500/15 text-amber-400 flex items-center justify-center border border-amber-500/30">
                                <i class="fa-solid fa-coins"></i>
                            </div>
                            <div>
                                <h4 class="font-bold text-white text-base">운명선 (Fate Line)</h4>
                                <p class="text-xs text-amber-400 font-medium">사회적 성취, 재물운, 커리어</p>
                            </div>
                        </div>
                        <span id="score-fate" class="text-xs font-bold px-2.5 py-1 rounded-full bg-amber-500/20 text-amber-300 border border-amber-500/30">94점</span>
                    </div>
                    <p id="desc-fate" class="text-xs sm:text-sm text-gray-300 leading-relaxed">
                        손바닥 중앙을 가로질러 위로 향하는 선입니다. 중년 이후 커리어에서 큰 도약을 이루며 재물이 안정적으로 축적되는 길상입니다. 주체적인 목표 의식을 갖고 정진할 때 더 큰 행운이 따릅니다.
                    </p>
                </div>

            </div>

            <!-- Eastern Divination & AI Synergy Card -->
            <div class="glass-panel rounded-3xl p-6 sm:p-8 border-gold-500/30 bg-gradient-to-br from-mystic-800/80 to-mystic-900/90 relative overflow-hidden">
                <div class="absolute top-0 right-0 transform translate-x-8 -translate-y-8 w-40 h-40 bg-gold-500/10 rounded-full blur-2xl"></div>
                <div class="flex items-start space-x-4">
                    <div class="w-12 h-12 rounded-2xl bg-gold-500/20 text-gold-400 flex items-center justify-center text-xl border border-gold-500/40 flex-shrink-0 mt-1">
                        <i class="fa-solid fa-scroll"></i>
                    </div>
                    <div class="space-y-3">
                        <h4 class="cinzel-font text-xl font-bold text-gold-400">동서양 관상학 융합 종합 조언</h4>
                        <p id="ai-synthesis-text" class="text-xs sm:text-sm text-gray-300 leading-relaxed">
                            동양의 오행(五行) 관상학과 서양의 전통 손금학을 인공지능이 종합 분석한 결과, 현재 귀하의 손금은 재물과 명예운이 상승하는 대운의 시기에 진입해 있습니다. 주변 사람들과의 협력을 중시하고 새로운 도전(창업, 이직, 자격증 취득 등)을 시도하기에 매우 최적의 타이밍입니다.
                        </p>
                        <div class="pt-2 flex flex-wrap gap-2 text-xs">
                            <span class="px-3 py-1 rounded-lg bg-mystic-700 text-gold-300 border border-gold-500/20"><i class="fa-solid fa-compass mr-1"></i> 행운의 방향: 동남쪽</span>
                            <span class="px-3 py-1 rounded-lg bg-mystic-700 text-gold-300 border border-gold-500/20"><i class="fa-solid fa-gem mr-1"></i> 행운의 아이템: 골드 액세서리</span>
                            <span class="px-3 py-1 rounded-lg bg-mystic-700 text-gold-300 border border-gold-500/20"><i class="fa-solid fa-calendar-check mr-1"></i> 최고 전성기: 다가오는 하반기</span>
                        </div>
                    </div>
                </div>
            </div>

        </section>

    </main>

    <!-- Camera Modal Overlay -->
    <div id="camera-modal" class="fixed inset-0 z-50 bg-mystic-950/90 backdrop-blur-md hidden flex flex-col items-center justify-center p-4">
        <div class="max-w-md w-full glass-panel rounded-3xl p-6 space-y-4 glow-gold relative">
            <div class="flex items-center justify-between">
                <h3 class="cinzel-font font-bold text-white text-lg flex items-center space-x-2">
                    <i class="fa-solid fa-camera text-gold-400"></i>
                    <span>손바닥 실시간 촬영</span>
                </h3>
                <button onclick="closeCameraModal()" class="w-8 h-8 rounded-full bg-mystic-800 hover:bg-mystic-700 text-gray-300 flex items-center justify-center transition-all">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>
            
            <div class="relative w-full aspect-[3/4] bg-mystic-900 rounded-2xl overflow-hidden border border-gold-500/30 flex items-center justify-center">
                <video id="camera-video" autoplay playsinline class="w-full h-full object-cover"></video>
                <canvas id="camera-canvas" class="hidden"></canvas>
                <!-- Guide Frame Overlay -->
                <div class="absolute inset-8 border-2 border-dashed border-gold-400/50 rounded-2xl pointer-events-none flex items-center justify-center">
                    <span class="bg-mystic-900/80 px-3 py-1 rounded-full text-[11px] text-gold-400 border border-gold-500/30">이 안에 손바닥을 위치시키세요</span>
                </div>
            </div>

            <div class="flex space-x-3">
                <button onclick="closeCameraModal()" class="flex-1 py-3 rounded-xl bg-mystic-800 hover:bg-mystic-700 text-gray-300 text-xs font-semibold transition-all">
                    취소
                </button>
                <button onclick="captureCameraPhoto()" class="flex-1 py-3 rounded-xl bg-gradient-to-r from-gold-600 to-amber-500 hover:brightness-110 text-mystic-900 text-xs font-bold transition-all shadow-lg flex items-center justify-center space-x-2">
                    <i class="fa-solid fa-camera-rotate"></i>
                    <span>촬영하기</span>
                </button>
            </div>
        </div>
    </div>

    <!-- Message / Notification Toast -->
    <div id="toast-message" class="fixed bottom-6 right-6 z-50 transform translate-y-20 opacity-0 transition-all duration-300 bg-mystic-800 border border-gold-500/40 text-white px-4 py-3 rounded-2xl shadow-2xl flex items-center space-x-3 text-sm">
        <i class="fa-solid fa-circle-check text-gold-400 text-lg"></i>
        <span id="toast-text">알림 메시지입니다.</span>
    </div>

    <!-- Footer -->
    <footer class="w-full border-t border-gold-500/10 py-6 text-center text-xs text-gray-500 bg-mystic-900/50">
        <p>© 2026 PalmAura AI Mystical Palmistry. All rights reserved.</p>
        <p class="mt-1">본 서비스의 손금 분석 및 사주 해석은 AI 시뮬레이션 기반의 오락 및 참고용 콘텐츠입니다.</p>
    </footer>

    <!-- JavaScript Application Logic -->
    <script>
        let selectedImageDataUrl = '';
        let videoStream = null;

        // DOM Elements
        const uploadSection = document.getElementById('upload-section');
        const loadingSection = document.getElementById('loading-section');
        const resultSection = document.getElementById('result-section');
        const previewContainer = document.getElementById('preview-container');
        const previewImg = document.getElementById('preview-img');
        const scanningImg = document.getElementById('scanning-img');
        const resultImg = document.getElementById('result-img');
        const fileNameEl = document.getElementById('file-name');
        const fileInput = document.getElementById('file-input');
        const cameraModal = document.getElementById('camera-modal');
        const cameraVideo = document.getElementById('camera-video');
        const cameraCanvas = document.getElementById('camera-canvas');
        const loadingProgress = document.getElementById('loading-progress');
        const loadingStatusTitle = document.getElementById('loading-status-title');
        const loadingStatusDesc = document.getElementById('loading-status-desc');

        // File Input Change Event
        fileInput.addEventListener('change', function(e) {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(event) {
                    selectedImageDataUrl = event.target.result;
                    previewImg.src = selectedImageDataUrl;
                    scanningImg.src = selectedImageDataUrl;
                    resultImg.src = selectedImageDataUrl;
                    fileNameEl.textContent = file.name;
                    previewContainer.classList.remove('hidden');
                    showToast('손바닥 이미지가 성공적으로 로드되었습니다.');
                };
                reader.readAsDataURL(file);
            }
        });

        // Clear Selected Image
        function clearSelectedImage() {
            selectedImageDataUrl = '';
            fileInput.value = '';
            previewContainer.classList.add('hidden');
            showToast('이미지가 초기화되었습니다.');
        }

        // Camera Modal Handlers
        async function openCameraModal() {
            cameraModal.classList.remove('hidden');
            try {
                videoStream = await navigator.mediaDevices.getUserMedia({ 
                    video: { facingMode: 'user', width: { ideal: 1280 }, height: { ideal: 720 } }, 
                    audio: false 
                });
                cameraVideo.srcObject = videoStream;
            } catch (err) {
                console.error("Camera access error:", err);
                closeCameraModal();
                showToast('카메라 권한을 허용해주시거나 파일 업로드를 이용해주세요.');
            }
        }

        function closeCameraModal() {
            if (videoStream) {
                videoStream.getTracks().forEach(track => track.stop());
                videoStream = null;
            }
            cameraModal.classList.add('hidden');
        }

        function captureCameraPhoto() {
            if (!cameraVideo.srcObject) return;
            const width = cameraVideo.videoWidth || 640;
            const height = cameraVideo.videoHeight || 480;
            cameraCanvas.width = width;
            cameraCanvas.height = height;
            const ctx = cameraCanvas.getContext('2d');
            ctx.drawImage(cameraVideo, 0, 0, width, height);

            selectedImageDataUrl = cameraCanvas.toDataURL('image/png');
            previewImg.src = selectedImageDataUrl;
            scanningImg.src = selectedImageDataUrl;
            resultImg.src = selectedImageDataUrl;
            fileNameEl.textContent = '카메라_촬영_손바닥.png';
            previewContainer.classList.remove('hidden');

            closeCameraModal();
            showToast('카메라 촬영이 완료되었습니다.');
        }

        // Start Analysis Simulation with Gemini AI vibe
        function startAnalysis() {
            if (!selectedImageDataUrl) {
                showToast('먼저 손바닥 사진을 업로드하거나 촬영해주세요.');
                return;
            }

            uploadSection.classList.add('hidden');
            loadingSection.classList.remove('hidden');
            resultSection.classList.add('hidden');

            let progress = 0;
            const statusSteps = [
                { percent: 20, title: "손바닥 이미지 특징 추출 중...", desc: "피부 결 및 주요 주름의 밀도를 측정합니다." },
                { percent: 45, title: "생명선 및 두뇌선 정밀 매핑...", desc: "체력 지수와 사고 패턴의 깊이를 분석하고 있습니다." },
                { percent: 75, title: "감정선 및 운명선 AI 시뮬레이션...", desc: "대인관계 성향과 미래 성취 잠재력을 계산 중입니다." },
                { percent: 100, title: "동서양 관상학 종합 리포트 생성 완료", desc: "신비로운 풀이 리포트가 완성되었습니다." }
            ];

            let stepIndex = 0;
            const interval = setInterval(() => {
                progress += 2;
                loadingProgress.style.width = progress + '%';

                if (progress >= statusSteps[stepIndex].percent && stepIndex < statusSteps.length - 1) {
                    stepIndex++;
                    loadingStatusTitle.textContent = statusSteps[stepIndex].title;
                    loadingStatusDesc.textContent = statusSteps[stepIndex].desc;
                }

                if (progress >= 100) {
                    clearInterval(interval);
                    setTimeout(() => {
                        loadingSection.classList.add('hidden');
                        resultSection.classList.remove('hidden');
                        generateRandomizedReport();
                        window.scrollTo({ top: 0, behavior: 'smooth' });
                        showToast('손금 정밀 분석 리포트가 완성되었습니다!');
                    }, 500);
                }
            }, 50);
        }

        // Randomize or customize report content for dynamic feel
        function generateRandomizedReport() {
            const reportTitles = [
                { title: "천생운기(天生運氣)형 손금", subtitle: "균형 잡힌 4대 주선과 강인한 생명력을 지닌 길상(吉相)" },
                { title: "대기만성(大器晩成)형 손금", subtitle: "시간이 지날수록 빛을 발하는 굳건한 운명선과 재물상" },
                { title: "천재직관(天才直觀)형 손금", subtitle: "통찰력과 창의적 두뇌선이 돋보이는 예술 및 기획 리더형" },
                { title: "귀인상조(貴人相助)형 손금", subtitle: "주변의 깊은 신뢰와 사랑을 받으며 복이 따르는 온화한 길상" }
            ];

            const selected = reportTitles[Math.floor(Math.random() * reportTitles.length)];
            document.getElementById('report-title').textContent = selected.title;
            document.getElementById('report-subtitle').textContent = selected.subtitle;

            // Randomize scores slightly
            document.getElementById('score-life').textContent = (88 + Math.floor(Math.random() * 10)) + '점';
            document.getElementById('score-head').textContent = (85 + Math.floor(Math.random() * 12)) + '점';
            document.getElementById('score-heart').textContent = (87 + Math.floor(Math.random() * 11)) + '점';
            document.getElementById('score-fate').textContent = (90 + Math.floor(Math.random() * 9)) + '점';
        }

        // Reset App
        function resetApp() {
            clearSelectedImage();
            resultSection.classList.add('hidden');
            loadingSection.classList.add('hidden');
            uploadSection.classList.remove('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Share Report
        function shareReport() {
            if (navigator.clipboard) {
                navigator.clipboard.writeText(window.location.href).then(() => {
                    showToast('리포트 링크가 클립보드에 복사되었습니다!');
                }).catch(() => {
                    showToast('링크 복사에 실패했습니다.');
                });
            } else {
                showToast('현재 브라우저에서는 공유 기능을 지원하지 않습니다.');
            }
        }

        // Toast Notification Helper
        function showToast(message) {
            const toast = document.getElementById('toast-message');
            const toastText = document.getElementById('toast-text');
            toastText.textContent = message;
            toast.classList.remove('translate-y-20', 'opacity-0');
            setTimeout(() => {
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 3000);
        }
    </script>
</body>
</html>
