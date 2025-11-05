<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Математический профиль | Определи свой стиль мышления</title>
    <meta name="description" content="Пройди тест и узнай свой математический профиль. 10 вопросов, которые раскроют твой уникальный стиль мышления.">
    <meta property="og:title" content="Математический профиль | Определи свой стиль мышления">
    <meta property="og:description" content="Узнай, какой у тебя математический тип мышления - все подходы ценны и важны!">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://yourwebsite.com/math-profile">
    <meta property="og:image" content="https://yourwebsite.com/math-profile/preview.jpg">
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #34495e;
            --success: #27ae60;
            --warning: #f39c12;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            line-height: 1.6;
        }
        
        .container {
            max-width: 900px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
        }
        
        .container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(90deg, var(--secondary), var(--accent));
        }
        
        .math-decoration {
            position: absolute;
            font-size: 120px;
            opacity: 0.1;
            color: var(--primary);
            z-index: 0;
            font-weight: bold;
        }
        
        .decoration-1 { top: 20px; right: 30px; }
        .decoration-2 { bottom: 40px; left: 40px; }
        .decoration-3 { top: 150px; left: 50px; }
        .decoration-4 { bottom: 100px; right: 80px; }
        
        h1 {
            text-align: center;
            color: var(--primary);
            margin-bottom: 15px;
            font-size: 2.8em;
            font-weight: 700;
            position: relative;
            z-index: 1;
        }
        
        .subtitle {
            text-align: center;
            color: var(--dark);
            margin-bottom: 40px;
            font-size: 1.2em;
            position: relative;
            z-index: 1;
        }
        
        .share-section {
            text-align: center;
            margin: 25px 0;
            padding: 20px;
            background: var(--light);
            border-radius: 12px;
            border-left: 4px solid var(--secondary);
        }
        
        .share-btn {
            padding: 12px 25px;
            background: var(--secondary);
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1em;
            margin: 10px;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .share-btn:hover {
            background: #2980b9;
            transform: translateY(-2px);
        }
        
        .share-btn.secondary {
            background: var(--dark);
        }
        
        .share-btn.secondary:hover {
            background: #2c3e50;
        }
        
        .question-container {
            display: none;
            position: relative;
            z-index: 1;
        }
        
        .question-container.active {
            display: block;
            animation: slideIn 0.6s ease-out;
        }
        
        .question {
            font-size: 1.4em;
            color: var(--primary);
            margin-bottom: 30px;
            text-align: center;
            font-weight: 600;
            padding: 0 20px;
        }
        
        .answers {
            display: grid;
            gap: 15px;
            margin-bottom: 40px;
        }
        
        .answer-btn {
            padding: 18px 20px;
            border: 2px solid #e0e0e0;
            border-radius: 15px;
            background: white;
            font-size: 1.05em;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: left;
            color: var(--dark);
            position: relative;
            overflow: hidden;
        }
        
        .answer-btn::before {
            content: '';
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 0;
            background: var(--light);
            transition: width 0.3s ease;
            z-index: -1;
        }
        
        .answer-btn:hover {
            border-color: var(--secondary);
            transform: translateX(10px);
        }
        
        .answer-btn:hover::before {
            width: 100%;
        }
        
        .progress-container {
            margin-bottom: 30px;
            position: relative;
            z-index: 1;
        }
        
        .progress-text {
            text-align: center;
            color: var(--dark);
            margin-bottom: 15px;
            font-size: 1em;
            font-weight: 500;
        }
        
        .progress-bar {
            width: 100%;
            height: 10px;
            background: var(--light);
            border-radius: 5px;
            overflow: hidden;
            position: relative;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--secondary), var(--accent));
            width: 0%;
            transition: width 0.5s ease;
            position: relative;
        }
        
        .progress-fill::after {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            bottom: 0;
            width: 20px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3));
        }
        
        .result {
            display: none;
            text-align: center;
            padding: 30px 20px;
            position: relative;
            z-index: 1;
        }
        
        .result-card {
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            border-top: 5px solid var(--secondary);
            margin-bottom: 25px;
        }
        
        .result-type {
            font-size: 1.8em;
            color: var(--primary);
            margin-bottom: 15px;
            font-weight: 700;
        }
        
        .result-score {
            font-size: 1.1em;
            color: var(--dark);
            margin-bottom: 20px;
            padding: 8px 20px;
            background: var(--light);
            border-radius: 20px;
            display: inline-block;
        }
        
        .result-description {
            font-size: 1.1em;
            line-height: 1.7;
            color: #555;
            margin-bottom: 20px;
            text-align: left;
        }
        
        .result-strengths {
            text-align: left;
            margin: 25px 0;
            padding: 20px;
            background: var(--light);
            border-radius: 10px;
            border-left: 4px solid var(--success);
        }
        
        .result-strengths h4 {
            color: var(--primary);
            margin-bottom: 10px;
        }
        
        .restart-btn {
            padding: 15px 35px;
            background: linear-gradient(135deg, var(--secondary), var(--accent));
            color: white;
            border: none;
            border-radius: 30px;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            margin: 10px;
        }
        
        .restart-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }
        
        .math-types-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .math-type-card {
            background: white;
            padding: 20px;
            border-radius: 12px;
            border: 2px solid var(--light);
            transition: all 0.3s ease;
        }
        
        .math-type-card:hover {
            border-color: var(--secondary);
            transform: translateY(-5px);
        }
        
        .math-type-card h4 {
            color: var(--primary);
            margin-bottom: 10px;
        }
        
        .url-display {
            background: var(--light);
            padding: 15px;
            border-radius: 10px;
            margin: 15px 0;
            word-break: break-all;
            font-family: monospace;
            border: 2px dashed var(--secondary);
        }
        
        @keyframes slideIn {
            from { 
                opacity: 0; 
                transform: translateY(30px) scale(0.95); 
            }
            to { 
                opacity: 1; 
                transform: translateY(0) scale(1); 
            }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .fade-in {
            animation: fadeIn 0.8s ease-in;
        }
        
        .hidden {
            display: none;
        }
        
        .footer {
            text-align: center;
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid var(--light);
            color: var(--dark);
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 25px 20px;
            }
            
            h1 {
                font-size: 2.2em;
            }
            
            .question {
                font-size: 1.2em;
            }
            
            .answer-btn {
                padding: 15px;
                font-size: 1em;
            }
            
            .math-decoration {
                font-size: 80px;
            }
            
            .math-types-grid {
                grid-template-columns: 1fr;
            }
            
            .share-btn {
                padding: 10px 20px;
                margin: 5px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Математические декорации -->
        <div class="math-decoration decoration-1">∫</div>
        <div class="math-decoration decoration-2">∑</div>
        <div class="math-decoration decoration-3">π</div>
        <div class="math-decoration decoration-4">∞</div>
        
        <!-- Стартовый экран -->
        <div id="start-screen" class="fade-in">
            <h1>Математический профиль</h1>
            <p class="subtitle">Определи свой уникальный стиль математического мышления</p>
            
            <div style="text-align: center; margin: 40px 0;">
                <div style="font-size: 4em; margin-bottom: 20px; color: var(--primary);">∫ ∑ π ∞</div>
                <p style="font-size: 1.2em; line-height: 1.7; margin-bottom: 30px; color: #555;">
                    Математика - это не только цифры и формулы, но и особый способ мышления. 
                    Пройди тест из 10 вопросов и узнай, какой математический профиль соответствует твоему стилю решения задач.
                </p>
                <button class="restart-btn" onclick="startTest()">Начать диагностику</button>
            </div>
            
            <div class="share-section">
                <h3 style="color: var(--primary); margin-bottom: 15px;">Поделись тестом с друзьями</h3>
                <button class="share-btn" onclick="shareTest()">
                    <span>📤</span> Поделиться
                </button>
                <button class="share-btn secondary" onclick="showLink()">
                    <span>🔗</span> Получить ссылку
                </button>
                
                <div id="link-section" class="hidden">
                    <div class="url-display" id="current-url">
                        https://math-profile-test.ru
                    </div>
                    <button class="share-btn" onclick="copyLink()">
                        <span>📋</span> Скопировать ссылку
                    </button>
                </div>
                
                <div id="copy-message" style="color: var(--success); margin-top: 10px; display: none;">
                    ✅ Ссылка скопирована в буфер обмена!
                </div>
            </div>
            
            <div class="math-types-grid">
                <div class="math-type-card">
                    <h4>🧠 Аналитик</h4>
                    <p>Любит глубокий анализ, доказательства и системный подход к решению задач</p>
                </div>
                <div class="math-type-card">
                    <h4>💡 Инноватор</h4>
                    <p>Находит нестандартные решения и творческие подходы к сложным проблемам</p>
                </div>
                <div class="math-type-card">
                    <h4>🔧 Практик</h4>
                    <p>Ценит реальное применение математики и полезные результаты</p>
                </div>
                <div class="math-type-card">
                    <h4>🔍 Исследователь</h4>
                    <p>Любопытство и желание понять суть математических явлений</p>
                </div>
            </div>
        </div>
        
        <!-- Контейнер теста -->
        <div id="test-container" class="hidden">
            <div class="progress-container">
                <div class="progress-text">Вопрос <span id="current-question">1</span> из 10</div>
                <div class="progress-bar">
                    <div class="progress-fill" id="progress-bar"></div>
                </div>
            </div>
            
            <!-- Вопрос 1 -->
            <div class="question-container active" id="question-1">
                <div class="question">Как ты подходишь к решению сложных математических задач?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(0, 0)">Составляю четкий план и следую ему шаг за шагом</button>
                    <button class="answer-btn" onclick="answerQuestion(0, 1)">Пробую разные подходы, пока не найду работающий</button>
                    <button class="answer-btn" onclick="answerQuestion(0, 2)">Ищу аналогичные примеры и изучаю готовые решения</button>
                    <button class="answer-btn" onclick="answerQuestion(0, 3)">Обдумываю задачу несколько дней, возвращаясь к ней</button>
                    <button class="answer-btn" onclick="answerQuestion(0, 4)">Сразу начинаю решать, действуя методом проб и ошибок</button>
                    <button class="answer-btn" onclick="answerQuestion(0, 5)">Стараюсь упростить задачу или разбить на более мелкие части</button>
                </div>
            </div>
            
            <!-- Вопрос 2 -->
            <div class="question-container" id="question-2">
                <div class="question">Что тебе больше всего нравится в математике?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(1, 0)">Точность, логическая строгость и ясность</button>
                    <button class="answer-btn" onclick="answerQuestion(1, 1)">Красота формул, симметрия и элегантность теорем</button>
                    <button class="answer-btn" onclick="answerQuestion(1, 2)">Практическое применение в реальной жизни</button>
                    <button class="answer-btn" onclick="answerQuestion(1, 3)">Головоломки, нестандартные и олимпиадные задачи</button>
                    <button class="answer-btn" onclick="answerQuestion(1, 4)">Программирование, алгоритмы и вычисления</button>
                    <button class="answer-btn" onclick="answerQuestion(1, 5)">Понимание того, как устроен мир через числа и закономерности</button>
                </div>
            </div>
            
            <!-- Вопрос 3 -->
            <div class="question-container" id="question-3">
                <div class="question">Как ты запоминаешь математические правила и формулы?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(2, 0)">Понимаю логику вывода и тогда запоминаю легко</button>
                    <button class="answer-btn" onclick="answerQuestion(2, 1)">Запоминаю через практические примеры и задачи</button>
                    <button class="answer-btn" onclick="answerQuestion(2, 2)">Создаю ассоциации и мнемонические правила</button>
                    <button class="answer-btn" onclick="answerQuestion(2, 3)">Повторяю несколько раз, пока не запомню</button>
                    <button class="answer-btn" onclick="answerQuestion(2, 4)">Использую шпаргалки и всегда держу под рукой</button>
                    <button class="answer-btn" onclick="answerQuestion(2, 5)">Запоминаю только то, что часто используется</button>
                </div>
            </div>
            
            <!-- Вопрос 4 -->
            <div class="question-container" id="question-4">
                <div class="question">Твоя первая реакция на новую математическую тему?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(3, 0)">Изучаю все внимательно с самого начала</button>
                    <button class="answer-btn" onclick="answerQuestion(3, 1)">Сразу пытаюсь решать задачи по этой теме</button>
                    <button class="answer-btn" onclick="answerQuestion(3, 2)">Ищу видеоуроки и наглядные материалы</button>
                    <button class="answer-btn" onclick="answerQuestion(3, 3)">Обсуждаю с друзьями или учителем</button>
                    <button class="answer-btn" onclick="answerQuestion(3, 4)">Пытаюсь связать с уже известными темами</button>
                    <button class="answer-btn" onclick="answerQuestion(3, 5)">Начинаю с простых примеров и постепенно усложняю</button>
                </div>
            </div>
            
            <!-- Вопрос 5 -->
            <div class="question-container" id="question-5">
                <div class="question">Какой тип математических задач тебе интереснее?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(4, 0)">Олимпиадные задачи с хитрыми решениями</button>
                    <button class="answer-btn" onclick="answerQuestion(4, 1)">Практические задачи из реальной жизни</button>
                    <button class="answer-btn" onclick="answerQuestion(4, 2)">Задачи на программирование и алгоритмы</button>
                    <button class="answer-btn" onclick="answerQuestion(4, 3)">Геометрические задачи с чертежами</button>
                    <button class="answer-btn" onclick="answerQuestion(4, 4)">Статистические задачи и анализ данных</button>
                    <button class="answer-btn" onclick="answerQuestion(4, 5)">Логические задачи и головоломки</button>
                </div>
            </div>
            
            <!-- Вопрос 6 -->
            <div class="question-container" id="question-6">
                <div class="question">Как ты проверяешь правильность своего решения?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(5, 0)">Перерешиваю задачу другим способом</button>
                    <button class="answer-btn" onclick="answerQuestion(5, 1)">Проверяю по эталонному решению</button>
                    <button class="answer-btn" onclick="answerQuestion(5, 2)">Ищу аналогичные решенные примеры</button>
                    <button class="answer-btn" onclick="answerQuestion(5, 3)">Использую специальные программы или калькулятор</button>
                    <button class="answer-btn" onclick="answerQuestion(5, 4)">Обсуждаю решение с другими</button>
                    <button class="answer-btn" onclick="answerQuestion(5, 5)">Проверяю, логично ли выглядит ответ</button>
                </div>
            </div>
            
            <!-- Вопрос 7 -->
            <div class="question-container" id="question-7">
                <div class="question">Что помогает тебе лучше понять математическую концепцию?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(6, 0)">Наглядные графики и диаграммы</button>
                    <button class="answer-btn" onclick="answerQuestion(6, 1)">Подробные текстовые объяснения</button>
                    <button class="answer-btn" onclick="answerQuestion(6, 2)">Практические эксперименты и опыты</button>
                    <button class="answer-btn" onclick="answerQuestion(6, 3)">Обсуждения и групповые занятия</button>
                    <button class="answer-btn" onclick="answerQuestion(6, 4)">Онлайн-курсы и интерактивные платформы</button>
                    <button class="answer-btn" onclick="answerQuestion(6, 5)">Реальные примеры из жизни</button>
                </div>
            </div>
            
            <!-- Вопрос 8 -->
            <div class="question-container" id="question-8">
                <div class="question">Как ты применяешь математику в повседневной жизни?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(7, 0)">Рассчитываю бюджет и финансовые операции</button>
                    <button class="answer-btn" onclick="answerQuestion(7, 1)">Планирую время и составляю расписания</button>
                    <button class="answer-btn" onclick="answerQuestion(7, 2)">Решаю бытовые технические задачи</button>
                    <button class="answer-btn" onclick="answerQuestion(7, 3)">Анализирую данные для хобби и увлечений</button>
                    <button class="answer-btn" onclick="answerQuestion(7, 4)">Разрабатываю алгоритмы для компьютерных игр</button>
                    <button class="answer-btn" onclick="answerQuestion(7, 5)">Использую для принятия бытовых решений</button>
                </div>
            </div>
            
            <!-- Вопрос 9 -->
            <div class="question-container" id="question-9">
                <div class="question">Как ты относишься к математическим ошибкам?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(8, 0)">Анализирую их, чтобы понять, где ошибаюсь</button>
                    <button class="answer-btn" onclick="answerQuestion(8, 1)">Воспринимаю как возможность научиться чему-то новому</button>
                    <button class="answer-btn" onclick="answerQuestion(8, 2)">Стараюсь сразу найти и исправить</button>
                    <button class="answer-btn" onclick="answerQuestion(8, 3)">Использую их для поиска альтернативных путей</button>
                    <button class="answer-btn" onclick="answerQuestion(8, 4)">Не расстраиваюсь - все учатся на ошибках</button>
                    <button class="answer-btn" onclick="answerQuestion(8, 5)">Обращаюсь за помощью, чтобы разобраться</button>
                </div>
            </div>
            
            <!-- Вопрос 10 -->
            <div class="question-container" id="question-10">
                <div class="question">Что для тебя значит "понять" математическую концепцию?</div>
                <div class="answers">
                    <button class="answer-btn" onclick="answerQuestion(9, 0)">Уметь доказать теорему или вывести формулу</button>
                    <button class="answer-btn" onclick="answerQuestion(9, 1)">Видеть красоту и логику в этой концепции</button>
                    <button class="answer-btn" onclick="answerQuestion(9, 2)">Применять ее для решения практических задач</button>
                    <button class="answer-btn" onclick="answerQuestion(9, 3)">Объяснить ее кому-то другому</button>
                    <button class="answer-btn" onclick="answerQuestion(9, 4)">Связать с другими известными концепциями</button>
                    <button class="answer-btn" onclick="answerQuestion(9, 5)">Найти ей аналогию в реальном мире</button>
                </div>
            </div>
        </div>
        
        <!-- Результаты -->
        <div class="result hidden" id="result">
            <div class="result-card">
                <div class="result-type" id="result-type">Аналитик</div>
                <div class="result-score" id="result-score">Баллов: 0 из 60</div>
                <div class="result-description" id="result-description">
                    Описание твоего математического профиля...
                </div>
                <div class="result-strengths">
                    <h4>Сильные стороны:</h4>
                    <div id="result-strengths">...</div>
                </div>
            </div>
            
            <button class="restart-btn" onclick="restartTest()">Пройти тест еще раз</button>
            <button class="share-btn secondary" onclick="shareResults()">
                <span>📤</span> Поделиться результатом
            </button>
            
            <div class="share-section" style="margin-top: 30px;">
                <h3>Понравился тест?</h3>
                <p style="margin-bottom: 15px; color: #555;">Отправь ссылку друзьям и узнай, какие у них математические профили!</p>
                <button class="share-btn" onclick="shareTest()">
                    <span>📤</span> Поделиться тестом
                </button>
                <button class="share-btn secondary" onclick="showLink()">
                    <span>🔗</span> Получить ссылку
                </button>
                
                <div id="result-link-section" class="hidden">
                    <div class="url-display" id="result-current-url">
                        https://math-profile-test.ru
                    </div>
                    <button class="share-btn" onclick="copyLink()">
                        <span>📋</span> Скопировать ссылку
                    </button>
                </div>
            </div>
        </div>
        
        <div class="footer">
            <p>© 2024 Математический профиль | Тест для определения стиля математического мышления</p>
        </div>
    </div>

    <script>
        let currentQuestion = 0;
        let score = 0;
        const totalQuestions = 10;
        
        // Баллы за ответы для 10 вопросов по 6 вариантов
        const points = [
            [5, 4, 3, 4, 3, 4], // Вопрос 1
            [5, 4, 3, 5, 4, 3], // Вопрос 2
            [5, 3, 4, 3, 2, 4], // Вопрос 3
            [4, 4, 3, 3, 5, 3], // Вопрос 4
            [5, 3, 4, 4, 3, 4], // Вопрос 5
            [5, 3, 3, 2, 3, 4], // Вопрос 6
            [3, 4, 3, 3, 4, 3], // Вопрос 7
            [3, 3, 4, 4, 4, 3], // Вопрос 8
            [4, 5, 3, 4, 3, 3], // Вопрос 9
            [5, 4, 3, 4, 4, 3]  // Вопрос 10
        ];
        
        // Получаем текущий URL для sharing
        const currentUrl = window.location.href;
        
        function startTest() {
            document.getElementById('start-screen').classList.add('hidden');
            document.getElementById('test-container').classList.remove('hidden');
            updateProgress();
        }
        
        function answerQuestion(questionIndex, answerIndex) {
            score += points[questionIndex][answerIndex];
            currentQuestion++;
            
            if (currentQuestion < totalQuestions) {
                showQuestion(currentQuestion);
                updateProgress();
            } else {
                showResults();
            }
        }
        
        function showQuestion(questionNum) {
            document.querySelectorAll('.question-container').forEach(container => {
                container.classList.remove('active');
            });
            document.getElementById(`question-${questionNum + 1}`).classList.add('active');
        }
        
        function updateProgress() {
            const progress = ((currentQuestion) / totalQuestions) * 100;
            document.getElementById('progress-bar').style.width = `${progress}%`;
            document.getElementById('current-question').textContent = currentQuestion + 1;
        }
        
        function showResults() {
            document.getElementById('test-container').classList.add('hidden');
            const resultDiv = document.getElementById('result');
            resultDiv.classList.remove('hidden');
            
            let mathType, description, strengths;
            
            if (score >= 45) {
                mathType = "Математический Аналитик";
                description = "Ты обладаешь глубоким аналитическим мышлением и системным подходом к решению задач. Тебе нравится разбираться в фундаментальных принципах, доказывать теоремы и выстраивать логические цепочки. Твоя сила - в тщательности и внимании к деталям. Ты мог бы стать отличным исследователем, ученым или аналитиком.";
                strengths = "Логическое мышление, системный подход, внимание к деталям, способность к глубокому анализу, математическая строгость, терпение в решении сложных задач";
            } else if (score >= 38) {
                mathType = "Творческий Инноватор";
                description = "Твой ум гибок и изобретателен! Ты находишь нестандартные подходы к решению задач и видишь математику как пространство для творчества. Олимпиадные задачи и головоломки - твоя стихия, где ты можешь проявить креативность и оригинальность мышления. Такой тип мышления ценен в разработке алгоритмов и решении сложных инженерных задач.";
                strengths = "Креативность, гибкость мышления, нестандартный подход, умение видеть закономерности, изобретательность, адаптивность";
            } else if (score >= 32) {
                mathType = "Практик-Прикладник";
                description = "Ты ценишь практическое применение математики и видишь ее ценность в реальном мире. Тебе интересно, как математические методы работают в технологиях, финансах, инженерии и других областях. Ты хорошо видишь связь между теорией и практикой. Этот подход делает тебя отличным кандидатом для работы в IT, аналитике или прикладных науках.";
                strengths = "Практическое мышление, умение применять знания, решение реальных задач, техническая грамотность, результативность, ориентированность на применение";
            } else if (score >= 26) {
                mathType = "Любознательный Исследователь";
                description = "Твое главное качество - любопытство и желание понять суть вещей. Ты любишь исследовать новые математические концепции, задавать вопросы и находить связи между разными областями знаний. Для тебя математика - это увлекательное путешествие в мир открытий. Такой подход ценен в науке, образовании и междисциплинарных исследованиях.";
                strengths = "Любознательность, исследовательский подход, умение задавать вопросы, поиск связей, стремление к пониманию, открытость новому";
            } else {
                mathType = "Перспективный Мыслитель";
                description = "Твой математический потенциал только начинает раскрываться! Ты обладаешь ценным качеством - готовностью учиться и развиваться. Сейчас тебе может быть непросто, но именно такой подход - медленное, но уверенное освоение материала - часто приводит к deepest пониманию. Твоя сила в упорстве и способности видеть математику в повседневной жизни. Продолжай в том же духе!";
                strengths = "Упорство, готовность учиться, практическая ориентация, наблюдательность, способность видеть математику в жизни, терпение, настойчивость";
            }
            
            document.getElementById('result-type').textContent = mathType;
            document.getElementById('result-score').textContent = `Баллов: ${score} из 60`;
            document.getElementById('result-description').textContent = description;
            document.getElementById('result-strengths').textContent = strengths;
            
            // Обновляем URL в разделе результатов
            document.getElementById('result-current-url').textContent = currentUrl;
        }
        
        function restartTest() {
            currentQuestion = 0;
            score = 0;
            document.getElementById('result').classList.add('hidden');
            document.getElementById('start-screen').classList.remove('hidden');
            updateProgress();
        }
        
        function showLink() {
            document.getElementById('link-section').classList.remove('hidden');
            document.getElementById('current-url').textContent = currentUrl;
        }
        
        function shareTest() {
            const shareText = 'Пройди тест "Математический профиль" и узнай свой стиль мышления!';
            
            if (navigator.share) {
                navigator.share({
                    title: 'Математический профиль',
                    text: shareText,
                    url: currentUrl
                });
            } else {
                showLink();
            }
        }
        
        function shareResults() {
            const mathType = document.getElementById('result-type').textContent;
            const shareText = `Мой математический профиль: ${mathType}. Пройди тест и узнай свой!`;
            
            if (navigator.share) {
                navigator.share({
                    title: 'Мой математический профиль',
                    text: shareText,
                    url: currentUrl
                });
            } else {
                document.getElementById('result-link-section').classList.remove('hidden');
                navigator.clipboard.writeText(`${shareText} ${currentUrl}`);
                showCopyMessage();
            }
        }
        
        function copyLink() {
            navigator.clipboard.writeText(currentUrl).then(() => {
                showCopyMessage();
            });
        }
        
        function showCopyMessage() {
            const message = document.getElementById('copy-message');
            message.style.display = 'block';
            setTimeout(() => {
                message.style.display = 'none';
            }, 3000);
        }
        
        // Инициализация при загрузке
        window.addEventListener('load', function() {
            document.getElementById('current-url').textContent = currentUrl;
            document.getElementById('result-current-url').textContent = currentUrl;
            updateProgress();
        });
    </script>
</body>
</html>
