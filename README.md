<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>길 잃은 나누를 데려다주세요 - CJ도너스캠프</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'cj-orange': '#F26522',
                        'cj-coral': '#FF5A79',
                        'cj-coral-light': '#FFF0F3',
                        'cj-bg': '#FAF8F5',
                        'cj-card': '#FFFFFF',
                        'cj-text-dark': '#2B2B2B',
                        'cj-text-gray': '#666666'
                    },
                    fontFamily: {
                        sans: ['Pretendard', '-apple-system', 'BlinkMacSystemFont', 'system-ui', 'Roboto', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css');
        body {
            font-family: 'Pretendard', sans-serif;
            background-color: #FAF8F5;
            color: #2B2B2B;
            -webkit-tap-highlight-color: transparent;
        }
        .pulse-subtle {
            animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }
        .custom-shadow {
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.05), 0 8px 10px -6px rgba(0, 0, 0, 0.03);
        }
    </style>
</head>
<body class="flex justify-center min-h-screen">

    <!-- Mobile Container -->
    <div class="w-full max-w-md bg-[#FAF8F5] min-h-screen flex flex-col justify-between relative pb-10 shadow-2xl border-x border-gray-100">

        <!-- Top Header -->
        <header class="sticky top-0 bg-[#FAF8F5]/90 backdrop-blur-md z-50 px-5 py-4 flex items-center justify-between border-b border-gray-100/50">
            <div class="flex items-center space-x-2">
                <div class="w-7 h-7 rounded-full bg-cj-orange flex items-center justify-center text-white font-bold text-xs">
                    <i class="fa-solid fa-heart"></i>
                </div>
                <span class="font-bold text-sm text-cj-text-dark tracking-tight">길 잃은 나누를 데려다주세요</span>
            </div>
            <button class="text-cj-text-dark text-xl p-1" aria-label="메뉴">
                <i class="fa-solid fa-bars"></i>
            </button>
        </header>

        <!-- Dynamic Content Area -->
        <main id="app-content" class="flex-grow flex flex-col px-5 pt-2">
            <!-- Content rendered via JS -->
        </main>

        <!-- Footer Notice -->
        <footer class="mt-8 text-center text-xs text-gray-400 py-4 border-t border-gray-200/50 flex items-center justify-center gap-1">
            <i class="fa-solid fa-heart text-cj-coral text-[10px]"></i>
            <span>나눔으로 아이들의 세상을 밝게 만들어주세요!</span>
        </footer>

    </div>

    <!-- VIP Invitation Modal -->
    <div id="invitation-modal" class="fixed inset-0 bg-black/70 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl p-6 w-full max-w-sm text-center relative custom-shadow transform transition-all duration-300 scale-95 opacity-0" id="modal-card">
            <button onclick="closeModal()" class="absolute top-4 right-4 text-gray-400 hover:text-gray-600 text-lg">
                <i class="fa-solid fa-xmark"></i>
            </button>
            
            <div class="inline-block bg-amber-100 text-amber-700 font-bold text-xs px-3 py-1 rounded-full mb-3">
                ✨ CJ DONORS CAMP SHOWCASE
            </div>
            
            <h3 class="text-xl font-extrabold text-gray-800 mb-1">VIP INVITATION</h3>
            <p class="text-xs text-cj-orange font-bold mb-4">나누의 완벽한 길잡이가 되어주신 하고잡이님을 초대합니다!</p>
            
            <div class="bg-gradient-to-br from-amber-50 to-orange-50 border border-orange-200 rounded-2xl p-5 mb-5 text-left relative overflow-hidden">
                <div class="absolute -right-4 -bottom-4 opacity-10 text-6xl text-cj-orange">
                    <i class="fa-solid fa-ticket"></i>
                </div>
                <p class="text-xs font-semibold text-gray-500 mb-1">To. 길잡이님</p>
                <p class="text-sm text-gray-800 font-medium leading-relaxed mb-4">
                    보내주신 따뜻한 응원 덕분에 무대에 불이 켜졌습니다! 아이들의 눈부신 성장을 현장에서 직접 확인해 보세요.
                </p>
                <div class="space-y-1.5 text-xs text-gray-700 bg-white/80 p-3 rounded-xl border border-orange-100">
                    <p><strong class="text-gray-900">일시:</strong> 2026년 9월 12일 (토) 14:00</p>
                    <p><strong class="text-gray-900">장소:</strong> CJ도너스캠프 쇼케이스 홀</p>
                </div>
            </div>

            <div class="space-y-2">
                <button onclick="alert('초대 이미지가 저장되었습니다!')" class="w-full py-3 bg-cj-orange text-white font-bold rounded-2xl text-sm shadow-md hover:bg-orange-600 transition flex items-center justify-center gap-2">
                    <i class="fa-solid fa-download"></i> 📸 내 초대장 이미지로 저장하기
                </button>
                <button onclick="copyInviteLink()" class="w-full py-3 bg-gray-100 text-gray-700 font-bold rounded-2xl text-sm hover:bg-gray-200 transition flex items-center justify-center gap-2">
                    <i class="fa-solid fa-share-nodes"></i> 💬 링크 공유하기
                </button>
                <button onclick="goToRewardStep()" class="w-full py-3 bg-cj-coral text-white font-bold rounded-2xl text-sm shadow-md hover:bg-rose-600 transition flex items-center justify-center gap-2 mt-2">
                    🎁 이벤트 리워드 받으러 가기
                </button>
            </div>
        </div>
    </div>

    <script>
        // App State
        let currentState = {
            step: 1, 
            quiz1Selected: null,
            quiz2Selected: null,
            quiz3Selected: null,
            selectedCategory: 'music', 
            naniCount: 1284,
            phone: ''
        };

        const categoryData = {
            music: { 
                name: '음악', 
                icon: '🎵', 
                bg: 'bg-rose-50', 
                border: 'border-rose-200', 
                color: 'text-rose-500', 
                title: '불협화음이 아름다운 하모니가 되기까지',
                storyText: '악기 잡는 법도, 서로의 눈을 맞추는 것도 어색했던 지난 시간.<br><strong class="text-gray-800">[음악 동아리]</strong> 친구들의 첫 시작은 삐걱대는 불협화음이었습니다.',
                highlightText: '서로의 소리에 귀 기울이는 법을 배우며, 각자의 서툰 음표는 어느새 하나의 완벽한 하모니가 되었습니다.'
            },
            performance: { 
                name: '공연', 
                icon: '🎭', 
                bg: 'bg-purple-50', 
                border: 'border-purple-200', 
                color: 'text-purple-500', 
                title: '무대를 향한 숨 가쁘고 뜨거운 발걸음',
                storyText: '동선 맞추는 것조차 마음처럼 되지 않아 수없이 주저앉았던 날들.<br><strong class="text-gray-800">[공연 동아리]</strong> 친구들은 매일 밤 연습실의 불을 밝혔습니다.',
                highlightText: '안무와 대사가 하나로 맞아떨어지는 순간, 무대 위에서 펼쳐질 눈부신 환상을 준비해왔습니다.'
            },
            video: { 
                name: '영상', 
                icon: '🎬', 
                bg: 'bg-blue-50', 
                border: 'border-blue-200', 
                color: 'text-blue-500', 
                title: '렌즈 끝에 담아낸 우리들의 진짜 이야기',
                storyText: '어떤 장면을 어떻게 담아야 할지 막막했던 시나리오 회의.<br><strong class="text-gray-800">[영상 동아리]</strong> 친구들은 카메라를 들고 세상 속으로 직접 뛰어들었습니다.',
                highlightText: '편집 화면 속에서 묵묵히 컷을 이어 붙이며, 우리만의 진심 어린 시선을 영상 속에 담아냈습니다.'
            },
            cooking: { 
                name: '요리', 
                icon: '🍳', 
                bg: 'bg-amber-50', 
                border: 'border-amber-200', 
                color: 'text-amber-500', 
                title: '마음을 담아 오븐을 예열하던 시간',
                storyText: '레시피를 보며 서툴게 재료를 다듬다 손을 베이기도 했던 요리 실습실.<br><strong class="text-gray-800">[요리 동아리]</strong> 친구들의 오븐은 매일 따뜻하게 구워졌습니다.',
                highlightText: '누군가에게 행복을 전하고 싶다는 마음으로, 정성스러운 손길 끝에 달콤하고 고소한 미소가 피어났습니다.'
            }
        };

        const INSTAGRAM_URL = "https://www.instagram.com/cjdonorscamp_univ?igsh=b3Jsbzg1M3N3NTF6";
        const SURVEY_URL = "https://naver.me/G4dVvST1";

        function render() {
            const container = document.getElementById('app-content');
            container.innerHTML = '';

            switch (currentState.step) {
                case 1:
                    container.appendChild(renderStep1());
                    break;
                case 2:
                    container.appendChild(renderStep2());
                    break;
                case 3:
                    container.appendChild(renderStep3());
                    break;
                case 4:
                    container.appendChild(renderStep4());
                    break;
                case 5:
                    container.appendChild(renderStep5());
                    break;
                case 6:
                    container.appendChild(renderStep6());
                    break;
            }
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // --- STEP 1: SCREEN 1 ---
        function renderStep1() {
            const div = document.createElement('div');
            div.className = 'flex flex-col items-center text-center my-auto py-2';
            div.innerHTML = `
                <div class="mb-3">
                    <h1 class="text-3xl font-extrabold text-gray-900 leading-tight tracking-tight">
                        앗! <span class="text-cj-orange">나누가</span><br>길을 잃었어요 💦
                    </h1>
                </div>

                <p class="text-xs text-gray-600 leading-relaxed font-medium mb-4">
                    청소년들의 눈부신 성장이 기다리고 있는<br>
                    <strong class="text-gray-800">CJ도너스캠프 문화동아리 쇼케이스!</strong><br><br>
                    나누가 늦지 않게 도착할 수 있도록,<br>
                    여러분이 나누의 <span class="text-cj-orange font-bold underline decoration-amber-300 decoration-2">길잡이</span>가 되어주세요!
                </p>

                <!-- Attached Image Integration -->
                <div class="w-full max-w-[280px] my-2 relative">
                    <img src="image.png" alt="[길 잃은 나누 캐릭터]" class="w-full h-auto rounded-3xl custom-shadow border border-orange-100 object-contain mx-auto" onerror="handleImageError(this)">
                </div>

                <button onclick="goToStep(2)" class="w-full mt-5 py-4 bg-cj-orange text-white text-base font-extrabold rounded-2xl shadow-lg shadow-orange-500/20 hover:bg-orange-600 active:scale-95 transition flex items-center justify-center gap-2">
                    나누의 길을 찾아주기 <i class="fa-solid fa-chevron-right text-sm"></i>
                </button>
            `;
            return div;
        }

        function handleImageError(imgEl) {
            const parent = imgEl.parentElement;
            parent.innerHTML = `
                <div class="w-full bg-[#FAF8F5] rounded-3xl p-4 border-2 border-orange-300 custom-shadow flex flex-col items-center justify-center min-h-[260px]">
                    <div class="text-6xl mb-2">🐑💦</div>
                    <div class="bg-white p-3 rounded-xl border border-orange-300 text-center shadow-sm w-full">
                        <p class="text-xs font-bold text-gray-800">길을 잃었어요...</p>
                        <p class="text-sm font-black text-cj-orange">도와주세요! 🥺</p>
                    </div>
                </div>
            `;
        }

        // --- STEP 2: QUIZ SCREEN ---
        function renderStep2() {
            const div = document.createElement('div');
            div.className = 'flex flex-col py-2';

            const isQ1Passed = currentState.quiz1Selected === 5;
            const isQ2Passed = currentState.quiz2Selected === 3;

            let activeQuizNum = 1;
            if (isQ1Passed) activeQuizNum = 2;
            if (isQ1Passed && isQ2Passed) activeQuizNum = 3;

            div.innerHTML = `
                <!-- Progress Indicator -->
                <div class="flex items-center justify-between mb-4 bg-white p-3 rounded-2xl custom-shadow border border-gray-100">
                    <span class="text-xs font-bold text-cj-orange">STEP 02. QUIZ</span>
                    <div class="flex items-center gap-1.5">
                        <span class="w-6 h-6 rounded-full ${activeQuizNum > 1 ? 'bg-emerald-500 text-white' : 'bg-cj-orange text-white'} text-xs font-bold flex items-center justify-center">
                            ${activeQuizNum > 1 ? '<i class="fa-solid fa-check"></i>' : '1'}
                        </span>
                        <div class="w-6 h-1 rounded-full ${activeQuizNum > 1 ? 'bg-cj-orange' : 'bg-gray-200'}"></div>
                        <span class="w-6 h-6 rounded-full ${activeQuizNum > 2 ? 'bg-emerald-500 text-white' : (activeQuizNum === 2 ? 'bg-cj-orange text-white' : 'bg-gray-200 text-gray-500')} text-xs font-bold flex items-center justify-center">
                            ${activeQuizNum > 2 ? '<i class="fa-solid fa-check"></i>' : '2'}
                        </span>
                        <div class="w-6 h-1 rounded-full ${activeQuizNum > 2 ? 'bg-cj-orange' : 'bg-gray-200'}"></div>
                        <span class="w-6 h-6 rounded-full ${activeQuizNum === 3 ? 'bg-cj-orange text-white' : 'bg-gray-200 text-gray-500'} text-xs font-bold flex items-center justify-center">3</span>
                    </div>
                </div>

                <div class="text-center mb-5">
                    <h2 class="text-xl font-bold text-gray-900 mb-1">“나누와 함께 올바른 길을 찾아주세요!”</h2>
                    <p class="text-xs text-gray-500">정답을 선택하면 나누가 목적지로 나아갑니다 🐾</p>
                </div>

                ${activeQuizNum === 1 ? `
                <!-- Quiz 1 -->
                <div class="bg-white p-5 rounded-3xl custom-shadow border border-amber-100 mb-4">
                    <div class="inline-block bg-amber-100 text-amber-800 font-bold text-xs px-2.5 py-1 rounded-lg mb-3">Q1.</div>
                    <p class="text-sm font-bold text-gray-800 leading-relaxed mb-5">
                        다음 보기 중 ‘CJ도너스캠프 문화동아리’를 적절하게 설명하지 못하는 보기 하나를 골라 주세요.
                    </p>
                    <div class="space-y-2.5">
                        <button onclick="handleQuiz1(1, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-xs sm:text-sm font-semibold rounded-2xl border border-gray-200 text-left transition">
                            ① CJ그룹의 대표적인 사회공헌사업 중 하나입니다.
                        </button>
                        <button onclick="handleQuiz1(2, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-xs sm:text-sm font-semibold rounded-2xl border border-gray-200 text-left transition">
                            ② 아동·청소년들에게 성장단계별 문화 활동을 지원합니다.
                        </button>
                        <button onclick="handleQuiz1(3, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-xs sm:text-sm font-semibold rounded-2xl border border-gray-200 text-left transition">
                            ③ 청소년이 스스로 기획부터 발표까지 전 과정을 창작하도록 돕습니다.
                        </button>
                        <button onclick="handleQuiz1(4, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-xs sm:text-sm font-semibold rounded-2xl border border-gray-200 text-left transition">
                            ④ 매해 11월마다 청소년들이 제작한 창작물을 발표하는 쇼케이스를 개최합니다.
                        </button>
                        <button onclick="handleQuiz1(5, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-xs sm:text-sm font-semibold rounded-2xl border border-gray-200 text-left transition">
                            ⑤ 청소년은 어른의 응원을 받아도 부끄러워하기 때문에 쇼케이스에 가지 않아도 됩니다.
                        </button>
                    </div>
                </div>
                ` : (activeQuizNum === 2 ? `
                <!-- Quiz 2 -->
                <div class="bg-white p-5 rounded-3xl custom-shadow border border-amber-100 mb-4">
                    <div class="inline-block bg-amber-100 text-amber-800 font-bold text-xs px-2.5 py-1 rounded-lg mb-3">Q2.</div>
                    <p class="text-sm font-bold text-gray-800 leading-relaxed mb-5">
                        아이들이 오늘 쇼케이스 무대에 오르기까지, 자신의 관심 분야를 탐색하고 연습하며 땀 흘린 시간은 무려 [<span class="text-cj-orange font-extrabold"> ? </span>]개월입니다.
                    </p>
                    <div class="space-y-2.5">
                        <button onclick="handleQuiz2(1, this)" class="w-full py-3.5 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-sm font-semibold rounded-2xl border border-gray-200 text-left transition">
                            ① 1개월
                        </button>
                        <button onclick="handleQuiz2(2, this)" class="w-full py-3.5 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-sm font-semibold rounded-2xl border border-gray-200 text-left transition">
                            ② 3개월
                        </button>
                        <button onclick="handleQuiz2(3, this)" class="w-full py-3.5 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-sm font-semibold rounded-2xl border border-gray-200 text-left transition">
                            ③ 8개월
                        </button>
                    </div>
                </div>
                ` : `
                <!-- Quiz 3 -->
                <div class="bg-white p-5 rounded-3xl custom-shadow border border-amber-100 mb-4">
                    <div class="inline-block bg-amber-100 text-amber-800 font-bold text-xs px-2.5 py-1 rounded-lg mb-3">Q3.</div>
                    <p class="text-sm font-bold text-gray-800 leading-relaxed mb-5">
                        오늘 나누가 찾아가야 할 문화동아리의 분야가 <span class="text-cj-coral underline">아닌 것</span>은 무엇일까요?
                    </p>
                    <div class="space-y-2.5">
                        <button onclick="handleQuiz3(1, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-sm font-semibold rounded-2xl border border-gray-200 text-left">
                            ① 음악
                        </button>
                        <button onclick="handleQuiz3(2, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-sm font-semibold rounded-2xl border border-gray-200 text-left">
                            ② 공연
                        </button>
                        <button onclick="handleQuiz3(3, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-sm font-semibold rounded-2xl border border-gray-200 text-left">
                            ③ 요리
                        </button>
                        <button onclick="handleQuiz3(4, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-sm font-semibold rounded-2xl border border-gray-200 text-left">
                            ④ 코딩
                        </button>
                        <button onclick="handleQuiz3(5, this)" class="w-full py-3 px-4 bg-gray-50 hover:bg-gray-100 text-gray-700 text-sm font-semibold rounded-2xl border border-gray-200 text-left">
                            ⑤ 영상미디어
                        </button>
                    </div>
                </div>
                `)}

                <div class="bg-orange-50/80 p-4 rounded-2xl border border-orange-100 flex items-center gap-3">
                    <div class="text-2xl">🐾</div>
                    <p class="text-xs text-orange-800 leading-snug">
                        보기를 선택하면 정답 여부를 알려드립니다! (틀려도 언제든 다시 선택할 수 있어요)
                    </p>
                </div>
            `;
            return div;
        }

        function handleQuiz1(option, btnEl) {
            if (option === 5) {
                btnEl.className = "w-full py-3 px-4 bg-emerald-50 text-emerald-700 border-2 border-emerald-500 text-xs font-extrabold rounded-2xl text-left transition flex justify-between items-center";
                btnEl.innerHTML = "<span>⑤ 청소년은 어른의 응원을 받아도 부끄러워하기 때문에 쇼케이스에 가지 않아도 됩니다.</span> <i class='fa-solid fa-circle-check text-emerald-500 text-lg'></i>";
                
                setTimeout(() => {
                    alert("딩동댕! 나누가 한 발짝 앞으로 나아갑니다 🐾");
                    currentState.quiz1Selected = 5;
                    render();
                }, 300);
            } else {
                btnEl.className = "w-full py-3 px-4 bg-rose-50 text-rose-600 border-2 border-rose-300 text-xs font-semibold rounded-2xl text-left transition";
                setTimeout(() => {
                    alert("아쉬워요! 올바른 설명이 아닌 보기를 다시 선택해 보세요 🐾");
                }, 200);
            }
        }

        function handleQuiz2(option, btnEl) {
            if (option === 3) {
                btnEl.className = "w-full py-3.5 px-4 bg-emerald-50 text-emerald-700 border-2 border-emerald-500 text-sm font-extrabold rounded-2xl text-left transition flex justify-between items-center";
                btnEl.innerHTML = "<span>③ 8개월</span> <i class='fa-solid fa-circle-check text-emerald-500 text-lg'></i>";
                
                setTimeout(() => {
                    alert("딩동댕! 나누가 또 한 발짝 앞으로 나아갑니다 🐾");
                    currentState.quiz2Selected = 3;
                    render();
                }, 300);
            } else {
                btnEl.className = "w-full py-3.5 px-4 bg-rose-50 text-rose-600 border-2 border-rose-300 text-sm font-semibold rounded-2xl text-left transition";
                setTimeout(() => {
                    alert("아쉬워요! 다시 한 번 선택해 보세요 🐾");
                }, 200);
            }
        }

        function handleQuiz3(option, btnEl) {
            if (option === 4) {
                btnEl.className = "w-full py-3 px-4 bg-emerald-50 text-emerald-700 border-2 border-emerald-500 text-sm font-extrabold rounded-2xl text-left flex justify-between items-center";
                btnEl.innerHTML = "<span>④ 코딩</span> <i class='fa-solid fa-circle-check text-emerald-500 text-lg'></i>";
                
                setTimeout(() => {
                    alert("딩동댕! 나누가 마지막 발걸음을 옮겼어요 🐾\n\n와아! 길잡이님 덕분에 나누가 무사히 목적지에 도착했어요! 🎉");
                    currentState.quiz3Selected = 4;
                    goToStep(3);
                }, 300);
            } else {
                btnEl.className = "w-full py-3 px-4 bg-rose-50 text-rose-600 border-2 border-rose-300 text-sm font-semibold rounded-2xl text-left";
                setTimeout(() => {
                    alert("아쉬워요! 해당 분야는 아이들이 열심히 준비한 핵심 문화동아리입니다. 다시 선택해 보세요!");
                }, 200);
            }
        }

        // --- STEP 3: FIND (FLAG SELECT) ---
        function renderStep3() {
            const div = document.createElement('div');
            div.className = 'flex flex-col py-2 text-center';

            div.innerHTML = `
                <div class="bg-amber-100/80 text-amber-800 text-xs font-bold py-1 px-3 rounded-full inline-block mx-auto mb-3">
                    🎉 목적지 도착!
                </div>
                <h2 class="text-xl font-extrabold text-gray-900 mb-2">
                    목적지 도착! 네 개의 깃발이 펄럭이고 있어요 🚩
                </h2>
                <p class="text-xs text-gray-600 leading-relaxed mb-6">
                    이곳에는 열심히 달려온<br>
                    네 분야의 동아리 친구들이 기다리고 있습니다.<br>
                    <strong class="text-gray-800">어떤 친구들의 깃발을 펼쳐볼까요?</strong>
                </p>

                <!-- 4 Flag Choice Grid -->
                <div class="grid grid-cols-2 gap-3 mb-6">
                    <button onclick="selectCategory('music')" class="bg-white p-5 rounded-3xl border-2 border-rose-200 hover:border-rose-500 custom-shadow flex flex-col items-center justify-center transition transform active:scale-95 group">
                        <div class="text-4xl mb-2 group-hover:scale-110 transition">🎵</div>
                        <span class="font-extrabold text-sm text-gray-800 mb-1">🎵 음악 깃발</span>
                        <span class="text-[10px] text-gray-400">하모니 음악 동아리</span>
                    </button>

                    <button onclick="selectCategory('performance')" class="bg-white p-5 rounded-3xl border-2 border-purple-200 hover:border-purple-500 custom-shadow flex flex-col items-center justify-center transition transform active:scale-95 group">
                        <div class="text-4xl mb-2 group-hover:scale-110 transition">🎭</div>
                        <span class="font-extrabold text-sm text-gray-800 mb-1">🎭 공연 깃발</span>
                        <span class="text-[10px] text-gray-400">연극·뮤지컬 동아리</span>
                    </button>

                    <button onclick="selectCategory('video')" class="bg-white p-5 rounded-3xl border-2 border-blue-200 hover:border-blue-500 custom-shadow flex flex-col items-center justify-center transition transform active:scale-95 group">
                        <div class="text-4xl mb-2 group-hover:scale-110 transition">🎬</div>
                        <span class="font-extrabold text-sm text-gray-800 mb-1">🎬 영상 깃발</span>
                        <span class="text-[10px] text-gray-400">미디어 제작 동아리</span>
                    </button>

                    <button onclick="selectCategory('cooking')" class="bg-white p-5 rounded-3xl border-2 border-amber-200 hover:border-amber-500 custom-shadow flex flex-col items-center justify-center transition transform active:scale-95 group">
                        <div class="text-4xl mb-2 group-hover:scale-110 transition">🍳</div>
                        <span class="font-extrabold text-sm text-gray-800 mb-1">🍳 요리 깃발</span>
                        <span class="text-[10px] text-gray-400">쿠킹 프로젝트 동아리</span>
                    </button>
                </div>

                <div class="bg-white p-3.5 rounded-2xl border border-gray-100 flex items-center justify-center gap-2 text-xs text-gray-500">
                    <i class="fa-solid fa-hand-pointer text-cj-orange"></i>
                    <span>원하는 분야의 깃발 버튼을 터치해 보세요!</span>
                </div>
            `;
            return div;
        }

        function selectCategory(cat) {
            currentState.selectedCategory = cat;
            goToStep(4);
        }

        // --- STEP 4: STORY (WITHOUT VIDEO, WITH CARD NEWS & SURVEY BUTTON) ---
        function renderStep4() {
            const div = document.createElement('div');
            div.className = 'flex flex-col py-2';
            const cat = categoryData[currentState.selectedCategory];

            div.innerHTML = `
                <!-- Back Button -->
                <button onclick="goToStep(3)" class="text-xs font-bold text-gray-500 mb-3 flex items-center gap-1 hover:text-gray-800 w-fit">
                    <i class="fa-solid fa-arrow-left"></i> 뒤로가기
                </button>

                <!-- Category Title Badge -->
                <div class="inline-flex items-center gap-1.5 ${cat.bg} border ${cat.border} px-3 py-1 rounded-full w-fit mb-3">
                    <span>${cat.icon}</span>
                    <span class="text-xs font-bold ${cat.color}">${cat.name} 동아리 이야기</span>
                </div>

                <!-- Scroll 1 -->
                <h2 class="text-2xl font-extrabold text-gray-900 leading-tight mb-3">
                    "${cat.title}"
                </h2>

                <p class="text-xs text-gray-600 leading-relaxed mb-5 bg-white p-4 rounded-2xl border border-gray-100">
                    ${cat.storyText}<br><br>
                    ${cat.highlightText}
                </p>

                <!-- Card News Image View (Replacing Video) -->
                <div class="bg-white p-4 rounded-3xl custom-shadow border border-gray-100 mb-5 text-center">
                    <div class="flex items-center justify-between mb-3">
                        <div class="flex items-center gap-2">
                            <span class="w-5 h-5 rounded-full bg-cj-coral text-white text-[10px] font-bold flex items-center justify-center">📸</span>
                            <span class="text-xs font-bold text-gray-800">동아리 활동 카드뉴스</span>
                        </div>
                        <span class="text-[10px] text-cj-coral font-bold">Story Highlight</span>
                    </div>

                    <div class="rounded-2xl overflow-hidden shadow-inner border border-gray-100 bg-orange-50/50 p-2">
                        <div class="w-full aspect-[4/3] bg-gradient-to-br from-amber-100 to-orange-100 rounded-xl flex flex-col items-center justify-center p-6 text-center">
                            <div class="text-4xl mb-2">${cat.icon}✨</div>
                            <p class="text-xs font-extrabold text-gray-800 mb-1">[${cat.name} 부문 카드뉴스 이미지]</p>
                            <p class="text-[11px] text-gray-600 leading-relaxed">아이들이 직접 구상하고 연습하며 이뤄낸 눈부신 성장의 기록들을 카드뉴스로 확인해보세요.</p>
                        </div>
                    </div>
                </div>

                <!-- Instagram Link Button (Positioned above survey button) -->
                <a href="${INSTAGRAM_URL}" target="_blank" rel="noopener noreferrer" class="bg-gradient-to-r from-rose-500 to-cj-coral text-white p-4 rounded-2xl flex items-center justify-between mb-4 shadow-md hover:opacity-95 transition">
                    <div class="flex items-center gap-3">
                        <div class="w-9 h-9 rounded-full bg-white/20 flex items-center justify-center text-lg">
                            <i class="fa-brands fa-instagram"></i>
                        </div>
                        <div class="text-left">
                            <p class="text-[10px] opacity-90">💡 좌충우돌 비하인드 스토리 확인하기</p>
                            <p class="text-xs font-bold underline decoration-white/50">도너스캠프 유니브 공식 인스타그램</p>
                        </div>
                    </div>
                    <i class="fa-solid fa-arrow-up-right-from-square text-xs opacity-80"></i>
                </a>

                <!-- Prominent Support/Survey Button (Moved below Instagram button, styled larger) -->
                <a href="${SURVEY_URL}" target="_blank" rel="noopener noreferrer" class="w-full py-5 bg-gradient-to-r from-cj-orange to-orange-600 text-white font-black rounded-2xl text-base shadow-xl shadow-orange-500/30 hover:opacity-95 active:scale-95 transition flex items-center justify-center gap-2 mb-6">
                    <span>수요조사 및 응원메시지 남기기</span> <i class="fa-solid fa-arrow-right text-base"></i>
                </a>

                <button onclick="goToStep(5)" class="w-full py-4 bg-gray-900 text-white font-extrabold rounded-2xl text-sm shadow-md hover:bg-gray-800 transition flex items-center justify-center gap-2">
                    🎟️ 쇼케이스 티켓 및 이벤트 리워드 확인하기
                </button>
            `;
            return div;
        }

        // --- STEP 5: INVITATION / TICKET ---
        function renderStep5() {
            const div = document.createElement('div');
            div.className = 'flex flex-col py-4 text-center my-auto';
            div.innerHTML = `
                <div class="bg-amber-100 text-amber-800 text-xs font-bold py-1 px-3 rounded-full inline-block mx-auto mb-3">
                    ✨ VIP INVITATION
                </div>
                <h2 class="text-2xl font-extrabold text-gray-900 mb-2">
                    "무대에 불이 켜졌습니다!"
                </h2>
                <p class="text-xs text-gray-600 leading-relaxed mb-6">
                    길잡이님의 따뜻한 참여 덕분에<br>청소년들의 꿈의 무대가 완성되었습니다.
                </p>

                <div class="bg-gradient-to-br from-amber-50 to-orange-50 border border-orange-200 rounded-3xl p-6 mb-6 text-left relative overflow-hidden custom-shadow">
                    <div class="absolute -right-4 -bottom-4 opacity-10 text-7xl text-cj-orange">
                        <i class="fa-solid fa-ticket"></i>
                    </div>
                    <p class="text-xs font-semibold text-gray-500 mb-1">To. 길잡이님</p>
                    <p class="text-sm text-gray-800 font-medium leading-relaxed mb-4">
                        아이들의 눈부신 성장을 현장에서 직접 확인해 보세요!
                    </p>
                    <div class="space-y-1.5 text-xs text-gray-700 bg-white/90 p-3.5 rounded-2xl border border-orange-100">
                        <p><strong class="text-gray-900">일시:</strong> 2026년 9월 12일 (토) 14:00</p>
                        <p><strong class="text-gray-900">장소:</strong> CJ도너스캠프 쇼케이스 홀</p>
                    </div>
                </div>

                <div class="space-y-3">
                    <button onclick="goToStep(6)" class="w-full py-4 bg-cj-coral text-white font-extrabold rounded-2xl text-sm shadow-lg shadow-rose-500/20 hover:bg-rose-600 transition flex items-center justify-center gap-2">
                        🎁 이벤트 리워드 받으러 가기
                    </button>
                    <button onclick="goToStep(1)" class="w-full py-3.5 bg-gray-100 text-gray-700 font-bold rounded-2xl text-xs hover:bg-gray-200 transition">
                        <i class="fa-solid fa-house"></i> 캠페인 처음으로 돌아가기
                    </button>
                </div>
            `;
            return div;
        }

        // --- STEP 6: REWARD PAGE ---
        function renderStep6() {
            const div = document.createElement('div');
            div.className = 'flex flex-col py-2';

            div.innerHTML = `
                <!-- Step Header -->
                <div class="flex items-center justify-between mb-4 bg-white p-3 rounded-2xl custom-shadow border border-gray-100">
                    <span class="text-xs font-bold text-cj-orange">STEP 05. REWARD</span>
                    <span class="text-xs text-cj-coral font-bold">이벤트 응모</span>
                </div>

                <div class="text-center mb-5">
                    <h2 class="text-xl font-extrabold text-gray-900 mb-1">
                        참여해주신 분들 중<br>추첨을 통해 <span class="text-cj-coral">선물을 드려요! 🎁</span>
                    </h2>
                    <p class="text-xs text-gray-500 leading-relaxed">
                        연락처를 남겨주시면 추첨을 통해 올리브영 기프트카드를 보내드립니다!<br>많은 참여 부탁드려요.
                    </p>
                </div>

                <!-- Reward Card -->
                <div class="bg-white rounded-3xl p-5 custom-shadow border border-gray-100 mb-5 relative">
                    <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-rose-100 text-cj-coral font-extrabold text-[10px] px-3 py-1 rounded-full border border-rose-200">
                        추첨 리워드
                    </div>

                    <!-- Giftcard Graphic -->
                    <div class="w-full bg-gradient-to-r from-lime-500 to-emerald-600 rounded-2xl p-4 text-white my-3 relative overflow-hidden shadow-md">
                        <div class="flex justify-between items-start mb-6">
                            <div>
                                <span class="text-[10px] tracking-widest text-emerald-100 font-bold block">OLIVE YOUNG</span>
                                <span class="text-[8px] text-emerald-200">GIFT CARD</span>
                            </div>
                            <div class="w-8 h-8 rounded-full bg-white text-emerald-600 font-black flex items-center justify-center text-xs shadow-sm">
                                OY
                            </div>
                        </div>
                        <div class="text-right">
                            <span class="text-xl font-black tracking-wide">10,000원</span>
                        </div>
                    </div>

                    <div class="text-left space-y-1 text-xs text-gray-600">
                        <p class="font-extrabold text-sm text-gray-800">올리브영 기프트카드 <span class="text-cj-coral">10,000원권 (추첨 100명)</span></p>
                        <ul class="text-[11px] text-gray-500 space-y-0.5 pt-1">
                            <li>• <strong>추첨 인원:</strong> 100명</li>
                            <li>• <strong>리워드:</strong> 올리브영 기프트카드 10,000원권</li>
                            <li>• <strong>발표일:</strong> 2026.09.02 (수)</li>
                            <li class="text-gray-400 text-[10px] pt-1">* 당첨자에게는 개별 연락드립니다.</li>
                        </ul>
                    </div>
                </div>

                <!-- Contact Box -->
                <div class="bg-white p-5 rounded-3xl custom-shadow border border-gray-100 mb-5">
                    <label class="block text-xs font-bold text-gray-800 mb-1">📞 연락처 남기기</label>
                    <p class="text-[11px] text-gray-500 mb-3">연락처를 남겨주셔야 추첨에 참여할 수 있어요! 정확한 번호를 입력해주세요.</p>
                    
                    <div class="flex gap-2 mb-3">
                        <input type="tel" id="phone-input" placeholder="예) 010-1234-5678" class="flex-grow p-3 text-xs border border-gray-200 rounded-2xl focus:outline-none focus:border-cj-coral bg-gray-50/50">
                        <button onclick="submitPhone()" class="bg-cj-coral text-white px-4 text-xs font-bold rounded-2xl hover:bg-rose-600 transition whitespace-nowrap">
                            등록하기
                        </button>
                    </div>

                    <p class="text-[10px] text-gray-400 flex items-center gap-1">
                        <i class="fa-solid fa-lock text-[9px]"></i>
                        <span>입력해주신 연락처는 추첨 및 리워드 발송 용도로만 사용됩니다.</span>
                    </p>
                </div>

                <div class="space-y-2">
                    <button onclick="goToStep(1)" class="w-full py-3.5 bg-cj-coral text-white font-bold rounded-2xl text-xs hover:bg-rose-600 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-house"></i> 캠페인 메인으로 돌아가기
                    </button>
                    <button onclick="copyInviteLink()" class="w-full py-3.5 bg-white border border-gray-200 text-gray-700 font-bold rounded-2xl text-xs hover:bg-gray-50 transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-share-nodes"></i> 이 캠페인 공유하기
                    </button>
                </div>
            `;
            return div;
        }

        function submitPhone() {
            const input = document.getElementById('phone-input');
            if (!input.value || input.value.length < 10) {
                alert('올바른 연락처 번호를 입력해주세요!');
                return;
            }
            alert('연락처가 정상적으로 등록되었습니다! 올리브영 기프트카드 추첨 응모가 완료되었습니다.');
            input.disabled = true;
        }

        function closeModal() {
            const modal = document.getElementById('invitation-modal');
            const card = document.getElementById('modal-card');
            card.classList.remove('scale-100', 'opacity-100');
            card.classList.add('scale-95', 'opacity-0');
            setTimeout(() => {
                modal.classList.add('hidden');
            }, 300);
        }

        function goToRewardStep() {
            closeModal();
            goToStep(6);
        }

        function copyInviteLink() {
            const dummy = document.createElement('input');
            document.body.appendChild(dummy);
            dummy.value = window.location.href;
            dummy.select();
            document.execCommand('copy');
            document.body.removeChild(dummy);
            alert('캠페인 링크가 성공적으로 복사되었습니다!');
        }

        function goToStep(stepNumber) {
            currentState.step = stepNumber;
            render();
        }

        window.onload = function() {
            render();
        };
    </script>
</body>
</html>