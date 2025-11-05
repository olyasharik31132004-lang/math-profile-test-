<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Математический профиль | Тест на стиль мышления</title>
    <meta name="description" content="Определи свой математический профиль. Узнай, как твой ум обрабатывает цифры и логику">
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Source+Sans+Pro:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --emerald-dark: #0d3b2e;
            --emerald-medium: #1a6b53;
            --emerald-light: #27ae60;
            --emerald-bright: #2ecc71;
            --emerald-pale: #ecf8f3;
            --gold: #d4af37;
            --silver: #bdc3c7;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Source Sans Pro', sans-serif;
            background: linear-gradient(135deg, var(--emerald-pale) 0%, #ffffff 100%);
            min-height: 100vh;
            padding: 20px;
            line-height: 1.7;
            color: var(--emerald-dark);
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 12px;
            padding: 50px 40px;
            box-shadow: 0 10px 30px rgba(13, 59, 46, 0.1);
            position: relative;
            overflow: hidden;
            border: 1px solid var(--emerald-pale);
        }
        
        .container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--emerald-medium), var(--emerald-light));
        }
        
        .math-symbol {
            position: absolute;
            font-size: 80px;
            opacity: 0.03;
            color: var(--emerald-dark);
            font-weight: bold;
            z-index: 0;
        }
        
        .symbol-1 { top: 30px; right: 40px; content: '∫'; }
        .symbol-2 { bottom: 60px; left: 50px; content: '∑'; }
        .symbol-3 { top: 180px; left: 60px; content: 'π'; }
        .symbol-4 { bottom: 120px; right: 70px; content: '∞'; }
        
        h1 {
            font-family: 'Playfair Display', serif;
            text-align: center;
            color: var(--emerald-dark);
            margin-bottom: 20px;
            font-size: 2.8em;
            font-weight: 700;
            position: relative;
            z-index: 1;
            letter-spacing: -0.5px;
        }
        
        .subtitle {
            text-align: center;
            color: var(--emerald-medium);
            margin-bottom: 50px;
            font-size: 1.3em;
            font-weight: 300;
            position: relative;
            z-index: 1;
            font-style: italic;
        }
        
        .hero-section {
            text-align: center;
            margin: 50px 0;
            position: relative;
            z-index: 1;
        }
        
        .math-icon {
            font-size: 4em;
            margin-bottom: 30px;
            color: var(--emerald-medium);
            opacity: 0.8;
        }
        
        .intro-text {
            font-size: 1.2em;
            line-height: 1.8;
            margin-bottom: 40px;
            color: var(--emerald-dark);
            text-align: center;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .start-btn {
            padding: 18px 45px;
            background: var(--emerald-medium);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.2em;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            margin: 30px 0;
            position: relative;
            overflow: hidden;
            letter-spacing: 0.5px;
        }
        
        .start-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }
        
        .start-btn:hover {
            background: var(--emerald-light);
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(39, 174, 96, 0.3);
        }
        
        .start-btn:hover::before {
            left: 100%;
        }
        
        .facts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin: 50px 0;
        }
        
        .fact-card {
            background: var(--emerald-pale);
            padding: 25px;
            border-radius: 8px;
            border-left: 4px solid var(--emerald-light);
            transition: transform 0.3s ease;
        }
        
        .fact-card:hover {
            transform: translateY(-5px);
        }
        
        .fact-card h3 {
            color: var(--emerald-dark);
            margin-bottom: 15px;
            font-family: 'Playfair Display', serif;
            font-size: 1.3em;
        }
        
        .quote-section {
            background: linear-gradient(135deg, var(--emerald-medium), var(--emerald-light));
            color: white;
            padding: 40px;
            border-radius: 8px;
            margin: 40px 0;
            text-align: center;
            position: relative;
        }
        
        .quote-section::before {
            content: '"';
            font-size: 80px;
            position: absolute;
            top: 10px;
            left: 30px;
            opacity: 0.2;
            font-family: 'Playfair Display', serif;
        }
        
        .quote-text {
            font-size: 1.3em;
            font-style: italic;
            margin-bottom: 20px;
            line-height: 1.6;
        }
        
        .quote-author {
            font-weight: 600;
            opacity: 0.9;
        }
        
        /* Стили для теста */
        .test-section {
            display: none;
            position: relative;
            z-index: 1;
        }
        
        .progress-container {
            margin-bottom: 40px;
        }
        
        .progress-text {
            text-align: center;
            color: var(--emerald-medium);
            margin-bottom: 15px;
            font-size: 1em;
            font-weight: 600;
            letter-spacing: 0.5px;
        }
        
        .progress-bar {
            width: 100%;
            height: 6px;
            background: var(--emerald-pale);
            border-radius: 3px;
            overflow: hidden;
            position: relative;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--emerald-medium), var(--emerald-light));
            width: 0%;
            transition: width 0.5s ease;
        }
        
        .question-container {
            display: none;
        }
        
        .question-container.active {
            display: block;
            animation: fadeSlide 0.6s ease-out;
        }
        
        .question {
            font-size: 1.4em;
            color: var(--emerald-dark);
            margin-bottom: 35px;
            text-align: center;
            font-weight: 600;
            font-family: 'Playfair Display', serif;
            line-height: 1.5;
        }
        
        .answers {
            display: grid;
            gap: 12px;
            margin-bottom: 40px;
        }
        
        .answer-btn {
            padding: 20px;
            border: 2px solid #e8f5e8;
            border-radius: 8px;
            background: white;
            font-size: 1.05em;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: left;
            color: var(--emerald-dark);
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
            background: var(--emerald-pale);
            transition: width 0.3s ease;
            z-index: -1;
        }
        
        .answer-btn:hover {
            border-color: var(--emerald-light);
            transform: translateX(8px);
        }
        
        .answer-btn:hover::before {
            width: 100%;
        }
        
        .result-section {
            display: none;
            text-align: center;
            position: relative;
            z-index: 1;
        }
        
        .result-card {
            background: white;
            border-radius: 12px;
            padding: 40px;
            box-shadow: 0 8px 25px rgba(13, 59, 46, 0.1);
            margin-bottom: 30px;
            border: 1px solid var(--emerald-pale);
        }
        
        .result-type {
            font-size: 2em;
            color: var(--emerald-dark);
            margin-bottom: 20px;
            font-weight: 700;
            font-family: 'Playfair Display', serif;
        }
        
        .result-score {
            font-size: 1.1em;
            color: var(--emerald-medium);
            margin-bottom: 25px;
            padding: 10px 25px;
            background: var(--emerald-pale);
            border-radius: 20px;
            display: inline-block;
            font-weight: 600;
        }
        
        .result-description {
            font-size: 1.1em;
            line-height: 1.7;
            color: var(--emerald-dark);
            margin-bottom: 25px;
            text-align: left;
        }
        
        .result-strengths {
            text-align: left;
            margin: 30px 0;
            padding: 25px;
            background: var(--emerald-pale);
            border-radius: 8px;
            border-left: 4px solid var(--emerald-light);
        }
        
        .result-strengths h4 {
            color: var(--emerald-dark);
            margin-bottom: 15px;
            font-family: 'Playfair Display', serif;
            font-size: 1.2em;
        }
        
        .restart-btn {
            padding: 15px 35px;
            background: var(--emerald-medium);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            margin: 20px 0;
        }
        
        .restart-btn:hover {
            background: var(--emerald-light);
            transform: translateY(-2px);
        }
        
        .footer {
            text-align: center;
            margin-top: 50px;
            padding-top: 30px;
            border-top: 1px solid var(--emerald-pale);
            color: var(--emerald-medium);
            font-size: 0.9em;
        }
        
        @keyframes fadeSlide {
            from { 
                opacity: 0; 
                transform: translateY(20px); 
            }
            to { 
                opacity: 1; 
                transform: translateY(0); 
            }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .fade-in {
            animation: fadeIn 0.8s ease-in;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 30px 20px;
            }
            
            h1 {
                font-size: 2.2em;
            }
            
            .question {
                font-size: 1.2em;
            }
            
            .answer-btn {
                padding: 16px;
                font-size: 1em;
            }
            
            .math-symbol {
                font-size: 60px;
            }
            
            .facts-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Математические символы как фон -->
        <div class="math-symbol symbol-1">∫</div>
        <div class="math-symbol symbol-2">∑</div>
        <div class="math-symbol symbol-3">π</div>
        <div class="math-symbol symbol-4">∞</div>
        
        <!-- Главная страница -->
        <div id="main-page" class="fade-in">
            <h1>Математический профиль</h1>
            <p class="subtitle">Раскрой уникальные особенности своего мышления</p>
            
            <div class="hero-section">
                <div class="math-icon">∫∑</div>
                <p class="intro-text">
                    Математика — это не просто цифры и формулы. Это язык, на котором говорит Вселенная, 
                    инструмент для понимания закономерностей и способ развития критического мышления. 
                    Узнай, как именно твой ум обрабатывает информацию и решает задачи.
                </p>
                
                <button class="start-btn" onclick="startTest()">Начать диагностику</button>
            </div>
            
            <div class="facts-grid">
                <div class="fact-card">
                    <h3>Математика и мозг</h3>
                    <p>Исследования показывают, что решение математических задач активирует те же области мозга, что и творческие процессы. Математическое мышление развивает нейропластичность.</p>
                </div>
                <div class="fact-card">
                    <h3>История чисел</h3>
                    <p>Первобытные люди использовали счёт до 3, всё что больше обозначали словом "много". Современная десятичная система пришла из Индии через арабские страны.</p>
                </div>
                <div class="fact-card">
                    <h3>Золотое сечение</h3>
                    <p>Число φ (фи) ≈ 1.618 встречается в природе, искусстве и архитектуре. От расположения семян подсолнуха до пропорций Парфенона — везде прослеживается эта закономерность.</p>
                </div>
            </div>
            
            <div class="quote-section">
                <p class="quote-text">
                    Математика выявляет порядок, симметрию и определённость, а это — важнейшие виды прекрасного.
                </p>
                <p class="quote-author">— Аристотель</p>
            </div>
            
            <div class="facts-grid">
                <div class="fact-card">
                    <h3>Ноль — великое открытие</h3>
                    <p>Концепция нуля как числа появилась в Индии в V веке. Без нуля не было бы современной математики, компьютеров и большей части технологий.</p>
                </div>
                <div class="fact-card">
                    <h3>Математика в природе</h3>
                    <p>Спирали Фибоначчи, фракталы, геометрические формы — математические принципы лежат в основе природных явлений от роста растений до формирования галактик.</p>
                </div>
                <div class="fact-card">
                    <h3>Язык Вселенной</h3>
                    <p>Галилей говорил, что математика — это язык, на котором написана книга природы. Современная физика подтверждает это: все фундаментальные законы выражаются математически.</p>
                </div>
            </div>
            
            <div class="quote-section">
                <p class="quote-text">
                    Чистая математика является, в своём роде, поэзией логической идеи.
                </p>
                <p class="quote-author">— Альберт Эйнштейн</p>
            </div>
        </div>
        
        <!-- Раздел теста -->
        <div id="test-section" class="test-section">
            <div class="progress-container">
                <div class="progress-text">Вопрос <span id="current-question">1</span> из 10</div>
                <div class="progress-bar">
                    <div class="progress-fill" id="progress-bar"></div>
                </div>
            </div>
            
            <!-- Вопросы теста -->
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
            
            <div class="question-container" id="question-10">
                <div class="question">Что для тебя значит "понять" математическую концепцию?</div>
                <div class="
