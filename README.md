<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stakan Cafe - Kosonsoy</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Nunito:wght@400;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
   
    <style>
        :root {
            --bg-dark: #0f1319;
            --bg-card: #171d26;
            --primary-yellow: #ffcc00;
            --accent-red: #ff5252;
            --text-light: #f3f4f6;
            --font-display: 'Fredoka', sans-serif;
            --font-sans: 'Nunito', sans-serif;
        }
 
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
        }
 
        body {
            font-family: var(--font-sans);
            background-color: var(--bg-dark);
            color: var(--text-light);
            height: 100vh;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }
 
        header {
            background-color: #0b0e12;
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--primary-yellow);
            z-index: 100;
        }
 
        .logo-area {
            display: flex;
            align-items: center;
            gap: 12px;
        }
 
        .logo-icon {
            background: linear-gradient(135deg, #1e2633, #0f1319);
            padding: 10px;
            border-radius: 12px;
            border: 2px solid var(--primary-yellow);
            box-shadow: 0 0 10px rgba(255, 204, 0, 0.2);
            font-size: 24px;
            color: var(--primary-yellow);
        }
 
        .logo-text h1 {
            font-family: var(--font-display);
            font-size: 24px;
            color: var(--primary-yellow);
            line-height: 1;
        }
 
        .logo-text span {
            font-size: 12px;
            color: var(--accent-red);
            letter-spacing: 2px;
            font-weight: bold;
        }
 
        /* Kompyuter uchun navigatsiya menyusi */
        nav.desktop-nav {
            display: flex;
            gap: 25px;
            align-items: center;
        }
 
        nav.desktop-nav a {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 700;
            font-size: 16px;
            transition: 0.3s;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 6px;
        }
 
        nav.desktop-nav a:hover, nav.desktop-nav a.active {
            color: var(--primary-yellow);
            transform: scale(1.05);
        }
 
        .savat-btn {
            background-color: var(--accent-red);
            color: white;
            padding: 10px 20px;
            border-radius: 25px;
            border: none;
            font-family: var(--font-display);
            font-weight: 600;
            cursor: pointer;
            display: flex; 
            align-items: center;
            gap: 8px;
            position: relative;
            transition: 0.3s;
        }
 
        .savat-btn:hover {
            background-color: #ff3333;
            box-shadow: 0 0 15px rgba(255, 82, 82, 0.4);
        }
 
        .badge {
            background-color: var(--primary-yellow);
            color: var(--bg-dark);
            font-size: 12px;
            font-weight: 900;
            padding: 2px 7px;
            border-radius: 50%;
            position: absolute;
            top: -5px;
            right: -5px;
        }
 
        /* Mobil uchun teng proporsiyali pastki panel */
        .mobile-nav {
            display: none;
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: #0b0e12;
            border-top: 2px solid var(--primary-yellow);
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            align-items: center;
            justify-items: center;
            padding: 8px 0;
            z-index: 999;
        }

        .mobile-nav a {
            color: #9ca3af;
            text-decoration: none;
            font-size: 18px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            text-align: center;
        }

        .mobile-nav a span {
            font-size: 10px;
        }

        .mobile-nav a.active {
            color: var(--primary-yellow);
        }

        /* Savat tugmasi roppa-rosa o'rtada ajralib turadi */
        .mobile-nav .mobile-cart-holder {
            grid-column: 3;
            position: relative;
            width: 100%;
            display: flex;
            justify-content: center;
        }

        .mobile-nav .mobile-cart-holder a {
            background-color: var(--accent-red);
            color: white;
            padding: 10px;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            justify-content: center;
            box-shadow: 0 -4px 10px rgba(255, 82, 82, 0.3);
            transform: translateY(-15px);
            border: 3px solid var(--bg-dark);
        }

        .mobile-nav .mobile-cart-holder a span {
            display: none; /* Doira ichida yozuv shart emas */
        }

        .mobile-nav .mobile-cart-holder a.active {
            background-color: var(--primary-yellow);
            color: var(--bg-dark);
        }
 
        main {
            flex: 1;
            position: relative;
            width: 100%;
            padding-bottom: 70px;
        }
 
        .page {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            padding: 40px 5%;
            display: none;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.4s ease-in-out;
            overflow-y: auto;
        }
 
        .page.active {
            display: flex;
            opacity: 1;
        }
 
        .home-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            width: 100%;
            align-items: center;
        }
 
        .home-text h2 {
            font-family: var(--font-display);
            font-size: 44px;
            color: var(--primary-yellow);
            margin-bottom: 20px;
            line-height: 1.2;
        }
 
        .home-text p {
            font-size: 18px;
            color: #9ca3af;
            margin-bottom: 30px;
            line-height: 1.6;
        }
 
        .home-btns {
            display: flex;
            gap: 20px;
        }
 
        .btn-main {
            padding: 15px 35px;
            border-radius: 30px;
            border: none;
            font-family: var(--font-display);
            font-size: 18px;
            cursor: pointer;
            transition: 0.3s;
        }
 
        .btn-yellow { background-color: var(--primary-yellow); color: var(--bg-dark); font-weight: 700; }
        .btn-yellow:hover { background-color: #e6b800; box-shadow: 0 0 20px rgba(255, 204, 0, 0.4); }
 
        /* 3D Ruletka / Slayder Oynasi */
        .roulette-container {
            width: 100%;
            height: 350px;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .roulette-track {
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            width: 100%;
            height: 100%;
        }

        .roulette-card {
            position: absolute;
            width: 200px;
            background: linear-gradient(145deg, var(--bg-card), #1e2530);
            border: 2px solid #252f3e;
            border-radius: 24px;
            padding: 25px 15px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            opacity: 0;
            pointer-events: none;
        }

        .roulette-card .food-emoji {
            font-size: 65px;
            margin-bottom: 15px;
            display: block;
        }

        .roulette-card h4 {
            font-family: var(--font-display);
            font-size: 18px;
            color: var(--primary-yellow);
        }

        /* Ruletka holatlari: Markaz, Chap va O'ng tomonlar */
        .roulette-card.active-center {
            opacity: 1;
            transform: translateX(0) scale(1.2);
            z-index: 5;
            border-color: var(--primary-yellow);
            pointer-events: auto;
        }

        .roulette-card.active-left {
            opacity: 0.6;
            transform: translateX(-180px) scale(0.9);
            z-index: 3;
            filter: blur(2px);
        }

        .roulette-card.active-right {
            opacity: 0.6;
            transform: translateX(180px) scale(0.9);
            z-index: 3;
            filter: blur(2px);
        }

        .roulette-card.hidden-left {
            opacity: 0;
            transform: translateX(-300px) scale(0.7);
            filter: blur(8px);
        }

        .roulette-card.hidden-right {
            opacity: 0;
            transform: translateX(300px) scale(0.7);
            filter: blur(8px);
        }
 
        .menu-container {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
        }
 
        .menu-header {
            font-family: var(--font-display);
            font-size: 32px;
            color: var(--primary-yellow);
            margin-bottom: 20px;
            text-align: center;
        }
 
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            overflow-y: auto;
            padding-right: 10px;
            flex: 1;
        }
 
        .menu-grid::-webkit-scrollbar { width: 6px; }
        .menu-grid::-webkit-scrollbar-thumb { background: #252f3e; border-radius: 10px; }
 
        .menu-item {
            background-color: var(--bg-card);
            border-radius: 20px;
            padding: 20px;
            text-align: center;
            border: 2px solid transparent;
            transition: 0.3s;
            position: relative;
        }
 
        .menu-item:hover {
            border-color: var(--primary-yellow);
            transform: translateY(-5px);
        }
 
        .menu-item-emoji {
            font-size: 55px;
            margin-bottom: 12px;
        }
 
        .menu-item h3 {
            font-family: var(--font-display);
            font-size: 20px;
            margin-bottom: 8px;
        }
 
        .menu-item p {
            font-size: 14px;
            color: #9ca3af;
            margin-bottom: 15px;
            height: 40px;
        }
 
        .menu-item .price {
            color: var(--accent-red);
            font-weight: 900;
            font-size: 18px;
            margin-bottom: 15px;
        }
 
        .count-badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background-color: var(--primary-yellow);
            color: var(--bg-dark);
            font-weight: 900;
            font-size: 14px;
            width: 26px;
            height: 26px;
            border-radius: 50%;
            display: none;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 8px rgba(0,0,0,0.3);
        }
 
        .about-content {
            display: grid;
            grid-template-columns: 1.1fr 0.9fr;
            gap: 40px;
            width: 100%;
            align-items: center;
        }
 
        .map-visual {
            background: linear-gradient(135deg, #1b2330, #0b0e12);
            border: 3px solid var(--primary-yellow);
            border-radius: 30px;
            padding: 30px;
            text-align: center;
            box-shadow: 0 15px 35px rgba(0,0,0,0.5);
            position: relative;
            overflow: hidden;
        }
 
        .landmark-illustration {
            display: flex;
            justify-content: center;
            gap: 20px;
            font-size: 75px;
            margin-bottom: 20px;
        }
 
        .landmark-illustration .building { color: #a1887f; animation: float 3s ease-in-out infinite; }
        .landmark-illustration .cafe { color: var(--primary-yellow); animation: float 3s ease-in-out infinite 1.5s; }
 
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
 
        .map-visual h4 { font-family: var(--font-display); font-size: 28px; color: var(--text-light); margin-bottom: 10px; }
        .map-visual p { color: #6b7280; font-size: 14px; }
        .map-visual .pin { color: var(--accent-red); font-size: 24px; margin-top: 15px; display: flex; align-items: center; justify-content: center; gap: 8px; }
 
        .about-text h2 { font-family: var(--font-display); font-size: 36px; color: var(--primary-yellow); margin-bottom: 15px; }
        .about-text p { font-size: 16px; line-height: 1.6; color: #d1d5db; margin-bottom: 15px; }
 
        .contact-card {
            background-color: var(--bg-card);
            border-radius: 24px;
            padding: 40px;
            width: 450px;
            text-align: center;
            border: 2px solid #252f3e;
            box-shadow: 0 15px 30px rgba(0,0,0,0.4);
        }
 
        .contact-card h2 { font-family: var(--font-display); font-size: 32px; color: var(--primary-yellow); margin-bottom: 25px; }
 
        .contact-link {
            display: flex;
            align-items: center;
            gap: 15px;
            background-color: #0f1319;
            padding: 15px 20px;
            border-radius: 15px;
            margin-bottom: 15px;
            color: white;
            text-decoration: none;
            font-size: 18px;
            font-weight: 700;
            transition: 0.3s;
            border: 1px solid transparent;
        }
 
        .contact-link:hover { border-color: var(--primary-yellow); transform: translateX(5px); }
        .contact-link.insta i { color: #e1306c; }
        .contact-link.tg i { color: #0088cc; }
        .contact-link.phone i { color: #4caf50; }
 
        .cart-page {
            display: grid;
            grid-template-columns: 1.2fr 0.8fr;
            gap: 30px;
            width: 100%;
            height: 100%;
        }
 
        .cart-list-container {
            background-color: var(--bg-card);
            border-radius: 20px;
            padding: 25px;
            display: flex;
            flex-direction: column;
            height: 100%;
        }
 
        .cart-items-scroll {
            flex: 1;
            overflow-y: auto;
            padding-right: 10px;
        }
 
        .cart-items-scroll::-webkit-scrollbar { width: 5px; }
        .cart-items-scroll::-webkit-scrollbar-thumb { background: #374151; border-radius: 10px; }
 
        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #0f1319;
            padding: 15px 20px;
            border-radius: 15px;
            margin-bottom: 12px;
        }
 
        .cart-item-info { display: flex; align-items: center; gap: 15px; }
        .cart-item-info .item-emoji { font-size: 28px; }
 
        .cart-item-controls { display: flex; align-items: center; gap: 15px; }
 
        .qty-btn {
            background-color: #252f3e;
            border: none;
            color: white;
            width: 30px;
            height: 30px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            font-size: 16px;
        }
 
        .qty-btn:hover { background-color: var(--primary-yellow); color: var(--bg-dark); }
.checkout-box {
    background-color: #0b0e12;
    border: 2px solid #252f3e;
    border-radius: 20px;
    padding: 25px;
    display: flex;
    flex-direction: column;
    height: 100%;
    overflow-y: auto;           /* ? BUNI O'CHIRIB TASHLANG */
} 
        .bill-details h3 {
            font-family: var(--font-display);
            color: var(--primary-yellow);
            margin-bottom: 20px;
            border-bottom: 2px dashed #273142;
            padding-bottom: 10px;
        }
  
        .bill-row { display: flex; justify-content: space-between; margin-bottom: 12px; font-size: 16px; }
 
        .total-row { border-top: 2px dashed #273142; padding-top: 15px; font-size: 20px; font-weight: bold; color: var(--accent-red); }
 
        .delivery-section { 
    margin-top: 20px; 
    display: none;
    flex: 1;                    /* ? QO'SHING */
    overflow-y: auto;          /* ? QO'SHING */
    padding-right: 8px;        /* ? QO'SHING */
}

        .customer-inputs { margin-bottom: 15px; display: flex; flex-direction: column; gap: 10px; }

        .customer-inputs input {
            width: 100%;
            background-color: #171d26;
            border: 1px solid #252f3e;
            padding: 10px 15px;
            border-radius: 10px;
            color: white;
            font-size: 15px;
            outline: none;
        }

        .customer-inputs input:focus { border-color: var(--primary-yellow); }

        .phone-method-selector {
            display: flex;
            gap: 10px;
            margin-bottom: 5px;
        }
        .method-btn {
            flex: 1;
            padding: 8px;
            border-radius: 8px;
            border: 1px solid #252f3e;
            background-color: #171d26;
            color: white;
            font-size: 13px;
            cursor: pointer;
            transition: 0.3s;
        }
        .method-btn.active {
            background-color: var(--primary-yellow);
            color: var(--bg-dark);
            font-weight: bold;
        }
 
        .history-section {
            margin-top: 20px;
            background-color: #171d26;
            border-radius: 15px;
            padding: 15px;
            border: 1px dashed #252f3e;
        }
        .history-title {
            font-size: 15px;
            color: var(--primary-yellow);
            margin-bottom: 10px;
            font-family: var(--font-display);
        }
        .history-item {
            background-color: #0f1319;
            padding: 10px;
            border-radius: 8px;
            font-size: 13px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: 0.2s;
            border: 1px solid transparent;
        }
        .history-item:hover {
            border-color: var(--primary-yellow);
            background-color: #141a22;
        }

        footer {
            background-color: #0b0e12;
            text-align: center;
            padding: 12px;
            font-size: 14px;
            color: #4b5563;
            border-top: 1px solid #1f2937;
        }

        .lang-modal {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-color: rgba(0,0,0,0.85);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
        }
        .lang-box {
            background-color: var(--bg-card);
            border: 2px solid var(--primary-yellow);
            border-radius: 25px;
            padding: 35px;
            text-align: center;
            width: 340px;
            box-shadow: 0 0 30px rgba(255,204,0,0.3);
        }
        .lang-box h3 {
            font-family: var(--font-display);
            color: white;
            font-size: 22px;
            margin-bottom: 25px;
        }
        .lang-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            width: 100%;
            padding: 14px;
            margin-bottom: 12px;
            border-radius: 15px;
            border: 2px solid #252f3e;
            background-color: #0f1319;
            color: white;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }
        .lang-btn:hover {
            border-color: var(--primary-yellow);
            transform: scale(1.03);
        }

        /* RESPONSIVE */
        @media (max-width: 768px) {
            header { padding: 10px 4%; }
            nav.desktop-nav { display: none; }
            .mobile-nav { display: grid; } /* Mobil panel ko'rinadi */
            .page { padding: 20px 4% 90px 4%; }
            .home-grid, .about-content, .cart-page { grid-template-columns: 1fr; gap: 25px; }
            .menu-grid { grid-template-columns: repeat(2, 1fr); gap: 12px; }
            .home-text h2 { font-size: 32px; text-align: center; }
            .home-text p { text-align: center; font-size: 16px; }
            .home-btns { justify-content: center; }
            .contact-card { width: 100%; padding: 20px; }
            footer { display: none; }
            .roulette-container { height: 280px; }
        }
    </style>
</head>
<body>

    <div class="lang-modal" id="languageModal">
        <div class="lang-box">
            <h3 id="lang-title">Choose Language / РўРёР»ni tanlang</h3>
            <button class="lang-btn" onclick="selectLanguage('uz')">рџ‡єрџ‡ї O'zbekcha</button>
            <button class="lang-btn" onclick="selectLanguage('ru')">рџ‡·рџ‡є Р СѓСЃСЃРєРёР№</button>
            <button class="lang-btn" onclick="selectLanguage('en')">рџ‡¬рџ‡§ English</button>
        </div>
    </div>
 
    <header>
        <div class="logo-area">
            <div class="logo-icon">в•</div>
            <div class="logo-text">
                <h1>STAKAN</h1>
                <span>CAFE</span>
            </div>
        </div>
        <nav class="desktop-nav">
            <a onclick="switchPage('home')" id="nav-home" class="active"><i class="fa-solid fa-house"></i> <span class="txt-home">Bosh sahifa</span></a>
            <a onclick="switchPage('menu')" id="nav-menu"><i class="fa-solid fa-utensils"></i> <span class="txt-menu">Menyu</span></a>
            <a onclick="switchPage('about')" id="nav-about"><i class="fa-solid fa-circle-info"></i> <span class="txt-about">Biz haqimizda</span></a>
            <a onclick="switchPage('contact')" id="nav-contact"><i class="fa-solid fa-phone"></i> <span class="txt-contact">Bog'lanish</span></a>
            <button class="savat-btn" onclick="switchPage('cart')">
                рџ›’ <span class="txt-cart">Savat</span>
                <div class="badge" id="cart-badge">0</div>
            </button>
        </nav>
    </header>

    <nav class="mobile-nav">
        <a onclick="switchPage('home')" id="m-nav-home" class="active"><i class="fa-solid fa-house"></i><span class="txt-home">Bosh sahifa</span></a>
        <a onclick="switchPage('menu')" id="m-nav-menu"><i class="fa-solid fa-utensils"></i><span class="txt-menu">Menyu</span></a>
        
        <div class="mobile-cart-holder">
            <a onclick="switchPage('cart')" id="m-nav-cart">рџ›’</a>
            <div class="badge" id="m-cart-badge" style="top: -22px; right: 18px; z-index: 1000;">0</div>
        </div>
        
        <a onclick="switchPage('about')" id="m-nav-about"><i class="fa-solid fa-circle-info"></i><span class="txt-about">Biz haqimizda</span></a>
        <a onclick="switchPage('contact')" id="m-nav-contact"><i class="fa-solid fa-phone"></i><span class="txt-contact">Aloqa</span></a>
    </nav>
 
    <main> 
        <div id="page-home" class="page active">
            <div class="home-grid">
                <div class="home-text">
                    <h2 id="main-hero-title">STAKAN CAFE: Eng Mazali Tezkor Ovqat va Premium Kofe!</h2>
                    <p id="main-hero-desc">Sizga yoqadigan eng yaxshi va hamyonbop taomlar. Tezkor xizmat, sifatli mahsulot va unutilmas shinam muhit.</p>
                    <div class="home-btns">
                        <button class="btn-main btn-yellow txt-order-btn" onclick="switchPage('menu')">Buyurtma berish</button>
                    </div>
                </div>
                <div class="roulette-container">
                    <div class="roulette-track" id="roulette-track-output"></div>
                </div>
            </div>
        </div>
 
        <div id="page-menu" class="page">
            <div class="menu-container">
                <h2 class="menu-header txt-menu-title">Bizning Menyu</h2>
                <div class="menu-grid" id="menu-items-output"></div>
            </div>
        </div>
 
        <div id="page-about" class="page">
            <div class="about-content">
                <div class="map-visual">
                    <div class="landmark-illustration">
                        <i class="fa-solid fa-gopuram building" title="Maxdumi A'zam Ziyoratgohi"></i>
                        <span>в•</span>
                    </div>
                    <h4 class="txt-city">Kosonsoy Tumani</h4>
                    <p class="txt-landmark">Maxdumi A'zam tarixiy majmuasi yonida</p>
                    <div class="pin">
                        <i class="fa-solid fa-location-dot"></i> <span class="txt-region">Namangan Viloyati</span>
                    </div>
                </div>
                <div class="about-text">
                    <h2 class="txt-about-h2">Biz Haqimizda</h2>
                    <p id="about-p1"><strong>STAKAN CAFE</strong> - Namangan viloyati, Kosonsoy shahrining eng muqaddas va tarixiy go'shalaridan biri bo'lgan Maxdumi A'zam ziyoratgohi majmuasi yaqinida joylashgan zamonaviy fast-food maskanidir.</p>
                    <p id="about-p2">Bizning maqsadimiz - har bir mijozga yuqori sifatli, tezkor va mazali taomlarni taqdim etish orqali unga a'lo kayfiyat ulashishdir.</p>
                </div>
            </div>
        </div> 
 
        <div id="page-contact" class="page">
            <div class="contact-card">
                <h2 class="txt-contact-h2">Biz bilan aloqa</h2>
                <a href="https://instagram.com" target="_blank" class="contact-link insta">
                    <i class="fa-brands fa-instagram"></i> @stakancafe_kosonsoy
                </a>
                <a href="https://t.me" target="_blank" class="contact-link tg">
                    <i class="fa-brands fa-telegram"></i> Telegram Kanalimiz
                </a>
                <a href="tel:+998336262223" class="contact-link phone">
                    <i class="fa-solid fa-phone"></i> +998 (33) 626-22-23
                </a>
            </div>
        </div>
 
        <div id="page-cart" class="page">
            <div class="cart-page">
                <div class="cart-list-container">
                    <h2 style="font-family: var(--font-display); color: var(--primary-yellow); margin-bottom: 15px;" class="txt-cart-h2">Savatdagi mahsulotlar</h2>
                    <div class="cart-items-scroll" id="cart-list-output"></div>
                    
                    <div class="history-section">
                        <div class="history-title"><i class="fa-solid fa-clock-rotate-left"></i> <span class="txt-history-title">Oxirgi buyurtmalarim:</span></div>
                        <div id="history-output"></div>
                    </div>
                </div>
                
                <div class="checkout-box">
                    <div class="bill-details">
                        <h3><i class="fa-solid fa-receipt"></i> <span class="txt-receipt">Buyurtma Cheki</span></h3>
                        <div id="bill-items"></div>
                        <div class="bill-row total-row">
                            <span class="txt-total">Umumiy summa:</span>
                            <span id="total-price-sum">0 UZS</span>
                        </div>
                    </div>
                    
                    <div class="delivery-section" id="delivery-area">
                        <div class="customer-inputs">
                            <input type="text" id="cust-name" placeholder="Ismingizni kiriting..." required>
                            
                            <div class="phone-method-selector">
                                <button type="button" class="method-btn active" id="btn-method-auto" onclick="setPhoneMethod('auto')">вњЁ Avto</button>
                                <button type="button" class="method-btn" id="btn-method-manual" onclick="setPhoneMethod('manual')">вњЌпёЏ Qo'lda</button>
                            </div>
                            
                            <input type="tel" id="cust-phone" name="telephone" placeholder="Telefon raqamingiz..." autocomplete="tel" inputmode="tel" required>
                        </div>

                        <div class="bill-row" style="color: #4caf50; font-weight: bold; margin-bottom: 15px;">
                            <span><i class="fa-solid fa-truck"></i> <span class="txt-our-phone">Aloqa raqamimiz:</span></span>
                            <span>+998 (33) 626-22-23</span>
                        </div>
                        <button class="btn-main btn-yellow" style="width: 100%;" onclick="confirmOrder()">
                            <i class="fa-solid fa-circle-check"></i> <span class="txt-confirm">Buyurtmani Tasdiqlash</span>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </main>
 
    <script>
        // Aniq va chiroyli haqiqiy Emojilar o'rnatildi
        const products = [
            { id: 1, name: "Stakan Burger", desc: "Mol go'shti, pishloq, yangi salat", price: 15000, emoji: "рџЌ”" }, 
            { id: 2, name: "Lavash Klassik", desc: "Tortilla, go'sht, sara sabzavotlar", price: 12000, emoji: "рџЊЇ" },
            { id: 3, name: "Pitsa Marinara", desc: "Pomidor, pishloq, zaytun", price: 18000, emoji: "рџЌ•" },
            { id: 4, name: "Espresso", desc: "Premium kuchli italyan kofesi", price: 5000, emoji: "в•" },
            { id: 5, name: "Kapuchino", desc: "Yumshoq ko'pikli sut va qahva", price: 6000, emoji: "рџҐ¤" },
            { id: 6, name: "Shakoli Shake", desc: "Toza sut va tabiiy shokolad", price: 7000, emoji: "рџ§‹" },
            { id: 7, name: "Gamburger mini", desc: "Klassik kichik kotletli burger", price: 10000, emoji: "рџЌ”" },
            { id: 8, name: "Klab Sendvich", desc: "Tost non, tovuq go'shti, sous", price: 14000, emoji: "рџҐЄ" }
        ];
 
        let cart = {};
        let currentLang = 'uz';
        let phoneMethod = 'auto';
        let rouletteIndex = 0;

        const languages = {
            uz: {
                home: "Bosh sahifa", menu: "Menyu", about: "Biz haqimizda", contact: "Bog'lanish", cart: "Savat",
                heroTitle: "STAKAN CAFE: Eng Mazali Fast-Food va Premium Kofe!", heroDesc: "Sizga yoqadigan eng yaxshi va hamyonbop taomlar. Tezkor xizmat va unutilmas shinam muhit.",
                orderBtn: "Buyurtma berish", menuTitle: "Bizning Menyu", city: "Kosonsoy Tumani", landmark: "Maxdumi A'zam majmuasi yaqinida",
                region: "Namangan Viloyati", aboutH2: "Biz Haqimizda", contactH2: "Biz bilan aloqa", cartH2: "Savatdagi mahsulotlar",
                receipt: "Buyurtma Cheki", total: "Umumiy summa:", ourPhone: "Aloqa raqami:", confirm: "Tasdiqlash",
                historyTitle: "Oxirgi buyurtmalarim (Tanlash uchun bosing):", emptyCart: "Savat bo'sh. Menyudan biror narsa qo'shing!",
                noItems: "Mahsulot tanlanmagan", placeholderName: "Ismingizni kiriting...", alertFields: "Iltimos, ism va telefonni kiriting!",
                alertSuccess: "Rahmat! Buyurtmangiz Telegramga yuborildi.", noHistory: "Eski buyurtmalar mavjud emas."
            },
            ru: {
                home: "Р“Р»Р°РІРЅР°СЏ", menu: "РњРµРЅСЋ", about: "Рћ РЅР°СЃ", contact: "РљРѕРЅС‚Р°РєС‚С‹", cart: "РљРѕСЂР·РёРЅР°",
                heroTitle: "STAKAN CAFE: Р’РєСѓСЃРЅС‹Р№ Р¤Р°СЃС‚-Р¤СѓРґ Рё РџСЂРµРјРёР»РёСЏ РљРѕС„Рµ!", heroDesc: "Р›СѓС‡С€РёРµ Рё РґРѕСЃС‚СѓРїРЅС‹Рµ Р±Р»СЋРґР°, РєРѕС‚РѕСЂС‹Рµ РІР°Рј РїРѕРЅСЂР°РІСЏС‚СЃСЏ. Р‘С‹СЃС‚СЂС‹Р№ СЃРµСЂРІРёСЃ Рё СѓСЋС‚РЅР°СЏ Р°С‚РјРѕСЃС„РµСЂР°.",
                orderBtn: "Р—Р°РєР°Р·Р°С‚СЊ СЃРµР№С‡Р°СЃ", menuTitle: "РќР°С€Рµ РњРµРЅСЋ", city: "РљР°СЃР°РЅСЃР°Р№СЃРєРёР№ СЂР°Р№РѕРЅ", landmark: "Р СЏРґРѕРј СЃ РєРѕРјРїР»РµРєСЃРѕРј РњР°С…РґСѓРјРё РђСЉР·Р°Рј",
                region: "РќР°РјР°РЅРіР°РЅСЃРєР°СЏ РѕР±Р»Р°СЃС‚СЊ", aboutH2: "Рћ РќР°СЃ", contactH2: "РЎРІСЏР·Р°С‚СЊСЃСЏ СЃ РЅР°РјРё", cartH2: "РўРѕРІР°СЂС‹ РІ РєРѕСЂР·РёРЅРµ",
                receipt: "Р§РµРє Р·Р°РєР°Р·Р°", total: "РћР±С‰Р°СЏ СЃСѓРјРјР°:", ourPhone: "РќР°С€ С‚РµР»РµС„РѕРЅ:", confirm: "РџРѕРґС‚РІРµСЂРґРёС‚СЊ Р·Р°РєР°Р·",
                historyTitle: "РњРѕРё РїРѕСЃР»РµРґРЅРёРµ Р·Р°РєР°Р·С‹ (РќР°Р¶РјРёС‚Рµ РґР»СЏ РІС‹Р±РѕСЂР°):", emptyCart: "РљРѕСЂР·РёРЅР° РїСѓСЃС‚Р°. Р”РѕР±Р°РІСЊС‚Рµ Р±Р»СЋРґР° РёР· РјРµРЅСЋ!",
                noItems: "РўРѕРІР°СЂС‹ РЅРµ РІС‹Р±СЂР°РЅС‹", placeholderName: "Р’РІРµРґРёС‚Рµ РІР°С€Рµ РёРјСЏ...", alertFields: "РџРѕР¶Р°Р»СѓР№СЃС‚Р°, РІРІРµРґРёС‚Рµ РёРјСЏ Рё С‚РµР»РµС„РѕРЅ!",
                alertSuccess: "РЎРїР°СЃРёР±Рѕ! Р’Р°С€ Р·Р°РєР°Р· РѕС‚РїСЂР°РІР»РµРЅ РІ Telegram.", noHistory: "РќРµС‚ РїСЂРµРґС‹РґСѓС‰РёС… Р·Р°РєР°Р·РѕРІ."
            },
            en: {
                home: "Home", menu: "Menu", about: "About Us", contact: "Contact", cart: "Cart",
                heroTitle: "STAKAN CAFE: Delicious Fast-Food & Premium Coffee!", heroDesc: "The best and affordable dishes you will love. Fast service and a cozy atmosphere.",
                orderBtn: "Order Now", menuTitle: "Our Menu", city: "Kasansay District", landmark: "Near Maxdumi A'zam complex",
                region: "Namangan Region", aboutH2: "About Us", contactH2: "Contact Us", cartH2: "Items in Cart",
                receipt: "Receipt Details", total: "Total Amount:", ourPhone: "Our Phone:", confirm: "Confirm Order",
                historyTitle: "My Recent Orders (Click to choose):", emptyCart: "Cart is empty. Add items from Menu!",
                noItems: "No items selected", placeholderName: "Enter your name...", alertFields: "Please enter name and phone number!",
                alertSuccess: "Thank you! Your order has been sent to Telegram.", noHistory: "No history found."
            }
        };

        function selectLanguage(lang) {
            currentLang = lang;
            document.getElementById('languageModal').style.display = 'none';
            applyTranslations();
        }

        function applyTranslations() {
            const l = languages[currentLang];
            document.querySelectorAll('.txt-home').forEach(el => el.innerText = l.home);
            document.querySelectorAll('.txt-menu').forEach(el => el.innerText = l.menu);
            document.querySelectorAll('.txt-about').forEach(el => el.innerText = l.about);
            document.querySelectorAll('.txt-contact').forEach(el => el.innerText = l.contact);
            document.querySelectorAll('.txt-cart').forEach(el => el.innerText = l.cart);
            
            document.getElementById('main-hero-title').innerText = l.heroTitle;
            document.getElementById('main-hero-desc').innerText = l.heroDesc;
            document.querySelector('.txt-order-btn').innerText = l.orderBtn;
            document.querySelector('.txt-menu-title').innerText = l.menuTitle;
            document.querySelector('.txt-city').innerText = l.city;
            document.querySelector('.txt-landmark').innerText = l.landmark;
            document.querySelector('.txt-region').innerText = l.region;
            document.querySelector('.txt-about-h2').innerText = l.aboutH2;
            document.querySelector('.txt-contact-h2').innerText = l.contactH2;
            document.querySelector('.txt-cart-h2').innerText = l.cartH2;
            document.querySelector('.txt-receipt').innerText = l.receipt;
            document.querySelector('.txt-total').innerText = l.total;
            document.querySelector('.txt-our-phone').innerText = l.ourPhone;
            document.querySelector('.txt-confirm').innerText = l.confirm;
            document.querySelector('.txt-history-title').innerText = l.historyTitle;
            
            document.getElementById('cust-name').placeholder = l.placeholderName;
            
            initMenu();
            initRoulette();
            updateCartPage();
        }

        // Avto raqam to'ldirish funksiyasi modernizatsiya qilindi
        function setPhoneMethod(method) {
            phoneMethod = method;
            document.getElementById('btn-method-auto').classList.remove('active');
            document.getElementById('btn-method-manual').classList.remove('active');
            
            const phoneInput = document.getElementById('cust-phone');
            
            if (method === 'auto') {
                document.getElementById('btn-method-auto').classList.add('active');
                phoneInput.value = ""; // Brauzerga avtomatik taklif chiqarish imkonini berish uchun bo'shatiladi
                phoneInput.placeholder = "Telefon raqamingizni bosing...";
                phoneInput.focus(); 
            } else {
                document.getElementById('btn-method-manual').classList.add('active');
                phoneInput.value = "+998";
                phoneInput.placeholder = "Kiritish...";
                phoneInput.focus();
            }
        }
 
        // 3D Ruletka Slayderini yaratish funksiyasi
        function initRoulette() {
            const track = document.getElementById('roulette-track-output');
            track.innerHTML = products.map((p, idx) => `
                <div class="roulette-card" id="roulette-card-${idx}">
                    <span class="food-emoji">${p.emoji}</span>
                    <h4>${p.name}</h4>
                </div>
            `).join('');
            
            animateRoulette();
            setInterval(() => {
                rouletteIndex = (rouletteIndex + 1) % products.length;
                animateRoulette();
            }, 2500); // Har 2.5 sekundda aylanadi
        }

        // Ruletka holatlarini yangilab blur effektini berish
        function animateRoulette() {
            const len = products.length;
            products.forEach((_, idx) => {
                const card = document.getElementById(`roulette-card-${idx}`);
                if (!card) return;
                
                card.className = "roulette-card"; // Tozalash
                
                if (idx === rouletteIndex) {
                    card.classList.add('active-center');
                } else if (idx === (rouletteIndex - 1 + len) % len) {
                    card.classList.add('active-left');
                } else if (idx === (rouletteIndex + 1) % len) {
                    card.classList.add('active-right');
                } else if (idx === (rouletteIndex - 2 + len) % len) {
                    card.classList.add('hidden-left');
                } else {
                    card.classList.add('hidden-right');
                }
            });
        }

        function initMenu() {
            const container = document.getElementById('menu-items-output');
            container.innerHTML = products.map(p => `
                <div class="menu-item">
                    <div class="count-badge" id="badge-${p.id}">0</div>
                    <div class="menu-item-emoji">${p.emoji}</div>
                    <h3>${p.name}</h3>
                    <p>${p.desc}</p>
                    <div class="price">${p.price.toLocaleString()} UZS</div>
                    <button class="btn-main btn-yellow" style="font-size: 14px; padding: 8px 20px;" onclick="addToCart(${p.id})">
                        рџ›’ ${currentLang === 'uz' ? 'Savatga qo\'shish' : currentLang === 'ru' ? 'Р’ РєРѕСЂР·РёРЅСѓ' : 'Add to Cart'}
                    </button>
                </div>
            `).join('');
            updateDOM();
        }
 
        function switchPage(pageId) {
            document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
            document.querySelectorAll('nav a').forEach(link => link.classList.remove('active'));
 
            document.getElementById(`page-${pageId}`).classList.add('active');
            
            const navLinkDesktop = document.getElementById(`nav-${pageId}`);
            if (navLinkDesktop) navLinkDesktop.classList.add('active');
            
            const navLinkMobile = document.getElementById(`m-nav-${pageId}`);
            if (navLinkMobile) navLinkMobile.classList.add('active');

            if(pageId === 'cart') {
                updateCartPage();
            }
        }
 
        function addToCart(id) {
            if (cart[id]) { cart[id]++; } else { cart[id] = 1; }
            updateDOM();
        }
 
        function changeQty(id, delta) {
            if (cart[id]) {
                cart[id] += delta;
                if (cart[id] <= 0) delete cart[id];
            }
            updateDOM();
            updateCartPage();
        }
 
        function updateDOM() {
            let totalItems = 0;
            products.forEach(p => {
                const countBadge = document.getElementById(`badge-${p.id}`);
                if (countBadge) {
                    if (cart[p.id] && cart[p.id] > 0) {
                        countBadge.innerText = cart[p.id];
                        countBadge.style.display = "flex";
                        totalItems += cart[p.id];
                    } else {
                        countBadge.style.display = "none";
                    }
                }
            });
            document.getElementById('cart-badge').innerText = totalItems;
            document.getElementById('m-cart-badge').innerText = totalItems;
        }
 
        function updateCartPage() {
            const listOutput = document.getElementById('cart-list-output');
            const billOutput = document.getElementById('bill-items');
            const deliveryArea = document.getElementById('delivery-area');
            const l = languages[currentLang];
            
            let totalSum = 0;
            let listHtml = "";
            let billHtml = "";
            const activeIds = Object.keys(cart);
 
            if (activeIds.length === 0) {
                listOutput.innerHTML = `<div style="text-align:center; padding:30px; color:#6b7280;">${l.emptyCart}</div>`;
                billOutput.innerHTML = `<div style="color:#6b7280; font-size:14px;">${l.noItems}</div>`;
                document.getElementById('total-price-sum').innerText = "0 UZS";
                deliveryArea.style.display = "none";
                showOrderHistory();
                return;
            }
 
            activeIds.forEach(id => {
                const item = products.find(p => p.id == id); 
                const itemTotal = item.price * cart[id];
                totalSum += itemTotal;
 
                listHtml += `
                    <div class="cart-item">
                        <div class="cart-item-info">
                            <span class="item-emoji">${item.emoji}</span>
                            <div>
                                <h4 style="font-family: var(--font-display);">${item.name}</h4>
                                <span style="color:var(--accent-red); font-weight:700;">${item.price.toLocaleString()} UZS</span>
                            </div>
                        </div>
                        <div class="cart-item-controls">
                            <button class="qty-btn" onclick="changeQty(${id}, -1)">-</button>
                            <span style="font-weight:bold; width:20px; text-align:center;">${cart[id]}</span>
                            <button class="qty-btn" onclick="changeQty(${id}, 1)">+</button>
                        </div>
                    </div>
                `;
 
                billHtml += `
                    <div class="bill-row">
                        <span>${item.name} x ${cart[id]}</span>
                        <span>${itemTotal.toLocaleString()} UZS</span>
                    </div>
                `;
            });
 
            listOutput.innerHTML = listHtml;
            billOutput.innerHTML = billHtml;
            document.getElementById('total-price-sum').innerText = totalSum.toLocaleString() + " UZS";
            deliveryArea.style.display = "block";
            
            showOrderHistory();
        }

        function showOrderHistory() {
            const historyOutput = document.getElementById('history-output');
            let historyData = localStorage.getItem('stakan_history');
            const l = languages[currentLang];

            if (!historyData) {
                historyOutput.innerHTML = `<div style="color:#6b7280; font-size:13px;">${l.noHistory}</div>`;
                return;
            }

            let orders = JSON.parse(historyData);
            let html = "";
            orders.forEach((order, index) => {
                html += `
                    <div class="history-item" onclick="loadOldOrder(${index})">
                        <strong>в„–${index + 1} | ${order.date}</strong><br>
                        <span style="color:#9ca3af;">${order.summary}</span>
                    </div>
                `;
            });
            historyOutput.innerHTML = html;
        }

        function loadOldOrder(index) {
            let historyData = localStorage.getItem('stakan_history');
            if(historyData) {
                let orders = JSON.parse(historyData);
                cart = orders[index].cart;
                updateDOM();
                updateCartPage();
            }
        }
 
        function confirmOrder() {
            const botToken = "8417416146:AAGc6wdf6E0mQaB9zH_tUNhBeIpfXFgP_BU";
            const chatId = "7583392349";
            const name = document.getElementById('cust-name').value.trim();
            const phone = document.getElementById('cust-phone').value.trim();
            const l = languages[currentLang];

            if (!name || !phone) {
                alert(l.alertFields);
                return;
            }
 
            const activeIds = Object.keys(cart);
            if (activeIds.length === 0) { return; }
 
            let message = `?? *YANGI BUYURTMA (STAKAN CAFE)*\n`;
            message += `---------------\n`;
            message += `?? *Mijoz:* ${name}\n`;
            message += `?? *Tel:* ${phone}\n`;
            message += `?? *Til:* ${currentLang.toUpperCase()}\n`;
            message += `---------------\n`;
            let totalSum = 0;
            let summaryText = "";

            activeIds.forEach(id => {
                const item = products.find(p => p.id == id);
                const itemTotal = item.price * cart[id];
                totalSum += itemTotal;
                message += `?? *${item.name}*\n` + `   ${cart[id]} ta x ${item.price.toLocaleString()} = ${itemTotal.toLocaleString()} UZS\n\n`;
                summaryText += `${item.name} (${cart[id]}x), `;
            });
            message += `---------------\n`;
            message += `?? *Umumiy summa:* ${totalSum.toLocaleString()} UZS`;
 
            const telegramUrl = `https://api.telegram.org/bot${botToken}/sendMessage`;
            fetch(telegramUrl, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ chat_id: chatId, text: message, parse_mode: "Markdown" })
            })
            .then(response => {
                if (response.ok) {
                    alert(l.alertSuccess);
                    
                    let historyData = localStorage.getItem('stakan_history');
                    let orders = historyData ? JSON.parse(historyData) : [];
                    
                    let now = new Date();
                    let dateStr = `${now.getDate()}.${now.getMonth()+1} ${now.getHours()}:${now.getMinutes()}`;
                    
                    orders.unshift({
                        date: dateStr,
                        cart: cart,
                        summary: summaryText.substring(0, summaryText.length - 2) + " = " + totalSum.toLocaleString() + " UZS"
                    });
                    
                    if(orders.length > 5) orders.pop();
                    localStorage.setItem('stakan_history', JSON.stringify(orders));

                    cart = {};
                    updateDOM();
                    switchPage('home');
                }
            });
        }
 
        window.onload = () => {
            document.getElementById('languageModal').style.display = 'flex';
            setPhoneMethod('auto');
        };
    </script>
</body>
</html>
