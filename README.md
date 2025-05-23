
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Electromagnetismo Interactivo</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #fff;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .section {
            display: none;
            animation: fadeIn 0.5s ease-in;
        }

        .section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Header */
        .header {
            text-align: center;
            margin-bottom: 2rem;
        }

        .logo {
            font-size: 2.5rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            background: linear-gradient(45deg, #ffd700, #ffeb3b);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 1rem;
        }

        .author {
            font-size: 0.9rem;
            opacity: 0.7;
            margin-top: 1rem;
        }

        /* Navigation */
        .nav-buttons {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin: 2rem 0;
        }

        .nav-btn {
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 15px;
            padding: 2rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            position: relative;
            overflow: hidden;
        }

        .nav-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transition: left 0.5s;
        }

        .nav-btn:hover::before {
            left: 100%;
        }

        .nav-btn:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.2);
            border-color: rgba(255, 255, 255, 0.4);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
        }

        .nav-btn-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .nav-btn-title {
            font-size: 1.3rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .nav-btn-desc {
            opacity: 0.8;
            font-size: 0.9rem;
        }

        /* Back button */
        .back-btn {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 25px;
            padding: 10px 20px;
            color: #fff;
            cursor: pointer;
            margin-bottom: 2rem;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            transition: all 0.3s ease;
        }

        .back-btn:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateX(-5px);
        }

        /* Quiz Section */
        .quiz-container {
            max-width: 800px;
            margin: 0 auto;
        }

        .question-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2rem;
            margin-bottom: 2rem;
            backdrop-filter: blur(10px);
        }

        .question {
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            font-weight: 500;
        }

        .options {
            display: grid;
            gap: 1rem;
        }

        .option {
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            padding: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }

        .option:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateX(5px);
        }

        .option.correct {
            background: rgba(76, 175, 80, 0.3);
            border-color: #4caf50;
        }

        .option.incorrect {
            background: rgba(244, 67, 54, 0.3);
            border-color: #f44336;
        }

        .score {
            text-align: center;
            font-size: 1.5rem;
            margin: 2rem 0;
            padding: 1rem;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            backdrop-filter: blur(10px);
        }

        /* Concepts Section */
        .concepts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .concept-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2rem;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            cursor: pointer;
            border: 2px solid rgba(255, 255, 255, 0.1);
        }

        .concept-card:hover {
            transform: translateY(-10px);
            background: rgba(255, 255, 255, 0.15);
            border-color: rgba(255, 255, 255, 0.3);
        }

        .concept-title {
            font-size: 1.4rem;
            font-weight: bold;
            margin-bottom: 1rem;
            color: #ffd700;
        }

        .concept-desc {
            line-height: 1.6;
            opacity: 0.9;
        }

        /* Game Section - Eddy Brake */
        .game-container {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
        }

        .game-canvas {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            margin: 2rem 0;
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.2);
            height: 400px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .brake-system {
            position: relative;
            width: 300px;
            height: 300px;
        }

        .disc {
            width: 180px;
            height: 180px;
            background: linear-gradient(135deg, #888, #bbb, #888);
            border-radius: 50%;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            border: 4px solid #666;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
        }

        .disc::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 20px;
            height: 20px;
            background: #333;
            border-radius: 50%;
            transform: translate(-50%, -50%);
        }

        .disc::after {
            content: '';
            position: absolute;
            top: 20px;
            left: 50%;
            width: 3px;
            height: 30px;
            background: #ff4444;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        .disc.spinning {
            animation: spin linear infinite;
        }

        @keyframes spin {
            from { transform: translate(-50%, -50%) rotate(0deg); }
            to { transform: translate(-50%, -50%) rotate(360deg); }
        }

        .magnet {
            width: 60px;
            height: 100px;
            background: linear-gradient(to bottom, #ff4444, #ffffff, #4444ff);
            border-radius: 10px;
            position: absolute;
            cursor: move;
            border: 2px solid #333;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            padding: 5px;
            font-size: 12px;
            font-weight: bold;
            color: #000;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
        }

        .magnet::before {
            content: 'N';
            color: white;
            text-shadow: 1px 1px 2px #000;
        }

        .magnet::after {
            content: 'S';
            color: white;
            text-shadow: 1px 1px 2px #000;
        }

        .magnet:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
        }

        .coil {
            width: 80px;
            height: 60px;
            position: absolute;
            cursor: move;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }

        .coil:hover {
            transform: scale(1.05);
        }

        .coil-wire {
            width: 70px;
            height: 50px;
            border: 4px solid #ffd700;
            border-radius: 50%;
            position: absolute;
        }

        .coil-wire:nth-child(1) { transform: scale(1); }
        .coil-wire:nth-child(2) { transform: scale(0.8); }
        .coil-wire:nth-child(3) { transform: scale(0.6); }

        .coil.active .coil-wire {
            border-color: #00ff88;
            box-shadow: 0 0 15px #00ff88;
            animation: coil-pulse 0.5s ease-in-out;
        }

        @keyframes coil-pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .eddy-currents {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .eddy-current {
            position: absolute;
            width: 40px;
            height: 40px;
            border: 2px solid #00ffff;
            border-radius: 50%;
            animation: eddy-flow 2s linear infinite;
        }

        .eddy-currents.active {
            opacity: 0.8;
        }

        @keyframes eddy-flow {
            0% { transform: rotate(0deg) scale(0.5); opacity: 1; }
            50% { transform: rotate(180deg) scale(1); opacity: 0.7; }
            100% { transform: rotate(360deg) scale(0.5); opacity: 1; }
        }

        .controls {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin: 2rem 0;
            flex-wrap: wrap;
        }

        .control-btn {
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.3);
            border-radius: 25px;
            padding: 12px 24px;
            color: #fff;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1rem;
        }

        .control-btn:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        .control-btn.active {
            background: rgba(76, 175, 80, 0.3);
            border-color: #4caf50;
        }

        .game-info {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 1.5rem;
            margin-top: 2rem;
            backdrop-filter: blur(10px);
        }

        .status-panel {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin: 1rem 0;
        }

        .status-item {
            background: rgba(255, 255, 255, 0.1);
            padding: 1rem;
            border-radius: 10px;
            text-align: center;
        }

        .status-value {
            font-size: 1.5rem;
            font-weight: bold;
            color: #ffd700;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .container {
                padding: 15px;
            }

            .logo {
                font-size: 2rem;
            }

            .nav-buttons {
                grid-template-columns: 1fr;
                gap: 1rem;
            }

            .nav-btn {
                padding: 1.5rem;
            }

            .nav-btn-icon {
                font-size: 2.5rem;
            }

            .controls {
                flex-direction: column;
                align-items: center;
            }

            .control-btn {
                width: 100%;
                max-width: 200px;
            }

            .brake-system {
                width: 250px;
                height: 250px;
            }

            .disc {
                width: 150px;
                height: 150px;
            }
        }

        @media (max-width: 480px) {
            .concepts-grid {
                grid-template-columns: 1fr;
            }

            .question {
                font-size: 1.1rem;
            }

            .game-canvas {
                height: 350px;
            }

            .brake-system {
                width: 200px;
                height: 200px;
            }

            .disc {
                width: 120px;
                height: 120px;
            }

            .magnet {
                width: 50px;
                height: 80px;
            }

            .coil {
                width: 60px;
                height: 45px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Home Section -->
        <section id="home" class="section active">
            <div class="header">
                <div class="logo">⚡ Electromagnetismo</div>
                <div class="subtitle">Hola Amigo Curioso</div>
                <div class="subtitle">Explora el fascinante mundo del electromagnetismo</div>
                <div class="author">
                    Autor: Ángel Antonio Ruiz García<br>
                    Facultad de Ingeniería
                </div>
            </div>

            <div class="nav-buttons">
                <div class="nav-btn" onclick="showSection('quiz')">
                    <div class="nav-btn-icon">🧠</div>
                    <div class="nav-btn-title">Quiz</div>
                    <div class="nav-btn-desc">Pon a prueba tus conocimientos</div>
                </div>

                <div class="nav-btn" onclick="showSection('concepts')">
                    <div class="nav-btn-icon">📚</div>
                    <div class="nav-btn-title">Conceptos</div>
                    <div class="nav-btn-desc">Aprende los fundamentos</div>
                </div>

                <div class="nav-btn" onclick="showSection('game')">
                    <div class="nav-btn-icon">🎮</div>
                    <div class="nav-btn-title">Freno de Eddy</div>
                    <div class="nav-btn-desc">Experimenta con corrientes parásitas</div>
                </div>
            </div>
        </section>

        <!-- Quiz Section -->
        <section id="quiz" class="section">
            <button class="back-btn" onclick="showSection('home')">
                ← Regresar al menú
            </button>

            <div class="header">
                <div class="logo">🧠 Quiz de Electromagnetismo</div>
            </div>

            <div class="quiz-container">
                <div id="quiz-content"></div>
                <div id="quiz-score" class="score" style="display: none;"></div>
                <div class="controls">
                    <button class="control-btn" onclick="restartQuiz()">Reiniciar Quiz</button>
                </div>
            </div>
        </section>

        <!-- Concepts Section -->
        <section id="concepts" class="section">
            <button class="back-btn" onclick="showSection('home')">
                ← Regresar al menú
            </button>

            <div class="header">
                <div class="logo">📚 Conceptos Fundamentales</div>
            </div>

            <div class="concepts-grid">
                <div class="concept-card">
                    <div class="concept-title">Campo Magnético</div>
                    <div class="concept-desc">
                        Es una región del espacio donde se manifiestan fuerzas magnéticas. Se representa mediante líneas de campo que van del polo norte al polo sur de un imán.
                    </div>
                </div>

                <div class="concept-card">
                    <div class="concept-title">Inducción Electromagnética</div>
                    <div class="concept-desc">
                        Fenómeno por el cual se genera una corriente eléctrica en un conductor cuando este se mueve a través de un campo magnético variable.
                    </div>
                </div>

                <div class="concept-card">
                    <div class="concept-title">Corrientes de Eddy</div>
                    <div class="concept-desc">
                        Corrientes eléctricas circulares inducidas en conductores cuando están expuestos a campos magnéticos cambiantes. Estas corrientes crean campos magnéticos opuestos que generan una fuerza de frenado.
                    </div>
                </div>

                <div class="concept-card">
                    <div class="concept-title">Freno de Eddy</div>
                    <div class="concept-desc">
                        Sistema de frenado que utiliza corrientes de Eddy para crear una fuerza de oposición al movimiento, sin contacto físico, comúnmente usado en trenes de alta velocidad.
                    </div>
                </div>

                <div class="concept-card">
                    <div class="concept-title">Ley de Lenz</div>
                    <div class="concept-desc">
                        La corriente inducida fluye en una dirección tal que su campo magnético se opone al cambio en el flujo magnético que la produce.
                    </div>
                </div>

                <div class="concept-card">
                    <div class="concept-title">Fuerza de Lorentz</div>
                    <div class="concept-desc">
                        Fuerza que experimenta una partícula cargada en movimiento cuando se encuentra en presencia de campos eléctricos y magnéticos.
                    </div>
                </div>
            </div>
        </section>

        <!-- Game Section -->
        <section id="game" class="section">
            <button class="back-btn" onclick="showSection('home')">
                ← Regresar al menú
            </button>

            <div class="header">
                <div class="logo">🎮 Freno de Eddy Interactivo</div>
                <div class="subtitle">Arrastra el imán o la bobina cerca del disco para ver el efecto de frenado</div>
            </div>

            <div class="game-container">
                <div class="game-canvas" id="gameCanvas">
                    <div class="brake-system">
                        <div class="disc" id="disc"></div>
                        
                        <div class="magnet" id="magnet" style="top: 50px; left: 50px;"></div>
                        
                        <div class="coil" id="coil" style="top: 200px; right: 50px;">
                            <div class="coil-wire"></div>
                            <div class="coil-wire"></div>
                            <div class="coil-wire"></div>
                        </div>

                        <div class="eddy-currents" id="eddyCurrents">
                            <div class="eddy-current" style="top: 30%; left: 30%;"></div>
                            <div class="eddy-current" style="top: 30%; right: 30%;"></div>
                            <div class="eddy-current" style="bottom: 30%; left: 30%;"></div>
                            <div class="eddy-current" style="bottom: 30%; right: 30%;"></div>
                        </div>
                    </div>
                </div>

                <div class="status-panel">
                    <div class="status-item">
                        <div>Velocidad del Disco</div>
                        <div class="status-value" id="discSpeed">0%</div>
                    </div>
                    <div class="status-item">
                        <div>Fuerza de Frenado</div>
                        <div class="status-value" id="brakingForce">0%</div>
                    </div>
                    <div class="status-item">
                        <div>Corrientes de Eddy</div>
                        <div class="status-value" id="eddyIntensity">Inactivas</div>
                    </div>
                </div>

                <div class="controls">
                    <button class="control-btn" id="spinBtn" onclick="toggleSpin()">Iniciar Giro</button>
                    <button class="control-btn" onclick="toggleCoilCurrent()">Activar/Desactivar Bobina</button>
                    <button class="control-btn" onclick="showEddyCurrents()">Ver Corrientes de Eddy</button>
                    <button class="control-btn" onclick="resetGame()">Reiniciar</button>
                </div>

                <div class="game-info">
                    <h3>¿Cómo funciona el Freno de Eddy?</h3>
                    <p>Cuando un conductor (como el disco metálico) se mueve a través de un campo magnético, 
                    se inducen corrientes eléctricas circulares llamadas "corrientes de Eddy". Estas corrientes 
                    crean su propio campo magnético que se opone al movimiento original, generando una fuerza 
                    de frenado sin contacto físico.</p>
                    
                    <div style="margin-top: 1rem;">
                        <strong>Instrucciones:</strong><br>
                        1. Haz clic en "Iniciar Giro" para que el disco comience a girar<br>
                        2. Arrastra el imán o la bobina cerca del disco<br>
                        3. Observa cómo el disco se desacelera por las corrientes de Eddy<br>
                        4. Aleja los elementos magnéticos para que el disco acelere nuevamente
                    </div>
                </div>
            </div>
        </section>
    </div>

    <script>
        // Global variables
        let currentQuestionIndex = 0;
        let quizScore = 0;
        let isSpinning = false;
        let spinSpeed = 0;
        let maxSpeed = 100;
        let coilActive = false;
        let dragElement = null;
        let eddyCurrentsVisible = false;
        let animationFrame;

        // Quiz questions
        const quizQuestions = [
            {
                question: "¿Qué científico formuló las leyes fundamentales del electromagnetismo?",
                options: ["Isaac Newton", "James Clerk Maxwell", "Albert Einstein", "Nikola Tesla"],
                correct: 1
            },
            {
                question: "¿Cuál es la unidad de medida del campo magnético en el Sistema Internacional?",
                options: ["Amperio (A)", "Voltio (V)", "Tesla (T)", "Watt (W)"],
                correct: 2
            },
            {
                question: "¿Qué son las corrientes de Eddy?",
                options: ["Corrientes en el océano", "Corrientes eléctricas circulares en conductores", "Corrientes de aire", "Corrientes de agua"],
                correct: 1
            },
            {
                question: "¿En qué dirección van las líneas de campo magnético?",
                options: ["Del polo sur al norte", "Del polo norte al sur", "En círculos", "No tienen dirección"],
                correct: 1
            },
            {
                question: "¿Qué principio físico permite el funcionamiento del freno de Eddy?",
                options: ["Ley de Ohm", "Ley de Lenz", "Ley de Coulomb", "Ley de Hooke"],
                correct: 1
            }
        ];

        // Navigation functions
        function showSection(sectionId) {
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(sectionId).classList.add('active');

            if (sectionId === 'quiz') {
                initQuiz();
            } else if (sectionId === 'game') {
                initGame();
            }
        }

        // Quiz functions
        function initQuiz() {
            currentQuestionIndex = 0;
            quizScore = 0;
            displayQuestion();
        }

        function displayQuestion() {
            const quizContent = document.getElementById('quiz-content');
            const scoreElement = document.getElementById('quiz-score');
            
            if (currentQuestionIndex < quizQuestions.length) {
                const question = quizQuestions[currentQuestionIndex];
                
                quizContent.innerHTML = `
                    <div class="question-card">
                        <div class="question">
                            Pregunta ${currentQuestionIndex + 1} de ${quizQuestions.length}:
                            <br><br>${question.question}
                        </div>
                        <div class="options">
                            ${question.options.map((option, index) => 
                                `<div class="option" onclick="selectOption(${index})">${option}</div>`
                            ).join('')}
                        </div>
                    </div>
                `;
                scoreElement.style.display = 'none';
            } else {
                showQuizResults();
            }
        }

        function selectOption(selectedIndex) {
            const question = quizQuestions[currentQuestionIndex];
            const options = document.querySelectorAll('.option');
            
            options.forEach((option, index) => {
                option.style.pointerEvents = 'none';
                if (index === question.correct) {
                    option.classList.add('correct');
                } else if (index === selectedIndex && index !== question.correct) {
                    option.classList.add('incorrect');
                }
            });

            if (selectedIndex === question.correct) {
                quizScore++;
            }

            setTimeout(() => {
                currentQuestionIndex++;
                displayQuestion();
            }, 1500);
        }

        function showQuizResults() {
            const quizContent = document.getElementById('quiz-content');
            const scoreElement = document.getElementById('quiz-score');
            
            quizContent.innerHTML = '';
            
            const percentage = (quizScore / quizQuestions.length) * 100;
            let message = '';
            
            if (percentage >= 80) {
                message = '¡Excelente! Eres un experto en electromagnetismo 🏆';
            } else if (percentage >= 60) {
                message = '¡Bien hecho! Tienes buenos conocimientos 👍';
            } else {
                message = 'Sigue estudiando, puedes mejorar 📚';
            }

            scoreElement.innerHTML = `
                <h2>Resultados del Quiz</h2>
                <div style="font-size: 2rem; margin: 1rem 0;">${percentage.toFixed(0)}%</div>
                <div>Has respondido correctamente ${quizScore} de ${quizQuestions.length} preguntas</div>
                <div style="margin-top: 1rem;">${message}</div>
            `;
            scoreElement.style.display = 'block';
        }

        function restartQuiz() {
            initQuiz();
        }

        // Game functions - Eddy Brake
        function initGame() {
            setupDragAndDrop();
            resetGame();
            startGameLoop();
        }

        function setupDragAndDrop() {
            const magnet = document.getElementById('magnet');
            const coil = document.getElementById('coil');
            
            [magnet, coil].forEach(element => {
                element.addEventListener('mousedown', startDrag);
                element.addEventListener('touchstart', startDrag);
            });

            document.addEventListener('mousemove', drag);
            document.addEventListener('mouseup', stopDrag);
            document.addEventListener('touchmove', drag);
            document.addEventListener('touchend', stopDrag);
        }

        function startDrag(e) {
            e.preventDefault();
            dragElement = e.target.closest('.magnet, .coil');
            const rect = dragElement.getBoundingClientRect();
            const clientX = e.clientX || e.touches[0].clientX;
            const clientY = e.clientY || e.touches[0].clientY;
            
            dragElement.offsetX = clientX - rect.left;
            dragElement.offsetY = clientY - rect.top;
        }

        function drag(e) {
            if (!dragElement) return;
            e.preventDefault();
            
            const canvas = document.getElementById('gameCanvas');
            const canvasRect = canvas.getBoundingClientRect();
            const clientX = e.clientX || e.touches[0].clientX;
            const clientY = e.clientY || e.touches[0].clientY;
            
            let newX = clientX - canvasRect.left - dragElement.offsetX;
            let newY = clientY - canvasRect.top - dragElement.offsetY;
            
            // Keep elements within canvas bounds
            newX = Math.max(0, Math.min(newX, canvas.offsetWidth - dragElement.offsetWidth));
            newY = Math.max(0, Math.min(newY, canvas.offsetHeight - dragElement.offsetHeight));
            
            dragElement.style.left = newX + 'px';
            dragElement.style.top = newY + 'px';
            
            calculateBrakingEffect();
        }

        function stopDrag() {
            dragElement = null;
        }

        function toggleSpin() {
            const disc = document.getElementById('disc');
            const spinBtn = document.getElementById('spinBtn');
            
            isSpinning = !isSpinning;
            
            if (isSpinning) {
                disc.classList.add('spinning');
                spinBtn.textContent = 'Detener Giro';
                spinBtn.classList.add('active');
                spinSpeed = maxSpeed;
            } else {
                disc.classList.remove('spinning');
                spinBtn.textContent = 'Iniciar Giro';
                spinBtn.classList.remove('active');
                spinSpeed = 0;
            }
            
            updateDiscAnimation();
        }

        function toggleCoilCurrent() {
            const coil = document.getElementById('coil');
            coilActive = !coilActive;
            
            if (coilActive) {
                coil.classList.add('active');
            } else {
                coil.classList.remove('active');
            }
            
            calculateBrakingEffect();
        }

        function showEddyCurrents() {
            const eddyCurrents = document.getElementById('eddyCurrents');
            eddyCurrentsVisible = !eddyCurrentsVisible;
            
            if (eddyCurrentsVisible) {
                eddyCurrents.classList.add('active');
            } else {
                eddyCurrents.classList.remove('active');
            }
        }

        function calculateBrakingEffect() {
            const disc = document.getElementById('disc');
            const magnet = document.getElementById('magnet');
            const coil = document.getElementById('coil');
            const eddyCurrents = document.getElementById('eddyCurrents');
            
            const discRect = disc.getBoundingClientRect();
            const magnetRect = magnet.getBoundingClientRect();
            const coilRect = coil.getBoundingClientRect();
            
            // Calculate distance from disc center
            const discCenterX = discRect.left + discRect.width / 2;
            const discCenterY = discRect.top + discRect.height / 2;
            
            const magnetCenterX = magnetRect.left + magnetRect.width / 2;
            const magnetCenterY = magnetRect.top + magnetRect.height / 2;
            
            const coilCenterX = coilRect.left + coilRect.width / 2;
            const coilCenterY = coilRect.top + coilRect.height / 2;
            
            const magnetDistance = Math.sqrt(
                Math.pow(discCenterX - magnetCenterX, 2) + 
                Math.pow(discCenterY - magnetCenterY, 2)
            );
            
            const coilDistance = Math.sqrt(
                Math.pow(discCenterX - coilCenterX, 2) + 
                Math.pow(discCenterY - coilCenterY, 2)
            );
            
            // Calculate braking force based on proximity
            let brakingForce = 0;
            const maxDistance = 150;
            
            // Magnet effect (always active)
            if (magnetDistance < maxDistance) {
                brakingForce += (1 - magnetDistance / maxDistance) * 70;
            }
            
            // Coil effect (only when active)
            if (coilActive && coilDistance < maxDistance) {
                brakingForce += (1 - coilDistance / maxDistance) * 80;
            }
            
            brakingForce = Math.min(brakingForce, 95);
            
            // Apply braking to spin speed
            if (isSpinning) {
                spinSpeed = maxSpeed * (1 - brakingForce / 100);
                updateDiscAnimation();
            }
            
            // Show eddy currents when braking
            if (brakingForce > 20) {
                eddyCurrents.classList.add('active');
                eddyCurrentsVisible = true;
            } else if (brakingForce < 10) {
                eddyCurrents.classList.remove('active');
                eddyCurrentsVisible = false;
            }
            
            updateStatusPanel(brakingForce);
        }

        function updateDiscAnimation() {
            const disc = document.getElementById('disc');
            if (isSpinning && spinSpeed > 0) {
                const duration = 4 - (spinSpeed / maxSpeed) * 3.5; // 0.5s to 4s
                disc.style.animationDuration = duration + 's';
            }
        }

        function updateStatusPanel(brakingForce) {
            document.getElementById('discSpeed').textContent = Math.round(spinSpeed) + '%';
            document.getElementById('brakingForce').textContent = Math.round(brakingForce) + '%';
            
            let eddyStatus = 'Inactivas';
            if (brakingForce > 50) {
                eddyStatus = 'Muy Intensas';
            } else if (brakingForce > 20) {
                eddyStatus = 'Moderadas';
            } else if (brakingForce > 5) {
                eddyStatus = 'Débiles';
            }
            
            document.getElementById('eddyIntensity').textContent = eddyStatus;
        }

        function startGameLoop() {
            function gameLoop() {
                if (isSpinning) {
                    calculateBrakingEffect();
                }
                animationFrame = requestAnimationFrame(gameLoop);
            }
            gameLoop();
        }

        function resetGame() {
            const disc = document.getElementById('disc');
            const spinBtn = document.getElementById('spinBtn');
            const coil = document.getElementById('coil');
            const magnet = document.getElementById('magnet');
            const eddyCurrents = document.getElementById('eddyCurrents');
            
            // Stop spinning
            isSpinning = false;
            spinSpeed = 0;
            disc.classList.remove('spinning');
            spinBtn.textContent = 'Iniciar Giro';
            spinBtn.classList.remove('active');
            
            // Reset coil
            coilActive = false;
            coil.classList.remove('active');
            
            // Reset positions
            magnet.style.top = '50px';
            magnet.style.left = '50px';
            coil.style.top = '200px';
            coil.style.right = '50px';
            coil.style.left = 'auto';
            
            // Hide eddy currents
            eddyCurrentsVisible = false;
            eddyCurrents.classList.remove('active');
            
            updateStatusPanel(0);
            
            if (animationFrame) {
                cancelAnimationFrame(animationFrame);
            }
            startGameLoop();
        }

        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            // Add some initial animations
            setTimeout(() => {
                document.querySelectorAll('.nav-btn').forEach((btn, index) => {
                    setTimeout(() => {
                        btn.style.animation = 'fadeIn 0.5s ease-in';
                    }, index * 100);
                });
            }, 500);
        });
    </script>
</body>
</html>
