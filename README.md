```html
<!DOCTYPE html>
<html lang="ru">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>TLP | SHOP</title>
 <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600&display=swap" rel="stylesheet">
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
   .admin-panel {
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
     gap: 10px;
     margin-bottom: 15px;
   }
   .admin-controls select, .admin-controls input {
     padding: 8px;
     border-radius: 5px;
     border: 1px solid #ddd;
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
     <button onclick="filterCategory()">Все товары</button>
   </div>
   <div class="products" id="product-list">
     <!-- JS добавит товары сюда -->
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

 <!-- Админ-панель (можно скрыть в production) -->
 <div class="admin-panel" id="adminPanel">
   <h2>Админ-панель</h2>
   <div class="admin-controls">
     <select id="adminProductSelect">
       <option value="">Выберите товар</option>
     </select>
     <select id="adminFlavorSelect" style="display: none;">
       <option value="">Выберите вкус</option>
     </select>
     <input type="number" id="adminQty" placeholder="Количество" min="1" value="1">
     <button onclick="updateStock()">Обновить остатки</button>
   </div>
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
   // Загрузка остатков из localStorage
   function loadStock() {
     const savedStock = localStorage.getItem('tlpShopStock');
     return savedStock ? JSON.parse(savedStock) : {
       "1": {"Еживика черника малина": 1, "Мята": 1, "Сакура виноград": 1, "Тройная ягода": 1, "Черника малина": 1, "Клюква виноград": 1, "Энергетик черная смородина": 1, "Арбуз": 1, "Клубника киви": 1, "Капучино": 1, "Черника малина ментол": 1}, 
       "2": {"Лайм": 1, "Киви маракуйя гуава": 1, "Ледяной арбуз": 1, "Гранатовый сок": 1},
       "3": {},
       "4": {"Подик": 1},
       "5": {"Экзотические фрукты": 1},
       "6": {"Испарик": 1},
       "7": {"0.6": 1 , "0.8": 1},
       "8": {"АКБ": 1},
       "9": {"Черная вишня": 1, "Киви гуава маракуйя": 1, "Персик бабл гам": 1, "Банан кокос": 1, "Манго грейпфрут": 1, "Земляничный мохито": 1, "Северные ягоды": 1, "Грейпфрутовый швепс": 1, "Гранат смородина": 1, "Фруктовые пластинки": 1},
       "10": {"Апельсиновая газировка": 1, "Брусничный морс": 1, "Ежевичный лимонад": 1, "Пина колада с грушей": 1, "Освежающий лимонад": 1, "Малиновый пунш": 1, "Морс черника виноград": 1, "Яблочный лимонад": 1}
     };
   }

   // Сохранение остатков в localStorage
   function saveStock(stock) {
     localStorage.setItem('tlpShopStock', JSON.stringify(stock));
     // Триггерим событие для обновления интерфейса
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
       description: "20 000 затяжек? Ну, если не жаришь её как последнюю хуйню в твоей жалкой жизни. Аккум 850mAh — хватит, чтобы вырубить даже слона. Выбирай вкус и наслаждайся, пока не сдохнешь от никотинового кайфа.", 
       flavors: serverStock["1"] 
     },
     { 
       id: 2, 
       name: "Lost Mary 16000", 
       category: "disposable", 
       price: 1700, 
       image: 'dis/2.jpg', 
       description: "16 000 тяг, но ты всё равно сожрёшь её за два дня, слабак. Профессиональная серия — потому что для тех, у кого яйца есть. Вкусы? Да хоть табак, хоть ваниль — главное, чтобы мозги вырубило.", 
       flavors: serverStock["2"] 
     },
     { 
       id: 3, 
       name: "WAKA 69 мг", 
       price: 550, 
       image: 'ju/1.jpg', 
       description: "69 мг никотина — не для школьников, а для дегенератов, которые хотят отъехать с первой затяжки. Лёд, фрукты или пиздатый микс — выбирай и готовься к тому, что лёгкие скажут пока.", 
       flavors: serverStock["3"] 
     },
     { 
       id: 4, 
       name: "Smoant Knight 80 kit", 
       category: "pod", 
       price: 3700, 
       image: 'pod/1.jpg', 
       description: "Не хуйня за 500 рублей, а серьёзный девайс для тех, кто не сосёт слабые испарители. Мощность, контроль и долгий ресурс — если, конечно, ты не разъебешь его за неделю.", 
       flavors: serverStock["4"] 
     },
     { 
       id: 5, 
       name: "Анаржия&зевс 70мг", 
       category: "juice", 
       price: 500, 
       image: 'ju/2.jpg', 
       description: "70 мг никотина — это не шутки, уёбок. Один пых — и ты уже в космосе. Для тех, кому обычные жижи кажутся водой.", 
       flavors: serverStock["5"] 
     },
     { 
       id: 6, 
       name: "Испарик К-1", 
       category: "vaporizer", 
       price: 350, 
       image: 'vap/1.jpg', 
       description: "Освежает так, будто тебя ебнули мятным ураганом в глотку. Лёд, фрукты или что-то посерьёзнее — выбирай и не ной, если лёгкие взвоют.", 
       flavors: serverStock["6"] 
     },
     { 
       id: 7, 
       name: "Картридж на xros 0.6/0.8 ом", 
       category: "vaporizer", 
       price: 450, 
       image: 'vap/2.jpg', 
       description: "Вставил, затянулся — и понеслась. Никакого геморроя с самозамесом, просто чистая никотиновая бомба.", 
       flavors: serverStock["7"] 
     },
     { 
       id: 8, 
       name: "АКБ банан", 
       category: "accessories", 
       price: 600, 
       image: 'acc/1.jpg', 
       description: "Чтоб твой девайс не сдох нахуй посреди дня. Мощная, удобная, но всё равно ты её потеряешь через месяц.", 
       flavors: serverStock["8"] 
     },
     { 
       id: 9, 
       name: "Rick and Morty Bad Trip 70мг", 
       category: "juice", 
       price: 550, 
       image: 'ju/3.jpg', 
       description: "70 мг никотина и вкус, от которого реально словишь bad trip. Если хочешь ощутить, как твои мозги плавятся — это твой выбор.", 
       flavors: serverStock["9"] 
     },
     {
      id: 10,
      name: "Podonki Vintage 70мг",
      category: "juice",
      price: 550,
      image: 'ju/4.jpg',
      description: "Старая школа с пиздатым ударом. 70 мг — как в те времена, когда вейперы ещё не были хипстерами.",
      flavors: serverStock["10"]
     }
   ];

   let cart = [];

   // Инициализация админ-панели
   function initAdminPanel() {
     const productSelect = document.getElementById('adminProductSelect');
     products.forEach(product => {
       const option = document.createElement('option');
       option.value = product.id;
       option.textContent = product.name;
       productSelect.appendChild(option);
     });

     productSelect.addEventListener('change', function() {
       const productId = this.value;
       const flavorSelect = document.getElementById('adminFlavorSelect');
       flavorSelect.innerHTML = '<option value="">Выберите вкус</option>';
       
       if (productId) {
         const product = products.find(p => p.id == productId);
         if (product.flavors) {
           flavorSelect.style.display = 'block';
           Object.keys(product.flavors).forEach(flavor => {
             const option = document.createElement('option');
             option.value = flavor;
             option.textContent = flavor;
             flavorSelect.appendChild(option);
           });
         } else {
           flavorSelect.style.display = 'none';
         }
       } else {
         flavorSelect.style.display = 'none';
       }
     });
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
     
     // Проверяем, есть ли уже такой вкус в корзине
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

   function filterCategory(cat) { renderProducts(cat); }

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

   function submitOrder() {
     const deliverySelect = document.getElementById("delivery");
     const district = deliverySelect.selectedOptions[0]?.text;
     const deliveryPrice = parseInt(deliverySelect.value);
     let address = '';

     if (deliveryPrice !== 0) {
       // Если не самовывоз, проверяем адрес
       address = document.getElementById('address').value.trim();
       if (!address) {
         alert("Укажите адрес доставки");
         return;
       }
     } else {
       // Если самовывоз
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

           // Обновляем остатки
           if (product.stock !== undefined) {
             product.stock -= qty;
             if (product.stock < 0) product.stock = 0;
             serverStock[product.id] = product.stock;
           }
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

             // Обновляем остатки
             product.flavors[flavorName] -= qty;
             if (product.flavors[flavorName] < 0) product.flavors[flavorName] = 0;
             serverStock[product.id][flavorName] = product.flavors[flavorName];
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

     const orderData = {
       items: cartItems,
       address: address,
       district: district,
       deliveryPrice: deliveryPrice,
       subtotal: subtotal,
       total: total,
       phone: window.Telegram?.WebApp?.initDataUnsafe?.user?.phone_number || "не указан"
     };

     // Сохраняем обновленные остатки
     saveStock(serverStock);

     // Отправка данных в Telegram бот
     if (window.Telegram && window.Telegram.WebApp) {
       try {
         window.Telegram.WebApp.sendData(JSON.stringify(orderData));
         window.Telegram.WebApp.close();
       } catch (e) {
         console.error("Ошибка отправки данных в Telegram:", e);
         alert("Заказ оформлен! Менеджер свяжется с вами.");
       }
     } else {
       console.log("Данные заказа (тестовый режим):", orderData);
       alert("Заказ оформлен! Менеджер свяжется с вами.");
     }

     // Обновляем интерфейс после заказа
     renderProducts();
     updateCartDisplay();
   }

   // Обновление интерфейса при изменении остатков
   function handleStockUpdate() {
     // Обновляем данные в products
     for (const product of products) {
       if (product.flavors) {
         product.flavors = serverStock[product.id];
       } else if (serverStock[product.id] !== undefined && typeof serverStock[product.id] === 'number') {
         product.stock = serverStock[product.id];
       }
     }
     
     // Перерисовываем товары
     const currentFilter = document.querySelector('.category-tabs button[style*="background: #2980b9"]')?.getAttribute('onclick')?.replace("filterCategory('", "").replace("')", "") || null;
     renderProducts(currentFilter);
     
     // Очищаем корзину
     document.querySelectorAll('[id^="selected-flavors-"]').forEach(el => el.innerHTML = '');
     document.querySelectorAll('[id^="qty-"]').forEach(el => el.textContent = '0');
     updateCartDisplay();
   }

   // Инициализация при загрузке
   document.addEventListener('DOMContentLoaded', () => {
     renderProducts();
     initAdminPanel();
     
     document.getElementById("delivery").addEventListener("change", function() {
       updateCartDisplay();
       // Скрываем/показываем поле адреса в зависимости от выбора доставки
       const addressField = document.getElementById("address");
       if (this.value === "0") {
         addressField.style.display = "none";
       } else {
         addressField.style.display = "block";
       }
     });
     
     // Слушаем события обновления остатков
     document.addEventListener('stockUpdated', handleStockUpdate);
     
     // Скрываем админ-панель для обычных пользователей (можно удалить в production)
     if (!window.location.href.includes('admin')) {
       document.getElementById('adminPanel').style.display = 'none';
     }
   });
 </script>
</body>
</html> 
```
