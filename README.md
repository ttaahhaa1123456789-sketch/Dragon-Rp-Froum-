<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DRAGON RP FORUM | فروم گیمینگ</title>
    
    <!-- فونت‌های گیمینگ -->
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@400;700;900&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Exo+2:wght@400;700;900&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Audiowide&display=swap" rel="stylesheet">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #00f7ff;
            --primary-glow: #00ffff;
            --secondary: #ff00ff;
            --secondary-glow: #ff33ff;
            --accent: #ffff00;
            --accent-glow: #ffff33;
            --dark: #030014;
            --darker: #000000;
        }

        body {
            font-family: 'Exo 2', 'Rajdhani', 'Orbitron', sans-serif;
            background: #000;
            color: #fff;
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
        }

        /* پس زمینه سایبرپانک */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 30%, rgba(0, 255, 255, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 80% 70%, rgba(255, 0, 255, 0.15) 0%, transparent 50%),
                repeating-linear-gradient(45deg, 
                    rgba(0, 255, 255, 0.02) 0px,
                    rgba(0, 255, 255, 0.02) 2px,
                    rgba(255, 0, 255, 0.02) 2px,
                    rgba(255, 0, 255, 0.02) 4px,
                    transparent 4px,
                    transparent 8px
                );
            pointer-events: none;
            z-index: 0;
            animation: matrixPulse 8s ease-in-out infinite;
        }

        @keyframes matrixPulse {
            0%, 100% { opacity: 1; filter: hue-rotate(0deg); }
            50% { opacity: 0.8; filter: hue-rotate(30deg); }
        }

        /* ذرات سه‌بعدی */
        .cyber-particle {
            position: fixed;
            width: 4px;
            height: 4px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border-radius: 50%;
            filter: blur(1px);
            pointer-events: none;
            z-index: 1;
            animation: float3D 15s linear infinite;
            box-shadow: 0 0 15px currentColor;
        }

        @keyframes float3D {
            0% { transform: translateY(100vh) translateX(0) rotate(0deg); opacity: 0; }
            10% { opacity: 0.8; }
            90% { opacity: 0.8; }
            100% { transform: translateY(-100vh) translateX(100px) rotate(360deg); opacity: 0; }
        }

        /* خطوط اسکن */
        .scan-line {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--primary), var(--secondary), transparent);
            animation: scan 4s linear infinite;
            z-index: 1;
            opacity: 0.5;
        }

        @keyframes scan {
            0% { transform: translateY(-50%) translateX(-100%); }
            100% { transform: translateY(-50%) translateX(100%); }
        }

        /* ===== Navbar ===== */
        .navbar {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.85);
            backdrop-filter: blur(15px);
            display: flex;
            gap: 15px;
            padding: 15px 30px;
            border-radius: 60px;
            z-index: 1000;
            border: 2px solid var(--primary);
            box-shadow: 0 0 30px var(--primary), 0 0 60px var(--secondary);
            animation: navbarGlow 3s infinite;
        }

        @keyframes navbarGlow {
            0%, 100% { box-shadow: 0 0 30px var(--primary), 0 0 60px var(--secondary); }
            50% { box-shadow: 0 0 50px var(--secondary), 0 0 90px var(--primary); }
        }

        .navbar a {
            text-decoration: none;
            color: #fff;
            padding: 12px 25px;
            border-radius: 40px;
            font-size: 16px;
            font-weight: 700;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
            text-transform: uppercase;
            letter-spacing: 1px;
            border: 1px solid rgba(0, 247, 255, 0.3);
        }

        .navbar a::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 247, 255, 0.3), transparent);
            transition: 0.5s;
        }

        .navbar a:hover::before {
            left: 100%;
        }

        .navbar a:hover {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: #000;
            box-shadow: 0 0 30px var(--primary), 0 0 60px var(--secondary);
            transform: scale(1.05) translateY(-2px);
            border-color: transparent;
        }

        /* ===== Main Container ===== */
        .container {
            position: relative;
            z-index: 2;
            padding-top: 120px;
            padding-bottom: 40px;
            max-width: 1400px;
            margin: 0 auto;
        }

        /* ===== Sections ===== */
        .section {
            display: none;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(15px);
            border-radius: 40px;
            padding: 40px;
            margin: 20px;
            border: 2px solid transparent;
            box-shadow: 0 0 40px rgba(0, 247, 255, 0.3);
            animation: sectionAppear 0.5s ease;
            position: relative;
            overflow: hidden;
        }

        .section.active {
            display: block;
            animation: borderGlow 4s infinite;
        }

        @keyframes borderGlow {
            0%, 100% { border-color: var(--primary); box-shadow: 0 0 40px var(--primary); }
            50% { border-color: var(--secondary); box-shadow: 0 0 60px var(--secondary); }
        }

        .section::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, var(--primary), var(--secondary), var(--accent));
            border-radius: 40px;
            z-index: -1;
            opacity: 0.3;
            animation: borderRotate 6s linear infinite;
        }

        @keyframes borderRotate {
            0% { filter: hue-rotate(0deg); }
            100% { filter: hue-rotate(360deg); }
        }

        @keyframes sectionAppear {
            from {
                opacity: 0;
                transform: translateY(30px) scale(0.95);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .section h2 {
            color: #fff;
            font-size: 48px;
            font-weight: 900;
            text-align: center;
            margin-bottom: 40px;
            font-family: 'Audiowide', cursive;
            text-transform: uppercase;
            background: linear-gradient(135deg, var(--primary), var(--secondary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px var(--primary), 0 0 60px var(--secondary);
            letter-spacing: 4px;
            animation: titlePulse 3s infinite;
        }

        @keyframes titlePulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .section h3 {
            color: var(--accent);
            font-size: 28px;
            font-weight: 900;
            margin: 30px 0 20px;
            text-shadow: 0 0 20px var(--accent);
            font-family: 'Audiowide', cursive;
        }

        /* ===== Form Grid ===== */
        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .form-group {
            margin-bottom: 15px;
            position: relative;
        }

        .form-group label {
            display: block;
            margin-bottom: 10px;
            color: var(--primary);
            font-weight: 700;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
            text-shadow: 0 0 10px var(--primary);
        }

        input, select, textarea {
            width: 100%;
            padding: 15px 20px;
            border: 2px solid var(--primary);
            border-radius: 15px;
            background: rgba(0, 0, 0, 0.6);
            color: #fff;
            font-family: 'Exo 2', sans-serif;
            font-size: 16px;
            transition: all 0.3s;
            outline: none;
            box-shadow: 0 0 15px rgba(0, 247, 255, 0.2);
        }

        input:focus, select:focus, textarea:focus {
            border-color: var(--secondary);
            box-shadow: 0 0 30px var(--secondary);
            transform: scale(1.02);
            background: rgba(0, 0, 0, 0.8);
        }

        input::placeholder, textarea::placeholder {
            color: rgba(255, 255, 255, 0.4);
            font-size: 14px;
        }

        textarea {
            resize: vertical;
            min-height: 100px;
        }

        input[type="file"] {
            padding: 12px;
            background: rgba(0, 247, 255, 0.1);
            border-style: dashed;
            cursor: pointer;
            border-color: var(--accent);
        }

        input[type="file"]:hover {
            box-shadow: 0 0 30px var(--accent);
        }

        input[type="file"]::-webkit-file-upload-button {
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: #000;
            padding: 10px 20px;
            border: none;
            border-radius: 10px;
            font-weight: 900;
            cursor: pointer;
            margin-left: 15px;
            transition: 0.3s;
        }

        input[type="file"]::-webkit-file-upload-button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 20px var(--primary);
        }

        select {
            cursor: pointer;
            appearance: none;
            background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 24 24' fill='none' stroke='%2300f7ff' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'><polyline points='6 9 12 15 18 9'/></svg>");
            background-repeat: no-repeat;
            background-position: left 15px center;
            background-size: 16px;
        }

        /* ===== Buttons ===== */
        .btn-group {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 40px;
        }

        button {
            padding: 16px 40px;
            border: none;
            border-radius: 50px;
            font-weight: 900;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
            letter-spacing: 2px;
            font-family: 'Orbitron', sans-serif;
            text-transform: uppercase;
            border: 2px solid transparent;
        }

        button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
            transition: 0.5s;
        }

        button:hover::before {
            left: 100%;
        }

        button:hover {
            transform: scale(1.05) translateY(-3px);
            box-shadow: 0 0 30px currentColor;
            border-color: #fff;
        }

        .btn-send {
            background: linear-gradient(45deg, #00ffae, #00ccff);
            color: #000;
            box-shadow: 0 0 20px #00ffae;
        }

        .btn-admin {
            background: linear-gradient(45deg, #1e90ff, #0066ff);
            color: #fff;
            box-shadow: 0 0 20px #1e90ff;
        }

        .btn-ok {
            background: linear-gradient(45deg, #00ff00, #00cc00);
            color: #000;
            box-shadow: 0 0 20px #00ff00;
        }

        .btn-no {
            background: linear-gradient(45deg, #ff004c, #ff0000);
            color: #fff;
            box-shadow: 0 0 20px #ff004c;
        }

        /* ===== Cards ===== */
        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .card {
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            border-radius: 25px;
            padding: 25px;
            border: 2px solid var(--primary);
            box-shadow: 0 0 25px rgba(0, 247, 255, 0.3);
            transition: all 0.4s;
            position: relative;
            overflow: hidden;
            animation: cardFloat 5s infinite;
        }

        .card:nth-child(even) {
            animation-delay: 1s;
        }

        @keyframes cardFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .card:hover {
            transform: translateY(-15px) scale(1.02);
            border-color: var(--secondary);
            box-shadow: 0 0 40px var(--secondary), 0 0 80px var(--primary);
        }

        .card::after {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, var(--primary), var(--secondary), var(--accent));
            border-radius: 25px;
            z-index: -1;
            opacity: 0;
            transition: opacity 0.4s;
        }

        .card:hover::after {
            opacity: 1;
            animation: borderRotate 3s linear infinite;
        }

        .card p {
            margin-bottom: 12px;
            font-size: 14px;
            line-height: 1.7;
            color: #ccc;
        }

        .card strong {
            color: var(--primary);
            font-weight: 900;
            text-shadow: 0 0 10px var(--primary);
        }

        .card-badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background: linear-gradient(45deg, var(--secondary), var(--accent));
            color: #fff;
            padding: 6px 15px;
            border-radius: 30px;
            font-size: 12px;
            font-weight: 900;
            box-shadow: 0 0 20px var(--secondary);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .card-actions {
            display: flex;
            gap: 12px;
            margin-top: 20px;
        }

        .card-actions button {
            flex: 1;
            padding: 12px;
            font-size: 14px;
        }

        /* ===== Admin Panel ===== */
        #adminBox {
            margin-top: 40px;
        }

        .admin-login {
            max-width: 450px;
            margin: 0 auto;
            text-align: center;
            padding: 30px;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 30px;
            border: 2px solid var(--secondary);
            box-shadow: 0 0 40px var(--secondary);
        }

        /* ===== Footer ===== */
        footer {
            text-align: center;
            color: var(--primary);
            padding: 40px;
            font-weight: 900;
            font-size: 20px;
            position: relative;
            z-index: 2;
            text-shadow: 0 0 15px var(--primary);
            margin-top: 60px;
            border-top: 2px solid var(--primary);
            box-shadow: 0 -5px 40px rgba(0, 247, 255, 0.3);
            background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(10px);
        }

        footer span {
            color: var(--secondary);
            text-shadow: 0 0 15px var(--secondary);
        }

        /* ===== Toast Notification ===== */
        .toast {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: rgba(0, 0, 0, 0.95);
            border: 2px solid var(--primary);
            border-radius: 50px;
            padding: 15px 30px;
            color: #fff;
            font-weight: 900;
            box-shadow: 0 0 30px var(--primary);
            z-index: 2000;
            animation: slideIn 0.3s ease;
            font-size: 16px;
            backdrop-filter: blur(10px);
        }

        @keyframes slideIn {
            from {
                transform: translateX(100%) scale(0.8);
                opacity: 0;
            }
            to {
                transform: translateX(0) scale(1);
                opacity: 1;
            }
        }

        /* ===== Loading Animation ===== */
        .loading {
            display: inline-block;
            width: 25px;
            height: 25px;
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: var(--primary);
            border-right-color: var(--secondary);
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* ===== Responsive ===== */
        @media (max-width: 900px) {
            .navbar {
                width: 95%;
                padding: 10px 15px;
                gap: 8px;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .navbar a {
                padding: 8px 15px;
                font-size: 13px;
            }
            
            .section {
                padding: 25px;
                margin: 10px;
            }
            
            .section h2 {
                font-size: 32px;
            }
            
            .form-grid {
                grid-template-columns: 1fr;
            }
            
            .btn-group {
                flex-direction: column;
            }
            
            button {
                width: 100%;
            }
        }

        @media (max-width: 480px) {
            .section h2 {
                font-size: 26px;
            }
            
            .navbar a {
                padding: 6px 10px;
                font-size: 12px;
            }
        }
    </style>
</head>
<body>

    <!-- ذرات سایبرپانک -->
    <script>
        for (let i = 0; i < 30; i++) {
            const particle = document.createElement('div');
            particle.className = 'cyber-particle';
            particle.style.left = Math.random() * 100 + '%';
            particle.style.animationDelay = Math.random() * 10 + 's';
            particle.style.background = `hsl(${Math.random() * 60 + 180}, 100%, 50%)`;
            document.body.appendChild(particle);
        }

        // خطوط اسکن
        for (let i = 0; i < 3; i++) {
            const line = document.createElement('div');
            line.className = 'scan-line';
            line.style.top = (20 + i * 30) + '%';
            line.style.animationDelay = i * 0.5 + 's';
            document.body.appendChild(line);
        }
    </script>

    <!-- Navbar -->
    <nav class="navbar">
        <a href="#" data-target="gov">🏛️ فروم دولت</a>
        <a href="#" data-target="ghetto">💀 فروم گتو</a>
        <a href="#" data-target="admin">⚡ پنل مدیریت</a>
    </nav>

    <div class="container">

        <!-- فروم دولت -->
        <section id="gov" class="section active">
            <h2>🏛️ فرم درخواست دولت</h2>
            
            <div class="form-grid">
                <div class="form-group">
                    <label>👤 نام اکانت</label>
                    <input type="text" id="gov_accName" placeholder="Dragon_Player">
                </div>
                
                <div class="form-group">
                    <label>📊 لول</label>
                    <input type="number" id="gov_accLevel" placeholder="5">
                </div>
                                
                <div class="form-group">
                    <label>📎 آپلود اسکرین‌شات</label>
                    <input type="file" id="gov_file" accept="image/*">
                </div>
                
                <div class="form-group">
                    <label>📘 Wbook</label>
                    <input type="text" id="gov_wbook" placeholder="100">
                </div>
                
                <div class="form-group">
                    <label>👤 نام واقعی</label>
                    <input type="text" id="gov_realName" placeholder="نام و نام خانوادگی">
                </div>
                
                <div class="form-group">
                    <label>🎂 سن واقعی</label>
                    <input type="number" id="gov_realAge" placeholder="20">
                </div>
                
                <div class="form-group">
                    <label>📱 آیدی روبیکا</label>
                    <input type="text" id="gov_rubikaID" placeholder="@username">
                </div>
                
                <div class="form-group">
                    <label>⏰ تایم پلی روزانه</label>
                    <input type="text" id="gov_playTime" placeholder="4-5 ساعت">
                </div>
                
                <div class="form-group" style="grid-column: 1 / -1;">
                    <label>🎯 هدف از لیدری</label>
                    <textarea id="gov_leadGoal" rows="3" placeholder="هدف خود را بنویسید..."></textarea>
                </div>
            </div>

            <h3>🏢 انتخاب فکشن دولتی</h3>
            <select id="gov_factionSelect" style="width: 100%; max-width: 400px;">
                <option value="Medic">🚑 Medic</option>
                <option value="News">📰 News</option>
                <option value="Army">💂 Army</option>
                <option value="FBI">🕵️ FBI</option>
                <option value="LsPd">👮 LSPD</option>
            </select>

            <div class="btn-group">
                <button class="btn-send" onclick="sendForum('gov')">🚀 ارسال فروم</button>
                <button class="btn-no" onclick="resetForm('gov')">🔄 پاک کردن فرم</button>
            </div>
        </section>

        <!-- فروم گتو -->
        <section id="ghetto" class="section">
            <h2>💀 فرم درخواست گتو</h2>
            
            <div class="form-grid">
                <div class="form-group">
                    <label>👤 نام اکانت</label>
                    <input type="text" id="ghetto_accName" placeholder="Dragon_Player">
                </div>
                
                <div class="form-group">
                    <label>📊 لول</label>
                    <input type="number" id="ghetto_accLevel" placeholder="5">
                </div>
                
                <div class="form-group">
                    <label>📎 آپلود اسکرین‌شات</label>
                    <input type="file" id="ghetto_file" accept="image/*">
                </div>
                
                <div class="form-group">
                    <label>📘 Wbook</label>
                    <input type="text" id="ghetto_wbook" placeholder="100">
                </div>
                
                <div class="form-group">
                    <label>👤 نام واقعی</label>
                    <input type="text" id="ghetto_realName" placeholder="نام و نام خانوادگی">
                </div>
                
                <div class="form-group">
                    <label>🎂 سن واقعی</label>
                    <input type="number" id="ghetto_realAge" placeholder="20">
                </div>
                
                <div class="form-group">
                    <label>📱 آیدی روبیکا</label>
                    <input type="text" id="ghetto_rubikaID" placeholder="@username">
                </div>
                
                <div class="form-group">
                    <label>⏰ تایم پلی روزانه</label>
                    <input type="text" id="ghetto_playTime" placeholder="4-5 ساعت">
                </div>
                
                <div class="form-group" style="grid-column: 1 / -1;">
                    <label>🎯 هدف از لیدری</label>
                    <textarea id="ghetto_leadGoal" rows="3" placeholder="هدف خود را بنویسید..."></textarea>
                </div>
            </div>

            <h3>🔪 انتخاب فکشن گتو</h3>
            <select id="ghetto_factionSelect" style="width: 100%; max-width: 400px;">
                <option value="Vagos">💛 Vagos</option>
                <option value="Ballas">💜 Ballas</option>
                <option value="Rifa">💚 Rifa</option>
                <option value="Aztecas">💙 Aztecas</option>
                <option value="Grove Street">💚 Grove Street</option>
            </select>

            <div class="btn-group">
                <button class="btn-send" onclick="sendForum('ghetto')">🚀 ارسال فروم</button>
                <button class="btn-no" onclick="resetForm('ghetto')">🔄 پاک کردن فرم</button>
            </div>
        </section>

        <!-- پنل مدیریت -->
        <section id="admin" class="section">
            <h2>⚡ پنل مدیریت</h2>

            <div class="admin-login">
                <div class="form-group">
                    <label>🔑 رمز مدیریت</label>
                    <input type="password" id="adminPass" placeholder="رمز عبور را وارد کنید">
                </div>
                <button class="btn-admin" onclick="loginAdmin()" style="width:100%;">🔓 ورود به پنل</button>
            </div>

            <div id="adminBox" style="display:none;">
                <h3>📋 فروم‌های ارسال شده</h3>
                <div class="cards" id="adminList"></div>
            </div>
        </section>

    </div>

    <footer>
        <p>🐉 <span>DRAGON ROLEPLAY</span> | همه حقوق محفوظ است © 2026</p>
        <p style="font-size: 16px; margin-top: 15px; color: var(--accent);">طراحی شده توسط <span>@Mashin_Mazndarn</span></p>
    </footer>

    <script>
        // تابع نمایش پیام
        function showToast(message, type = 'success') {
            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.style.borderColor = type === 'success' ? '#00ffae' : '#ff004c';
            toast.style.color = type === 'success' ? '#00ffae' : '#ff004c';
            toast.textContent = message;
            document.body.appendChild(toast);
            
            setTimeout(() => {
                toast.style.animation = 'slideIn 0.3s reverse';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // منو ناوبری
        const links = document.querySelectorAll('.navbar a');
        const sections = document.querySelectorAll('.section');

        links.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                sections.forEach(s => s.classList.remove('active'));
                document.getElementById(link.dataset.target).classList.add('active');
                
                // انیمیشن کلیک
                link.style.transform = 'scale(0.95)';
                setTimeout(() => link.style.transform = '', 200);
            });
        });

        // ریست فرم
        function resetForm(type) {
            const inputs = document.querySelectorAll(`#${type} input, #${type} textarea`);
            inputs.forEach(input => {
                if (input.type !== 'file') {
                    input.value = '';
                }
            });
            
            const selects = document.querySelectorAll(`#${type} select`);
            selects.forEach(select => select.selectedIndex = 0);
            
            showToast('✅ فرم پاک شد', 'success');
        }

        // ارسال فروم
        function sendForum(type) {
            let data = {};

            if (type === 'gov') {
                data = {
                    acc: document.getElementById('gov_accName').value,
                    level: document.getElementById('gov_accLevel').value,
                    wbook: document.getElementById('gov_wbook').value,
                    realName: document.getElementById('gov_realName').value,
                    realAge: document.getElementById('gov_realAge').value,
                    rubika: document.getElementById('gov_rubikaID').value,
                    playTime: document.getElementById('gov_playTime').value,
                    goal: document.getElementById('gov_leadGoal').value,
                    faction: document.getElementById('gov_factionSelect').value,
                    type: '🏛️ دولتی',
                    date: new Date().toLocaleString('fa-IR'),
                    ip: 'کاربر مهمان' // نمایش IP به صورت پیش‌فرض
                };
            } else {
                data = {
                    acc: document.getElementById('ghetto_accName').value,
                    level: document.getElementById('ghetto_accLevel').value,
                    wbook: document.getElementById('ghetto_wbook').value,
                    realName: document.getElementById('ghetto_realName').value,
                    realAge: document.getElementById('ghetto_realAge').value,
                    rubika: document.getElementById('ghetto_rubikaID').value,
                    playTime: document.getElementById('ghetto_playTime').value,
                    goal: document.getElementById('ghetto_leadGoal').value,
                    faction: document.getElementById('ghetto_factionSelect').value,
                    type: '💀 گتو',
                    date: new Date().toLocaleString('fa-IR'),
                    ip: 'کاربر مهمان' // نمایش IP به صورت پیش‌فرض
                };
            }

            if (!data.acc || !data.level || !data.goal) {
                showToast('❌ فیلدهای ضروری را پر کن!', 'error');
                return;
            }

            let forums = JSON.parse(localStorage.getItem('pendingForums') || '[]');
            forums.push(data);
            localStorage.setItem('pendingForums', JSON.stringify(forums));

            showToast('✅ فروم ارسال شد!', 'success');
            resetForm(type);
        }

        // ورود به پنل مدیریت
        function loginAdmin() {
            const password = document.getElementById('adminPass').value;
            
            if (password !== '123321') {
                showToast('❌ رمز عبور اشتباه است!', 'error');
                return;
            }

            document.getElementById('adminBox').style.display = 'block';
            showToast('✅ ورود موفق به پنل مدیریت', 'success');
            loadAdmin();
        }

        // بارگذاری فروم‌ها
        function loadAdmin() {
            const forums = JSON.parse(localStorage.getItem('pendingForums') || '[]');
            const adminList = document.getElementById('adminList');

            if (forums.length === 0) {
                adminList.innerHTML = '<p style="text-align:center; color:#666; grid-column:1/-1;">📭 هیچ فرومی ارسال نشده است</p>';
                return;
            }

            adminList.innerHTML = forums.map((forum, index) => `
                <div class="card">
                    <span class="card-badge">${forum.type}</span>
                    <p><strong>👤 اکانت:</strong> ${forum.acc}</p>
                    <p><strong>📊 لول:</strong> ${forum.level}</p>
                    <p><strong>📘 Wbook:</strong> ${forum.wbook || 'نامشخص'}</p>
                    <p><strong>👤 نام واقعی:</strong> ${forum.realName || 'نامشخص'}</p>
                    <p><strong>🎂 سن واقعی:</strong> ${forum.realAge || 'نامشخص'}</p>
                    <p><strong>📱 روبیکا:</strong> ${forum.rubika || 'نامشخص'}</p>
                    <p><strong>⏰ تایم پلی:</strong> ${forum.playTime || 'نامشخص'}</p>
                    <p><strong>🎯 هدف:</strong> ${forum.goal.substring(0, 50)}${forum.goal.length > 50 ? '...' : ''}</p>
                    <p><strong>🏢 فکشن:</strong> ${forum.faction}</p>
                    <p><strong>📅 تاریخ:</strong> ${forum.date}</p>
                    <p><strong>🌐 IP:</strong> ${forum.ip || 'کاربر مهمان'}</p>
                    <div class="card-actions">
                        <button class="btn-ok" onclick="handleForum(${index}, 'accept')">✅ قبول</button>
                        <button class="btn-no" onclick="handleForum(${index}, 'reject')">❌ رد</button>
                    </div>
                </div>
            `).join('');
        }

        // مدیریت فروم (قبول/رد)
        function handleForum(index, action) {
            let forums = JSON.parse(localStorage.getItem('pendingForums') || '[]');
            
            if (action === 'accept') {
                let accepted = JSON.parse(localStorage.getItem('acceptedForums') || '[]');
                accepted.push(forums[index]);
                localStorage.setItem('acceptedForums', JSON.stringify(accepted));
                showToast('✅ فروم پذیرفته شد', 'success');
            } else {
                let rejected = JSON.parse(localStorage.getItem('rejectedForums') || '[]');
                rejected.push(forums[index]);
                localStorage.setItem('rejectedForums', JSON.stringify(rejected));
                showToast('❌ فروم رد شد', 'error');
            }

            forums.splice(index, 1);
            localStorage.setItem('pendingForums', JSON.stringify(forums));
            loadAdmin();
        }
    </script>
</body>
</html>            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.85);
            backdrop-filter: blur(10px);
            display: flex;
            gap: 10px;
            padding: 12px 25px;
            border-radius: 50px;
            z-index: 1000;
            border: 2px solid #00f7ff;
            box-shadow: 0 0 20px #00f7ff, 0 0 40px rgba(0, 247, 255, 0.3);
            animation: navbarGlow 3s infinite;
        }

        @keyframes navbarGlow {
            0%, 100% { box-shadow: 0 0 20px #00f7ff; }
            50% { box-shadow: 0 0 40px #00f7ff, 0 0 60px rgba(0, 247, 255, 0.5); }
        }

        .navbar a {
            text-decoration: none;
            color: #00f7ff;
            padding: 10px 20px;
            border-radius: 30px;
            font-size: 16px;
            font-weight: 700;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .navbar a::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 247, 255, 0.2), transparent);
            transition: 0.5s;
        }

        .navbar a:hover::before {
            left: 100%;
        }

        .navbar a:hover {
            background: #00f7ff;
            color: #000;
            box-shadow: 0 0 20px #00f7ff;
            transform: scale(1.05);
        }

        /* ===== Main Container ===== */
        .container {
            position: relative;
            z-index: 1;
            padding-top: 120px;
            padding-bottom: 40px;
            max-width: 1300px;
            margin: 0 auto;
        }

        /* ===== Sections ===== */
        .section {
            display: none;
            background: rgba(0, 0, 0, 0.75);
            backdrop-filter: blur(10px);
            border-radius: 30px;
            padding: 35px;
            margin: 20px;
            border: 2px solid #00f7ff;
            box-shadow: 0 0 30px rgba(0, 247, 255, 0.3);
            animation: sectionAppear 0.5s ease;
        }

        @keyframes sectionAppear {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section.active {
            display: block;
        }

        .section h2 {
            color: #00f7ff;
            font-size: 36px;
            font-weight: 900;
            text-align: center;
            margin-bottom: 30px;
            text-shadow: 0 0 15px #00f7ff, 0 0 30px rgba(0, 247, 255, 0.5);
            letter-spacing: 2px;
        }

        .section h3 {
            color: #ff00ff;
            font-size: 24px;
            font-weight: 700;
            margin: 25px 0 15px;
            text-shadow: 0 0 10px #ff00ff;
        }

        /* ===== Form Grid ===== */
        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 25px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #00f7ff;
            font-weight: 700;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        input, select {
            width: 100%;
            padding: 14px 18px;
            border: 2px solid #00f7ff;
            border-radius: 12px;
            background: rgba(0, 0, 0, 0.5);
            color: #fff;
            font-family: 'Vazirmatn', sans-serif;
            font-size: 16px;
            transition: all 0.3s;
            outline: none;
        }

        input:focus, select:focus {
            border-color: #ff00ff;
            box-shadow: 0 0 20px #ff00ff;
            transform: scale(1.02);
        }

        input::placeholder {
            color: rgba(255, 255, 255, 0.5);
            font-size: 14px;
        }

        input[type="file"] {
            padding: 10px;
            background: rgba(0, 247, 255, 0.1);
            border-style: dashed;
            cursor: pointer;
        }

        input[type="file"]::-webkit-file-upload-button {
            background: #00f7ff;
            color: #000;
            padding: 8px 15px;
            border: none;
            border-radius: 8px;
            font-weight: 700;
            cursor: pointer;
            margin-left: 10px;
        }

        select {
            cursor: pointer;
            appearance: none;
            background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='%2300f7ff' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'><polyline points='6 9 12 15 18 9'/></svg>");
            background-repeat: no-repeat;
            background-position: left 15px center;
            background-size: 16px;
        }

        /* ===== Buttons ===== */
        .btn-group {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 30px;
        }

        button {
            padding: 14px 35px;
            border: none;
            border-radius: 50px;
            font-weight: 900;
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
            letter-spacing: 1px;
            font-family: 'Vazirmatn', sans-serif;
        }

        button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: 0.5s;
        }

        button:hover::before {
            left: 100%;
        }

        button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 25px currentColor;
        }

        .btn-send {
            background: #00ffae;
            color: #000;
            box-shadow: 0 0 15px #00ffae;
            flex: 1;
            min-width: 200px;
        }

        .btn-admin {
            background: #1e90ff;
            color: #fff;
            box-shadow: 0 0 15px #1e90ff;
        }

        .btn-ok {
            background: #00ff00;
            color: #000;
            box-shadow: 0 0 15px #00ff00;
        }

        .btn-no {
            background: #ff004c;
            color: #fff;
            box-shadow: 0 0 15px #ff004c;
        }

        /* ===== Cards ===== */
        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .card {
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(5px);
            border-radius: 20px;
            padding: 20px;
            border: 2px solid #00f7ff;
            box-shadow: 0 0 20px rgba(0, 247, 255, 0.3);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .card:hover {
            transform: translateY(-5px);
            border-color: #ff00ff;
            box-shadow: 0 0 30px #ff00ff;
        }

        .card::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #00f7ff, #ff00ff, #00f7ff);
            animation: cardBorder 3s linear infinite;
        }

        @keyframes cardBorder {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .card p {
            margin-bottom: 10px;
            font-size: 14px;
            line-height: 1.6;
        }

        .card strong {
            color: #00f7ff;
            font-weight: 900;
        }

        .card-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: #ff00ff;
            color: #fff;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 700;
            box-shadow: 0 0 10px #ff00ff;
        }

        .card-actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .card-actions button {
            flex: 1;
            padding: 10px;
            font-size: 14px;
        }

        /* ===== Admin Panel ===== */
        #adminBox {
            margin-top: 30px;
        }

        .admin-login {
            max-width: 400px;
            margin: 0 auto;
            text-align: center;
        }

        /* ===== Footer ===== */
        footer {
            text-align: center;
            color: #00f7ff;
            padding: 30px;
            font-weight: 900;
            font-size: 18px;
            position: relative;
            z-index: 1;
            text-shadow: 0 0 10px #00f7ff;
            margin-top: 50px;
        }

        /* ===== Responsive ===== */
        @media (max-width: 768px) {
            .navbar {
                width: 90%;
                padding: 8px 15px;
            }
            
            .navbar a {
                padding: 8px 12px;
                font-size: 14px;
            }
            
            .section {
                padding: 20px;
                margin: 10px;
            }
            
            .section h2 {
                font-size: 28px;
            }
            
            .form-grid {
                grid-template-columns: 1fr;
            }
            
            .btn-group {
                flex-direction: column;
            }
            
            button {
                width: 100%;
            }
        }

        /* ===== Loading Animation ===== */
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: #00f7ff;
            animation: spin 1s ease-in-out infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* ===== Toast Notification ===== */
        .toast {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: rgba(0, 0, 0, 0.9);
            border: 2px solid #00f7ff;
            border-radius: 12px;
            padding: 15px 25px;
            color: #fff;
            font-weight: 700;
            box-shadow: 0 0 20px #00f7ff;
            z-index: 2000;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
    </style>
</head>
<body>

    <nav class="navbar">
        <a href="#" data-target="gov">🏛️ فروم دولت</a>
        <a href="#" data-target="ghetto">💀 فروم گتو</a>
        <a href="#" data-target="admin">⚡ پنل مدیریت</a>
    </nav>

    <div class="container">

        <!-- فروم دولت -->
        <section id="gov" class="section active">
            <h2>🏛️ فرم درخواست دولت</h2>
            
            <div class="form-grid">
                <div class="form-group">
                    <label>👤 نام اکانت</label>
                    <input type="text" id="gov_accName" placeholder="مثال: Dragon_Player">
                </div>
                
                <div class="form-group">
                    <label>📊 لول</label>
                    <input type="number" id="gov_accLevel" placeholder="مثال: 5">
                </div>
                
                <div class="form-group">
                    <label>📅 سن اکانت</label>
                    <input type="text" id="gov_accAge" placeholder="مثال: 2 ماه">
                </div>
                
                <div class="form-group">
                    <label>⚠️ اکانت سابقه</label>
                    <input type="text" id="gov_accOld" placeholder="آیا اکانت قبلی دارید؟">
                </div>
                
                <div class="form-group">
                    <label>📜 سابقه در فکشن‌های دولتی</label>
                    <input type="text" id="gov_factionHistory" placeholder="نام فکشن‌های قبلی">
                </div>
                
                <div class="form-group">
                    <label>📎 آپلود اسکرین‌شات</label>
                    <input type="file" id="gov_file" accept="image/*">
                </div>
                
                <div class="form-group">
                    <label>📘 Wbook</label>
                    <input type="text" id="gov_wbook" placeholder="مثال: 100">
                </div>
                
                <div class="form-group">
                    <label>👤 نام واقعی</label>
                    <input type="text" id="gov_realName" placeholder="نام و نام خانوادگی">
                </div>
                
                <div class="form-group">
                    <label>🎂 سن واقعی</label>
                    <input type="number" id="gov_realAge" placeholder="مثال: 20">
                </div>
                
                <div class="form-group">
                    <label>📱 آیدی روبیکا</label>
                    <input type="text" id="gov_rubikaID" placeholder="@username">
                </div>
                
                <div class="form-group">
                    <label>⏰ تایم پلی روزانه</label>
                    <input type="text" id="gov_playTime" placeholder="مثال: 4-5 ساعت">
                </div>
                
                <div class="form-group">
                    <label>🎯 هدف از لیدری</label>
                    <textarea id="gov_leadGoal" rows="3" style="width:100%; padding:14px; background:rgba(0,0,0,0.5); border:2px solid #00f7ff; border-radius:12px; color:#fff; font-family:inherit;"></textarea>
                </div>
            </div>

            <h3>🏢 انتخاب فکشن دولتی</h3>
            <select id="gov_factionSelect">
                <option value="Medic">🚑 Medic</option>
                <option value="News">📰 News</option>
                <option value="Army">💂 Army</option>
                <option value="FBI">🕵️ FBI</option>
                <option value="LsPd">👮 LSPD</option>
            </select>

            <div class="btn-group">
                <button class="btn-send" onclick="sendForum('gov')">🚀 ارسال فروم</button>
                <button class="btn-no" onclick="resetForm('gov')">🔄 پاک کردن فرم</button>
            </div>
        </section>

        <!-- فروم گتو -->
        <section id="ghetto" class="section">
            <h2>💀 فرم درخواست گتو</h2>
            
            <div class="form-grid">
                <div class="form-group">
                    <label>👤 نام اکانت</label>
                    <input type="text" id="ghetto_accName" placeholder="مثال: Dragon_Player">
                </div>
                
                <div class="form-group">
                    <label>📊 لول</label>
                    <input type="number" id="ghetto_accLevel" placeholder="مثال: 5">
                </div>
                
                <div class="form-group">
                    <label>📅 سن اکانت</label>
                    <input type="text" id="ghetto_accAge" placeholder="مثال: 2 ماه">
                </div>
                
                <div class="form-group">
                    <label>⚠️ اکانت سابقه</label>
                    <input type="text" id="ghetto_accOld" placeholder="آیا اکانت قبلی دارید؟">
                </div>
                
                <div class="form-group">
                    <label>🔫 سابقه در فکشن‌های گتو</label>
                    <input type="text" id="ghetto_factionHistory" placeholder="نام فکشن‌های قبلی">
                </div>
                
                <div class="form-group">
                    <label>📎 آپلود اسکرین‌شات</label>
                    <input type="file" id="ghetto_file" accept="image/*">
                </div>
                
                <div class="form-group">
                    <label>📘 Wbook</label>
                    <input type="text" id="ghetto_wbook" placeholder="مثال: 100">
                </div>
                
                <div class="form-group">
                    <label>👤 نام واقعی</label>
                    <input type="text" id="ghetto_realName" placeholder="نام و نام خانوادگی">
                </div>
                
                <div class="form-group">
                    <label>🎂 سن واقعی</label>
                    <input type="number" id="ghetto_realAge" placeholder="مثال: 20">
                </div>
                
                <div class="form-group">
                    <label>📱 آیدی روبیکا</label>
                    <input type="text" id="ghetto_rubikaID" placeholder="@username">
                </div>
                
                <div class="form-group">
                    <label>⏰ تایم پلی روزانه</label>
                    <input type="text" id="ghetto_playTime" placeholder="مثال: 4-5 ساعت">
                </div>
                
                <div class="form-group">
                    <label>🎯 هدف از لیدری</label>
                    <textarea id="ghetto_leadGoal" rows="3" style="width:100%; padding:14px; background:rgba(0,0,0,0.5); border:2px solid #00f7ff; border-radius:12px; color:#fff; font-family:inherit;"></textarea>
                </div>
            </div>

            <h3>🔪 انتخاب فکشن گتو</h3>
            <select id="ghetto_factionSelect">
                <option value="Vagos">💛 Vagos</option>
                <option value="Ballas">💜 Ballas</option>
                <option value="Rifa">💚 Rifa</option>
                <option value="Aztecas">💙 Aztecas</option>
                <option value="Grove Street">💚 Grove Street</option>
            </select>

            <div class="btn-group">
                <button class="btn-send" onclick="sendForum('ghetto')">🚀 ارسال فروم</button>
                <button class="btn-no" onclick="resetForm('ghetto')">🔄 پاک کردن فرم</button>
            </div>
        </section>

        <!-- پنل مدیریت -->
        <section id="admin" class="section">
            <h2>⚡ پنل مدیریت</h2>

            <div class="admin-login">
                <div class="form-group">
                    <label>🔑 رمز مدیریت</label>
                    <input type="password" id="adminPass" placeholder="رمز عبور را وارد کنید">
                </div>
                <button class="btn-admin" onclick="loginAdmin()" style="width:100%;">🔓 ورود به پنل</button>
            </div>

            <div id="adminBox" style="display:none;">
                <h3>📋 فروم‌های ارسال شده</h3>
                <div class="cards" id="adminList"></div>
            </div>
        </section>

    </div>

    <footer>
        <p>🐉 Dragon RolePlay | همه حقوق محفوظ است © سازنده @Mashin_Mazndarn2026</p>
    </footer>

    <script>
        // تابع نمایش پیام
        function showToast(message, type = 'success') {
            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.style.borderColor = type === 'success' ? '#00ff00' : '#ff004c';
            toast.style.color = type === 'success' ? '#00ff00' : '#ff004c';
            toast.textContent = message;
            document.body.appendChild(toast);
            
            setTimeout(() => {
                toast.style.animation = 'slideIn 0.3s reverse';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // منو ناوبری
        const links = document.querySelectorAll('.navbar a');
        const sections = document.querySelectorAll('.section');

        links.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                sections.forEach(s => s.classList.remove('active'));
                document.getElementById(link.dataset.target).classList.add('active');
            });
        });

        // ریست فرم
        function resetForm(type) {
            const inputs = document.querySelectorAll(`#${type} input, #${type} textarea, #${type} select`);
            inputs.forEach(input => {
                if (input.type !== 'file') {
                    input.value = '';
                }
            });
            showToast('✅ فرم پاک شد', 'success');
        }

        // ارسال فروم
        function sendForum(type) {
            let data = {};

            if (type === 'gov') {
                data = {
                    acc: document.getElementById('gov_accName').value,
                    level: document.getElementById('gov_accLevel').value,
                    age: document.getElementById('gov_accAge').value,
                    oldAcc: document.getElementById('gov_accOld').value,
                    history: document.getElementById('gov_factionHistory').value,
                    wbook: document.getElementById('gov_wbook').value,
                    realName: document.getElementById('gov_realName').value,
                    realAge: document.getElementById('gov_realAge').value,
                    rubika: document.getElementById('gov_rubikaID').value,
                    playTime: document.getElementById('gov_playTime').value,
                    goal: document.getElementById('gov_leadGoal').value,
                    faction: document.getElementById('gov_factionSelect').value,
                    type: 'دولتی',
                    date: new Date().toLocaleString('fa-IR')
                };
            } else {
                data = {
                    acc: document.getElementById('ghetto_accName').value,
                    level: document.getElementById('ghetto_accLevel').value,
                    age: document.getElementById('ghetto_accAge').value,
                    oldAcc: document.getElementById('ghetto_accOld').value,
                    history: document.getElementById('ghetto_factionHistory').value,
                    wbook: document.getElementById('ghetto_wbook').value,
                    realName: document.getElementById('ghetto_realName').value,
                    realAge: document.getElementById('ghetto_realAge').value,
                    rubika: document.getElementById('ghetto_rubikaID').value,
                    playTime: document.getElementById('ghetto_playTime').value,
                    goal: document.getElementById('ghetto_leadGoal').value,
                    faction: document.getElementById('ghetto_factionSelect').value,
                    type: 'گتو',
                    date: new Date().toLocaleString('fa-IR')
                };
            }

            // اعتبارسنجی
            if (!data.acc || !data.level || !data.age || !data.goal) {
                showToast('❌ لطفا فیلدهای ضروری را پر کنید!', 'error');
                return;
            }

            let forums = JSON.parse(localStorage.getItem('pendingForums') || '[]');
            forums.push(data);
            localStorage.setItem('pendingForums', JSON.stringify(forums));

            showToast('✅ فروم با موفقیت ارسال شد!', 'success');
            resetForm(type);
        }

        // ورود به پنل مدیریت
        function loginAdmin() {
            const password = document.getElementById('adminPass').value;
            
            if (password !== '123321') {
                showToast('❌ رمز عبور اشتباه است!', 'error');
                return;
            }

            document.getElementById('adminBox').style.display = 'block';
            showToast('✅ ورود موفق به پنل مدیریت', 'success');
            loadAdmin();
        }

        // بارگذاری فروم‌ها
        function loadAdmin() {
            const forums = JSON.parse(localStorage.getItem('pendingForums') || '[]');
            const adminList = document.getElementById('adminList');

            if (forums.length === 0) {
                adminList.innerHTML = '<p style="text-align:center; color:#666; grid-column:1/-1;">📭 هیچ فرومی ارسال نشده است</p>';
                return;
            }

            adminList.innerHTML = forums.map((forum, index) => `
                <div class="card">
                    <span class="card-badge">${forum.type}</span>
                    <p><strong>👤 اکانت:</strong> ${forum.acc}</p>
                    <p><strong>📊 لول:</strong> ${forum.level}</p>
                    <p><strong>📅 سن:</strong> ${forum.age}</p>
                    <p><strong>⚠️ سابقه:</strong> ${forum.oldAcc || 'ندارد'}</p>
                    <p><strong>📜 سابقه فکشن:</strong> ${forum.history || 'ندارد'}</p>
                    <p><strong>📘 Wbook:</strong> ${forum.wbook || 'نامشخص'}</p>
                    <p><strong>👤 نام واقعی:</strong> ${forum.realName || 'نامشخص'}</p>
                    <p><strong>🎂 سن واقعی:</strong> ${forum.realAge || 'نامشخص'}</p>
                    <p><strong>📱 روبیکا:</strong> ${forum.rubika || 'نامشخص'}</p>
                    <p><strong>⏰ تایم پلی:</strong> ${forum.playTime || 'نامشخص'}</p>
                    <p><strong>🎯 هدف:</strong> ${forum.goal}</p>
                    <p><strong>🏢 فکشن:</strong> ${forum.faction}</p>
                    <p><strong>📅 تاریخ:</strong> ${forum.date}</p>
                    <div class="card-actions">
                        <button class="btn-ok" onclick="handleForum(${index}, 'accept')">✅ قبول</button>
                        <button class="btn-no" onclick="handleForum(${index}, 'reject')">❌ رد</button>
                    </div>
                </div>
            `).join('');
        }

        // مدیریت فروم (قبول/رد)
        function handleForum(index, action) {
            let forums = JSON.parse(localStorage.getItem('pendingForums') || '[]');
            
            if (action === 'accept') {
                let accepted = JSON.parse(localStorage.getItem('acceptedForums') || '[]');
                accepted.push(forums[index]);
                localStorage.setItem('acceptedForums', JSON.stringify(accepted));
                showToast('✅ فروم پذیرفته شد', 'success');
            } else {
                let rejected = JSON.parse(localStorage.getItem('rejectedForums') || '[]');
                rejected.push(forums[index]);
                localStorage.setItem('rejectedForums', JSON.stringify(rejected));
                showToast('❌ فروم رد شد', 'error');
            }

            forums.splice(index, 1);
            localStorage.setItem('pendingForums', JSON.stringify(forums));
            loadAdmin();
        }

        // نمایش اولین بخش
        document.getElementById('gov').classList.add('active');
    </script>
</body>
</html>
