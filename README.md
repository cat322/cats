let currentUser = "";
        let cart = [];

        // الأقسام الجديدة
        const categoriesList = ['إلكترونيات', 'ملابس', 'منزل', 'ألعاب', 'سيارات', 'حيوانات'];
        
        // توليد بيانات تلقائية (50 منتج لكل قسم)
        const data = {};
        categoriesList.forEach(cat => {
            data[cat] = [];
            for (let i = 1; i <= 50; i++) {
                // استخدام روابط صور عشوائية من Unsplash بناءً على اسم القسم
                let searchKeyword = (cat === 'سيارات') ? 'car' : (cat === 'حيوانات' ? 'animal' : 'product');
                data[cat].push({
                    id: Math.random(),
                    name: `${cat} منتج رقم ${i}`,
                    price: Math.floor(Math.random() * 1000) + 10,
                    image: `https://loremflickr.com/320/240/${searchKeyword}?lock=${i}`
                });
            }
        });

        function showPage(pageId) {
            document.querySelectorAll('.container > div, nav').forEach(el => {
                if(el.id !== 'navbar') el.classList.add('hidden');
            });
            document.getElementById(pageId + (pageId.includes('page') ? '' : '-page')).classList.remove('hidden');
        }

        function login() {
            currentUser = document.getElementById('username').value;
            if(currentUser) {
                document.getElementById('user-name-display').innerText = currentUser;
                document.getElementById('navbar').classList.remove('hidden');
                renderCategories();
                showPage('categories');
            } else { alert("يرجى إدخال الاسم"); }
        }

        // تحديث عرض الأقسام ديناميكياً
        function renderCategories() {
            const catGrid = document.querySelector('#categories-page .grid');
            catGrid.innerHTML = "";
            categoriesList.forEach(cat => {
                catGrid.innerHTML += `<button onclick="loadProducts('${cat}')">${cat}</button>`;
            });
        }

        function loadProducts(cat) {
            const list = document.getElementById('products-list');
            document.getElementById('category-title').innerText = "قسم " + cat;
            list.innerHTML = "";
            data[cat].forEach(prod => {
                list.innerHTML += `
                    <div class="product-item">
                        <img src="${prod.image}" alt="${prod.name}" style="width:100%; border-radius:5px;">
                        <h4>${prod.name}</h4>
                        <p style="color: green; font-weight: bold;">${prod.price}$</p>
                        <button onclick="addToCart('${prod.name}', ${prod.price})">إضافة للسلة</button>
                    </div>`;
            });
            showPage('products');
        }

        // ... بقية وظائف السلة والبحث (نفس الكود السابق) ...
