<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>عالم القطط</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            margin: 0;
            padding: 0;
        }

        /* الشريط العلوي */
        header {
            background-color: #ffcc99;
            color: #fff;
            padding: 15px 0;
            text-align: center;
            font-size: 24px;
        }

        nav {
            background-color: #ff9966;
            padding: 10px 0;
        }

        nav a {
            color: #fff;
            margin: 0 15px;
            text-decoration: none;
            font-size: 18px;
        }

        nav a:hover {
            text-decoration: underline;
        }

        /* الصورة الرئيسية */
        .hero {
            background-image: url('cat.jpg'); /* ضع صورة للقطة هنا */
            background-size: cover;
            background-position: center;
            height: 400px;
            color: white;
            text-align: center;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 36px;
            font-weight: bold;
        }

        /* أقسام الموقع */
        .section {
            padding: 40px 20px;
            text-align: center;
        }

        .section h2 {
            font-size: 28px;
            margin-bottom: 20px;
        }

        .section p {
            font-size: 16px;
            color: #555;
            line-height: 1.6;
        }

        .cat-grid {
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .cat-card {
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
            max-width: 300px;
            text-align: center;
        }

        .cat-card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 8px;
        }

        /* الجزء السفلي */
        footer {
            background-color: #ff9966;
            color: #fff;
            padding: 20px;
            text-align: center;
            font-size: 14px;
        }

        footer a {
            color: #fff;
            margin: 0 10px;
            text-decoration: none;
        }
    </style>
</head>
<body>

    <!-- الشعار -->
    <header>
        <div>my_cat</div>
    </header>

    <!-- شريط التنقل -->
    <nav>
        <a href="#">الصفحة الرئيسية</a>
        <a href="#">معلومات عن القطط</a>
        <a href="#">العناية بالقطط</a>
        <a href="#">تبني القطط</a>
        <a href="#">معرض صور</a>
        <a href="#">تواصل معنا</a>
    </nav>

    <!-- الصورة الرئيسية -->
    <div class="hero">
        أهلاً بك في عالم القطط
    </div>

    <!-- أقسام الموقع -->
    <section class="section">
        <h2>أنواع القطط</h2>
        <div class="cat-grid">
            <div class="cat-card">
                <img src="data:image/jpeg;base64,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" alt="قطط سيامي">
                <h3>قط سيامي</h3>
                <p>القط السيامي يتميز بجماله وأناقة مظهره، ويُعد من أكثر القطط شهرة.</p>
            </div>
            <div class="cat-card">
                <img src="cat2.jpg" alt="قطط شيرازي">
                <h3>قط شيرازي</h3>
                <p>القط الشيرازي له فرو طويل وكثيف ويتميز بطبيعته الهادئة واللطيفة.</p>
            </div>
            <div class="cat-card">
                <img src="cat3.jpg" alt="قطط بنغالي">
                <h3>قط بنغالي</h3>
                <p>القط البنغالي يمتاز بجلده المنقط وشخصيته النشيطة والحيوية.</p>
            </div>
        </div>
    </section>

    <section class="section" style="background-color: #f2f2f2;">
        <h2>نصائح للعناية بالقطط</h2>
        <p>تعرف على أفضل الطرق للعناية بصحة وسلامة قطتك، بدءًا من التغذية وحتى الحفاظ على نشاطها البدني والعقلي.</p>
    </section>

    <!-- الجزء السفلي -->
    <footer>
        &copy; 2024 عالم القطط. جميع الحقوق محفوظة.
        <br>
        <a href="#">فيسبوك</a> | <a href="#">إنستغرام</a> | <a href="#">تويتر</a>
    </footer>

</body>
</html>
