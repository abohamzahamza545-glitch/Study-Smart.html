<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StudySmart - رفيقك الذكي في التعلم</title>
    <style>
        :root {
            --primary-blue: #007bff;
            --bright-blue: #1e90ff;
            --dark-blue: #0056b3;
            --accent-yellow: #ffd700;
            --text-dark: #333;
            --bg-gradient: linear-gradient(135deg, #0f2b46, #1a5f7a, #00d2ff);
            --card-bg: rgba(255, 255, 255, 0.95);
        }

        body, html {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--bg-gradient);
            color: var(--text-dark);
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        #app-container {
            width: 100%;
            max-width: 500px;
            height: 100%;
            max-height: 900px;
            background: #f0f8ff;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
        }

        .screen {
            flex: 1;
            display: none;
            flex-direction: column;
            padding: 20px;
            box-sizing: border-box;
            overflow-y: auto;
        }

        .screen.active {
            display: flex;
            animation: fadeIn 0.3s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.98); }
            to { opacity: 1; transform: scale(1); }
        }

        header {
            background: linear-gradient(to right, #0056b3, #007bff);
            color: white;
            padding: 15px;
            text-align: center;
            font-size: 1.2rem;
            font-weight: bold;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .btn {
            background: var(--accent-yellow);
            color: #333;
            border: none;
            padding: 10px 20px;
            border-radius: 25px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s, background 0.2s;
            margin-top: 10px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
        }

        .btn:active {
            transform: scale(0.95);
        }

        .input-group {
            margin-bottom: 15px;
        }

        input, select, textarea {
            width: 100%;
            padding: 12px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 8px;
            box-sizing: border-box;
            font-size: 1rem;
        }

        .grid-buttons {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-top: 20px;
        }

        .menu-btn {
            background: white;
            border: 2px solid var(--primary-blue);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            font-weight: bold;
            color: var(--dark-blue);
            cursor: pointer;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .menu-btn:active {
            background: var(--primary-blue);
            color: white;
        }

        .character-art {
            text-align: center;
            margin: 20px 0;
        }

        .character-placeholder {
            width: 150px;
            height: 150px;
            background: var(--accent-yellow);
            border-radius: 50%;
            display: inline-flex;
            justify-content: center;
            align-items: center;
            font-size: 4rem;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .card {
            background: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 15px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        .question-item {
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        .options-list {
            list-style: none;
            padding: 0;
        }

        .options-list li {
            margin: 10px 0;
        }

        .radio-label {
            display: flex;
            align-items: center;
            background: #f9f9f9;
            padding: 10px;
            border-radius: 8px;
            cursor: pointer;
        }

        .radio-label input {
            width: auto;
            margin-left: 10px;
        }

        .hidden {
            display: none !important;
        }

        #ai-conversation {
            flex: 1;
            overflow-y: auto;
            border: 1px solid #ddd;
            border-radius: 10px;
            padding: 10px;
            background: #fff;
            margin-bottom: 10px;
            display: flex;
            flex-direction: column;
        }

        .chat-bubble {
            max-width: 80%;
            padding: 10px;
            border-radius: 15px;
            margin-bottom: 10px;
        }

        .ai-message {
            background: #e1f5fe;
            align-self: flex-start;
        }

        .user-message {
            background: var(--primary-blue);
            color: white;
            align-self: flex-end;
        }

        .book-link {
            display: block;
            padding: 15px;
            background: var(--bright-blue);
            color: white;
            text-align: center;
            text-decoration: none;
            border-radius: 8px;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .subject-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
        }
    </style>
</head>
<body>

<div id="app-container">
    
    <!-- شاشة البداية والتسجيل -->
    <div id="screen-splash" class="screen active">
        <header>StudySmart</header>
        <div class="character-art">
            <div class="character-placeholder">👧</div>
            <h2>StudySmart</h2>
            <p>رفيقك الذكي في التعلم</p>
        </div>
        <div class="card">
            <h3>تسجيل بيانات الطالب</h3>
            <div class="input-group">
                <label>اسم الطالب:</label>
                <input type="text" id="student-name" placeholder="أدخل اسمك الثلاثي">
            </div>
            <div class="input-group">
                <label>السنة الدراسية:</label>
                <select id="grade-level" onchange="updateTracks()">
                    <option value="1">الصف الأول الثانوي</option>
                    <option value="2">الصف الثاني الثانوي</option>
                    <option value="3">الصف الثالث الثانوي</option>
                </select>
            </div>
            <div class="input-group hidden" id="track-group">
                <label>المسار الدراسي:</label>
                <select id="track-select" onchange="updateSpecialization()">
                    <!-- خيارات مسارات تانية وتالتة -->
                </select>
            </div>
            <div class="input-group hidden" id="spec-group">
                <label>المادة التخصصية:</label>
                <select id="spec-select">
                    <!-- مواد التخصص -->
                </select>
            </div>
            <div class="input-group">
                <label>رقم هاتف ولي الأمر (لاستلام التقارير):</label>
                <input type="tel" id="parent-phone" placeholder="01xxxxxxxxxx">
            </div>
            <button class="btn" style="width: 100%;" onclick="startApp()">دخول التطبيق</button>
        </div>
    </div>

    <!-- الواجهة الرئيسية -->
    <div id="screen-main" class="screen">
        <header>
            <span>الرئيسية</span>
            <span id="student-display" style="font-size: 0.9rem;"></span>
        </header>

        <div class="character-art" style="margin: 10px 0;">
            <div class="character-placeholder" style="width: 100px; height: 100px; font-size: 2.5rem;">👧</div>
            <h3 style="margin: 5px 0;">أهلاً بك يا بطل</h3>
        </div>

        <div class="grid-buttons">
            <div class="menu-btn" onclick="showScreen('screen-smart-coach')">
                🤖<br>المعلم الذكي AI
            </div>
            <div class="menu-btn" onclick="showScreen('screen-books')">
                📚<br>مكتبة الكتب الوزارية
            </div>
            <div class="menu-btn" onclick="showScreen('screen-evaluations')">
                📝<br>التقييمات الأسبوعية
            </div>
            <div class="menu-btn" onclick="showScreen('screen-monthly-exam')">
                📅<br>امتحان الشهر
            </div>
        </div>

        <div class="card" style="margin-top: 20px;">
            <h4>إحصائيات ومتابعة ولي الأمر</h4>
            <div id="parent-report-summary">
                <p>يتم إرسال التقارير والرسوم البيانية لولي الأمر تلقائياً.</p>
            </div>
        </div>
    </div>

    <!-- شاشة المعلم الذكي -->
    <div id="screen-smart-coach" class="screen">
        <header>
            <button class="btn" style="margin:0; padding: 5px 10px;" onclick="showScreen('screen-main') ←">الرئيسية</button>
            <span>المعلم الذكي AI</span>
            <div></div>
        </header>
        <div id="ai-conversation">
            <div class="chat-bubble ai-message">مرحباً بك! أنا معلمك الذكي، اختر مادة لنبدأ الشرح التفاعلي.</div>
        </div>
        <div class="input-group">
            <select id="ai-subject-select">
                <option value="اللغة العربية">اللغة العربية</option>
                <option value="الرياضيات">الرياضيات</option>
                <option value="اللغة الإنجليزية">اللغة الإنجليزية</option>
                <option value="العلوم المتكاملة">العلوم المتكاملة</option>
            </select>
        </div>
        <div style="display: flex; gap: 10px;">
            <input type="text" id="user-input" placeholder="اكتب سؤالك هنا...">
            <button class="btn" style="margin:0;" onclick="sendMessage()">إرسال</button>
        </div>
        <button class="btn" style="background: #28a745; color: white;" onclick="startVoiceInteraction()">🎤 تحدث صوتياً</button>
    </div>

    <!-- شاشة مكتبة الكتب الوزارية -->
    <div id="screen-books" class="screen">
        <header>
            <button class="btn" style="margin:0; padding: 5px 10px;" onclick="showScreen('screen-main') ←">الرئيسية</button>
            <span>المكتبة الوزارية الرقمية</span>
            <div></div>
        </header>
        <h3>الكتب المدرسية المعتمدة</h3>
        <div id="books-container" class="subject-grid">
            <!-- سيتم ملء الكتب برمجياً -->
        </div>
    </div>

    <!-- شاشة التقييمات الأسبوعية -->
    <div id="screen-evaluations" class="screen">
        <header>
            <button class="btn" style="margin:0; padding: 5px 10px;" onclick="showScreen('screen-main') ←">الرئيسية</button>
            <span>التقييمات الأسبوعية</span>
            <div></div>
        </header>
        <h3>اختر الأسبوع الدراسي</h3>
        <div class="grid-buttons">
            <div class="menu-btn" onclick="openEvaluation('الأسبوع الأول')">الأسبوع الأول</div>
            <div class="menu-btn" onclick="openEvaluation('الأسبوع الثاني')">الأسبوع الثاني</div>
            <div class="menu-btn" onclick="openEvaluation('الأسبوع الثالث')">الأسبوع الثالث</div>
            <div class="menu-btn" onclick="openEvaluation('الأسبوع الرابع')">الأسبوع الرابع</div>
        </div>
        <div id="evaluation-sheet" class="card hidden" style="margin-top: 20px;">
            <h4 id="eval-title"></h4>
            <div id="eval-questions-container"></div>
            <button class="btn" style="width: 100%;" onclick="submitEvaluation()">إرسال التقييم</button>
        </div>
    </div>

    <!-- شاشة امتحان الشهر -->
    <div id="screen-monthly-exam" class="screen">
        <header>
            <button class="btn" style="margin:0; padding: 5px 10px;" onclick="showScreen('screen-main') ←">الرئيسية</button>
            <span>امتحان الشهر التفاعلي</span>
            <div></div>
        </header>
        <div id="exam-selection">
            <h3>اختر المادة لأداء امتحان الشهر</h3>
            <div id="exam-subjects-grid" class="subject-grid"></div>
        </div>
        <div id="exam-paper" class="card hidden">
            <h3 id="exam-header"></h3>
            <form id="exam-form">
                <div id="questions-area"></div>
                <button type="button" class="btn" style="width: 100%; background: #28a745; color: white;" onclick="submitMonthlyExam()">تسليم وإرسال النتيجة لولي الأمر</button>
            </form>
        </div>
    </div>

</div>

<script>
    let studentData = {
        name: "",
        grade: "1",
        track: "",
        specialization: "",
        phone: ""
    };

    const curriculumData = {
        "1": {
            subjects: ["اللغة العربية", "الرياضيات", "اللغة الإنجليزية", "العلوم المتكاملة", "التاريخ", "الفلسفة والمنطق", "الفرنسية", "التربية الدينية"],
            books: {
                "اللغة العربية": "https://moe.gov.eg/ar/arabic-language-first-secondary/",
                "الرياضيات": "https://moe.gov.eg/ar/mathematics-first-secondary/",
                "اللغة الإنجليزية": "https://moe.gov.eg/ar/english-first-secondary/",
                "العلوم المتكاملة": "https://moe.gov.eg/ar/integrated-science-first-secondary/",
                "التاريخ": "https://moe.gov.eg/ar/history-first-secondary/",
                "الفلسفة والمنطق": "https://moe.gov.eg/ar/philosophy-first-secondary/",
                "الفرنسية": "https://moe.gov.eg/ar/french-first-secondary/",
                "التربية الدينية": "https://moe.gov.eg/ar/religious-studies-first-secondary/"
            }
        },
        "2": {
            tracks: [
                { name: "مسار الطب وعلوم الحياة", specs: ["الأحياء والكيمياء والفيزياء"] },
                { name: "مسار الهندسة وعلوم الحاسب", specs: ["الرياضيات والفيزياء والحاسب الآلي"] },
                { name: "مسار الأعمال", specs: ["الاقتصاد وإدارة الأعمال والرياضيات"] },
                { name: "مسار الآداب والفنون", specs: ["اللغات والتاريخ والجغرافيا والفلسفة"] }
            ],
            books: {
                "الأحياء والكيمياء والفيزياء": "https://moe.gov.eg/ar/scientific-books-second-sec/",
                "الرياضيات والفيزياء والحاسب الآلي": "https://moe.gov.eg/ar/stem-books-second-sec/",
                "الاقتصاد وإدارة الأعمال والرياضيات": "https://moe.gov.eg/ar/business-books-second-sec/",
                "اللغات والتاريخ والجغرافيا والفلسفة": "https://moe.gov.eg/ar/humanities-books-second-sec/"
            }
        },
        "3": {
            tracks: [
                { name: "الشعبة العلمية (علوم)", specs: ["الأحياء", "الكيمياء", "الفيزياء", "الجيولوجيا"] },
                { name: "الشعبة العلمية (رياضيات)", specs: ["الرياضيات البحتة", "الرياضيات التطبيقية", "الكيمياء", "الفيزياء"] },
                { name: "الشعبة الأدبية", specs: ["التاريخ", "الجغرافيا", "الفلسفة والمنطق", "علم النفس والاجتماع"] }
            ],
            books: {
                "الأحياء": "https://moe.gov.eg/ar/biology-third-sec/",
                "الكيمياء": "https://moe.gov.eg/ar/chemistry-third-sec/",
                "الفيزياء": "https://moe.gov.eg/ar/physics-third-sec/",
                "الجيولوجيا": "https://moe.gov.eg/ar/geology-third-sec/",
                "الرياضيات البحتة": "https://moe.gov.eg/ar/pure-math-third-sec/",
                "الرياضيات التطبيقية": "https://moe.gov.eg/ar/applied-math-third-sec/",
                "التاريخ": "https://moe.gov.eg/ar/history-third-sec/",
                "الجغرافيا": "https://moe.gov.eg/ar/geography-third-sec/",
                "الفلسفة والمنطق": "https://moe.gov.eg/ar/philosophy-third-sec/",
                "علم النفس والاجتماع": "https://moe.gov.eg/ar/psychology-third-sec/"
            }
        }
    };

    function updateTracks() {
        const grade = document.getElementById("grade-level").value;
        const trackGroup = document.getElementById("track-group");
        const specGroup = document.getElementById("spec-group");
        const trackSelect = document.getElementById("track-select");

        trackSelect.innerHTML = "";
        specGroup.classList.add("hidden");

        if (grade === "1") {
            trackGroup.classList.add("hidden");
        } else {
            trackGroup.classList.remove("hidden");
            const tracks = curriculumData[grade].tracks;
            tracks.forEach((t, index) => {
                let opt = document.createElement("option");
                opt.value = index;
                opt.innerHTML = t.name;
                trackSelect.appendChild(opt);
            });
            updateSpecialization();
        }
    }

    function updateSpecialization() {
        const grade = document.getElementById("grade-level").value;
        const trackIndex = document.getElementById("track-select").value;
        const specGroup = document.getElementById("spec-group");
        const specSelect = document.getElementById("spec-select");

        specSelect.innerHTML = "";
        specGroup.classList.remove("hidden");

        const specs = curriculumData[grade].tracks[trackIndex].specs;
        specs.forEach(s => {
            let opt = document.createElement("option");
            opt.value = s;
            opt.innerHTML = s;
            specSelect.appendChild(opt);
        });
    }

    function showScreen(screenId) {
        document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
        document.getElementById(screenId).classList.add('active');
        if (screenId === 'screen-books') {
            renderBooks();
        } else if (screenId === 'screen-monthly-exam') {
            renderMonthlyExamSubjects();
        }
    }

    function startApp() {
        studentData.name = document.getElementById("student-name").value;
        studentData.grade = document.getElementById("grade-level").value;
        studentData.phone = document.getElementById("parent-phone").value;

        if (!studentData.name || !studentData.phone) {
            alert("يرجى ملء البيانات الأساسية للطالب وولي الأمر");
            return;
        }

        if (studentData.grade !== "1") {
            studentData.track = document.getElementById("track-select").options[document.getElementById("track-select").selectedIndex].text;
            studentData.specialization = document.getElementById("spec-select").value;
        } else {
            studentData.track = "عام";
            studentData.specialization = "المواد الأساسية";
        }

        document.getElementById("student-display").innerHTML = `${studentData.name} (${studentData.grade == '1' ? 'أولى ثانوي' : studentData.grade == '2' ? 'تانية ثانوي' : 'تالتة ثانوي'})`;
        showScreen('screen-main');
    }

    // المعلم الذكي الصوتي
    function sendMessage() {
        const input = document.getElementById("user-input");
        const text = input.value.trim();
        if(!text) return;

        const chatBox = document.getElementById("ai-conversation");
        chatBox.innerHTML += `<div class="chat-bubble user-message">${text}</div>`;
        input.value = "";

        const subject = document.getElementById("ai-subject-select").value;

        setTimeout(() => {
            let reply = `بصفتي معلمك الذكي لمادة ${subject}، أؤكد لك أن هذا المفهوم أساسي ومبني على مخرجات التعلم المعتمدة من الوزارة. هل تحب أن نحله سوياً كأداء صفي؟`;
            chatBox.innerHTML += `<div class="chat-bubble ai-message">${reply}</div>`;
            chatBox.scrollTop = chatBox.scrollHeight;
            speakText(reply);
        }, 1000);
    }

    function speakText(text) {
        if ('speechSynthesis' in window) {
            const utterance = new SpeechSynthesisUtterance(text);
            utterance.lang = 'ar-EG';
            window.speechSynthesis.speak(utterance);
        }
    }

    function startVoiceInteraction() {
        alert("🎤 تم تفعيل الميكروفون... تحدث الآن (محاكاة).");
        setTimeout(() => {
            document.getElementById("user-input").value = "ما هي أهم النقاط في هذا الدرس؟";
            sendMessage();
        }, 2000);
    }

    // مكتبة الكتب الرقمية
    function renderBooks() {
        const container = document.getElementById("books-container");
        container.innerHTML = "";
        let subjects = [];

        if (studentData.grade === "1") {
            subjects = curriculumData["1"].subjects;
        } else {
            subjects = studentData.specialization.split(" والـ ");
        }

        subjects.forEach(sub => {
            let link = "#";
            if(curriculumData["1"].books[sub]) link = curriculumData["1"].books[sub];
            else if(curriculumData["2"].books[sub]) link = curriculumData["2"].books[sub];
            else if(curriculumData["3"].books[sub]) link = curriculumData["3"].books[sub];

            container.innerHTML += `<a href="${link}" target="_blank" class="book-link">📖 ${sub}</a>`;
        });
    }

    // التقييمات الأسبوعية
    function openEvaluation(weekName) {
        document.getElementById("eval-title").innerHTML = `${weekName} - أوراق التقييم المعتمدة`;
        const qContainer = document.getElementById("eval-questions-container");
        qContainer.innerHTML = `
            <div class="question-item">
                <p>1. ما هي النتيجة المترتبة على تطبيق المفاهيم الأساسية للدرس؟</p>
                <textarea rows="3" placeholder="اكتب إجابتك المقالية هنا..."></textarea>
            </div>
            <div class="question-item">
                <p>2. اختر الإجابة الصحيحة: أي مما يلي يعتبر جزءاً أساسياً من المنهج؟</p>
                <ul class="options-list">
                    <li><label class="radio-label"><input type="radio" name="q2"> الخيار الأول المعتمد</label></li>
                    <li><label class="radio-label"><input type="radio" name="q2"> الخيار الثاني</label></li>
                </ul>
            </div>
        `;
        document.getElementById("evaluation-sheet").classList.remove("hidden");
    }

    function submitEvaluation() {
        alert("تم إرسال التقييم بنجاح وتوثيق اجتياز الدرس في سجل الطالب!");
        showScreen('screen-main');
    }

    // امتحان الشهر
    function renderMonthlyExamSubjects() {
        const grid = document.getElementById("exam-subjects-grid");
        grid.innerHTML = "";
        let subjects = studentData.grade === "1" ? curriculumData["1"].subjects : studentData.specialization.split(" والـ ");

        subjects.forEach(sub => {
            grid.innerHTML += `<div class="menu-btn" style="background:#0056b3; color:white;" onclick="startExam('${sub}')">امتحان ${sub}</div>`;
        });
    }

    function startExam(subject) {
        document.getElementById("exam-header").innerHTML = `ورقة امتحان شهر نوفمبر - ${subject}`;
        const area = document.getElementById("questions-area");
        area.innerHTML = "";

        // توليد 4 أسئلة (50% مقالي، 50% اختياري)
        for(let i=1; i<=2; i++) {
            area.innerHTML += `
                <div class="question-item">
                    <p><strong>س${i} (سؤال مقالي):</strong> اشرح بالتفصيل أهمية ${subject} في ضوء ما درست؟</p>
                    <textarea rows="2" required placeholder="الإجابة..."></textarea>
                </div>
            `;
        }
        for(let i=3; i<=4; i++) {
            area.innerHTML += `
                <div class="question-item">
                    <p><strong>س${i} (سؤال اختيار من متعدد):</strong> المحور الرئيسي لـ ${subject} يعتمد على:</p>
                    <ul class="options-list">
                        <li><label class="radio-label"><input type="radio" name="mq${i}" required> المفهوم الأساسي أ</label></li>
                        <li><label class="radio-label"><input type="radio" name="mq${i}"> المفهوم الفرعي ب</label></li>
                    </ul>
                </div>
            `;
        }
        document.getElementById("exam-selection").classList.add("hidden");
        document.getElementById("exam-paper").classList.remove("hidden");
    }

    function submitMonthlyExam() {
        alert("تم إرسال ورقة الامتحان بنجاح. يتم الآن معالجة النتائج وإرسال الرسم البياني لولي الأمر عبر الواتساب.");
        document.getElementById("exam-paper").classList.add("hidden");
        document.getElementById("exam-selection").classList.remove("hidden");
        showScreen('screen-main');
    }
</script>
</body>
</html>
                    
