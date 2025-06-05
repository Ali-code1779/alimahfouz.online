<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>🍽️ Restaurant Qualification Apps</title>
  <style>
    :root {
      --main-color: #1d4ed8;
      --main-dark: #172554;
      --text-color: #1e293b;
      --bg-light: #f8fafc;
      --bg-dark: #0f172a;
      --gray: #94a3b8;
    }

    body {
      font-family: 'Segoe UI', Tahoma, sans-serif;
      margin: 0;
      padding: 0;
      background: var(--bg-light);
      color: var(--text-color);
      font-size: clamp(14px, 1.2vw, 18px);
      transition: all 0.3s ease;
    }

    body.dark-mode {
      background: var(--bg-dark);
      color: white;
    }

    header {
      background: var(--main-color);
      color: white;
      padding: 10px 20px;
    }

    .top-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
    }

    .logo {
      font-size: 1.2rem;
      font-weight: bold;
    }

    .controls {
      display: flex;
      align-items: center;
      gap: 10px;
      flex-wrap: wrap;
    }

    .controls button {
      background: white;
      color: var(--main-color);
      padding: 6px 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
    }

    .datetime {
      font-size: 0.85rem;
      margin-left: 15px;
      white-space: nowrap;
    }

    main {
      max-width: 1000px;
      margin: 30px auto;
      padding: 20px;
      text-align: center;
    }

    .hero img {
      max-width: 100%;
      max-height: 240px;
      margin: 20px auto;
    }

    .features {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 20px;
      margin-top: 30px;
    }

    .feature {
      background: #e2e8f0;
      padding: 15px;
      border-radius: 10px;
      transition: transform 0.2s;
    }

    body.dark-mode .feature {
      background: #1e293b;
    }

    .feature:hover {
      transform: translateY(-5px);
    }

    footer {
      text-align: center;
      padding: 15px;
      color: var(--gray);
      font-size: 0.9rem;
    }

    .rtl {
      direction: rtl;
      text-align: right;
    }
  </style>
</head>
<body>
  <header>
    <div class="top-bar">
      <div class="logo" id="logo">🍽️ <span id="appName">Restaurant Apps</span></div>
      <div class="controls">
        <div class="datetime" id="datetime"></div>
        <button id="homeBtn">🏠 الرئيسية</button>
        <button id="helpBtn">❓ المساعدة</button>
        <button id="aboutBtn">ℹ️ من نحن</button>
        <button id="langBtn">العربية</button>
        <button id="themeBtn">🌙</button>
        <button id="loginBtn">🔐 تسجيل الدخول</button>
      </div>
    </div>
  </header>

  <main>
    <div class="hero">
      <h1 id="mainTitle">🍽️ Restaurant Qualification Apps</h1>
      <p id="mainDesc">Smart solutions for modern restaurants – track quality, speed, and alerts in one system.</p>
      <img src="https://via.placeholder.com/300x200?text=🍽️+Illustration" alt="Illustration" />
    </div>

    <div class="features">
      <div class="feature">
        <h3 id="f1">🔔 Smart Alerts</h3>
        <p id="f1d">Get notified instantly when actions are needed in your restaurant.</p>
      </div>
      <div class="feature">
        <h3 id="f2">📊 Analytics</h3>
        <p id="f2d">Review performance and waste metrics in real-time.</p>
      </div>
      <div class="feature">
        <h3 id="f3">⏱️ Timers</h3>
        <p id="f3d">Track customer service speed and optimize operations.</p>
      </div>
    </div>
  </main>

  <footer>
    &copy; 2025 🍽️ Restaurant Qualification Apps. All rights reserved.
  </footer>

  <script>
    const translations = {
      en: {
        homeBtn: "🏠 Home",
        helpBtn: "❓ Help",
        aboutBtn: "ℹ️ About",
        langBtn: "العربية",
        loginBtn: "🔐 Login",
        mainTitle: "🍽️ Restaurant Qualification Apps",
        mainDesc: "Smart solutions for modern restaurants – track quality, speed, and alerts in one system.",
        f1: "🔔 Smart Alerts",
        f1d: "Get notified instantly when actions are needed in your restaurant.",
        f2: "📊 Analytics",
        f2d: "Review performance and waste metrics in real-time.",
        f3: "⏱️ Timers",
        f3d: "Track customer service speed and optimize operations.",
        appName: "Restaurant Apps"
      },
      ar: {
        homeBtn: "🏠 الرئيسية",
        helpBtn: "❓ المساعدة",
        aboutBtn: "ℹ️ من نحن",
        langBtn: "English",
        loginBtn: "🔐 تسجيل الدخول",
        mainTitle: "🍽️ تطبيق تأهيل المطاعم",
        mainDesc: "حلول ذكية للمطاعم الحديثة – راقب الجودة والسرعة والتنبيهات في نظام واحد.",
        f1: "🔔 تنبيهات ذكية",
        f1d: "احصل على تنبيهات فورية عند الحاجة لاتخاذ إجراء داخل المطعم.",
        f2: "📊 التحليلات",
        f2d: "استعرض الأداء ومؤشرات الهدر مباشرة.",
        f3: "⏱️ مؤقتات الخدمة",
        f3d: "تتبع سرعة الخدمة وتحسين العمليات.",
        appName: "تطبيق المطاعم"
      }
    };

    let currentLang = localStorage.getItem("lang") || "en";

    // تحديث النصوص حسب اللغة
    function applyLanguage(lang) {
      const t = translations[lang];
      for (const id in t) {
        const el = document.getElementById(id);
        if (el) el.innerText = t[id];
      }

      document.body.classList.toggle("rtl", lang === "ar");
      document.documentElement.setAttribute("dir", lang === "ar" ? "rtl" : "ltr");
      document.documentElement.setAttribute("lang", lang);

      localStorage.setItem("lang", lang);
      updateDateTime();
    }

    // تحديث التاريخ والوقت كل دقيقة
    const datetime = document.getElementById("datetime");
    function updateDateTime() {
      const now = new Date();
      const options = {
        weekday: 'short', year: 'numeric', month: 'short',
        day: 'numeric', hour: '2-digit', minute: '2-digit'
      };
      datetime.innerText = now.toLocaleString(currentLang === 'ar' ? 'ar-EG' : 'en-US', options);
    }
    updateDateTime();
    setInterval(updateDateTime, 60000);

    // أزرار التنقل بالصفحات
    document.getElementById("homeBtn").addEventListener("click", () => {
      window.location.href = "index.html";  // الصفحة الرئيسية
    });
    document.getElementById("helpBtn").addEventListener("click", () => {
      window.location.href = "help.html";
    });
    document.getElementById("aboutBtn").addEventListener("click", () => {
      window.location.href = "about.html";
    });
    document.getElementById("loginBtn").addEventListener("click", () => {
      window.location.href = "login.html";
    });

    // زر تبديل اللغة
    document.getElementById("langBtn").addEventListener("click", () => {
      currentLang = currentLang === "en" ? "ar" : "en";
      applyLanguage(currentLang);
    });

    // زر الوضع الليلي
    document.getElementById("themeBtn").addEventListener("click", () => {
      document.body.classList.toggle("dark-mode");
      localStorage.setItem("theme", document.body.classList.contains("dark-mode") ? "dark" : "light");
    });

    // تحميل إعدادات الوضع الليلي من التخزين المحلي
    if (localStorage.getItem("theme") === "dark") {
      document.body.classList.add("dark-mode");
    }

    // تطبيق اللغة عند تحميل الصفحة
    applyLanguage(currentLang);
  </script>
</body>
</html>
