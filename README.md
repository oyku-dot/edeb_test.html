<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Türk Edebiyatı Kapsamlı Sınav Hazırlık Seti</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-50 font-sans min-h-screen p-4 flex flex-col items-center">
    <div class="max-w-2xl w-full bg-white rounded-2xl shadow-xl p-6 mt-6">
        <header class="text-center mb-6">
            <h1 class="text-3xl font-extrabold text-indigo-700">Edebiyat Full Tekrar & Sınav Merkezi</h1>
            <p class="text-gray-500 text-sm mt-1">Notlarındaki tüm yazar ve eserler bu sistemde bir arada!</p>
        </header>

        <!-- Sekmeler -->
        <div class="flex justify-center space-x-2 mb-6 border-b pb-4">
            <button onclick="switchTab('quiz')" id="btn-quiz" class="px-4 py-2 bg-indigo-600 text-white font-semibold rounded-lg shadow transition">Sınav Modu (Quiz)</button>
            <button onclick="switchTab('list')" id="btn-list" class="px-4 py-2 bg-gray-200 text-gray-700 font-semibold rounded-lg hover:bg-gray-300 transition">Tüm Liste Arşivi</button>
        </div>

        <!-- Quiz Alanı -->
        <div id="quiz-section">
            <div class="flex justify-between items-center mb-4 text-sm text-gray-600 font-bold">
                <span id="q-counter">Soru 1 / 20</span>
                <span id="q-score" class="text-indigo-600">Puan: 0</span>
            </div>
            <div id="question-box" class="text-lg font-semibold text-gray-800 mb-4 bg-indigo-50 p-4 rounded-xl border border-indigo-100">
                Soru yükleniyor...
            </div>
            <div id="options-container" class="space-y-3 mb-4"></div>
            <div id="explanation-box" class="hidden p-3 rounded-lg bg-emerald-50 text-emerald-800 text-sm mb-4 border border-emerald-200"></div>
            <button id="next-q-btn" onclick="nextQuestion()" class="w-full bg-indigo-600 text-white py-3 rounded-xl font-bold hover:bg-indigo-700 transition hidden shadow-md">
                Sonraki Soruya Geç
            </button>
        </div>

        <!-- Liste Alanı -->
        <div id="list-section" class="hidden">
            <h2 class="text-xl font-bold text-gray-800 mb-3">Tüm Yazar ve Eserler Arşivi</h2>
            <div class="mb-4">
                <input type="text" id="search-input" onkeyup="filterList()" placeholder="Yazar veya eser ara..." class="w-full p-3 border rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500">
            </div>
            <div id="archive-container" class="space-y-4 max-h-96 overflow-y-auto pr-2">
  </div>


function nextQuestion() {

currentIdx++;

loadQuestion();

}


function renderArchive() {

const container = document.getElementById("archive-container");

container.innerHTML = "";

database.forEach(item => {

const div = document.createElement("div");

div.className = "p-4 border rounded-xl bg-white shadow-sm";

div.innerHTML = `<h3 class="font-bold text-indigo-700">${item.author} <span class="text-xs text-gray-400 font-normal">(${item.category})</span></h3>

<p class="text-sm text-gray-600 mt-1"><b>Eserler:</b> ${item.works.join(", ")}</p>`;

container.appendChild(div);

});

}


function filterList() {

let query = document.getElementById("search-input").value.toLowerCase();

const container = document.getElementById("archive-container");

container.innerHTML = "";

database.filter(item => item.author.toLowerCase().includes(query) || item.works.some(w => w.toLowerCase().includes(query))).forEach(item => {

const div = document.createElement("div");

div.className = "p-4 border rounded-xl bg-white shadow-sm";

div.innerHTML = `<h3 class="font-bold text-indigo-700">${item.author} <span class="text-xs text-gray-400 font-normal">(${item.category})</span></h3>

<p class="text-sm text-gray-600 mt-1"><b>Eserler:</b> ${item.works.join(", ")}</p>`;

container.appendChild(div);

});

}


initQuiz();

</script>

</body>

</html>

```eof
      
