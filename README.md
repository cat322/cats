<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سوق العالم | التسوق الشامل</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --main-color: #2563eb;
            --bg-color: #f1f5f9;
            --card-bg: #ffffff;
            --text-dark: #0f172a;
        }

        body {
            font-family: 'Cairo', sans-serif;
            background-color: var(--bg-color);
            margin: 0; padding: 0;
            color: var(--text-dark);
        }

        /* شريط التنقل */
        nav {
            background: var(--main-color);
            color: white;
            padding: 1rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky; top: 0; z-index: 1000;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1);
        }

        .back-btn {
            background: rgba(255,255,255,0.2);
            border: none; color: white;
            padding: 5px 15px; border-radius: 8px;
            cursor: pointer; font-size: 1.2rem;
            display: none; margin-left: 15px;
        }

        .container { max-width: 1200px; margin: 2rem auto; padding: 0 20px; }

        /* نموذج التسجيل */
        .registration-card {
            max-width: 450px;
            margin: 50px auto;
            background: white;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }

        .input-group { text-align: right; margin-bottom: 15px; }
        .input-group label { display: block; margin-bottom: 5px; font-weight: bold; font-size: 0.9rem; }
        
        input {
            width: 100%; padding: 12px;
            border: 1px solid #cbd5e1;
            border-radius: 8px; box-sizing: border-box;
            font-family: 'Cairo';
        }

        /* الأقسام والمنتجات */
        .category-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 15px;
        }

        .cat-card {
            background: white; border: 1px solid #e2e8f0;
            padding: 20px; border-radius: 12px;
            cursor: pointer; text-align: center;
            transition: 0.2s; font-weight: bold;
        }

        .cat-card:hover { border-color: var(--main-color); background: #eff6ff; color: var(--main-color); }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
        }

        .product-card {
            background: white; border-radius: 12px;
            overflow: hidden; border: 1px solid #e2e8f0;
            display: flex; flex-direction: column;
        }

        .product-card img { width: 100%; height: 180px; object-fit: cover; }
        
        .btn-action {
            background: var(--main-color); color: white;
            border: none; padding: 12px; border-radius: 8px;
            cursor: pointer; font-weight: bold; width: 100%;
        }

        .hidden { display: none; }
    </style>
</head>
<body>

    <nav id="navbar" class="hidden">
        <div style="display: flex; align-items: center;">
            <button class="back-btn" id="global-back-btn" onclick="goBack()">➔</button>
            <div style="font-weight: bold; font-size: 1.2rem;">🛒 متجري الشامل</div>
        </div>
        <div>
            <span onclick="showPage('categories')" style="cursor:pointer">الأقسام</span> | 
            <span onclick="showPage('cart')" style="cursor:pointer">السلة (<span id="cart-count">0</span>)</span>
        </div>
    </nav>

    <div class="container">
        
        <div id="login-page">
            <div class="registration-card">
                <h2 style="text-align: center; margin-top: 0;">إنشاء حساب جديد</h2>
                <div class="input-group">
                    <label>الاسم الكامل</label>
                    <input type="text" id="reg-name" placeholder="مثال: محمد علي">
                </div>
                <div class="input-group">
                    <label>البريد الإلكتروني</label>
                    <input type="email" id="reg-email" placeholder="name@example.com">
                </div>
                <div class="input-group">
                    <label>رقم الهاتف</label>
                    <input type="tel" id="reg-phone" placeholder="07XXXXXXXX">
                </div>
                <div class="input-group">
                    <label>رقم الدار / العنوان</label>
                    <input type="text" id="reg-address" placeholder="رقم الزقاق أو الدار">
                </div>
                <button class="btn-action" onclick="registerUser()">تسجيل والدخول للمتجر</button>
            </div>
        </div>

        <div id="categories-page" class="hidden">
            <h2 id="welcome-msg"></h2>
            <div class="category-grid" id="category-list"></div>
        </div>

        <div id="products-page" class="hidden">
            <input type="text" id="searchBar" placeholder="ابحث عن منتج..." onkeyup="searchProducts()" style="margin-bottom: 20px;">
            <h2 id="current-cat-name"></h2>
            <div class="products-grid" id="products-list"></div>
        </div>

        <div id="cart-page" class="hidden">
            <div class="registration-card" style="max-width: 600px;">
                <h2>سلتك المشتريات</h2>
                <div id="cart-items-list" style="margin-bottom: 20px;"></div>
                <div id="shipping-info" style="background: #f8fafc; padding: 10px; border-radius: 8px; font-size: 0.9rem; margin-bottom: 15px;"></div>
                <h3 id="total-price">الإجمالي: 0$</h3>
                <button class="btn-action" onclick="finishOrder()">تأكيد طلب الشراء</button>
            </div>
        </div>

    </div>

    <script>
        const categories = ['سيارات', 'حيوانات', 'جوالات', 'أثاث', 'ساعات', 'عطور', 'أدوات مطبخ', 'ألعاب أطفال', 'كتب', 'رياضة', 'ملابس', 'كاميرات', 'أجهزة لوحية', 'حقائب', 'أحذية', 'نظارات', 'مجوهرات', 'صناعة يدوية', 'بذور', 'طيور', 'أسماك', 'قطط', 'معدات تخييم', 'دراجات', 'شاشات', 'صوتيات', 'موسيقى', 'هدايا', 'حلويات', 'عسل', 'قهوة', 'أجبان', 'زيوت', 'خضروات', 'مكسرات', 'منظفات', 'عناية بالبشرة', 'مكياج', 'إضاءة', 'ديكور جدران', 'سجاد', 'مكيفات', 'غسالات', 'ثلاجات', 'لابتوبات', 'برمجيات', 'ألعاب فيديو', 'إكسسوارات', 'صيد', 'خياطة'];

        let userData = {};
        let cart = [];
        let navHistory = [];
        const productsStore = {};

        // إنشاء 2500 منتج (50 لكل قسم)
        function initData() {
            categories.forEach(cat => {
                productsStore[cat] = Array.from({length: 50}, (_, i) => ({
                    name: `${cat} - منتج ${i+1}`,
                    price: Math.floor(Math.random() * 900) + 10,
                    img: `https://loremflickr.com/320/240/${encodeURIComponent(cat)}?lock=${i}`
                }));
            });
        }

        function registerUser() {
            userData = {
                name: document.getElementById('reg-name').value,
                email: document.getElementById('reg-email').value,
                phone: document.getElementById('reg-phone').value,
                address: document.getElementById('reg-address').value
            };

            if(Object.values(userData).some(val => val === "")) {
                alert("يرجى ملء كافة الحقول");
                return;
            }

            document.getElementById('welcome-msg').innerText = `مرحباً بك يا ${userData.name}، تصفح أقسامنا:`;
            document.getElementById('navbar').classList.remove('hidden');
            renderCategories();
            showPage('categories');
        }

        function renderCategories() {
            const grid = document.getElementById('category-list');
            grid.innerHTML = categories.map(cat => `
                <div class="cat-card" onclick="loadProducts('${cat}')">${cat}</div>
            `).join('');
        }

        function loadProducts(cat) {
            document.getElementById('current-cat-name').innerText = "قسم " + cat;
            const list = document.getElementById('products-list');
            list.innerHTML = productsStore[cat].map(p => `
                <div class="product-card">
                    <img src="${p.img}" loading="lazy">
                    <div style="padding:15px">
                        <h4 style="margin:0">${p.name}</h4>
                        <p style="color:var(--main-color); font-weight:bold">${p.price}$</p>
                        <button class="btn-action" onclick="addToCart('${p.name}', ${p.price})">أضف للسلة</button>
                    </div>
                </div>
            `).join('');
            showPage('products');
        }

        function showPage(pageId, record = true) {
            ['login-page', 'categories-page', 'products-page', 'cart-page'].forEach(p => {
                document.getElementById(p).classList.add('hidden');
            });
            document.getElementById(pageId + (pageId.includes('page') ? '' : '-page')).classList.remove('hidden');
            
            if(record) navHistory.push(pageId);
            document.getElementById('global-back-btn').style.display = (pageId === 'categories' || pageId === 'login') ? 'none' : 'block';
        }

        function goBack() {
            if(navHistory.length > 1) {
                navHistory.pop();
                showPage(navHistory[navHistory.length-1], false);
            }
        }

        function addToCart(name, price) {
            cart.push({name, price});
            document.getElementById('cart-count').innerText = cart.length;
            updateCart();
        }

        function updateCart() {
            const list = document.getElementById('cart-items-list');
            const shipping = document.getElementById('shipping-info');
            let total = 0;
            
            list.innerHTML = cart.map(i => {
                total += i.price;
                return `<div style="display:flex; justify-content:space-between; padding:5px; border-bottom:1px solid #eee">
                    <span>${i.name}</span> <span>${i.price}$</span>
                </div>`;
            }).join('');

            shipping.innerHTML = `<strong>معلومات الشحن:</strong><br>${userData.name} | ${userData.phone}<br>${userData.address}`;
            document.getElementById('total-price').innerText = `الإجمالي: ${total}$`;
        }

        function searchProducts() {
            let filter = document.getElementById('searchBar').value.toLowerCase();
            let cards = document.getElementsByClassName('product-card');
            for(let c of cards) c.style.display = c.innerText.toLowerCase().includes(filter) ? "" : "none";
        }

        function finishOrder() {
            if(cart.length === 0) return alert("السلة فارغة");
            alert(`شكراً لك ${userData.name}! تم تأكيد الطلب وسنقوم بالتوصيل إلى الدار رقم: ${userData.address}`);
            cart = [];
            document.getElementById('cart-count').innerText = "0";
            showPage('categories');
        }

        initData();
    </script>
</body>
</html>
