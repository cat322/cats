<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>متجري الشامل</title>
    <style>
        :root { --primary: #2c3e50; --accent: #3498db; --white: #ffffff; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f4f4f4; margin: 0; }
        .container { max-width: 800px; margin: 20px auto; padding: 20px; }
        .hidden { display: none; }
        
        /* تصميم الصفحات */
        .card { background: white; padding: 30px; border-radius: 10px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); text-align: center; }
        input, select { width: 100%; padding: 12px; margin: 10px 0; border: 1px solid #ddd; border-radius: 5px; box-sizing: border-box; }
        button { background: var(--accent); color: white; border: none; padding: 12px 25px; border-radius: 5px; cursor: pointer; transition: 0.3s; }
        button:hover { background: #2980b9; }

        /* الأقسام والمنتجات */
        .grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 20px; margin-top: 20px; }
        .product-item { background: white; padding: 15px; border-radius: 8px; border: 1px solid #eee; text-align: center; }
        .product-item img { max-width: 100px; height: auto; margin-bottom: 10px; }
        
        /* السلة */
        .cart-status { background: #e74c3c; color: white; padding: 5px 10px; border-radius: 50%; font-size: 12px; }
        nav { background: var(--primary); color: white; padding: 15px; display: flex; justify-content: space-between; align-items: center; }
    </style>
</head>
<body>

    <nav id="navbar" class="hidden">
        <span>متجري الشامل</span>
        <div>
            <span onclick="showPage('categories')" style="cursor:pointer">الأقسام</span> | 
            <span onclick="showPage('cart-page')" style="cursor:pointer">السلة (<span id="cart-count">0</span>)</span>
        </div>
    </nav>

    <div class="container">
        
        <div id="login-page" class="card">
            <h2>تسجيل الدخول للمتجر</h2>
            <input type="text" id="username" placeholder="اسم المستخدم">
            <input type="password" placeholder="كلمة المرور">
            <button onclick="login()">دخول</button>
        </div>

        <div id="categories-page" class="card hidden">
            <h3>مرحباً <span id="user-name-display"></span>، اختر القسم:</h3>
            <div class="grid">
                <button onclick="loadProducts('إلكترونيات')">إلكترونيات</button>
                <button onclick="loadProducts('ملابس')">ملابس</button>
                <button onclick="loadProducts('منزل')">أدوات منزلية</button>
                <button onclick="loadProducts('ألعاب')">ألعاب</button>
            </div>
        </div>

        <div id="products-page" class="hidden">
            <div style="display: flex; gap: 10px;">
                <button onclick="showPage('categories')">العودة للأقسام</button>
                <input type="text" id="searchBar" placeholder="ابحث عن منتج في هذا القسم..." onkeyup="searchProducts()">
            </div>
            <h2 id="category-title"></h2>
            <div id="products-list" class="grid"></div>
        </div>

        <div id="cart-page" class="card hidden">
            <h2>سلة المشتريات</h2>
            <div id="cart-items"></div>
            <hr>
            <h3>الإجمالي: <span id="total-price">0</span>$</h3>
            <button onclick="alert('شكراً لشرائك!')">إتمام الشراء</button>
        </div>

    </div>

    <script>
        let currentUser = "";
        let cart = [];
        const data = {
            'إلكترونيات': [{id:1, name: 'هاتف ذكي', price: 500}, {id:2, name: 'لابتوب', price: 1200}],
            'ملابس': [{id:3, name: 'قميص', price: 25}, {id:4, name: 'حذاء رياضي', price: 60}],
            'منزل': [{id:5, name: 'خلاط', price: 40}, {id:6, name: 'مصباح', price: 15}],
            'ألعاب': [{id:7, name: 'بلايستيشن', price: 450}, {id:8, name: 'كرة قدم', price: 20}]
        };

        function showPage(pageId) {
            ['login-page', 'categories-page', 'products-page', 'cart-page'].forEach(id => {
                document.getElementById(id).classList.add('hidden');
            });
            document.getElementById(pageId + (pageId.includes('-page') ? '' : '-page')).classList.remove('hidden');
        }

        function login() {
            currentUser = document.getElementById('username').value;
            if(currentUser) {
                document.getElementById('user-name-display').innerText = currentUser;
                document.getElementById('navbar').classList.remove('hidden');
                showPage('categories');
            } else { alert("يرجى إدخال الاسم"); }
        }

        function loadProducts(cat) {
            const list = document.getElementById('products-list');
            document.getElementById('category-title').innerText = "قسم " + cat;
            list.innerHTML = "";
            data[cat].forEach(prod => {
                list.innerHTML += `
                    <div class="product-item">
                        <h4>${prod.name}</h4>
                        <p>${prod.price}$</p>
                        <button onclick="addToCart('${prod.name}', ${prod.price})">إضافة للسلة</button>
                    </div>`;
            });
            showPage('products');
        }

        function addToCart(name, price) {
            cart.push({name, price});
            updateCart();
            alert(name + " أضيف للسلة");
        }

        function updateCart() {
            document.getElementById('cart-count').innerText = cart.length;
            const cartList = document.getElementById('cart-items');
            const totalDisplay = document.getElementById('total-price');
            cartList.innerHTML = "";
            let total = 0;
            cart.forEach(item => {
                cartList.innerHTML += `<p>${item.name} - ${item.price}$</p>`;
                total += item.price;
            });
            totalDisplay.innerText = total;
        }

        function searchProducts() {
            let input = document.getElementById('searchBar').value.toLowerCase();
            let items = document.getElementsByClassName('product-item');
            for (let i = 0; i < items.length; i++) {
                if (!items[i].innerHTML.toLowerCase().includes(input)) {
                    items[i].style.display = "none";
                } else {
                    items[i].style.display = "block";
                }
            }
        }
    </script>
</body>
</html>
