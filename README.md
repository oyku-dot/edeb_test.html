# edebiyat_test.html<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Türk Edebiyatı Yazar-Eser Sınav Hazırlık</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-100 font-sans min-h-screen flex flex-col items-center justify-center p-4">
    <div class="max-w-xl w-full bg-white rounded-xl shadow-lg p-6">
        <h1 class="text-2xl font-bold text-center text-indigo-700 mb-2">Türk Edebiyatı Sınav Hazırlığı</h1>
        <p class="text-center text-gray-500 mb-6 text-sm">Notlarındaki yazar ve eserleri pekiştir!</p>

        <div id="quiz-container">
            <div class="flex justify-between items-center mb-4 text-sm text-gray-600 font-semibold">
                <span id="question-counter">Soru 1 / 10</span>
                <span id="score" class="text-indigo-600">Puan: 0</span>
            </div>

            <div id="question-box" class="text-lg font-medium text-gray-800 mb-4">
                Soru yükleniyor...
            </div>

            <div id="options-container" class="space-y-3 mb-4">
                <!-- Şıklar buraya gelecek -->
            </div>

            <div id="rationale-box" class="hidden p-3 rounded-lg bg-indigo-50 text-indigo-800 text-sm mb-4"></div>

            <button id="next-btn" onclick="nextQuestion()" class="w-full bg-indigo-600 text-white py-2 rounded-lg font-semibold hover:bg-indigo-700 transition hidden">
                Sonraki Soru
            </button>
        </div>

        <div id="result-container" class="hidden text-center py-8">
            <h2 class="text-3xl font-bold text-indigo-700 mb-3">Sınav Tamamlandı!</h2>
            <p id="final-score" class="text-xl text-gray-700 mb-6"></p>
            <button onclick="restartQuiz()" class="bg-indigo-600 text-white px-6 py-2 rounded-lg font-semibold hover:bg-indigo-700 transition">
                Tekrar Çöz
            </button>
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "Aşağıdaki eserlerden hangisi 'Saf Şir' anlayışıyla yazan Ahmet Muhip Dıranas'a aittir?",
                options: [
                    "Fahriye Abla",
                    "Kaldırımlar",
                    "Bursa'da Zaman",
                    "35 Yaş"
                ],
                correct: 0,
                rationale: "'Fahriye Abla', 'Kar', 'Olvido', 'Ağrı' ve 'Serenad' Ahmet Muhip Dıranas'ın en bilinen şiirlerindendir."
            },
            {
                question: "Toplumcu Gerçekçi yazarlarımızdan Sabahattin Ali'ye ait olmayan eser hangisidir?",
                options: [
                    "Sırça Köşk",
                    "Kağnı",
                    "Göl İnsanları",
                    "Değirmen"
                ],
                correct: 2,
                rationale: "'Göl İnsanları' Sabahattin Ali'ye değil, Kemal Tahir'e ait bir romandır."
            },
            {
                question: "Aşağıdaki eserlerden hangisi 'Atatürk Şairi' olarak bilinen Behçet Kemal Çağlar'ın eseridir?",
                options: [
                    "Erciyesten Kopan Çığ",
                    "Bu Vatan Kimin",
                    "Bir Bayrak Rüzgar Bekliyor",
                    "Gurbet"
                ],
                correct: 0,
                rationale: "'Erciyesten Kopan Çığ', 'Burada Bir Kalp Çarpıyor' ve 'Benden İçeri' Behçet Kemal Çağlar'a aittir."
            },
            {
                question: "Bireyin iç dünyasını esas alan yazarlardan Peyami Safa'nın otobiyografik izler taşıyan ünlü eseri aşağıdakilerden hangisidir?",
                options: [
                    "Dokuzuncu Hariciye Koğuşu (veya İstanbul Hikayeleri)",
                    "Alemdağ'da Var Bir Yılan",
                    "Tütün Zamanı",
                    "Yaralı Hayvan"
                ],
                correct: 0,
                rationale: "Peyami Safa'nın notlarında İstanbul Hikayeleri, Beyaz Gölgeler, Sümbüllerin Gölgesinde gibi eserler yer alır."
            },
            {
                question: "Milli Edebiyat zevk ve anlayışını sürdüren 'Gurbet Şairi' olarak tanınan ve 'Bingöl Çobanları' şiirini yazan şair kimdir?",
                options: [
                    "Kemalettin Kamu",
                    "Orhan Şaik Gökyay",
                    "Arif Nihat Asya",
                    "Ömer Bedrettin Uşaklı"
                ],
                correct: 0,
                rationale: "Kemalettin Kamu, gurbet temasını işlemesiyle tanınır ve 'Bingöl Çobanları', 'Gurbet' onun eserleridir."
            },
            {
                question: "Modernizmi esas alan yazarlardan Yusuf Atılgan'a ait hikaye/eser hangisidir?",
                options: [
                    "Bodur Minareden Öte",
                    "Korkuyu Beklerken",
                    "Siyah Beyaz",
                    "Gülün İçinde Bülbül Sesi Var"
                ],
                correct: 0,
                rationale: "'Eylenci' ve 'Bodur Minareden Öte' Yusuf Atılgan'ın modernizmi esas alan eserlerindendir."
            },
            {
                question: "Yedi Meşaleciler topluluğu içinde yer alan ve 'Sebil ve Güvercinler', 'Nefes Almak' eserlerini yazan şair kimdir?",
                options: [
                    "Ziya Osman Saba",
                    "Yaşar Nabi Nayır",
                    "Cevdet Kudret Solok",
                    "Sabri Esat Siyavuşgil"
                ],
                correct: 0,
                rationale: "Ziya Osman Saba Yedi Meşaleciler'in en önemli şairlerinden olup anılan eserlerin sahibidir."
            },
            {
                question: "Serbest Toplumcu Şiir geleneğinde yer alan ve 'Hasretinden Prangalar Eskittim' kitabının yazarı kimdir?",
                options: [
                    "Ahmet Arif",
                    "Nâzım Hikmet Ran",
                    "Rıfat Ilgaz",
                    "Can Yücel"
                ],
                correct: 0,
                rationale: "'Hasretinden Prangalar Eskittim' Ahmet Arif'in tek şiir kitabıdır."
            },
            {
                question: "Milli ve Dini Duyarlılığı yansıtan hikaye ve roman yazarlarından Halikarnas Balıkçısı'nın (Cevat Şakir Kabaağaçlı) eseri hangisidir?",
                options: [
                    "Merhaba Akdeniz",
                    "Dağa Çıkan Kurt",
                    "Memleket Hikayeleri",
                    "Tanrı Misafiri"
                ],
                correct: 0,
                rationale: "'Merhaba Akdeniz', 'Egenin Dibi', 'Gülen Ada' Halikarnas Balıkçısı'nın deniz temalı eserleridir."
            },
            {
                question: "Sait Faik Abasıyanık'ın doğayı ve insanları merkeze alan ünlü hikaye kitabı aşağıdakilerden hangisidir?",
                options: [
                    "Alemdağ'da Var Bir Yılan",
                    "Mendil Altında",
                    "Otlakçı",
                    "Kumpanya dışındaki modern eser"
                ],
                correct: 0,
                rationale: "'Semaver', 'Sarnıç', 'Son Kuşlar' ve 'Alemdağ'da Var Bir Yılan' Sait Faik Abasıyanık'ın eserleridir."
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let answered = false;

        function loadQuestion() {
            answered = false;
            const q = questions[currentQuestion];
            document.getElementById("question-counter").innerText = `Soru ${currentQuestion + 1} / ${questions.length}`;
            document.getElementById("question-box").innerText = q.question;
            
            const optionsContainer = document.getElementById("options-container");
            optionsContainer.innerHTML = "";

            q.options.forEach((opt, index) => {
                const btn = document.createElement("button");
                btn.className = "w-full text-left p-3 rounded-lg border border-gray-300 hover:bg-indigo-50 transition font-medium text-gray-700";
                btn.innerText = opt;
                btn.onclick = () => selectOption(index);
                optionsContainer.appendChild(btn);
            });

            document.getElementById("rationale-box").classList.add("hidden");
            document.getElementById("next-btn").classList.add("hidden");
        }

        function selectOption(selectedIndex) {
            if (answered) return;
            answered = true;

            const q = questions[currentQuestion];
            const optionsContainer = document.getElementById("options-container");
            const buttons = optionsContainer.children;

            if (selectedIndex === q.correct) {
                buttons[selectedIndex].classList.add("bg-green-100", "border-green-500", "text-green-800");
                score += 10;
                document.getElementById("score").innerText = `Puan: ${score}`;
            } else {
                buttons[selectedIndex].classList.add("bg-red-100", "border-red-500", "text-red-800");
                buttons[q.correct].classList.add("bg-green-100", "border-green-500", "text-green-800");
            }

            const rationaleBox = document.getElementById("rationale-box");
            rationaleBox.innerText = q.rationale;
            rationaleBox.classList.remove("hidden");

            document.getElementById("next-btn").classList.remove("hidden");
        }

        function nextQuestion() {
            currentQuestion++;
            if (currentQuestion < questions.length) {
                loadQuestion();
            } else {
                document.getElementById("quiz-container").classList.add("hidden");
                document.getElementById("result-container").classList.remove("hidden");
                document.getElementById("final-score").innerText = `Toplam Puanın: ${score} / 100`;
            }
        }

        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            document.getElementById("score").innerText = `Puan: 0`;
            document.getElementById("quiz-container").classList.remove("hidden");
            document.getElementById("result-container").classList.add("hidden");
            loadQuestion();
        }

        loadQuestion();
    </script>
</body>
</html>
```eof
