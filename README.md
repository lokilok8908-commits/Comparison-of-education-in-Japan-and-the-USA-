# Comparison-of-education-in-Japan-and-the-USA-
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Сравнение систем образования: Япония vs США</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        body {
            background-color: #f8f9fa;
            color: #333;
            line-height: 1.6;
            background-image: url('https://images.unsplash.com/photo-1523050854058-8df90110c9f1?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80');
            background-size: cover;
            background-attachment: fixed;
            background-position: center;
            position: relative;
        }
        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.92);
            z-index: -1;
        }
        .container {
            max-width: 100%;
            margin: 0 auto;
            padding: 10px;
        }
        header {
            text-align: center;
            padding: 20px 10px;
            background: linear-gradient(135deg, #1a237e 0%, #283593 100%);
            color: white;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }
        h1 {
            font-size: 1.8rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            padding: 0 10px;
        }        
        .subtitle {
            font-size: 1rem;
            opacity: 0.9;
            max-width: 100%;
            margin: 0 auto;
            padding: 0 10px;
        }        
        .country-selector {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 20px 0;
            flex-wrap: wrap;
        }
        .country-icon {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            padding: 10px;
        }
        .country-icon.japan {
            background: linear-gradient(135deg, #ffffff 0%, #f5f5f5 100%);
            border: 3px solid #000000;
        }
        .country-icon.usa {
            background: linear-gradient(135deg, #ffffff 0%, #f5f5f5 100%);
            border: 3px solid #000000;
        }
        .country-icon:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
        }
        .country-icon.active {
            transform: scale(1.05);
            box-shadow: 0 0 0 4px rgba(0, 0, 0, 0.2);
        }       
        .country-icon i {
            font-size: 30px;
            margin-bottom: 8px;
            color: #000000;
        }    
        .country-icon span {
            font-weight: bold;
            font-size: 0.9rem;
            color: #000000;
            text-align: center;
        }  
        .country-section {
            display: none;
            padding: 20px 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            position: relative;
            overflow: hidden;
        }
        .country-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            opacity: 0.15;
            z-index: -1;
        } 
        #japan-section::before {
            background-image: url('https://images.unsplash.com/photo-1540959733332-eab4deabeeaf?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80');
        } 
        #usa-section::before {
            background-image: url('https://images.unsplash.com/photo-1485738422979-f5c462d49f74?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80');
        }
        .country-section.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        } 
        .country-header {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid rgba(0, 0, 0, 0.1);
            flex-direction: column;
            text-align: center;
        }        
        .country-header h2 {
            font-size: 1.5rem;
            margin-left: 0;
            margin-top: 10px;
        }        
        .country-header.japan h2 {
            color: #000000;
        }        
        .country-header.usa h2 {
            color: #000000;
        }        
        .country-content {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }        
        .country-image {
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            height: 200px;
        }        
        .country-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
                .country-info {
            padding: 15px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
        }
                .country-info h3 {
            margin-bottom: 15px;
            color: #1a237e;
            font-size: 1.2rem;
            text-align: center;
        }
                .country-info ul {
            list-style-type: none;
        }        
        .country-info li {
        padding: 8px 0;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
            font-size: 0.9rem;
        }       
        .country-info li:last-child {
            border-bottom: none;
        }        
        .country-info li::before {
            content: "•";
            font-weight: bold;
            display: inline-block;
            width: 1em;
            margin-right: 10px;
            color: #000000;
        }        
        .employment-section {
            margin-top: 20px;
            padding: 15px;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.8);
        }
                .employment-section h3 {
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            color: #1a237e;
            justify-content: center;
            font-size: 1.2rem;
        }        
        .employment-section h3 i {
            margin-right: 10px;
            color: #000000;
        }        
        .employment-content {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }       
        .employment-stats {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
                .stat-item {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            background: white;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
            font-size: 0.9rem;
        }        
        .stat-label {
            font-weight: 600;
        }        
        .stat-value {
            font-weight: bold;
            color: #000000;
        }      
        .employment-features ul {
            list-style-type: none;
        }        
        .employment-features li {
            padding: 8px 0;
            display: flex;
            align-items: center;
            font-size: 0.9rem;
        }        
        .employment-features li::before {
            content: "✓";
            font-weight: bold;
            display: inline-block;
            width: 1.5em;
            margin-right: 10px;
            color: #000000;
        }        
        .comparison-section {
            background-color: white;
            padding: 20px 15px;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
        }      
        .comparison-section h2 {
            text-align: center;
            margin-bottom: 20px;
            color: #1a237e;
            font-size: 1.5rem;
        } 
        .chart-container {
            margin-bottom: 30px;
        }        
        .chart-box {
            height: 300px;
            position: relative;
        }        
        .employment-chart-box {
            height: 250px;
            position: relative;
            margin-top: 20px;
        }        
        .key-differences {
            background-color: #f5f7ff;
            padding: 20px;
            border-radius: 10px;
            border-left: 5px solid #1a237e;
        }       
        .key-differences h3 {
            margin-bottom: 15px;
            color: #1a237e;
            font-size: 1.2rem;
            text-align: center;
        }        
        .key-differences ul {
            list-style-position: inside;
            padding-left: 0;
        }        
        .key-differences li {
            margin-bottom: 10px;
            padding-left: 10px;
            font-size: 0.9rem;
        } 
        .conclusion {
            background-color: white;
            padding: 20px 15px;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            text-align: center;
        }    
        .conclusion h2 {
            margin-bottom: 20px;
            color: #1a237e;
            font-size: 1.5rem;
        }        
        .conclusion-content {
            display: flex;
            flex-direction: column;
            gap: 20px;
            text-align: left;
        }        
        .conclusion-item {
            padding: 15px;
            border-radius: 8px;
        }        
        .conclusion-japan {
            background-color: #f5f5f5;
            border-left: 4px solid #000000;
        }        
        .conclusion-usa {
            background-color: #f5f5f5;
            border-left: 4px solid #000000;
        }
                .conclusion-item h3 {
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            font-size: 1.1rem;
        }        
        .conclusion-item h3 i {
            margin-right: 10px;
            color: #000000;
        }
        .conclusion-item p {
            font-size: 0.9rem;
            margin-bottom: 10px;
        }        
        footer {
            text-align: center;
            padding: 15px;
            background: linear-gradient(135deg, #1a237e 0%, #283593 100%);
            color: white;
            border-radius: 10px;
            margin-top: 20px;
            font-size: 0.9rem;
        }   
        /* Улучшения для очень маленьких экранов */
        @media (max-width: 360px) {
            h1 {
                font-size: 1.5rem;
            }         
            .country-icon {
                width: 85px;
                height: 85px;
            }            
            .country-icon i {
                font-size: 25px;
            }            
            .country-icon span {
                font-size: 0.8rem;
            }            
            .chart-box {
                height: 250px;
            }            
            .employment-chart-box {
                height: 200px;
            }
        }        
        /* Горизонтальная ориентация */
        @media (max-width: 768px) and (orientation: landscape) {
            .country-content {
                flex-direction: row;
            }            
            .country-image {
                height: 250px;
            }            
            .employment-content {
                flex-direction: row;
            }
        }        
        /* Улучшения для планшетов */
        @media (min-width: 768px) {
            .container {
                padding: 15px;
            }            
            h1 {
                font-size: 2.2rem;
            }            
            .country-content, .conclusion-content, .employment-content {
                flex-direction: row;
            }            
            .country-image {
                height: 250px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Системы образования: Япония vs США</h1>
            <p class="subtitle">Сравнительный анализ двух различных подходов к образованию и трудоустройству</p>            
            <div class="country-selector">
                <div class="country-icon japan active" data-country="japan">
                    <i class="fas fa-landmark"></i>
                    <span>Япония</span>
                </div>
                <div class="country-icon usa" data-country="usa">
                    <i class="fas fa-university"></i>
                    <span>США</span>
                </div>
            </div>
        </header>        
        <!-- Секция Японии -->
        <section id="japan-section" class="country-section active">
            <div class="country-header japan">
                <i class="fas fa-landmark fa-2x"></i>
                <h2>Система образования Японии</h2>
            </div>
            <div class="country-content">
                <div class="country-image">
                    <img src="https://images.unsplash.com/photo-1528164344705-47542687000d?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Японская школа">
                </div>
                <div class="country-info">
                    <h3>Основные характеристики</h3>
                    <ul>
                        <li>Сильный акцент на дисциплине и уважении к учителям</li>
                        <li>Единая национальная учебная программа</li>
                        <li>Продолжительный учебный день (до 6-7 часов)</li>
                        <li>Обязательное образование: 9 лет (6-15 лет)</li>
                        <li>Высокий уровень участия в дополнительных занятиях (дзюку)</li>
                        <li>Важность групповой гармонии над индивидуальными достижениями</li>
                        <li>Высококонкурентные вступительные экзамены в вузы</li>
                        <li>Минимальное количество дней пропусков занятий</li>
                    </ul>
                </div>
            </div>            
            <div class="employment-section">
                <h3><i class="fas fa-briefcase"></i> Трудоустройство после учебы</h3>
                <div class="employment-content">
                    <div class="employment-stats">
                        <div class="stat-item">
                            <span class="stat-label">Уровень безработицы выпускников:</span>
                            <span class="stat-value">3.2%</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Среднее время поиска работы:</span>
                            <span class="stat-value">3.8 месяцев</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Процент трудоустройства по специальности:</span>
                            <span class="stat-value">72%</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Средняя начальная зарплата:</span>
                            <span class="stat-value">28,000 USD/год</span>
                        </div>
                    </div>
                    <div class="employment-features">
                        <ul>
                            <li>Система "пожизненного найма" в крупных компаниях</li>
                            <li>Выпускники часто трудоустраиваются через университетские связи</li>
                            <li>Важность корпоративной культуры и лояльности компании</li>
                            <li>Сезон найма выпускников (апрель)</li>
                            <li>Высокая конкуренция за места в престижных компаниях</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>        
        <!-- Секция США -->
        <section id="usa-section" class="country-section">
            <div class="country-header usa">
                <i class="fas fa-university fa-2x"></i>
                <h2>Система образования США</h2>
            </div>
            <div class="country-content">
                <div class="country-image">
                    <img src="https://images.unsplash.com/photo-1523580494863-6f3031224c94?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Американская школа">
                </div>
                <div class="country-info">
                    <h3>Основные характеристики</h3>
                    <ul>
                        <li>Акцент на развитие индивидуальности и критического мышления</li>
                        <li>Децентрализованная система (разные стандарты по штатам)</li>
                        <li>Короче учебный день (обычно 5-6 часов)</li>
                        <li>Обязательное образование: 12 лет (6-18 лет)</li>
                        <li>Широкий выбор факультативов и внеклассных мероприятий</li>
                        <li>Поощрение индивидуальных достижений и самовыражения</li>
                        <li>Разносторонний подход к поступлению в вузы (не только экзамены)</li>
                        <li>Больше гибкости в выборе предметов и специализации</li>
                    </ul>
                </div>
            </div>            
            <div class="employment-section">
                <h3><i class="fas fa-briefcase"></i> Трудоустройство после учебы</h3>
                <div class="employment-content">
                    <div class="employment-stats">
                        <div class="stat-item">
                            <span class="stat-label">Уровень безработицы выпускников:</span>
                            <span class="stat-value">4.5%</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Среднее время поиска работы:</span>
                            <span class="stat-value">5.2 месяцев</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Процент трудоустройства по специальности:</span>
                            <span class="stat-value">65%</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Средняя начальная зарплата:</span>
                            <span class="stat-value">35,000 USD/год</span>
                        </div>
                    </div>
                    <div class="employment-features">
                        <ul>
                            <li>Гибкий рынок труда с частой сменой работы</li>
                            <li>Карьерные ярмарки и центры карьеры при университетах</li>
                            <li>Важность сетей контактов (networking) и рекомендаций</li>
                            <li>Развитая система стажировок и программ для выпускников</li>
                            <li>Возможности для предпринимательства и стартапов</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>      
        <!-- Секция сравнения -->
        <section class="comparison-section">
            <h2>Сравнительный анализ</h2>            
            <div class="chart-container">
                <div class="chart-box">
                    <canvas id="comparisonChart"></canvas>
                </div>                
                <div class="employment-chart-box">
                    <canvas id="employmentChart"></canvas>
                </div>
            </div>            
            <div class="key-differences">
                <h3>Ключевые различия в трудоустройстве</h3>
                <ul>
                    <li><strong>Подход к карьере:</strong> В Японии преобладает система пожизненного найма, в США - гибкость и мобильность на рынке труда.</li>
                    <li><strong>Процесс найма:</strong> В Японии существует сезон найма выпускников, в США найм происходит круглый год.</li>
                    <li><strong>Корпоративная культура:</strong> Японские компании ценят лояльность и стаж, американские - результаты и инновации.</li>
                    <li><strong>Зарплаты:</strong> В США выше начальные зарплаты, но в Японии больше социальных гарантий.</li>
                    <li><strong>Карьерный рост:</strong> В Японии карьера строится постепенно внутри компании, в США возможны резкие карьерные скачки.</li>
                </ul>
            </div>
        </section>        
        <!-- Заключение -->
        <section class="conclusion">
            <h2>Выводы</h2>
            <div class="conclusion-content">
                <div class="conclusion-item conclusion-japan">
                    <h3><i class="fas fa-landmark"></i> Сильные стороны Японии</h3>
                    <p>Японская система образования производит высокодисциплинированных и трудолюбивых студентов с сильными базовыми знаниями. Акцент на групповой работе создает сплоченные коллективы. Выпускники ценятся за лояльность и умение работать в команде.</p>
                    <p>Система трудоустройства обеспечивает стабильность и социальные гарантии, но ограничивает мобильность на рынке труда.</p>
                </div>
                <div class="conclusion-item conclusion-usa">
                    <h3><i class="fas fa-university"></i> Сильные стороны США</h3>
                    <p>Американская система развивает критическое мышление, креативность и лидерские качества. Гибкость выбора позволяет студентам развивать свои уникальные таланты.</p>
                    <p>Рынок труда предлагает больше возможностей для карьерного роста и смены профессиональной траектории, но требует большей самостоятельности от выпускников.</p>
                </div>
            </div>
        </section>        
        <footer>
            <p>© 2023 Сравнительный анализ систем образования Японии и США</p>
            <p>Информация предназначена для образовательных целей</p>
        </footer>
    </div>
    <script>        document.addEventListener('DOMContentLoaded', function() {
            // Переключение между странами
            const countryIcons = document.querySelectorAll('.country-icon');
            const countrySections = document.querySelectorAll('.country-section');
                        countryIcons.forEach(icon => {
                icon.addEventListener('click', function() {
                    const country = this.getAttribute('data-country');                                   // Убираем активный класс у всех иконок                   countryIcons.forEach(i => i.classList.remove('active'));
                    // Добавляем активный класс к текущей иконке
                    this.classList.add('active');
                                        // Скрываем все секции
                    countrySections.forEach(section => section.classList.remove('active'));
                    // Показываем нужную секцию
                    document.getElementById(`${country}-section`).classList.add('active');
                });
            });            
            // График сравнения образования
            const ctx = document.getElementById('comparisonChart').getContext('2d');            
            const data = {                labels: ['Длительность учебного дня (часы)', 'Дней в учебном году', 'Домашние задания (часы/неделя)', 'Внеклассные занятия (часы/неделя)', 'Размер классов (учеников)', 'Расходы на образование (% ВВП)'],
                datasets: [
                    {
                        label: 'Япония',
                        data: [7.5, 240, 14, 10, 28, 3.5],
                        backgroundColor: 'rgba(0, 0, 0, 0.7)',
                        borderColor: 'rgba(0, 0, 0, 1)',
                        borderWidth: 2
                    },
                    {
                        label: 'США',
                        data: [6.5, 180, 6, 8, 24, 5.0],
                        backgroundColor: 'rgba(100, 100, 100, 0.7)',
                        borderColor: 'rgba(100, 100, 100, 1)',
                        borderWidth: 2
                    }
                ]
            };            
            const config = {
                type: 'bar',
                data: data,
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            title: {
                                display: true,
                                text: 'Значения'
                            }
                        }
                    },
                    plugins: {
                        legend: {
                            position: 'top',
                        },
                        title: {
                            display: true,
                            text: 'Сравнение систем образования Японии и США'
                        }
                    }
                }
            };
                        new Chart(ctx, config);                        // График сравнения трудоустройства
            const employmentCtx = document.getElementById('employmentChart').getContext('2d');            
            const employmentData = {
                labels: ['Уровень безработицы (%)', 'Время поиска работы (месяцы)', 'Трудоустройство по специальности (%)', 'Начальная зарплата (тыс. USD)'],
                datasets: [
                    {
                        label: 'Япония',
                        data: [3.2, 3.8, 72, 28],
                        backgroundColor: 'rgba(0, 0, 0, 0.7)',
                        borderColor: 'rgba(0, 0, 0, 1)',
                        borderWidth: 2
                    },
                    {
                        label: 'США',
                        data: [4.5, 5.2, 65, 35],
                        backgroundColor: 'rgba(100, 100, 100, 0.7)',
                        borderColor: 'rgba(100, 100, 100, 1)',
                        borderWidth: 2
                    }
                ]
            };            
            const employmentConfig = {
                type: 'bar',
                data: employmentData,
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            title: {
                                display: true,
                                text: 'Значения'
                            }
                        }
                    },
                    plugins: {
                        legend: {
                            position: 'top',
                        },
                        title: {
                            display: true,
                            text: 'Сравнение трудоустройства выпускников'
                        }
                    }
                }
            };
                        new Chart(employmentCtx, employmentConfig);
        });
    </script>
</body>
</html>

На оценку
