<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StudySmart - منصة التعلم الذكي لأول ثانوي</title>
    <style>
        :root {
            --primary: #4f46e5;
            --secondary: #06b6d4;
            --bg-color: #f0f4f8;
            --card-bg: #ffffff;
            --text-color: #1f2937;
        }
        body {
            font-family: 'Cairo', sans-serif, Tahoma;
            background: linear-gradient(135deg, #e0f2fe, #f0fdf4);
            margin: 0;
            padding: 0;
            color: var(--text-color);
        }
        .app-container {
            max-width: 480px;
            margin: 0 auto;
            background: var(--bg-color);
            min-height: 100vh;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
            display: flex;
            flex-direction: column;
            position: relative;
        }
        header {
            background: linear-gradient(135deg, #4338ca, #6366f1);
            color: white;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom-left-radius: 20px;
            border-bottom-right-radius: 20px;
        }
        .header-title h2 { margin: 0; font-size: 1.2rem; }
        .header-title p { margin: 3px 0 0; font-size: 0.85rem; opacity: 0.9; }
        .profile-badge {
            background: rgba(255,255,255,0.2);
            padding: 5px 10px;
            border-radius: 50px;
            font-size: 0.8rem;
        }
        .main-content {
            padding: 15px;
            flex: 1;
            overflow-y: auto;
            padding-bottom: 70px;
        }
        .welcome-card {
            background: white;
            border-radius: 15px;
            padding: 15px;
            display: flex;
            align-items: center;
            gap: 15px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            margin-bottom: 15px;
        }
        .welcome-card img {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            object-fit: cover;
        }
        .grid-menu {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-bottom: 15px;
        }
        .menu-card {
            background: white;
            padding: 15px;
            border-radius: 14px;
            text-align: center;
            box-shadow: 0 2px 4px rgba(0,0,0,0.04);
            cursor: pointer;
            transition: transform 0.2s, background 0.2s;
            border: 2px solid transparent;
        }
        .menu-card:hover {
            transform: translateY(-3px);
            border-color: var(--primary);
        }
        .menu-card span { font-size: 2rem; display: block; margin-bottom: 5px; }
        .menu-card h4 { margin: 0; font-size: 0.95rem; color: #374151; }
        
        /* شاشات الأقسام الفرعية */
        .section-view {
            display: none;
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            animation: fadeIn 0.3s ease;
        }
        .section-view.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .back-btn {
            background: #e5e7eb;
            border: none;
            padding: 6px 12px;
            border-radius: 8px;
            cursor: pointer;
            margin-bottom: 15px;
            font-family: 'Cairo', sans-serif;
        }
        
        /* شريط التنقل السفلي */
        nav.bottom-nav {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.05);
            border-top-left-radius: 15px;
            border-top-right-radius: 15px;
        }
        .nav-item {
            text-align: center;
            font-size: 0.75rem;
            color: #6b7280;
            cursor: pointer;
            background: none;
            border: none;
        }
        .nav-item.active { color: var(--primary); font-weight: bold; }
        .nav-item span { font-size: 1.2rem; display: block; }

        /* تنسيق الأزرار والإدخال */
        .btn-action {
            background: var(--primary);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            width: 100%;
            font-family: 'Cairo', sans-serif;
            font-size: 1rem;
            cursor: pointer;
            margin-top: 10px;
        }
        .btn-action:hover { background: #4338ca; }
        input, select {
            width: 100%;
            padding: 10px;
            margin: 8px 0;
            border: 1px solid #d1d5db;
            border-radius: 8px;
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
        }
        
        /* شهادة التقدير */
        .certificate {
            border: 5px solid #d97706;
            padding: 20px;
            text-align: center;
            background: #fffbeb;
            border-radius: 10px;
            margin-top: 15px;
        }
    </style>
</head>
<body>

<div class="app-container">
    <!-- رأس التطبيق -->
    <header>
        <div class="header-title">
            <h2>StudySmart 🎓</h2>
            <p>الصف الأول الثانوي - العام الدراسي</p>
        </div>
        <div class="profile-badge">نيرة أحمد</div>
    </header>

    <!-- المحتوى الرئيسي -->
    <div class="main-content">
        
        <!-- الواجهة الرئيسية (القائمة) -->
        <div id="home-view" class="section-view active">
            <div class="welcome-card">
                <div style="font-size: 3rem;">👩‍🎓</div>
                <div>
                    <h3 style="margin:0 0 5px 0;">أهلاً بكِ يا نيرة!</h3>
                    <p style="margin:0; color:#6b7280; font-size:0.9rem;">مستعدة للتفوق في منهج أولى ثانوي؟</p>
                </div>
            </div>

            <div class="grid-menu">
                <div class="menu-card" onclick="showSection('ai-coach')">
                    <span>🤖</span>
                    <h4>المعلم الذكي</h4>
                </div>
                <div class="menu-card" onclick="showSection('library')">
                    <span>📚</span>
                    <h4>شرح وكتب الوزارة</h4>
                </div>
                <div class="menu-card" onclick="showSection('quizzes')">
                    <span>📝</span>
                    <h4>التقييمات الوزارية</h4>
                </div>
                <div class="menu-card" onclick="showSection('monthly-exam')">
                    <span>🏆</span>
                    <h4>امتحان الشهر</h4>
                </div>
                <div class="menu-card" onclick="showSection('reports')">
                    <span>📊</span>
                    <h4>التقارير وولي الأمر</h4>
                </div>
                <div class="menu-card" onclick="showSection('settings')">
                    <span>⚙️</span>
                    <h4>الإعدادات</h4>
                </div>
            </div>
        </div>

        <!-- 1. المعلم الذكي الصوتي -->
        <div id="ai-coach" class="section-view">
            <button class="back-btn" onclick="showSection('home-view')">← عودة للرئيسية</button>
            <h3>🤖 المعلم الذكي (مساعدك الصوتي)</h3>
            <p style="font-size: 0.9rem; color: #4b5563;">اسألي أي سؤال في المنهج وسيقوم المعلم بالرد الصوتي فوراً:</p>
            <input type="text5" id="user-question" placeholder="اكتبي سؤالك هنا (مثلاً: ما هي أهمية العلوم المتكاملة؟)">
            <button class="btn-action" onclick="askAICoach()">اسأل المعلم الذكي 🗣️</button>
            <div id="ai-response" style="margin-top: 15px; background: #f3f4f6; padding: 12px; border-radius: 8px; display: none;"></div>
        </div>

        <!-- 2. مكتبة الكتب (أولى ثانوي) -->
        <div id="library" class="section-view">
            <button class="back-btn" onclick="showSection('home-view')">← عودة للرئيسية</button>
            <h3>📚 مكتبة كتب الصف الأول الثانوي</h3>
            <p>اضغطي على أي كتاب ليفتح تلقائياً:</p>
            <ul style="padding-right: 20px; line-height: 2;">
                <li><a href="https://moe.gov.eg" target="_blank" style="color:var(--primary); font-weight:bold;">📖 كتاب العلوم المتكاملة - أولى ثانوي (وزارة التربية والتعليم)</a></li>
                <li><a href="https://moe.gov.eg" target="_blank" style="color:var(--primary); font-weight:bold;">📖 كتاب الفلسفة والمنطق - أولى ثانوي</a></li>
                <li><a href="https://moe.gov.eg" target="_blank" style="color:var(--primary); font-weight:bold;">📖 كتاب اللغة العربية واللغات الأجنبية</a></li>
            </ul>
        </div>

        <!-- 3. التقييمات الوزارية -->
        <div id="quizzes" class="section-view">
            <button class="back-btn" onclick="showSection('home-view')">← عودة للرئيسية</button>
            <h3>📝 التقييم الأسبوعي - العلوم المتكاملة</h3>
            <p>سؤال (1): ما هو المحور الرئيسي للعلوم المتكاملة؟</p>
            <label><input type="radio" name="q1" value="wrong"> دراسة كل علم بمعزل عن الآخر</label><br>
            <label><input type="radio" name="q1" value="correct"> تكامل العلوم الفيزيائية والكيميائية والبيولوجية لفهم الطبيعة</label><br>
            <button class="btn-action" onclick="submitQuiz()">تسليم الإجابة وإرسال النتيجة لولي الأمر</button>
            <div id="quiz-result" style="margin-top: 15px; font-weight: bold;"></div>
        </div>

        <!-- 4. امتحان الشهر وشهادة التقدير -->
        <div id="monthly-exam" class="section-view">
            <button class="back-btn" onclick="showSection('home-view')">← عودة للرئيسية</button>
            <h3>🏆 امتحان الشهر التجريبي</h3>
            <p>اختبري نفسك الآن في مقررات نوفمبر لاجتياز الشهادة:</p>
            <button class="btn-action" onclick="passExam()">ابدأ الامتحان واجتز بنجاح ✨</button>
            <div id="certificate-container"></div>
        </div>

        <!-- 5. التقارير وربط ولي الأمر واتساب -->
        <div id="reports" class="section-view">
            <button class="back-btn" onclick="showSection('home-view')">← عودة للرئيسية</button>
            <h3>📊 تقارير الأداء الموجهة لولي الأمر</h3>
            <p>رقم ولي الأمر المسجل: <b>+201xxxxxxxxx</b></p>
            <p style="color: #059669;">حالة الإرسال التلقائي: <b>مفعلة ✅</b></p>
            <button class="btn-action" style="background: #25D366;" onclick="sendWhatsAppReport()">إرسال تقرير اليوم عبر واتساب 💬</button>
        </div>

        <!-- 6. الإعدادات -->
        <div id="settings" class="section-view">
            <button class="back-btn" onclick="showSection('home-view')">← عودة للرئيسية</button>
            <h3>⚙️ إعدادات التطبيق</h3>
            <label>اسم الطالبة:</label>
            <input type="text" value="نيرة أحمد عبد الرحيم">
            <label>رقم هاتف ولي الأمر للإشعارات:</label>
            <input type="text" value="01xxxxxxxx">
            <button class="btn-action" onclick="alert('تم حفظ الإعدادات بنجاح!')">حفظ التغييرات</button>
        </div>

    </div>

    <!-- شريط التنقل السفلي -->
    <nav class="bottom-nav">
        <button class="nav-item active" onclick="showSection('home-view')">
            <span>🏠</span>الرئيسية
        </button>
        <button class="nav-item" onclick="showSection('ai-coach')">
            <span>🤖</span>المعلم
        </button>
        <button class="nav-item" onclick="showSection('library')">
            <span>📚</span>الكتب
        </button>
        <button class="nav-item" onclick="showSection('quizzes')">
            <span>📝</span>التقييمات
        </button>
        <button class="nav-item" onclick="showSection('reports')">
            <span>👤</span>حساب ولي الأمر
        </button>
    </nav>
</div>

<script>
    // التنقل بين الأقسام
    function showSection(sectionId) {
        document.querySelectorAll('.section-view').forEach(el => el.classList.remove('active'));
        document.getElementById(sectionId).classList.add('active');
    }

    // محاكاة المعلم الذكي الناطق (Text-to-Speech)
    function askAICoach() {
        const q = document.getElementById('user-question').value;
        const resDiv = document.getElementById('ai-response');
        if(!q) {
            alert('الرجاء كتابة سؤال أولاً');
            return;
        }
        resDiv.style.display = 'block';
        resDiv.innerHTML = "<b>المعلم الذكي:</b> أهلاً بكِ يا نيرة. سؤال ممتاز حول (" + q + "). العلوم المتكاملة تربط بين الكيمياء والفيزياء والأحياء لفهم الظواهر الكونية بشكل مترابط.";
        
        // تشغيل النطق الصوتي المباشر
        if ('speechSynthesis' in window) {
            const utterance = new SpeechSynthesisUtterance("أهلاً بك يا نيرة. الإجابة هي أن العلوم المتكاملة تربط بين العلوم المختلفة لفهم الطبيعة.");
            utterance.lang = 'ar-SA';
            window.speechSynthesis.speak(utterance);
        }
    }

    // تسليم التقييم وإرسال إشعار ولي الأمر
    function submitQuiz() {
        const resultDiv = document.getElementById('quiz-result');
        resultDiv.innerHTML = "✅ تم تصحيح التقييم بنجاح! الدرجة: 10/10. <br><span style='color:green;'>📩 تم إرسال رسالة نجاح تلقائية عبر واتساب لولي الأمر برقم الهاتف المسجل.</span>";
    }

    // اجتياز الامتحان وإصدار شهادة تقدير
    function passExam() {
        const certContainer = document.getElementById('certificate-container');
        certContainer.innerHTML = `
            <div class="certificate">
                <h2 style="color: #b45309; margin:0;">شهادة تقدير وتفوق 🌟</h2>
                <p>تمنح هذه الشهادة للطالبة المتميزة:</p>
                <h3 style="color: #1e3a8a;">نيرة أحمد عبد الرحيم</h3>
                <p>لاجتيازها امتحان شهر نوفمبر في منهج أولى ثانوي بتقدير امتياز (98%)</p>
                <p style="font-size: 0.8rem; color: #6b7280;">منصة StudySmart التعليمية</p>
            </div>
        `;
        alert("🎉 مبروك يا نيرة! تم حفظ النتيجة وإصدار شهادة التقدير وإرسالها لولي الأمر.");
    }

    // محاكاة إرسال واتساب
    function sendWhatsAppReport() {
        alert("💬 تم إرسال تقرير أداء اليوم ونقاط التقييم مباشرة إلى رقم واتساب ولي الأمر بنجاح!");
    }
</script>

</body>
</html>
