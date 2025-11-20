<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rat-toothers | 0期生</title>
    <link href="https://fonts.googleapis.com/css2?family=Shippori+Mincho:wght@500;800&family=Cinzel:wght@700&display=swap" rel="stylesheet">
    <style>
        /* === デザイン設定 === */
        
        body, html { margin: 0; padding: 0; width: 100%; }
        body {
            background-color: #050505;
            color: #fff;
            font-family: 'Shippori Mincho', serif;
            overflow-x: hidden;
        }
        a { text-decoration: none; color: inherit; transition: 0.3s; }
        * { box-sizing: border-box; }
        img { max-width: 100%; height: auto; }

        /* 色定義 */
        :root {
            --daikoku-red: #c9171e;
            --daikoku-dark: #220000;
            --ebisu-blue: #174ec9;
            --ebisu-dark: #000a22;
            --gold: #d4af37;
        }

        /* ヘッダー */
        header {
            position: fixed;
            width: 100%;
            padding: 20px;
            z-index: 100;
            text-align: center;
            mix-blend-mode: difference;
            pointer-events: none;
        }
        .logo-text {
            font-family: 'Cinzel', serif;
            font-size: 1.5rem;
            letter-spacing: 0.2em;
            border: 1px solid #fff;
            padding: 5px 20px;
            display: inline-block;
        }

        /* --- HERO SECTION (スプリットスクリーン) --- */
        .hero-container {
            display: flex;
            height: 100vh;
            width: 100%;
            position: relative;
        }

        .hero-half {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
            transition: 0.5s ease;
            overflow: hidden;
        }
        .hero-half:hover { flex: 1.5; }

        /* 背景設定 */
        .side-daikoku {
            background: radial-gradient(circle at center, var(--daikoku-dark) 0%, #000 100%);
            border-right: 1px solid rgba(255,255,255,0.1);
        }
        .side-ebisu {
            background: radial-gradient(circle at center, var(--ebisu-dark) 0%, #000 100%);
            border-left: 1px solid rgba(255,255,255,0.1);
        }

        /* 名前 */
        .char-name {
            writing-mode: vertical-rl;
            font-size: 3rem;
            font-weight: 800;
            letter-spacing: 0.2em;
            z-index: 10;
            margin: 0;
            text-shadow: 0 0 20px rgba(0,0,0,0.8);
        }
        .char-name span {
            font-size: 1rem;
            color: var(--gold);
            margin-bottom: 10px;
            font-family: 'Cinzel', serif;
        }

        /* キャッチコピー */
        .catch-copy {
            position: absolute;
            font-size: 5rem;
            font-weight: 900;
            opacity: 0.05;
            white-space: nowrap;
            pointer-events: none;
            user-select: none;
        }
        .side-daikoku .catch-copy {
            top: 50%; left: 50%;
            transform: translate(-50%, -50%) rotate(-90deg);
            color: var(--daikoku-red);
        }

        /* 立ち絵画像 */
        .char-img {
            position: absolute;
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            width: 100%; height: 100%;
            max-width: 700px;
            background-size: contain;
            background-repeat: no-repeat;
            background-position: center;
            opacity: 0.6;
            filter: grayscale(80%) contrast(1.2);
            transition: 0.5s;
            z-index: 1;
        }
        .hero-half:hover .char-img {
            opacity: 1;
            filter: grayscale(0%) contrast(1);
            transform: translate(-50%, -50%) scale(1.05);
        }
        
        /* ★ 画像の設定 ★ */
        .img-daikoku { background-image: url('image_0.png'); } 
        .img-ebisu { background-image: url('https://via.placeholder.com/600x800/005/fff?text=Ebisu'); }

        /* ボタン */
        .btn-group {
            position: absolute;
            bottom: 15%;
            z-index: 20;
            display: flex;
            gap: 15px;
        }
        .sns-btn {
            padding: 10px 20px;
            border: 1px solid rgba(255,255,255,0.4);
            background: rgba(0,0,0,0.6);
            color: #fff;
            font-size: 0.8rem;
            font-family: 'Cinzel', serif;
            backdrop-filter: blur(5px);
        }
        .side-daikoku .sns-btn:hover { background: var(--daikoku-red); border-color: var(--daikoku-red); }
        .side-ebisu .sns-btn:hover { background: var(--ebisu-blue); border-color: var(--ebisu-blue); }

        /* --- PROFILE & HISTORY SECTION --- */
        .content-section {
            padding: 80px 20px;
            background: #0a0a0a;
            border-top: 2px solid #222;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        /* プロフィールカード */
        .profile-card {
            background: rgba(255,255,255,0.03);
            border: 1px solid #333;
            padding: 40px;
            margin-bottom: 60px; /* 下の間隔を広げました */
            position: relative;
            overflow: hidden;
        }
        .card-daikoku { border-left: 4px solid var(--daikoku-red); }
        .card-daikoku::before {
            content: '運命怪奇現象';
            position: absolute;
            right: -20px; bottom: -20px;
            font-size: 4rem;
            font-weight: bold;
            color: var(--daikoku-red);
            opacity: 0.1;
            z-index: 0;
        }

        .profile-header {
            display: flex;
            align-items: baseline;
            border-bottom: 1px solid #333;
            padding-bottom: 15px;
            margin-bottom: 20px;
            position: relative;
            z-index: 1;
        }
        .p-name { font-size: 1.8rem; font-weight: bold; margin-right: 15px; }
        .p-gen { font-size: 0.9rem; color: var(--gold); background: #222; padding: 2px 8px; border-radius: 2px; }
        .p-body { color: #ccc; line-height: 1.8; font-size: 0.95rem; position: relative; z-index: 1; }
        
        .data-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-top: 20px;
            background: rgba(0,0,0,0.3);
            padding: 15px;
            border-radius: 4px;
        }
        .data-item { display: flex; flex-direction: column; }
        .data-label { font-size: 0.75rem; color: var(--gold); margin-bottom: 3px; }
        .data-value { font-size: 1rem; font-family: 'Cinzel', serif; }

        .milestones {
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid rgba(255,255,255,0.1);
        }
        .ms-item { display: block; font-size: 0.9rem; margin-bottom: 5px; }
        .check { color: var(--daikoku-red); margin-right: 5px; font-weight: bold; }

        /* --- 履歴（ギャラリー）エリア --- */
        .section-title {
            font-size: 1.5rem;
            color: var(--gold);
            font-family: 'Cinzel', serif;
            margin-bottom: 30px;
            text-align: center;
            letter-spacing: 0.2em;
        }
        .history-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }
        .history-item {
            background: #111;
            border: 1px solid #333;
            padding: 10px;
            transition: 0.3s;
        }
        .history-item:hover {
            border-color: var(--daikoku-red);
            transform: translateY(-5px);
        }
        .history-img-box {
            width: 100%;
            height: 200px;
            background: #000;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 10px;
        }
        .history-img-box img {
            width: 100%;
            height: 100%;
            object-fit: cover; /* 画像を枠いっぱいに表示 */
            opacity: 0.8;
            transition: 0.3s;
        }
        .history-item:hover img { opacity: 1; }
        
        .history-date { font-size: 0.75rem; color: var(--daikoku-red); display: block; margin-bottom: 5px; font-family: 'Cinzel', serif; }
        .history-text { font-size: 0.9rem; color: #ddd; }

        /* スマホ対応 */
        @media (max-width: 768px) {
            .hero-container { flex-direction: column; height: auto; }
            .hero-half { width: 100%; height: 500px; }
            .char-name { writing-mode: horizontal-tb; font-size: 2rem; margin-bottom: 10px; }
            .catch-copy { font-size: 3rem; transform: translate(-50%, -50%); rotate: 0deg; }
            .data-grid { grid-template-columns: 1fr; }
            .history-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo-text">RAT-TOOTHERS</div>
    </header>

    <div class="hero-container">
        <div class="hero-half side-daikoku">
            <div class="catch-copy">運命怪奇現象</div>
            <div class="char-img img-daikoku"></div>
            <h2 class="char-name">
                <span>Gen.0</span>
                古未月<br>だいこくじ
            </h2>
            <div class="btn-group">
                <a href="#daikoku-detail" class="sns-btn">PROFILE</a>
                <a href="https://www.youtube.com/@三面だいこくじ" target="_blank" class="sns-btn">YOUTUBE</a>
            </div>
        </div>

        <div class="hero-half side-ebisu">
            <div class="char-img img-ebisu"></div>
            <h2 class="char-name">
                <span>Gen.0</span>
                ???<br>えびすじ
            </h2>
            <div class="btn-group">
                <a href="#" class="sns-btn">PROFILE</a>
                <a href="#" class="sns-btn">YOUTUBE</a>
            </div>
        </div>
    </div>

    <section class="content-section">
        <div class="container">
            
            <div id="daikoku-detail" class="profile-card card-daikoku">
                <div class="profile-header">
                    <span class="p-name">古未月 だいこくじ</span>
                    <span class="p-gen">0期生</span>
                </div>
                <div class="p-body">
                    <p>
                        Rat-toothers所属【0期生】古未月 だいこくじです。<br>
                        ゲームとネタの両立とその他ジャンルを目標に動画を作っております。
                    </p>
                    <div class="data-grid">
                        <div class="data-item">
                            <span class="data-label">START DATE</span>
                            <span class="data-value">2020.06.05</span>
                        </div>
                        <div class="data-item">
                            <span class="data-label">SUBSCRIBERS</span>
                            <span class="data-value">202+ Users</span>
                        </div>
                    </div>
                    <div class="milestones">
                        <span class="data-label" style="display:block; margin-bottom:5px;">MILESTONES</span>
                        <span class="ms-item"><span class="check">✔</span>チャンネル登録者 100人達成</span>
                        <span class="ms-item"><span class="check">✔</span>チャンネル登録者 200人達成</span>
                    </div>
                    <div style="margin-top:20px;">
                         <a href="https://x.com/mfxqnny_y" target="_blank" style="color:var(--gold); border-bottom:1px solid var(--gold);">▶ X (Twitter) : @mfxqnny_y</a>
                    </div>
                </div>
            </div>

            <div class="profile-card" style="border-left: 4px solid var(--ebisu-blue);">
                <div class="profile-header">
                    <span class="p-name">??? えびすじ</span>
                    <span class="p-gen">0期生</span>
                </div>
                <div class="p-body">
                    <p>相方の情報待機中...</p>
                </div>
            </div>

            <h3 class="section-title">- HISTORY -</h3>
            <div class="history-grid">
                
                <div class="history-item">
                    <div class="history-img-box">
                        <img src="art_20251031.jpg" alt="Halloween Art">
                    </div>
                    <div style="padding: 10px;">
                        <span class="history-date">2025.10.31</span>
                        <p class="history-text">Happy Halloween Illustration.</p>
                    </div>
                </div>

                </div>

        </div>
    </section>

</body>
</html>
