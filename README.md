   <!-- Font Awesome 6 (أيقونات) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- Google Fonts: خطوط متنوعة دعم اللغات -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&family=Cairo:wght@400;500;600;700&family=Noto+Sans+JP:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        * {حج
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #f1f5f9;
            font-family: 'Inter', 'Cairo', 'Noto Sans JP', sans-serif;
            color: #0f172a;
            transition: all 0.2s;
        }

        /* دعم اللغة العربية */
        [dir="rtl"] {
            font-family: 'Cairo', 'Inter', 'Noto Sans JP', sans-serif;
        }

        /* الحاوية الرئيسية */
        .app-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 1.5rem 2rem;
        }

        /* الهيدر */
        .hero {
            text-align: center;
            margin-bottom: 2rem;
        }
        .hero h1 {
            font-size: 2.6rem;
            font-weight: 800;
            background: linear-gradient(135deg, #0f2b4d, #1e4a76);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            display: inline-flex;
            align-items: center;
            gap: 12px;
        }
        .hero h1 i {
            background: none;
            color: #2563eb;
        }
        .hero p {
            color: #334155;
            font-weight: 500;
            margin-top: 0.5rem;
        }

        /* شريط اللغة والبحث */
        .search-panel {
            background: white;
            border-radius: 56px;
            padding: 0.5rem;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 12px;
            justify-content: space-between;
            box-shadow: 0 8px 20px rgba(0,0,0,0.05);
            margin-bottom: 2rem;
            border: 1px solid #e2e8f0;
        }
        .lang-selector {
            display: flex;
            background: #f1f5f9;
            border-radius: 48px;
            padding: 0.2rem;
            gap: 0.2rem;
        }
        .lang-btn {
            border: none;
            background: transparent;
            padding: 0.6rem 1.2rem;
            border-radius: 40px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            font-family: inherit;
            font-size: 0.9rem;
        }
        .lang-btn.active {
            background: #1e293b;
            color: white;
            box-shadow: 0 2px 6px rgba(0,0,0,0.1);
        }
        .search-box-wrapper {
            flex: 1;
            display: flex;
            min-width: 200px;
        }
        .search-input {
            flex: 1;
            border: 1px solid #e2e8f0;
            border-radius: 48px;
            padding: 0.8rem 1.5rem;
            font-size: 1rem;
            font-family: inherit;
            outline: none;
            transition: 0.2s;
        }
        .search-input:focus {
            border-color: #3b82f6;
            box-shadow: 0 0 0 2px #bfdbfe;
        }
        .search-btn {
            background: #0f172a;
            border: none;
            color: white;
            padding: 0 1.8rem;
            border-radius: 48px;
            margin-right: 10px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .search-btn:hover {
            background: #1e3a8a;
            transform: scale(0.97);
        }

        /* حالة التحميل */
        .loading {
            text-align: center;
            padding: 3rem;
            color: #2563eb;
        }

        /* شبكة النتائج */
        .results-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(330px, 1fr));
            gap: 1.8rem;
            margin-top: 1rem;
        }

        /* بطاقة المقال */
        .wiki-card {
            background: white;
            border-radius: 28px;
            overflow: hidden;
            transition: all 0.25s;
            box-shadow: 0 6px 14px rgba(0,0,0,0.05);
            border: 1px solid #eef2ff;
            display: flex;
            flex-direction: column;
        }
        .wiki-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 25px -12px rgba(0,0,0,0.2);
        }
        .card-img {
            height: 180px;
            background-color: #eef2ff;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            position: relative;
        }
        .card-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: 0.3s;
        }
        .card-img .no-img {
            color: #94a3b8;
            font-size: 2.5rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
        }
        .card-content {
            padding: 1.2rem 1.2rem 1rem;
            flex: 1;
        }
        .card-title {
            font-size: 1.35rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            color: #0f172a;
        }
        .card-excerpt {
            font-size: 0.85rem;
            color: #334155;
            line-height: 1.45;
            margin-bottom: 1rem;
            display: -webkit-box;
            -webkit-line-clamp: 3;
            line-clamp: 3;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }
        .card-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.8rem 1.2rem 1.2rem;
            border-top: 1px solid #f0f2f5;
        }
        .analyze-btn {
            background: #f1f5f9;
            border: none;
            padding: 0.4rem 1rem;
            border-radius: 40px;
            font-weight: 600;
            font-size: 0.75rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 6px;
            transition: 0.2s;
        }
        .analyze-btn:hover {
            background: #e2e8f0;
        }
        .wiki-link {
            color: #3b82f6;
            text-decoration: none;
            font-size: 0.8rem;
            font-weight: 500;
        }

        /* مودال التحليل */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.6);
            backdrop-filter: blur(4px);
            align-items: center;
            justify-content: center;
            z-index: 1000;
        }
        .modal-content {
            background: white;
            max-width: 550px;
            width: 90%;
            border-radius: 36px;
            padding: 1.6rem;
            direction: ltr;
            box-shadow: 0 30px 40px rgba(0,0,0,0.3);
            animation: fadeInUp 0.2s ease;
        }
        [dir="rtl"] .modal-content {
            direction: rtl;
            text-align: right;
        }
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #eef2ff;
            padding-bottom: 0.8rem;
            margin-bottom: 1rem;
        }
        .close-modal {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
        }
        .analysis-stats {
            background: #f8fafc;
            border-radius: 24px;
            padding: 1rem;
            margin: 1rem 0;
        }
        .keyword-cloud {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 12px;
        }
        .keyword-tag {
            background: #e2e8f0;
            padding: 4px 12px;
            border-radius: 40px;
            font-size: 0.75rem;
            font-weight: 500;
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(20px);}
            to { opacity: 1; transform: translateY(0);}
        }

        .no-results {
            text-align: center;
            padding: 4rem;
            background: white;
            border-radius: 48px;
            margin-top: 1rem;
        }

        footer {
            text-align: center;
            margin-top: 3rem;
            color: #5b6e8c;
            font-size: 0.8rem;
        }
        @media (max-width: 750px) {
            .app-container { padding: 1rem; }
            .search-panel { flex-direction: column; align-items: stretch; border-radius: 28px; }
            .search-box-wrapper { width: 100%; }
            .search-btn { margin-right: 0; margin-top: 6px; justify-content: center; }
        }
    </style>
</head>
<body>
<div class="app-container">
    <div class="hero"> <style>
        :root {
            --bg: #f9fafb;
            --card-bg: #ffffff;
            --text: #1f2937;
            --text-light: #6b7280;
            --primary: #0f766e;
            --primary-light: #14b8a6;
            --secondary: #3b82f6;
            --accent: #f59e0b;
            --border: #e5e7eb;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.1);
            --shadow-lg: 0 10px 25px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1);
            --radius: 16px;
            --transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            --font-heading: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            --font-body: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        [dir="ltr"] {
            --font-heading: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            --font-body: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-body);
            background: #f0fdf4;
            background-image:
                radial-gradient(ellipse at 10% 20%, rgba(20, 184, 166, 0.05) 0%, transparent 60%),
                radial-gradient(ellipse at 90% 80%, rgba(59, 130, 246, 0.05) 0%, transparent 60%),
                radial-gradient(ellipse at 50% 50%, rgba(245, 158, 11, 0.03) 0%, transparent 60%);
            color: var(--text);
            line-height: 1.7;
            min-height: 100vh;
            transition: background 0.5s;
        }

        /* ============ HEADER ============ */
        .header {
            background: linear-gradient(135deg, #0f766e 0%, #115e59 30%, #0d9488 60%, #0f766e 100%);
            background-size: 200% 200%;
            animation: gradientShift 8s ease infinite;
            color: #fff;
            padding: 16px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 20px rgba(15, 118, 110, 0.3);
            backdrop-filter: blur(10px);
        }
        @keyframes gradientShift {
            0%,
            100% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
        }
        .header-inner {
            max-width: 1300px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 12px;
        }
        .logo-area {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .logo-icon {
            width: 48px;
            height: 48px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            backdrop-filter: blur(4px);
            transition: transform 0.3s;
        }
        .logo-icon:hover {
            transform: rotate(15deg) scale(1.1);
        }
        .logo-text {
            font-size: 1.5rem;
            font-weight: 800;
            letter-spacing: -0.5px;
            font-family: var(--font-heading);
        }
        .logo-sub {
            font-size: 0.75rem;
            opacity: 0.85;
            font-weight: 400;
        }

        /* Language Switcher */
        .lang-switcher {
            display: flex;
            gap: 6px;
            background: rgba(255, 255, 255, 0.15);
            border-radius: 30px;
            padding: 4px;
            backdrop-filter: blur(6px);
            flex-wrap: wrap;
        }
        .lang-btn {
            padding: 8px 16px;
            border-radius: 26px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.9rem;
            transition: all 0.3s;
            background: transparent;
            color: #fff;
            white-space: nowrap;
            font-family: var(--font-body);
        }
        .lang-btn.active {
            background: #fff;
            color: #0f766e;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
        }
        .lang-btn:hover:not(.active) {
            background: rgba(255, 255, 255, 0.25);
        }
        .lang-flag {
            margin-right: 4px;
        }

        /* ============ HERO ============ */
        .hero {
            text-align: center;
            padding: 50px 20px 40px;
            max-width: 900px;
            margin: 0 auto;
        }
        .hero h1 {
            font-size: 2.5rem;
            font-weight: 900;
            color: #0f766e;
            margin-bottom: 8px;
            font-family: var(--font-heading);
            letter-spacing: -1px;
        }
        .hero .subtitle {
            font-size: 1.15rem;
            color: #6b7280;
            max-width: 600px;
            margin: 0 auto;
        }
        .hero-emoji-row {
            font-size: 3rem;
            margin-bottom: 10px;
            animation: float 3s ease-in-out infinite;
        }
        @keyframes float {
            0%,
            100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-15px);
            }
        }

        /* ============ MAIN CONTAINER ============ */
        .main-container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 0 20px 60px;
        }

        /* ============ TABS ============ */
        .tab-nav {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            justify-content: center;
            margin-bottom: 30px;
        }
        .tab-btn {
            padding: 14px 24px;
            border-radius: 30px;
            border: 2px solid #e5e7eb;
            cursor: pointer;
            font-weight: 700;
            font-size: 1rem;
            transition: all 0.3s;
            background: #fff;
            color: #374151;
            display: flex;
            align-items: center;
            gap: 8px;
            font-family: var(--font-body);
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
        }
        .tab-btn:hover {
            border-color: #14b8a6;
            color: #0f766e;
            transform: translateY(-2px);
            box-shadow: var(--shadow);
        }
        .tab-btn.active {
            background: #0f766e;
            color: #fff;
            border-color: #0f766e;
            box-shadow: var(--shadow-lg);
        }
        .tab-icon {
            font-size: 1.4rem;
        }
         </style>
<h1>1تراخيصنا</h1>
<hr><a href="https://www.Google.com">رخص تحديثbnk</a>
<hr>Gmail: mohammedmekk23@gmail.com
<hr />Google مالكة النظام
<hr /><p> دعم مستمر</p> 
<hr />حماية شخصية <a href="https://www.Google.com">Google.com</a>
<hr />
<h1>المعالج</h1>
<hr />انفديا معالج
<hr /><a href="http://www.apache.org/licenses/">رسمي موقع</a>
<hr /><h1>المكتوب</h1>
<hr>
apex/com.google.android.sdkext.apex
Android
To obtain the source code for third-party components where the open source license grants you the right to receive the source go to https://source.android.com/opensourcerequest
MIT OR Apache-2.0 WITH LLVM-exception
=====================================


MIT License
-----------

Copyright (c) 1999-2022, Arm Limited.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


Apache-2.0 WITH LLVM-exception
------------------------------

                                Apache License
                           Version 2.0, January 2004
                        http://www.apache.org/licenses/

    TERMS AND CONDITIONS FOR USE, REPRODUCTION, AND DISTRIBUTION

    1. Definitions.

      "License" shall mean the terms and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, direct or indirect, to cause the
      direction or management of such entity, whether by contract or
      otherwise, or (ii) ownership of fifty percent (50%) or more of the
      outstanding shares, or (iii) beneficial ownership of such entity.

      "You" (or "Your") shall mean an individual or Legal Entity
      exercising permissions granted by this License.

      "Source" form shall mean the preferred form for making modifications,
      including but not limited to software source code, documentation
      source, and configuration files.

      "Object" form shall mean any form resulting from mechanical
      transformation or translation of a Source form, including but
      not limited to compiled object code, generated documentation,
      and conversions to other media types.

      "Work" shall mean the work of authorship, whether in Source or
      Object form, made available under the License, as indicated by a
      <hr><h1>معلومات كثير </h1>
<hr>
and conditions for use, reproduction,
      and distribution as defined by Sections 1 through 9 of this document.

      "Licensor" shall mean the copyright owner or entity authorized by
      the copyright owner that is granting the License.

      "Legal Entity" shall mean the union of the acting entity and all
      other entities that control, are controlled by, or are under common
      control with that entity. For the purposes of this definition,
      "control" means (i) the power, HTHL 
