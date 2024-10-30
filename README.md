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
        <div>wafaa salem shalash</div>
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
                <img src="cat1.jpg" alt="قطط سيامي">
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
