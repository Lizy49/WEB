```html
<!DOCTYPE html>
<html lang="ru">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>TLP | SHOP</title>
 <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600&display=swap" rel="stylesheet">
 <script src="https://telegram.org/js/telegram-web-app.js"></script>
 <style>
   * { margin: 0; padding: 0; box-sizing: border-box; }
   body {
     font-family: 'Montserrat', sans-serif;
     background-color: #f5f9ff;
     color: #2c3e50;
     min-height: 100vh;
     display: flex;
     flex-direction: column;
     align-items: center;
     padding: 20px;
     animation: fadeIn 0.5s ease-in-out;
   }
   .hero { text-align: center; margin-bottom: 30px; }
   .logo { 
     font-size: 2.5rem; 
     font-weight: 600; 
     color: #3498db;
     margin-bottom: 10px;
   }
   .welcome { font-size: 1.1rem; color: #7f8c8d; font-weight: 300; }
   .container { width: 100%; max-width: 1000px; }
   .category-tabs { 
     display: flex; 
     justify-content: center; 
     flex-wrap: wrap; 
     gap: 10px; 
     margin-bottom: 20px;
   }
   .category-tabs button {
     background: #3498db; 
     color: white; 
     padding: 8px 15px; 
     border: none;
     border-radius: 20px; 
     cursor: pointer; 
     font-weight: 400; 
     transition: all 0.3s;
     font-size: 0.9rem;
   }
   .category-tabs button.active {
     background: #2980b9;
   }
   .category-tabs button:hover { background: #2980b9; }
   .products { 
     display: grid; 
     grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); 
     gap: 20px;
   }
   .product-card {
     background: white;
     border-radius: 10px; 
     padding: 15px; 
     text-align: center; 
     box-shadow: 0 5px 15px rgba(52, 152, 219, 0.1);
     transition: transform 0.3s ease;
     border: 1px solid #e0f2ff;
   }
   .product-card:hover { transform: translateY(-5px); }
   .product-card img { 
     width: 100%; 
     height: 160px; 
     object-fit: cover; 
     border-radius: 8px;
     margin-bottom: 10px;
   }
   .product-card h3 { 
     margin-top: 5px; 
     font-size: 1.1rem; 
     color: #2c3e50; 
     font-weight: 600;
   }
   .product-card p { 
     font-size: 0.85rem; 
     color: #7f8c8d; 
     margin: 8px 0;
     font-weight: 300;
   }
   .price { 
     color: #3498db; 
     font-weight: 600; 
     margin-bottom: 10px;
     font-size: 1.1rem;
   }
   .qty-controls { 
     display: flex; 
     justify-content: center; 
     align-items: center; 
     gap: 8px; 
     margin-top: 10px;
   }
   .qty-controls button {
     background: #3498db; 
     color: white;
     border: none; 
     border-radius: 50%;
     width: 28px; 
     height: 28px; 
     font-weight: 600; 
     cursor: pointer;
     transition: background 0.3s;
   }
   .qty-controls button:hover { background: #2980b9; }
   .flavor-select { 
     margin: 10px 0; 
     width: 100%; 
     padding: 8px;
     border-radius: 5px; 
     border: 1px solid #e0f2ff;
     font-size: 0.85rem;
     background: white;
   }
   .cart {
     margin-top: 30px; 
     background: white;
     padding: 20px;
     border-radius: 10px; 
     width: 100%; 
     max-width: 1000px;
     box-shadow: 0 5px 15px rgba(52, 152, 219, 0.1);
     border: 1px solid #e0f2ff;
   }
   #delivery, #address {
     width: 100%; 
     padding: 10px; 
     margin: 8px 0;
     border-radius: 5px; 
     border: 1px solid #e0f2ff;
     font-size: 0.9rem;
   }
   #delivery { background: white; }
   .delivery-info { 
     color: #3498db; 
     margin: 5px 0; 
     font-size: 0.85rem;
     font-weight: 300;
   }
   #confirmOrder {
     margin-top: 15px; 
     width: 100%; 
     padding: 12px;
     background: #3498db; 
     color: white;
     border: none; 
     font-weight: 500;
     border-radius: 5px; 
     cursor: pointer; 
     transition: all 0.3s;
     font-size: 0.95rem;
   }
   #confirmOrder:hover { 
     background: #2980b9; 
   }
   footer { 
     margin-top: 40px; 
     text-align: center; 
     color: #95a5a6; 
     font-size: 0.8rem;
     font-weight: 300;
   }
   footer a { 
     color: #3498db; 
     text-decoration: none;
   }
   @keyframes fadeIn { 
     0% { opacity: 0; transform: translateY(10px); } 
     100% { opacity: 1; transform: translateY(0); } 
   }
   #total-summary { 
     margin: 10px 0; 
     font-weight: 500;
     color: #2c3e50;
   }
   #total-summary p { margin: 5px 0; }
   .stock-info { 
     color: #3498db; 
     font-size: 0.75rem; 
     margin-top: 5px;
     font-weight: 300;
   }
   .stock-amount { color: #27ae60; font-weight: 500; }
   .out-of-stock { color: #e74c3c; }
   .flavor-item {
     margin-bottom: 10px;
     padding: 10px;
     border: 1px solid #e0f2ff;
     border-radius: 5px;
   }
   .flavor-item-header {
     display: flex;
     justify-content: space-between;
     margin-bottom: 5px;
   }
   .remove-flavor {
     color: #e74c3c;
     cursor: pointer;
   }
   .add-flavor-btn {
     background: #3498db;
     color: white;
     border: none;
     padding: 8px 12px;
     border-radius: 5px;
     cursor: pointer;
     margin-top: 5px;
     font-size: 0.85rem;
   }
   .add-flavor-btn:hover {
     background: #2980b9;
   }
   #adminPanel {
     display: none;
     margin-top: 20px;
     padding: 15px;
     background: #f8f9fa;
     border-radius: 10px;
     width: 100%;
     max-width: 1000px;
   }
   .admin-panel h2 {
     color: #2c3e50;
     margin-bottom: 15px;
   }
   .admin-controls {
     display: flex;
     flex-wrap: wrap;
     gap: 10px;
     margin-bottom: 15px;
   }
   .admin-controls select, .admin-controls input {
     padding: 8px;
     border-radius: 5px;
     border: 1px solid #ddd;
     min-width: 200px;
   }
   .admin-controls button {
     padding: 8px 15px;
     background: #27ae60;
     color: white;
     border: none;
     border-radius: 5px;
     cursor: pointer;
   }
   .admin-controls button:hover {
     background: #219653;
   }
   .logout-btn {
     background: #e74c3c !important;
     margin-top: 10px;
   }
   .logout-btn:hover {
     background: #c0392b !important;
   }
   .login-panel {
     text-align: center;
     margin-top: 20px;
   }
   #loginForm {
     display: flex;
     flex-direction: column;
     gap: 10px;
     max-width: 300px;
     margin: 0 auto;
   }
   #loginForm input {
     padding: 10px;
     border-radius: 5px;
     border: 1px solid #ddd;
   }
   #loginForm button {
     padding: 10px;
     background: #3498db;
     color: white;
     border: none;
     border-radius: 5px;
     cursor: pointer;
   }
   .remove-flavor-admin {
     background: #e74c3c;
     color: white;
     border: none;
     padding: 5px 10px;
     border-radius: 5px;
     cursor: pointer;
     margin-left: 10px;
     font-size: 0.8rem;
   }
   .remove-flavor-admin:hover {
     background: #c0392b;
   }
   .flavor-list-item {
     display: flex;
     justify-content: space-between;
     align-items: center;
     margin: 5px 0;
     padding: 5px;
     background: #f8f9fa;
     border-radius: 5px;
   }
   .refresh-btn {
     background: #3498db;
     color: white;
     border: none;
     padding: 8px 15px;
     border-radius: 5px;
     cursor: pointer;
     margin-top: 10px;
   }
 </style>
</head>
<body>
 <div class="hero">
   <h1 class="logo">TLP | SHOP</h1>
   <p class="welcome">Минимализм. Качество. Надежность.</p>
 </div>

 <div class="container">
   <div class="category-tabs">
     <button onclick="filterCategory('pod')">Поды</button>
     <button onclick="filterCategory('juice')">Жидкости</button>
     <button onclick="filterCategory('disposable')">Одноразки</button>
     <button onclick="filterCategory('vaporizer')">Испарители</button>
     <button onclick="filterCategory('accessories')">Аксессуары</button>
     <button onclick="filterCategory()" class="active">Все товары</button>
   </div>
   <div class="products" id="product-list">
     <!-- Товары будут добавлены через JavaScript -->
   </div>
 </div>

 <div class="cart" id="cart">
   <h2>🛒 Корзина</h2>
   <div id="cart-items"></div>
   <select id="delivery">
     <option value="">-- Выберите район доставки --</option>
     <option value="200">По городу(200₽)</option>
     <option value="250">Пригородный, моргородок, автотек(250₽)</option>
     <option value="300">Пионерный(300₽)</option>
     <option value="300">Солнечный(350₽)</option>
     <option value="500">Сокол, Ола (500₽)</option>
     <option value="1000">Палатка (1000₽)</option>
     <option value="0"> Самовывоз (0₽)</option>    
   </select>
   <p class="delivery-info">Доставка в течение 60 минут после подтверждения заказа</p>
   <input type="text" id="address" placeholder="Укажите точный адрес доставки" />
   <div id="total-summary"></div>
   <button id="confirmOrder" onclick="submitOrder()">Подтвердить заказ</button>
 </div>

 <!-- Панель входа -->
 <div class="login-panel" id="loginPanel">
   <h3>Вход в админ-панель</h3>
   <form id="loginForm">
     <input type="password" id="adminPassword" placeholder="Пароль" required>
     <button type="button" onclick="checkAdminAccess()">Войти</button>
   </form>
 </div>

 <!-- Админ-панель -->
 <div id="adminPanel">
   <h2>Админ-панель</h2>
   <div class="admin-controls">
     <select id="adminProductSelect">
       <option value="">Выберите товар</option>
     </select>
     <select id="adminFlavorSelect" style="display: none;">
       <option value="">Выберите вкус</option>
     </select>
     <input type="number" id="adminQty" placeholder="Количество" min="0" value="1">
     <button onclick="updateStock()">Обновить остатки</button>
     <button onclick="addNewFlavor()" id="addFlavorBtn" style="display: none;">Добавить вкус</button>
     <input type="text" id="newFlavorName" placeholder="Название вкуса" style="display: none;">
     <button onclick="removeSelectedFlavor()" id="removeFlavorBtn" style="display: none; background: #e74c3c;">Удалить вкус</button>
   </div>
   <div id="flavorsList" style="margin-top: 15px; display: none;">
     <h3>Список вкусов:</h3>
     <div id="flavorsListContainer"></div>
   </div>
   <button class="refresh-btn" onclick="forceRefresh()">Обновить данные</button>
   <button class="logout-btn" onclick="logoutAdmin()">Выйти</button>
 </div>

 <footer>
   <hr style="border-color: rgba(52, 152, 219, 0.2); margin-bottom: 15px;">
   <p>© 2025 TLP | SHOP. Все права защищены.</p>
   <p>
     <a href="https://t.me/tlpshopmgdn" target="_blank">Наш Telegram</a> |
     <a href="#">Политика конфиденциальности</a> |
     <a href="#">Контакты</a>
   </p>
 </footer>

 <script>
   // Пароль для админ-панели
   const ADMIN_PASSWORD = "tlpadmin123";
   const WEBAPP_VERSION = "2.6";
   
   // Инициализация Telegram WebApp
   const tg = window.Telegram?.WebApp;
   if (tg) {
     tg.expand();
     tg.enableClosingConfirmation();
   }

   // Данные товаров с оригинальными описаниями и количеством
   const products = [
     { 
       id: 1, 
       name: "WAKA 20000 КОПИЯ", 
       category: "disposable", 
       price: 1500, 
       image: 'dis/1.jpg', 
       description: "20 000 затяжек, компактный корпус, долгий срок службы", 
       flavors: {"Еживика черника малина": 1, "Мята": 1, "Сакура виноград": 1, "Тройная ягода": 1, "Черника малина": 1, "Клюква виноград": 1, "Энергетик черная смородина": 1, "Арбуз": 1, "Клубника киви": 1, "Капучино": 1, "Черника малина ментол": 1} 
     },
     { 
       id: 2, 
       name: "Lost Mary 16000", 
       category: "disposable", 
       price: 1700, 
       image: 'dis/2.jpg', 
       description: "16 000 затяжек, эргономичный дизайн, насыщенный вкус", 
       flavors: {"Лайм": 1, "Киви маракуйя гуава": 1, "Ледяной арбуз": 1, "Гранатовый сок": 1} 
     },
     { 
       id: 3, 
       name: "WAKA 69 мг", 
       category: "juice",
       price: 550, 
       image: 'ju/1.jpg', 
       description: "69 мг никотина, насыщенный вкус, плавное попадание", 
       flavors: {"Нет в наличии": 0} 
     },
     { 
       id: 4, 
       name: "Smoant Knight 80 kit", 
       category: "pod", 
       price: 3700, 
       image: 'pod/1.jpg', 
       description: "Профессиональный под, регулируемая мощность, долгая работа от аккумулятора", 
       flavors: {"Подик": 1} 
     },
     { 
       id: 5, 
       name: "Анаржия&зевс 70мг", 
       category: "juice", 
       price: 500, 
       image: 'ju/2.jpg', 
       description: "70 мг никотина, яркий вкус, плавное попадание", 
       flavors: {"Экзотические фрукты": 1} 
     },
     { 
       id: 6, 
       name: "Испарик К-1", 
       category: "vaporizer", 
       price: 350, 
       image: 'vap/1.jpg', 
       description: "Профессиональный испаритель, долгий срок службы, качественные материалы", 
       flavors: {"Испарик": 1} 
     },
     { 
       id: 7, 
       name: "Картридж на xros 0.6/0.8 ом", 
       category: "vaporizer", 
       price: 450, 
       image: 'vap/2.jpg', 
       description: "Картридж для испарителя, совместимость с xros, долгий срок службы", 
       flavors: {"0.6": 1, "0.8": 1} 
     },
     { 
       id: 8, 
       name: "АКБ банан", 
       category: "accessories", 
       price: 600, 
       image: 'acc/1.jpg', 
       description: "Аккумулятор, долгая работа, быстрая зарядка", 
       flavors: {"АКБ": 1} 
     },
     { 
       id: 9, 
       name: "Rick and Morty Bad Trip 70мг", 
       category: "juice", 
       price: 550, 
       image: 'ju/3.jpg', 
       description: "70 мг никотина, уникальный вкус, плавное попадание", 
       flavors: {"Черная вишня": 1, "Киви гуава маракуйя": 1, "Персик бабл гам": 1, "Банан кокос": 1, "Манго грейпфрут": 1, "Земляничный мохито": 1, "Северные ягоды": 1, "Грейпфрутовый швепс": 1, "Гранат смородина": 1, "Фруктовые пластинки": 1} 
     },
     {
       id: 10,
       name: "Podonki Vintage 70мг",
       category: "juice",
       price: 550,
       image: 'ju/4.jpg',
       description: "70 мг никотина, классические вкусы, насыщенный аромат",
       flavors: {"Апельсиновая газировка": 1, "Брусничный морс": 1, "Ежевичный лимонад": 1, "Пина колада с грушей": 1, "Освежающий лимонад": 1, "Малиновый пунш": 1, "Морс черника виноград": 1, "Яблочный лимонад": 1}
     }
   ];

   let currentFilter = null;

   // Функция рендеринга товаров
   function renderProducts(filter = null) {
     currentFilter = filter;
     const list = document.getElementById('product-list');
     list.innerHTML = '';
     const filtered = filter ? products.filter(p => p.category === filter) : products;
     
     if (filtered.length === 0) {
       list.innerHTML = '<p style="grid-column: 1/-1; text-align: center;">Товары отсутствуют</p>';
       return;
     }
     
     for (const product of filtered) {
       const card = document.createElement('div');
       card.className = 'product-card';
       const flavorOptions = product.flavors ? Object.entries(product.flavors).map(
         ([flavor, stock]) => `<option value="${flavor}" ${stock === 0 ? 'disabled' : ''}>
                                 ${flavor}${stock === 0 ? ' (нет в наличии)' : ''} 
                               </option>`
       ).join('') : '';
       
       const stockInfo = product.flavors ? 
         Object.entries(product.flavors).map(([flavor, stock]) => 
           `<div>${flavor}: <span class="${stock === 0 ? 'out-of-stock' : 'stock-amount'}">${stock} шт.</span></div>`
         ).join('') : '';
       
       card.innerHTML = `
         <img src="${product.image}" alt="${product.name}" />
         <h3>${product.name}</h3>
         <p>${product.description}</p>
         <p class="price">${product.price} ₽</p>
         ${product.flavors && Object.keys(product.flavors).length > 0 ? `
           <select class="flavor-select" id="flavor-${product.id}">
             <option value="">-- Выберите вкус --</option>
             ${flavorOptions}
           </select>
           <div class="stock-info" id="stock-${product.id}">
             ${stockInfo}
           </div>
           <button class="add-flavor-btn" onclick="addFlavorToCart(${product.id})">Добавить вкус</button>
           <div id="selected-flavors-${product.id}"></div>
         ` : `
           <div class="stock-info">В наличии: <span class="stock-amount">${product.stock || 10} шт.</span></div>
           <div class="qty-controls">
             <button onclick="decreaseQty(${product.id})">−</button>
             <span id="qty-${product.id}">0</span>
             <button onclick="increaseQty(${product.id})">+</button>
           </div>
         `}
       `;
       list.appendChild(card);
     }
   }

   // Функция добавления вкуса в корзину
   function addFlavorToCart(productId) {
     const flavorSelect = document.getElementById(`flavor-${productId}`);
     const selectedFlavor = flavorSelect.value;
     
     if (!selectedFlavor) {
       alert("Сначала выберите вкус");
       return;
     }
     
     const product = products.find(p => p.id === productId);
     const container = document.getElementById(`selected-flavors-${productId}`);
     
     const existingFlavor = document.getElementById(`flavor-item-${productId}-${selectedFlavor}`);
     
     if (existingFlavor) {
       const qtySpan = existingFlavor.querySelector('.flavor-qty');
       const currentQty = parseInt(qtySpan.textContent);
       const maxQty = product.flavors[selectedFlavor];
       
       if (currentQty < maxQty) {
         qtySpan.textContent = currentQty + 1;
       } else {
         alert("Нет в наличии");
       }
     } else {
       const flavorItem = document.createElement('div');
       flavorItem.className = 'flavor-item';
       flavorItem.id = `flavor-item-${productId}-${selectedFlavor}`;
       flavorItem.innerHTML = `
         <div class="flavor-item-header">
           <span>${selectedFlavor}</span>
           <span class="remove-flavor" onclick="removeFlavor(${productId}, '${selectedFlavor}')">×</span>
         </div>
         <div class="qty-controls">
           <button onclick="decreaseFlavorQty(${productId}, '${selectedFlavor}')">−</button>
           <span class="flavor-qty">1</span>
           <button onclick="increaseFlavorQty(${productId}, '${selectedFlavor}')">+</button>
         </div>
       `;
       container.appendChild(flavorItem);
     }
     
     updateCartDisplay();
   }

   // Функция удаления вкуса из корзины
   function removeFlavor(productId, flavor) {
     const item = document.getElementById(`flavor-item-${productId}-${flavor}`);
     if (item) {
       item.remove();
     }
     updateCartDisplay();
   }

   // Функция увеличения количества вкуса
   function increaseFlavorQty(productId, flavor) {
     const item = document.getElementById(`flavor-item-${productId}-${flavor}`);
     if (item) {
       const qtySpan = item.querySelector('.flavor-qty');
       const currentQty = parseInt(qtySpan.textContent);
       const product = products.find(p => p.id === productId);
       const maxQty = product.flavors[flavor];
       
       if (currentQty < maxQty) {
         qtySpan.textContent = currentQty + 1;
       } else {
         alert("Нет в наличии");
       }
     }
     updateCartDisplay();
   }

   // Функция уменьшения количества вкуса
   function decreaseFlavorQty(productId, flavor) {
     const item = document.getElementById(`flavor-item-${productId}-${flavor}`);
     if (item) {
       const qtySpan = item.querySelector('.flavor-qty');
       const currentQty = parseInt(qtySpan.textContent);
       
       if (currentQty > 1) {
         qtySpan.textContent = currentQty - 1;
       } else {
         item.remove();
       }
     }
     updateCartDisplay();
   }

   // Функция фильтрации по категориям
   function filterCategory(cat) {
     document.querySelectorAll('.category-tabs button').forEach(btn => {
       btn.classList.remove('active');
     });
     event.target.classList.add('active');
     renderProducts(cat);
   }

   // Функция увеличения количества товара
   function increaseQty(id) {
     const qtySpan = document.getElementById(`qty-${id}`);
     let currentQty = parseInt(qtySpan.innerText);
     const product = products.find(p => p.id === id);
     const maxQty = product.stock || 10;

     if (currentQty < maxQty) {
       currentQty++;
       qtySpan.innerText = currentQty;
     } else {
       alert("Нет в наличии");
     }
     updateCartDisplay();
   }

   // Функция уменьшения количества товара
   function decreaseQty(id) {
     const qtySpan = document.getElementById(`qty-${id}`);
     let currentQty = parseInt(qtySpan.innerText);
     if (currentQty > 0) {
       currentQty--;
       qtySpan.innerText = currentQty;
     }
     updateCartDisplay();
   }

   // Функция обновления отображения корзины
   function updateCartDisplay() {
     const cartItems = document.getElementById("cart-items");
     cartItems.innerHTML = '';
     let subtotal = 0;

     // Обрабатываем товары без вкусов
     for (const product of products) {
       if (!product.flavors || Object.keys(product.flavors).length === 0) {
         const qty = parseInt(document.getElementById(`qty-${product.id}`)?.innerText || 0);
         if (qty > 0) {
           const cost = product.price * qty;
           const p = document.createElement('p');
           p.textContent = `${product.name} x${qty} — ${cost}₽`;
           cartItems.appendChild(p);
           subtotal += cost;
         }
       }
     }

     // Обрабатываем товары с вкусами
     for (const product of products) {
       if (product.flavors && Object.keys(product.flavors).length > 0) {
         const container = document.getElementById(`selected-flavors-${product.id}`);
         if (container) {
           const flavorItems = container.querySelectorAll('.flavor-item');
           flavorItems.forEach(item => {
             const flavorName = item.querySelector('.flavor-item-header span:first-child').textContent;
             const qty = parseInt(item.querySelector('.flavor-qty').textContent);
             const cost = product.price * qty;
             const p = document.createElement('p');
             p.textContent = `${product.name} (${flavorName}) x${qty} — ${cost}₽`;
             cartItems.appendChild(p);
             subtotal += cost;
           });
         }
       }
     }

     const deliverySelect = document.getElementById("delivery");
     const deliveryPrice = deliverySelect.value ? parseInt(deliverySelect.value) : 0;
     const deliveryName = deliverySelect.selectedOptions[0]?.text || "";

     document.getElementById("total-summary").innerHTML = `
       <p>Товары: ${subtotal}₽</p>
       ${deliveryName ? `<p>Доставка: ${deliveryName}</p>` : ''}
       <p>Итого: ${subtotal + deliveryPrice}₽</p>
     `;
   }

   // Функция отправки заказа
   function submitOrder() {
     const deliverySelect = document.getElementById("delivery");
     const district = deliverySelect.selectedOptions[0]?.text;
     const deliveryPrice = parseInt(deliverySelect.value);
     let address = '';

     if (deliveryPrice !== 0) {
       address = document.getElementById('address').value.trim();
       if (!address) {
         alert("Укажите адрес доставки");
         return;
       }
     } else {
       address = "Самовывоз";
     }

     if (!deliverySelect.value) {
       alert("Выберите район доставки");
       return;
     }

     const cartItems = [];

     // Собираем товары без вкусов
     for (const product of products) {
       if (!product.flavors || Object.keys(product.flavors).length === 0) {
         const qty = parseInt(document.getElementById(`qty-${product.id}`)?.innerText || 0);
         if (qty > 0) {
           cartItems.push({
             id: product.id,
             name: product.name,
             qty: qty,
             flavor: 'Стандарт',
             price: product.price,
             description: product.description
           });
         }
       }
     }

     // Собираем товары с вкусами
     for (const product of products) {
       if (product.flavors && Object.keys(product.flavors).length > 0) {
         const container = document.getElementById(`selected-flavors-${product.id}`);
         if (container) {
           const flavorItems = container.querySelectorAll('.flavor-item');
           flavorItems.forEach(item => {
             const flavorName = item.querySelector('.flavor-item-header span:first-child').textContent;
             const qty = parseInt(item.querySelector('.flavor-qty').textContent);
             
             cartItems.push({
               id: product.id,
               name: product.name,
               qty: qty,
               flavor: flavorName,
               price: product.price,
               description: product.description
             });
           });
         }
       }
     }

     if (cartItems.length === 0) {
       alert("Корзина пуста");
       return;
     }

     const subtotal = cartItems.reduce((sum, item) => sum + item.price * item.qty, 0);
     const total = subtotal + deliveryPrice;

     // Формируем данные заказа
     const orderData = {
       type: "new_order",
       items: cartItems,
       address: address,
       district: district,
       deliveryPrice: deliveryPrice,
       subtotal: subtotal,
       total: total,
       phone: tg?.initDataUnsafe?.user?.phone_number || "не указан",
       webapp_version: WEBAPP_VERSION
     };

     console.log("Отправляемые данные:", orderData);

     // Отправка данных в Telegram бот
     if (window.Telegram && window.Telegram.WebApp) {
       try {
         tg.sendData(JSON.stringify(orderData));
         
         // Закрываем WebApp с небольшой задержкой
         setTimeout(() => {
           tg.close();
         }, 300);
       } catch (e) {
         console.error("Ошибка отправки данных в Telegram:", e);
         alert("Ошибка отправки заказа. Пожалуйста, попробуйте еще раз или свяжитесь с менеджером.");
       }
     } else {
       console.log("Данные заказа (тестовый режим):", orderData);
       alert("Заказ оформлен! Менеджер свяжется с вами.");
     }
   }

   // Функции для админ-панели
   function checkAdminAccess() {
     const password = document.getElementById('adminPassword').value;
     if (password === ADMIN_PASSWORD) {
       localStorage.setItem('adminAccess', 'true');
       document.getElementById('loginPanel').style.display = 'none';
       document.getElementById('adminPanel').style.display = 'block';
       initAdminPanel();
     } else {
       alert("Неверный пароль!");
     }
   }

   function logoutAdmin() {
     localStorage.removeItem('adminAccess');
     location.reload();
   }

   function forceRefresh() {
     localStorage.removeItem('tlpShopStock');
     location.reload();
   }

   function initAdminPanel() {
     const productSelect = document.getElementById('adminProductSelect');
     productSelect.innerHTML = '<option value="">Выберите товар</option>';
     
     products.forEach(product => {
       const option = document.createElement('option');
       option.value = product.id;
       option.textContent = product.name;
       productSelect.appendChild(option);
     });

     productSelect.addEventListener('change', function() {
       const productId = this.value;
       const flavorSelect = document.getElementById('adminFlavorSelect');
       const addFlavorBtn = document.getElementById('addFlavorBtn');
       const removeFlavorBtn = document.getElementById('removeFlavorBtn');
       const newFlavorName = document.getElementById('newFlavorName');
       const flavorsList = document.getElementById('flavorsList');
       
       flavorSelect.innerHTML = '<option value="">Выберите вкус</option>';
       
       if (productId) {
         const product = products.find(p => p.id == productId);
         if (product.flavors && Object.keys(product.flavors).length > 0) {
           flavorSelect.style.display = 'block';
           addFlavorBtn.style.display = 'block';
           removeFlavorBtn.style.display = 'block';
           newFlavorName.style.display = 'block';
           flavorsList.style.display = 'block';
           
           updateFlavorsList(productId);
           
           Object.keys(product.flavors).forEach(flavor => {
             const option = document.createElement('option');
             option.value = flavor;
             option.textContent = `${flavor} (${product.flavors[flavor]} шт.)`;
             flavorSelect.appendChild(option);
           });
         } else {
           flavorSelect.style.display = 'none';
           addFlavorBtn.style.display = 'none';
           removeFlavorBtn.style.display = 'none';
           newFlavorName.style.display = 'none';
           flavorsList.style.display = 'none';
         }
       } else {
         flavorSelect.style.display = 'none';
         addFlavorBtn.style.display = 'none';
         removeFlavorBtn.style.display = 'none';
         newFlavorName.style.display = 'none';
         flavorsList.style.display = 'none';
       }
     });
   }

   function updateFlavorsList(productId) {
     const container = document.getElementById('flavorsListContainer');
     container.innerHTML = '';
     
     const product = products.find(p => p.id == productId);
     if (!product || !product.flavors) return;
     
     Object.entries(product.flavors).forEach(([flavor, qty]) => {
       const item = document.createElement('div');
       item.className = 'flavor-list-item';
       item.innerHTML = `
         <span>${flavor}: ${qty} шт.</span>
         <button class="remove-flavor-admin" onclick="adminRemoveFlavor(${productId}, '${flavor}')">Удалить</button>
       `;
       container.appendChild(item);
     });
   }

   function addNewFlavor() {
     const productId = document.getElementById('adminProductSelect').value;
     const flavorName = document.getElementById('newFlavorName').value.trim();
     
     if (!productId) {
       alert("Выберите товар");
       return;
     }
     
     if (!flavorName) {
       alert("Введите название вкуса");
       return;
     }
     
     const product = products.find(p => p.id == productId);
     
     if (!product.flavors) {
       product.flavors = {};
     }
     
     if (product.flavors[flavorName] !== undefined) {
       alert("Этот вкус уже существует");
       return;
     }
     
     product.flavors[flavorName] = 5; // Устанавливаем стандартное количество
     updateFlavorsList(productId);
     document.getElementById('newFlavorName').value = '';
     alert(`Вкус "${flavorName}" добавлен!`);
   }

   function removeSelectedFlavor() {
     const productId = document.getElementById('adminProductSelect').value;
     const flavor = document.getElementById('adminFlavorSelect').value;
     
     if (!productId || !flavor) {
       alert("Выберите товар и вкус");
       return;
     }
     
     adminRemoveFlavor(productId, flavor);
   }

   function adminRemoveFlavor(productId, flavor) {
     if (!confirm(`Удалить вкус "${flavor}"? Это действие нельзя отменить!`)) {
       return;
     }
     
     const product = products.find(p => p.id == productId);
     
     if (product && product.flavors && product.flavors[flavor] !== undefined) {
       delete product.flavors[flavor];
       
       updateFlavorsList(productId);
       
       const flavorSelect = document.getElementById('adminFlavorSelect');
       flavorSelect.innerHTML = '<option value="">Выберите вкус</option>';
       Object.keys(product.flavors).forEach(f => {
         const option = document.createElement('option');
         option.value = f;
         option.textContent = `${f} (${product.flavors[f]} шт.)`;
         flavorSelect.appendChild(option);
       });
       
       alert(`Вкус "${flavor}" удален!`);
     }
   }

   function updateStock() {
     const productId = document.getElementById('adminProductSelect').value;
     const flavorSelect = document.getElementById('adminFlavorSelect');
     const flavor = flavorSelect.style.display === 'none' ? null : flavorSelect.value;
     const qty = parseInt(document.getElementById('adminQty').value);

     if (!productId) {
       alert("Выберите товар");
       return;
     }

     if (flavorSelect.style.display !== 'none' && !flavor) {
       alert("Выберите вкус");
       return;
     }

     const product = products.find(p => p.id == productId);
     
     if (flavor) {
       product.flavors[flavor] = qty;
     } else {
       product.stock = qty;
     }

     alert("Остатки обновлены!");
     updateFlavorsList(productId);
   }

   // Инициализация при загрузке
   document.addEventListener('DOMContentLoaded', () => {
     // Проверяем доступ к админ-панели
     if (localStorage.getItem('adminAccess') === 'true') {
       document.getElementById('loginPanel').style.display = 'none';
       document.getElementById('adminPanel').style.display = 'block';
       initAdminPanel();
     } else {
       document.getElementById('adminPanel').style.display = 'none';
     }
     
     renderProducts();
     
     document.getElementById("delivery").addEventListener("change", function() {
       updateCartDisplay();
       const addressField = document.getElementById("address");
       if (this.value === "0") {
         addressField.style.display = "none";
       } else {
         addressField.style.display = "block";
       }
     });
   });
 </script>
</body>
</html>
```
