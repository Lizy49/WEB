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
   const WEBAPP_VERSION = "2.5";
   
   // Инициализация Telegram WebApp
   const tg = window.Telegram?.WebApp;
   if (tg) {
     tg.expand();
     tg.enableClosingConfirmation();
     
     // Отправляем версию при открытии
     tg.sendData(JSON.stringify({
       type: "webapp_init",
       version: WEBAPP_VERSION
     }));
   }

   // Проверяем версию и очищаем кэш при необходимости
   if (localStorage.getItem('webappVersion') !== WEBAPP_VERSION) {
     localStorage.clear();
     localStorage.setItem('webappVersion', WEBAPP_VERSION);
     if (tg) {
       tg.showAlert("Данные магазина обновлены. Пожалуйста, перезагрузите страницу.");
     }
   }

   // Загрузка остатков из localStorage
   function loadStock() {
     const savedStock = localStorage.getItem('tlpShopStock');
     return savedStock ? JSON.parse(savedStock) : {
       "1": {"Еживика черника малина": 5, "Мята": 5, "Сакура виноград": 5},
       "2": {"Лайм": 5, "Киви маракуйя гуава": 5},
       "3": {},
       "4": {"Подик": 5},
       "5": {"Экзотические фрукты": 5},
       "6": {"Испарик": 5},
       "7": {"0.6": 5, "0.8": 5},
       "8": {"АКБ": 5},
       "9": {"Черная вишня": 5, "Киви гуава маракуйя": 5},
       "10": {"Апельсиновая газировка": 5, "Брусничный морс": 5}
     };
   }

   // Сохранение остатков в localStorage
   function saveStock(stock) {
     localStorage.setItem('tlpShopStock', JSON.stringify(stock));
     updateProductsFromStock();
     document.dispatchEvent(new Event('stockUpdated'));
   }

   let serverStock = loadStock();

   const products = [
     { 
       id: 1, 
       name: "WAKA 20000 КОПИЯ", 
       category: "disposable", 
       price: 1500, 
       image: 'dis/1.jpg', 
       description: "20 000 затяжек", 
       flavors: serverStock["1"] 
     },
     { 
       id: 2, 
       name: "Lost Mary 16000", 
       category: "disposable", 
       price: 1700, 
       image: 'dis/2.jpg', 
       description: "16 000 затяжек", 
       flavors: serverStock["2"] 
     },
     { 
       id: 3, 
       name: "WAKA 69 мг", 
       price: 550, 
       image: 'ju/1.jpg', 
       description: "69 мг никотина", 
       flavors: serverStock["3"] 
     },
     { 
       id: 4, 
       name: "Smoant Knight 80 kit", 
       category: "pod", 
       price: 3700, 
       image: 'pod/1.jpg', 
       description: "Профессиональный под", 
       flavors: serverStock["4"] 
     },
     { 
       id: 5, 
       name: "Анаржия&зевс 70мг", 
       category: "juice", 
       price: 500, 
       image: 'ju/2.jpg', 
       description: "70 мг никотина", 
       flavors: serverStock["5"] 
     },
     { 
       id: 6, 
       name: "Испарик К-1", 
       category: "vaporizer", 
       price: 350, 
       image: 'vap/1.jpg', 
       description: "Профессиональный испаритель", 
       flavors: serverStock["6"] 
     },
     { 
       id: 7, 
       name: "Картридж на xros 0.6/0.8 ом", 
       category: "vaporizer", 
       price: 450, 
       image: 'vap/2.jpg', 
       description: "Картридж для испарителя", 
       flavors: serverStock["7"] 
     },
     { 
       id: 8, 
       name: "АКБ банан", 
       category: "accessories", 
       price: 600, 
       image: 'acc/1.jpg', 
       description: "Аккумулятор", 
       flavors: serverStock["8"] 
     },
     { 
       id: 9, 
       name: "Rick and Morty Bad Trip 70мг", 
       category: "juice", 
       price: 550, 
       image: 'ju/3.jpg', 
       description: "70 мг никотина", 
       flavors: serverStock["9"] 
     },
     {
      id: 10,
      name: "Podonki Vintage 70мг",
      category: "juice",
      price: 550,
      image: 'ju/4.jpg',
      description: "70 мг никотина",
      flavors: serverStock["10"]
     }
   ];

   let cart = [];
   let currentFilter = null;

   // Обновление данных products из serverStock
   function updateProductsFromStock() {
     for (const product of products) {
       if (product.flavors) {
         product.flavors = serverStock[product.id];
       } else if (serverStock[product.id] !== undefined && typeof serverStock[product.id] === 'number') {
         product.stock = serverStock[product.id];
       }
     }
   }

   // Проверка доступа к админ-панели
   function checkAdminAccess() {
     const password = document.getElementById('adminPassword').value;
     if (password === ADMIN_PASSWORD) {
       localStorage.setItem('adminAccess', 'true');
       document.getElementById('loginPanel').style.display = 'none';
       document.getElementById('adminPanel').style.display = 'block';
     } else {
       alert("Неверный пароль!");
     }
   }

   // Выход из админ-панели
   function logoutAdmin() {
     localStorage.removeItem('adminAccess');
     location.reload();
   }

   // Принудительное обновление данных
   function forceRefresh() {
     localStorage.removeItem('tlpShopStock');
     localStorage.setItem('forceRefresh', 'true');
     location.reload();
   }

   // Инициализация админ-панели
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
         if (product.flavors) {
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

   // Обновление списка вкусов для админа
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

   // Добавление нового вкуса
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
     
     if (product.flavors[flavorName] !== undefined) {
       alert("Этот вкус уже существует");
       return;
     }
     
     product.flavors[flavorName] = 0;
     serverStock[productId][flavorName] = 0;
     
     saveStock(serverStock);
     document.getElementById('newFlavorName').value = '';
     alert(`Вкус "${flavorName}" добавлен! Установите количество и нажмите "Обновить остатки"`);
   }

   // Удаление выбранного вкуса
   function removeSelectedFlavor() {
     const productId = document.getElementById('adminProductSelect').value;
     const flavor = document.getElementById('adminFlavorSelect').value;
     
     if (!productId || !flavor) {
       alert("Выберите товар и вкус");
       return;
     }
     
     adminRemoveFlavor(productId, flavor);
   }

   // Удаление вкуса (админ)
   function adminRemoveFlavor(productId, flavor) {
     if (!confirm(`Удалить вкус "${flavor}"? Это действие нельзя отменить!`)) {
       return;
     }
     
     const product = products.find(p => p.id == productId);
     
     if (product && product.flavors && product.flavors[flavor] !== undefined) {
       delete product.flavors[flavor];
       delete serverStock[productId][flavor];
       
       saveStock(serverStock);
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

   // Обновление остатков через админ-панель
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
       serverStock[productId][flavor] = qty;
     } else {
       product.stock = qty;
       serverStock[productId] = qty;
     }

     saveStock(serverStock);
     alert("Остатки обновлены!");
   }

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
         ${product.flavors ? `
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

   function removeFlavor(productId, flavor) {
     const item = document.getElementById(`flavor-item-${productId}-${flavor}`);
     if (item) {
       item.remove();
     }
     updateCartDisplay();
   }

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

   function filterCategory(cat) {
     document.querySelectorAll('.category-tabs button').forEach(btn => {
       btn.classList.remove('active');
     });
     event.target.classList.add('active');
     renderProducts(cat);
   }

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

   function decreaseQty(id) {
     const qtySpan = document.getElementById(`qty-${id}`);
     let currentQty = parseInt(qtySpan.innerText);
     if (currentQty > 0) {
       currentQty--;
       qtySpan.innerText = currentQty;
     }
     updateCartDisplay();
   }

   function updateCartDisplay() {
     const cartItems = document.getElementById("cart-items");
     cartItems.innerHTML = '';
     let subtotal = 0;

     // Обрабатываем товары без вкусов
     for (const product of products) {
       if (!product.flavors) {
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
       if (product.flavors) {
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

   function validateOrderData(orderData) {
     if (!orderData.type || orderData.type !== "new_order") {
       console.error("Неверный тип заказа");
       return false;
     }
     
     if (!Array.isArray(orderData.items) || orderData.items.length === 0) {
       console.error("Нет товаров в заказе");
       return false;
     }
     
     if (!orderData.address || !orderData.district) {
       console.error("Не указан адрес или район");
       return false;
     }
     
     if (isNaN(orderData.total) || orderData.total <= 0) {
       console.error("Неверная сумма заказа");
       return false;
     }
     
     return true;
   }

   function updateStockAfterOrder(cartItems) {
     for (const item of cartItems) {
       const product = products.find(p => p.id === item.id);
       if (!product) continue;
       
       if (product.flavors && item.flavor !== 'Стандарт') {
         // Обновляем остатки для товаров с вкусами
         if (product.flavors[item.flavor] !== undefined) {
           product.flavors[item.flavor] -= item.qty;
           if (product.flavors[item.flavor] < 0) product.flavors[item.flavor] = 0;
           serverStock[product.id][item.flavor] = product.flavors[item.flavor];
         }
       } else if (product.stock !== undefined) {
         // Обновляем остатки для товаров без вкусов
         product.stock -= item.qty;
         if (product.stock < 0) product.stock = 0;
         serverStock[product.id] = product.stock;
       }
     }
     
     saveStock(serverStock);
   }

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

     // Добавляем товары без вкусов
     for (const product of products) {
       if (!product.flavors) {
         const qty = parseInt(document.getElementById(`qty-${product.id}`)?.innerText || 0);
         if (qty > 0) {
           cartItems.push({
             id: product.id,
             name: product.name,
             qty: qty,
             flavor: 'Стандарт',
             price: product.price
           });
         }
       }
     }

     // Добавляем товары с вкусами
     for (const product of products) {
       if (product.flavors) {
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
               price: product.price
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

     // Формируем данные заказа с проверкой всех полей
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

     // Проверяем данные перед отправкой
     if (!validateOrderData(orderData)) {
       alert("Ошибка в данных заказа. Пожалуйста, попробуйте еще раз.");
       return;
     }

     // Отправка данных в Telegram бот
     if (window.Telegram && window.Telegram.WebApp) {
       try {
         tg.sendData(JSON.stringify(orderData));
         
         // Обновляем остатки только после успешной отправки
         updateStockAfterOrder(cartItems);
         
         // Закрываем WebApp с небольшой задержкой
         setTimeout(() => {
           tg.close();
         }, 300);
       } catch (e) {
         console.error("Ошибка отправки данных в Telegram:", e);
         alert("Заказ оформлен! Менеджер свяжется с вами.");
       }
     } else {
       console.log("Данные заказа (тестовый режим):", orderData);
       alert("Заказ оформлен! Менеджер свяжется с вами.");
     }

     // Обновляем интерфейс после заказа
     renderProducts(currentFilter);
     updateCartDisplay();
   }

   // Обновление интерфейса при изменении остатков
   function handleStockUpdate() {
     renderProducts(currentFilter);
     updateCartDisplay();
   }

   // Инициализация при загрузке
   document.addEventListener('DOMContentLoaded', () => {
     // Проверяем доступ к админ-панели
     if (localStorage.getItem('adminAccess') === 'true') {
       document.getElementById('loginPanel').style.display = 'none';
       document.getElementById('adminPanel').style.display = 'block';
     } else {
       document.getElementById('adminPanel').style.display = 'none';
     }
     
     renderProducts();
     initAdminPanel();
     
     document.getElementById("delivery").addEventListener("change", function() {
       updateCartDisplay();
       const addressField = document.getElementById("address");
       if (this.value === "0") {
         addressField.style.display = "none";
       } else {
         addressField.style.display = "block";
       }
     });
     
     // Слушаем события обновления остатков
     document.addEventListener('stockUpdated', handleStockUpdate);
     
     // Принудительное обновление при изменении версии
     if (localStorage.getItem('forceRefresh') === 'true') {
       localStorage.removeItem('forceRefresh');
       location.reload();
     }
   });
 </script>
</body>
</html> 
```
