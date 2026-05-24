<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Бесплатный онлайн генератор QR-кодов. Создайте QR для ссылок, текста и Wi-Fi быстро и без регистрации.">
<meta name="keywords" content="генератор qr, qr код онлайн, создать qr код, qr-код для ссылки">
    <title>Бесплатный Генератор QR Кодов</title>
    <!-- Подключение библиотеки для генерации QR -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    
    <!-- СЮДА ВСТАВИТЬ КОД РЕКЛАМЫ ADSTERRA (HEAD SECTION) -->
    <!-- Например: <script src="//pl123456789.highperformanceformat.com/..."></script> -->

    <style>
        :root {
            --primary-color: #4a90e2;
            --bg-color: #f4f7f6;
            --card-bg: #ffffff;
            --text-color: #333;
            --ad-bg: #eef2f5; /* Цвет фона для рекламных блоков */
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        /* --- Рекламный блок ВЕРХНИЙ --- */
        .ad-banner-top {
            width: 100%;
            height: 90px; /* Высота баннера */
            background-color: var(--ad-bg);
            display: flex;
            align-items: center;
            justify-content: center;
            border-bottom: 1px solid #ddd;
            margin-bottom: 20px;
            overflow: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            display: grid;
            grid-template-columns: 1fr 300px; /* Основной контент + Сайдбар */
            gap: 20px;
            flex: 1;
        }

        /* --- Основной контент --- */
        .main-content {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        h1 { text-align: center; margin-bottom: 30px; color: var(--primary-color); }

        .input-group {
            margin-bottom: 20px;
        }

        label { display: block; margin-bottom: 8px; font-weight: bold; }
        
        input[type="text"], input[type="url"] {
            width: 100%;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
            box-sizing: border-box; /* Важно для отступов */
        }

        button.generate-btn {
            width: 100%;
            padding: 15px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
            transition: background 0.3s;
        }

        button.generate-btn:hover { background-color: #357abd; }

        #qrcode {
            margin-top: 30px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 200px;
            border: 2px dashed #eee;
            border-radius: 10px;
            padding: 20px;
        }

        #qrcode img { max-width: 100%; height: auto; }

        /* --- Рекламный блок ПОД РЕЗУЛЬТАТОМ --- */
        .ad-banner-bottom {
            width: 100%;
            height: 250px;
            background-color: var(--ad-bg);
            margin-top: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 8px;
        }

        /* --- Боковая реклама (Сайдбар) --- */
        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .ad-sidebar-block {
            width: 100%;
            height: 600px; /* Высокий вертикальный блок */
            background-color: var(--ad-bg);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: sticky;
            top: 20px;
        }

        /* Адаптивность для мобильных */
        @media (max-width: 768px) {
            .container { grid-template-columns: 1fr; }
            .ad-sidebar-block { height: 250px; position: static; }
            .ad-banner-top { height: 60px; }
        }
        
        .placeholder-text { color: #999; font-size: 14px; }
    </style>
</head>
<body>

    <!-- РЕКЛАМА: Верхний баннер -->
    <div class="ad-banner-top">
        <!-- Вставьте код Adsterra сюда -->
        <span class="placeholder-text">Реклама (Adsterra Top Banner)</span>
    </div>

    <div class="container">
        <!-- Левая часть: Генератор -->
        <div class="main-content">
            <h1>Генератор QR Кодов</h1>
            
            <div class="input-group">
                <label for="qr-text">Введите текст или ссылку:</label>
                <input type="text" id="qr-text" placeholder="https://example.com или любой текст...">
            </div>

            <button class="generate-btn" onclick="generateQR()">Создать QR Код</button>

            <div id="qrcode">
                <span class="placeholder-text">Здесь появится ваш QR код</span>
            </div>

            <!-- РЕКЛАМА: Блок под генератором -->
            <div class="ad-banner-bottom">
                <!-- Вставьте код Adsterra сюда -->
                <span class="placeholder-text">Реклама (Native Banner / In-Page Push)</span>
            </div>
        </div>

        <!-- Правая часть: Реклама -->
        <aside class="sidebar">
            <div class="ad-sidebar-block">
                <!-- Вставьте код Adsterra сюда -->
                <span class="placeholder-text">Реклама (Vertical Banner)</span>
            </div>
        </aside>
    </div>

    <script>
        function generateQR() {
            const text = document.getElementById("qr-text").value;
            const qrContainer = document.getElementById("qrcode");

            if (!text) {
                alert("Пожалуйста, введите текст или ссылку!");
                return;
            }

            // Очищаем предыдущий QR код
            qrContainer.innerHTML = "";

            // Генерируем новый
            new QRCode(qrContainer, {
                text: text,
                width: 256,
                height: 256,
                colorDark : "#000000",
                colorLight : "#ffffff",
                correctLevel : QRCode.CorrectLevel.H
            });
        }
    </script>
</body>
</html>

