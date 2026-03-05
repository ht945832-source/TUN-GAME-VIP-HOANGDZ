<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>HOANGDZ TUN - SUPREME EDITION</title>
    <style>
        :root { --red: #ff0000; --black: #050505; --gold: #ffcc00; --blue: #00d2ff; }
        * { box-sizing: border-box; touch-action: manipulation; user-select: none; font-family: 'Orbitron', sans-serif; }
        
        body {
            background-color: var(--black); margin: 0; height: 100vh;
            display: flex; justify-content: center; align-items: center;
            overflow: hidden; background: radial-gradient(circle, #200 0%, #000 100%);
            color: white;
        }

        /* --- MÀN HÌNH NHẬP KEY SIÊU ĐẸP --- */
        #login {
            position: fixed; inset: 0; background: var(--black); z-index: 9999;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            background: url('https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJndXIzZ3R4bmR4Z3R4Z3R4Z3R4Z3R4Z3R4Z3R4Z3R4Z3R4Z3R4JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/3o7TKMGpxxX1v9T2ZG/giphy.gif') center/cover;
        }
        #login::after { content: ''; position: absolute; inset: 0; background: rgba(0,0,0,0.85); z-index: -1; }

        .led-hoangdz {
            font-size: 50px; font-weight: 900; 
            background: linear-gradient(90deg, #ff0000, #fff, #ff0000);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 15px var(--red));
            letter-spacing: 12px; margin-bottom: 30px; animation: rgb-glow 2s infinite linear;
        }
        @keyframes rgb-glow { 0% { filter: hue-rotate(0deg); } 100% { filter: hue-rotate(360deg); } }

        .key-container {
            background: rgba(20, 20, 20, 0.9); padding: 40px; border-radius: 30px;
            border: 2px solid var(--red); box-shadow: 0 0 30px var(--red);
            text-align: center; backdrop-filter: blur(10px);
        }

        .input-key {
            background: transparent; border: none; border-bottom: 2px solid var(--red);
            color: white; font-size: 20px; padding: 10px; text-align: center;
            width: 250px; letter-spacing: 5px; margin-bottom: 25px;
        }

        /* --- PANEL CHÍNH --- */
        .panel {
            width: 380px; height: 680px; background: rgba(10, 10, 10, 0.98);
            border: 2px solid var(--red); border-radius: 30px;
            display: none; flex-direction: column; overflow: hidden;
            box-shadow: 0 0 50px rgba(255, 0, 0, 0.6); position: relative;
        }

        .header {
            padding: 20px; border-bottom: 1px solid var(--red);
            display: flex; justify-content: space-between; align-items: center;
            background: linear-gradient(to right, #400, #000);
        }

        .scroll-content { flex: 1; overflow-y: auto; padding: 20px; }
        .scroll-content::-webkit-scrollbar { width: 0; }

        .card {
            background: #111; padding: 18px; border-radius: 20px;
            margin-bottom: 15px; border: 1px solid #222; transition: 0.3s;
        }

        /* Settings Gear Menu */
        #settings-menu {
            position: absolute; inset: 0; background: #050505; z-index: 100;
            display: none; flex-direction: column; padding: 25px;
        }

        /* Nút Switch */
        .sw { width: 50px; height: 26px; background: #333; border-radius: 50px; position: relative; transition: 0.4s; }
        .sw::after { content: ''; position: absolute; width: 20px; height: 20px; background: #fff; border-radius: 50%; top: 3px; left: 3px; transition: 0.4s; }
        .active-sw { background: var(--red); box-shadow: 0 0 15px var(--red); }
        .active-sw::after { left: 27px; }

        /* Slider */
        input[type=range] { -webkit-appearance: none; width: 100%; height: 6px; background: #222; border-radius: 10px; margin-top: 15px; }
        input[type=range]::-webkit-slider-thumb { -webkit-appearance: none; width: 20px; height: 20px; background: var(--red); border-radius: 50%; box-shadow: 0 0 15px var(--red); }

        .toast {
            position: fixed; top: 20px; background: white; color: black;
            padding: 12px 30px; border-radius: 50px; font-weight: bold;
            z-index: 10000; box-shadow: 0 0 20px white; animation: slideIn 0.4s forwards;
        }
        @keyframes slideIn { from { transform: translateY(-100px); } to { transform: translateY(0); } }
    </style>
</head>
<body>

<div id="login">
    <div class="led-hoangdz">HOANGDZ</div>
    <div class="key-container">
        <h3 style="color: var(--red); margin: 0 0 20px 0;">HỆ THỐNG BẢO MẬT</h3>
        <input type="password" id="key-input" class="input-key" placeholder="••••••••">
        <br>
        <button onclick="unlock()" style="background:var(--red); color:white; border:none; padding:15px 40px; border-radius:50px; cursor:pointer; font-weight:bold; font-size:16px; box-shadow: 0 0 20px var(--red);">TRUY CẬP NGAY</button>
    </div>
</div>

<div class="panel" id="panel">
    <div class="header">
        <span style="letter-spacing: 2px; color: #fff;">HOANGDZ <span style="color:var(--red)">TUN v10</span></span>
        <span style="font-size: 25px; cursor:pointer;" onclick="toggleSettings()">⚙️</span>
    </div>

    <div id="settings-menu">
        <h2 style="color:var(--red); text-align:center;">HỆ THỐNG ⚙️</h2>
        <div style="background:#111; padding:15px; border-radius:15px; font-size:12px; border:1px solid var(--red);">
            <b>GIỚI THIỆU:</b> HOANGDZ TUN là công cụ tối ưu hóa đẳng cấp nhất 2024. Chuyên sâu về FPS, DPI và ổn định tâm ngắm cho Game thủ Pro.
        </div>
        <br>
        <label style="color:var(--gold)">CHỌN THIẾT BỊ ĐỂ TỐI ƯU:</label>
        <select id="device" onchange="applyDevice()" style="width:100%; padding:12px; background:#222; color:white; border:1px solid var(--red); margin-top:10px; border-radius:10px;">
            <option value="">-- Chọn dòng máy --</option>
            <option value="iPhone">Apple iPhone</option>
            <option value="Samsung">Samsung Galaxy</option>
            <option value="Xiaomi">Xiaomi / Poco</option>
            <option value="Oppo">Oppo / Realme</option>
        </select>
        <button onclick="toggleSettings()" style="margin-top:auto; padding:15px; background:var(--red); color:white; border:none; border-radius:10px; font-weight:bold;">QUAY LẠI MENU</button>
    </div>

    <div class="scroll-content">
        <div class="card" style="border: 2px solid var(--gold);">
            <div style="display:flex; justify-content:space-between;">
                <span style="color:var(--gold); font-weight:bold;">⚙️ HIỆU SUẤT TỐI ĐA</span>
                <span id="p-val" style="color:var(--gold);">100%</span>
            </div>
            <input type="range" min="0" max="200" value="100" oninput="updatePerf(this.value)">
            <p style="font-size:10px; color:#666; margin-top:8px;">*Gia tăng 200% tài nguyên hệ thống cho Tun.</p>
        </div>

        <div class="card">
            <div style="display:flex; justify-content:space-between;">
                <span>🎯 DPI CỦA BẠN</span>
                <span id="dpi-val" style="color:var(--blue);">500</span>
            </div>
            <input type="range" min="300" max="1200" value="500" oninput="document.getElementById('dpi-val').innerText=this.value">
        </div>

        <div class="card" onclick="toggleSw(this, 'Nhẹ Tâm')"><div style="display:flex; justify-content:space-between;"><span>NHẸ TÂM 🎯</span><div class="sw"></div></div></div>
        <div class="card" onclick="toggleSw(this, 'Đầm Tâm')"><div style="display:flex; justify-content:space-between;"><span>ĐẦM TÂM 🎯</span><div class="sw"></div></div></div>
        <div class="card" onclick="toggleSw(this, 'Aimlock')"><div style="display:flex; justify-content:space-between;"><span>AIMLOCK 🔒</span><div class="sw"></div></div></div>
        <div class="card" onclick="toggleSw(this, 'Bypass')"><div style="display:flex; justify-content:space-between;"><span>BYPASS ANTI-CHEAT 🛡️</span><div class="sw"></div></div></div>
        <div class="card" onclick="toggleSw(this, 'Ultra Smooth')"><div style="display:flex; justify-content:space-between;"><span>ULTRA SMOOTH ✨</span><div class="sw"></div></div></div>
    </div>

    <div style="padding:15px; text-align:center; font-size:11px; color:#444;">
        DESIGNED BY HOANGDZ - PRIVATE TUN
    </div>
</div>

<audio id="s-iphone" src="https://www.soundjay.com/buttons/sounds/button-20.mp3"></audio>
<audio id="s-android" src="https://www.soundjay.com/buttons/sounds/button-37.mp3"></audio>
<audio id="s-unlock" src="https://www.soundjay.com/buttons/sounds/button-10.mp3"></audio>

<script>
    const SECRET_KEY = "HOANGDZ999"; 

    function unlock() {
        const key = document.getElementById('key-input').value;
        if(key === SECRET_KEY) {
            document.getElementById('s-unlock').play();
            alert("✨ CHÚC MỪNG HOANGDZ! HỆ THỐNG ĐÃ SẴN SÀNG.");
            document.getElementById('login').style.display = 'none';
            document.getElementById('panel').style.display = 'flex';
        } else {
            alert("Sai mã rồi đại ca ơi!");
        }
    }

    function toggleSettings() {
        const m = document.getElementById('settings-menu');
        m.style.display = (m.style.display === 'flex') ? 'none' : 'flex';
    }

    function updatePerf(v) {
        document.getElementById('p-val').innerText = v + "%";
    }

    function applyDevice() {
        const d = document.getElementById('device').value;
        if(d === 'iPhone') {
            document.getElementById('s-iphone').play();
            document.getElementById('dpi-val').innerText = 850;
        } else if(d !== "") {
            document.getElementById('s-android').play();
            document.getElementById('dpi-val').innerText = 620;
        }
        showToast("Đã tối ưu hóa cho " + d, "#00d2ff");
    }

    function toggleSw(el, name) {
        const s = el.querySelector('.sw');
        s.classList.toggle('active-sw');
        if(s.classList.contains('active-sw')) {
            showToast("✅ Kích hoạt: " + name, "#ff0000");
            if(navigator.vibrate) navigator.vibrate(60);
        } else {
            showToast("❌ Đã tắt: " + name, "#555");
        }
    }

    function showToast(m, c) {
        const t = document.createElement('div');
        t.className = 'toast'; t.innerText = m; t.style.borderLeft = "5px solid " + c;
        document.body.appendChild(t);
        setTimeout(() => { t.style.opacity='0'; setTimeout(()=>t.remove(), 500); }, 1800);
    }

    document.addEventListener('touchstart', (e) => { if (e.touches.length > 1) e.preventDefault(); }, {passive: false});
</script>
</body>
</html>
