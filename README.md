<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dragon RolePlay - فروم رسمی</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Vazirmatn', 'Orbitron', sans-serif;
            background: linear-gradient(135deg, #0b1020, #1a1f3a, #2a1f4a);
            color: #fff;
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
        }

        /* انیمیشن پس زمینه */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 30%, rgba(0, 255, 255, 0.05) 0%, transparent 50%),
                        radial-gradient(circle at 80% 70%, rgba(255, 0, 255, 0.05) 0%, transparent 50%);
            pointer-events: none;
            z-index: 0;
        }

        /* ===== Navbar ===== */
        .navbar {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
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
