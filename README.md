```html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Автошкола "МастерВождение"</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #2c3e50;
            --secondary: #e74c3c;
            --accent: #3498db;
            --light: #ecf0f1;
            --dark: #2c3e50;
        }

        body {
            background-color: #f9f9f9;
            color: #333;
            line-height: 1.6;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Шапка */
        header {
            background: linear-gradient(135deg, var(--primary), #1a2530);
            color: white;
            padding: 15px 0;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo {
            width: 60px;
            height: 60px;
            background: var(--accent);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            color: white;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .logo-text {
            font-size: 24px;
            font-weight: 700;
        }

        .logo-text span {
            color: var(--accent);
        }

        .contact-info {
            text-align: right;
        }

        .phone {
            font-size: 20px;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .author {
            font-size: 14px;
            opacity: 0.9;
        }

        /* Слоган */
        .slogan {
            background: linear-gradient(rgba(44, 62, 80, 0.9), rgba(44, 62, 80, 0.9)), url('https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?ixlib=rb-4.0.3&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            color: white;
            text-align: center;
            padding: 80px 0;
        }

        .slogan h2 {
            font-size: 36px;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        .slogan p {
            font-size: 20px;
            max-width: 700px;
            margin: 0 auto;
        }

        /* Статьи */
        .articles {
            padding: 60px 0;
            background-color: white;
        }

        .section-title {
            text-align: center;
            margin-bottom: 40px;
            color: var(--primary);
            font-size: 32px;
            position: relative;
        }

        .section-title:after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: var(--secondary);
            margin: 10px auto;
        }

        .articles-container {
            display: flex;
            gap: 30px;
        }

        .article {
            flex: 1;
            background: var(--light);
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease;
        }

        .article:hover {
            transform: translateY(-5px);
        }

        .article h3 {
            color: var(--primary);
            margin-bottom: 15px;
            font-size: 22px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .article h3 i {
            color: var(--accent);
        }

        /* Навигация */
        .categories-nav {
            background-color: var(--primary);
            padding: 20px 0;
        }

        .categories-container {
            display: flex;
            justify-content: center;
            gap: 30px;
        }

        .category-link {
            color: white;
            text-decoration: none;
            font-size: 18px;
            font-weight: bold;
            padding: 12px 25px;
            background: var(--accent);
            border-radius: 30px;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        .category-link:hover {
            background: var(--secondary);
            transform: translateY(-3px);
            box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
        }

        /* Преподаватели */
        .instructors {
            padding: 60px 0;
            background-color: var(--light);
        }

        .instructors-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 30px;
        }

        .instructor {
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            text-align: center;
            transition: transform 0.3s ease;
        }

        .instructor:hover {
            transform: translateY(-5px);
        }

        .instructor-img {
            height: 200px;
            background: var(--accent);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 80px;
        }

        .instructor-info {
            padding: 20px;
        }

        .instructor-info h3 {
            margin-bottom: 10px;
            color: var(--primary);
        }

        .instructor-info p {
            color: #7f8c8d;
            font-size: 14px;
        }

        /* Основной контент и боковая панель */
        .main-content {
            display: flex;
            gap: 30px;
            padding: 60px 0;
            background-color: white;
        }

        .content {
            flex: 3;
        }

        .category-section {
            margin-bottom: 40px;
            padding: 25px;
            background: var(--light);
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .category-section h2 {
            color: var(--primary);
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .category-section h2 i {
            color: var(--accent);
        }

        .price {
            font-size: 24px;
            font-weight: bold;
            color: var(--secondary);
            margin: 15px 0;
        }

        /* Боковая панель */
        .sidebar {
            flex: 1;
            background: var(--light);
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            align-self: flex-start;
        }

        .sidebar h3 {
            color: var(--primary);
            margin-bottom: 20px;
            text-align: center;
            font-size: 22px;
        }

        .advantages-list {
            list-style-type: none;
        }

        .advantages-list li {
            padding: 12px 0;
            border-bottom: 1px solid #dce4e8;
            display: flex;
            align-items: center;
        }

        .advantages-list li:last-child {
            border-bottom: none;
        }

        .advantage-icon {
            color: var(--accent);
            margin-right: 10px;
            font-size: 18px;
        }

        /* Подвал */
        footer {
            background: linear-gradient(135deg, var(--primary), #1a2530);
            color: white;
            padding: 60px 0 30px;
        }

        .reviews-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }

        .review {
            background: rgba(255, 255, 255, 0.1);
            padding: 25px;
            border-radius: 8px;
            backdrop-filter: blur(5px);
        }

        .review-text {
            font-style: italic;
            margin-bottom: 15px;
        }

        .review-author {
            text-align: right;
            font-weight: bold;
        }

        .copyright {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
            font-size: 14px;
        }

        /* Адаптивность */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            .contact-info {
                margin-top: 15px;
                text-align: center;
            }
            
            .articles-container, 
            .main-content {
                flex-direction: column;
            }
            
            .categories-container {
                flex-direction: column;
                align-items: center;
            }
            
            .slogan h2 {
                font-size: 28px;
            }
            
            .slogan p {
                font-size: 18px;
            }
        }
    </style>
</head>
<body>
    <!-- Шапка -->
    <header>
        <div class="container header-content">
            <div class="logo-container">
                <div class="logo">
                    <i class="fas fa-car"></i>
                </div>
                <div class="logo-text">Автошкола <span>МастерВождение</span></div>
            </div>
            <div class="contact-info">
                <div class="phone">+7 (123) 456-78-90</div>
                <div class="author">Иванов Иван Иванович</div>
            </div>
        </div>
    </header>

    <!-- Слоган -->
    <section class="slogan">
        <div class="container">
            <h2>Стань уверенным водителем с первой поездки!</h2>
            <p>Профессиональное обучение вождению с индивидуальным подходом к каждому ученику</p>
        </div>
    </section>

    <!-- Статьи -->
    <section class="articles">
        <div class="container">
            <h2 class="section-title">О нашей автошколе</h2>
            <div class="articles-container">
                <article class="article">
                    <h3><i class="fas fa-history"></i> Наша история</h3>
                    <p>Автошкола "МастерВождение" успешно работает на рынке образовательных услуг более 15 лет. За это время мы выпустили более 5000 квалифицированных водителей, которые уверенно чувствуют себя на дорогах в любых условиях.</p>
                    <p>Мы постоянно совершенствуем методики обучения, следим за изменениями в законодательстве и обновляем наш автопарк для обеспечения максимально эффективного и комфортного обучения.</p>
                </article>
                <article class="article">
                    <h3><i class="fas fa-graduation-cap"></i> Наш подход</h3>
                    <p>Мы используем современные методики обучения, сочетающие теоретическую подготовку с практическими занятиями на специально оборудованных площадках и в городских условиях.</p>
                    <p>Наши преподаватели и инструкторы - опытные профессионалы, которые найдут подход к каждому ученику, помогут преодолеть страх и неуверенность, и сделают процесс обучения интересным и продуктивным.</p>
                </article>
            </div>
        </div>
    </section>

    <!-- Навигация -->
    <section class="categories-nav">
        <div class="container categories-container">
            <a href="category-b.html" class="category-link">
                <i class="fas fa-car-side"></i> Категория B
            </a>
            <a href="category-c.html" class="category-link">
                <i class="fas fa-truck"></i> Категория C
            </a>
            <a href="category-dopog.html" class="category-link">
                <i class="fas fa-exclamation-triangle"></i> ДОПОГ
            </a>
        </div>
    </section>

    <!-- Преподаватели -->
    <section class="instructors">
        <div class="container">
            <h2 class="section-title">Наши преподаватели</h2>
            <div class="instructors-grid">
                <div class="instructor">
                    <div class="instructor-img">
                        <i class="fas fa-user-tie"></i>
                    </div>
                    <div class="instructor-info">
                        <h3>Петров Алексей</h3>
                        <p>Опыт работы: 12 лет. Специализация: категория B. Индивидуальный подход к каждому ученику.</p>
                    </div>
                </div>
                <div class="instructor">
                    <div class="instructor-img">
                        <i class="fas fa-user-graduate"></i>
                    </div>
                    <div class="instructor-info">
                        <h3>Сидорова Мария</h3>
                        <p>Опыт работы: 8 лет. Специализация: категория B и C. Терпеливый и внимательный инструктор.</p>
                    </div>
                </div>
                <div class="instructor">
                    <div class="instructor-img">
                        <i class="fas fa-user-cog"></i>
                    </div>
                    <div class="instructor-info">
                        <h3>Козлов Дмитрий</h3>
                        <p>Опыт работы: 15 лет. Специализация: категория C и ДОПОГ. Мастер производственного обучения.</p>
                    </div>
                </div>
                <div class="instructor">
                    <div class="instructor-img">
                        <i class="fas fa-chalkboard-teacher"></i>
                    </div>
                    <div class="instructor-info">
                        <h3>Николаева Ольга</h3>
                        <p>Опыт работы: 10 лет. Специализация: теория ПДД. Ясно и доступно объясняет сложные моменты.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Основной контент и боковая панель -->
    <div class="container main-content">
        <!-- Основной контент -->
        <main class="content">
            <section class="category-section">
                <h2><i class="fas fa-car-side"></i> Категория B</h2>
                <p>Полный курс обучения на право управления автомобилями массой до 3,5 тонн с количеством пассажирских мест до 8.</p>
                <div class="price">25 000 рублей</div>
                <p>В курс входит: 134 часа теории, 56 часов практики, подготовка к экзамену в ГИБДД.</p>
            </section>
            
            <section class="category-section">
                <h2><i class="fas fa-truck"></i> Категория C</h2>
                <p>Обучение управлению грузовыми автомобилями массой свыше 3,5 тонн.</p>
                <div class="price">35 000 рублей</div>
                <p>В курс входит: 168 часов теории, 84 часа практики, обучение на современных грузовых автомобилях.</p>
            </section>
            
            <section class="category-section">
                <h2><i class="fas fa-exclamation-triangle"></i> ДОПОГ</h2>
                <p>Специализированная подготовка для перевозки опасных грузов.</p>
                <div class="price">15 000 рублей</div>
                <p>В курс входит: изучение классов опасных грузов, правил их перевозки, мер безопасности и оказания первой помощи.</p>
            </section>
        </main>
        
        <!-- Боковая панель -->
        <aside class="sidebar">
            <h3>Наши преимущества</h3>
            <ul class="advantages-list">
                <li><span class="advantage-icon"><i class="fas fa-check"></i></span> Современный автопарк</li>
                <li><span class="advantage-icon"><i class="fas fa-check"></i></span> Опытные инструкторы</li>
                <li><span class="advantage-icon"><i class="fas fa-check"></i></span> Гибкий график занятий</li>
                <li><span class="advantage-icon"><i class="fas fa-check"></i></span> Рассрочка платежа</li>
                <li><span class="advantage-icon"><i class="fas fa-check"></i></span> Высокий процент сдачи</li>
                <li><span class="advantage-icon"><i class="fas fa-check"></i></span> Современные методики обучения</li>
                <li><span class="advantage-icon"><i class="fas fa-check"></i></span> Подготовка к экзамену в ГИБДД</li>
                <li><span class="advantage-icon"><i class="fas fa-check"></i></span> Удобное расположение</li>
            </ul>
        </aside>
    </div>

    <!-- Подвал -->
    <footer>
        <div class="container">
            <h2 class="section-title" style="color: white;">Отзывы наших учеников</h2>
            <div class="reviews-grid">
                <div class="review">
                    <p class="review-text">Отличная автошкола! Инструктор Алексей очень терпеливо и доступно объяснял все нюансы вождения. Сдала экзамен с первого раза!</p>
                    <p class="review-author">- Анна, выпуск 2023</p>
                </div>
                <div class="review">
                    <p class="review-text">Долго выбирал автошколу и не ошибся с "МастерВождением". Теория преподается интересно, а практические занятия проходят на современных автомобилях.</p>
                    <p class="review-author">- Дмитрий, выпуск 2023</p>
                </div>
                <div class="review">
                    <p class="review-text">Проходил обучение на категорию С. Отличные инструкторы и хорошо организованный процесс обучения. Рекомендую!</p>
                    <p class="review-author">- Сергей, выпуск 2022</p>
                </div>
            </div>
            <div class="copyright">
                <p>© 2023 Автошкола "МастерВождение". Все права защищены.</p>
            </div>
        </div>
    </footer>
</body>
</html>
```
