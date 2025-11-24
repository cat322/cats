<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لعبة الدودة</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            color: white;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
            max-width: 800px;
            width: 100%;
        }
        
        header {
            text-align: center;
            margin-bottom: 20px;
        }
        
        h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        
        .game-info {
            display: flex;
            justify-content: space-between;
            width: 100%;
            max-width: 600px;
            background-color: rgba(0, 0, 0, 0.3);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 10px;
        }
        
        .score-container, .high-score-container {
            text-align: center;
        }
        
        .score-label, .high-score-label {
            font-size: 1.2rem;
            margin-bottom: 5px;
        }
        
        .score-value, .high-score-value {
            font-size: 2rem;
            font-weight: bold;
        }
        
        .game-area {
            position: relative;
            width: 100%;
            max-width: 600px;
            aspect-ratio: 1/1;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
        }
        
        canvas {
            display: block;
            width: 100%;
            height: 100%;
        }
        
        .controls {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
            margin-top: 20px;
        }
        
        .buttons {
            display: flex;
            gap: 15px;
        }
        
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 12px 25px;
            font-size: 1.1rem;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        
        button:hover {
            background-color: #45a049;
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
        }
        
        button:active {
            transform: translateY(0);
        }
        
        #restart-btn {
            background-color: #f44336;
        }
        
        #restart-btn:hover {
            background-color: #d32f2f;
        }
        
        .instructions {
            background-color: rgba(0, 0, 0, 0.3);
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            max-width: 600px;
            text-align: center;
        }
        
        .instructions h2 {
            margin-bottom: 10px;
        }
        
        .instructions p {
            margin-bottom: 10px;
            line-height: 1.6;
        }
        
        .game-over {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10;
            border-radius: 10px;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.5s ease;
        }
        
        .game-over.active {
            opacity: 1;
            pointer-events: all;
        }
        
        .game-over h2 {
            font-size: 3rem;
            margin-bottom: 20px;
            color: #ff5252;
        }
        
        .game-over p {
            font-size: 1.5rem;
            margin-bottom: 30px;
        }
        
        .mobile-controls {
            display: none;
            grid-template-columns: repeat(3, 1fr);
            grid-template-rows: repeat(3, 1fr);
            gap: 10px;
            margin-top: 20px;
            width: 200px;
            height: 200px;
        }
        
        .mobile-controls button {
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            background-color: rgba(255, 255, 255, 0.2);
        }
        
        .up-btn {
            grid-column: 2;
            grid-row: 1;
        }
        
        .left-btn {
            grid-column: 1;
            grid-row: 2;
        }
        
        .right-btn {
            grid-column: 3;
            grid-row: 2;
        }
        
        .down-btn {
            grid-column: 2;
            grid-row: 3;
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }
            
            .mobile-controls {
                display: grid;
            }
            
            .instructions {
                font-size: 0.9rem;
            }
        }
        
        @media (max-width: 480px) {
            h1 {
                font-size: 2rem;
            }
            
            .game-info {
                flex-direction: column;
                gap: 10px;
            }
            
            .mobile-controls {
                width: 150px;
                height: 150px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>لعبة الدودة</h1>
            <p>توجيه الدودة لتناول الطعام وتجنب الاصطدام بالجدران أو جسمك!</p>
        </header>
        
        <div class="game-info">
            <div class="score-container">
                <div class="score-label">النقاط</div>
                <div class="score-value">0</div>
            </div>
            <div class="high-score-container">
                <div class="high-score-label">أفضل نتيجة</div>
                <div class="high-score-value">0</div>
            </div>
        </div>
        
        <div class="game-area">
            <canvas id="game-canvas"></canvas>
            <div class="game-over">
                <h2>انتهت اللعبة!</h2>
                <p>نقاطك: <span id="final-score">0</span></p>
                <button id="play-again-btn">العب مرة أخرى</button>
            </div>
        </div>
        
        <div class="controls">
            <div class="buttons">
                <button id="start-btn">بدء اللعبة</button>
                <button id="pause-btn">إيقاف مؤقت</button>
                <button id="restart-btn">إعادة تشغيل</button>
            </div>
            
            <div class="mobile-controls">
                <button class="up-btn">↑</button>
                <button class="left-btn">←</button>
                <button class="right-btn">→</button>
                <button class="down-btn">↓</button>
            </div>
        </div>
        
        <div class="instructions">
            <h2>كيفية اللعب</h2>
            <p>استخدم مفاتيح الأسهم على لوحة المفاتيح للتحكم في اتجاه الدودة</p>
            <p>تناول الطعام الأحمر لزيادة طول الدودة وزيادة نقاطك</p>
            <p>تجنب الاصطدام بالجدران أو بجسم الدودة نفسه</p>
        </div>
    </div>

    <script>
        // عناصر DOM
        const canvas = document.getElementById('game-canvas');
        const ctx = canvas.getContext('2d');
        const scoreValue = document.querySelector('.score-value');
        const highScoreValue = document.querySelector('.high-score-value');
        const finalScore = document.getElementById('final-score');
        const startBtn = document.getElementById('start-btn');
        const pauseBtn = document.getElementById('pause-btn');
        const restartBtn = document.getElementById('restart-btn');
        const playAgainBtn = document.getElementById('play-again-btn');
        const gameOverScreen = document.querySelector('.game-over');
        const upBtn = document.querySelector('.up-btn');
        const leftBtn = document.querySelector('.left-btn');
        const rightBtn = document.querySelector('.right-btn');
        const downBtn = document.querySelector('.down-btn');

        // إعدادات اللعبة
        const gridSize = 20;
        let snake = [];
        let food = {};
        let direction = 'right';
        let nextDirection = 'right';
        let gameSpeed = 150;
        let score = 0;
        let highScore = localStorage.getItem('snakeHighScore') || 0;
        let gameInterval;
        let isPaused = false;
        let isGameOver = false;

        // تعيين أفضل نتيجة
        highScoreValue.textContent = highScore;

        // تهيئة اللعبة
        function initGame() {
            // تعيين حجم الـ canvas
            canvas.width = canvas.offsetWidth;
            canvas.height = canvas.offsetHeight;
            
            // إعادة تعيين المتغيرات
            snake = [
                {x: 5, y: 10},
                {x: 4, y: 10},
                {x: 3, y: 10}
            ];
            direction = 'right';
            nextDirection = 'right';
            score = 0;
            scoreValue.textContent = score;
            isGameOver = false;
            gameOverScreen.classList.remove('active');
            
            // إنشاء الطعام الأول
            generateFood();
            
            // رسم اللعبة
            draw();
        }

        // رسم عناصر اللعبة
        function draw() {
            // مسح الـ canvas
            ctx.fillStyle = 'rgba(0, 0, 0, 0.2)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            
            // رسم الشبكة
            drawGrid();
            
            // رسم الدودة
            snake.forEach((segment, index) => {
                if (index === 0) {
                    // رأس الدودة
                    ctx.fillStyle = '#4CAF50';
                } else {
                    // جسم الدودة
                    ctx.fillStyle = '#8BC34A';
                }
                ctx.fillRect(segment.x * gridSize, segment.y * gridSize, gridSize, gridSize);
                
                // إضافة حدود للدودة
                ctx.strokeStyle = '#33691E';
                ctx.strokeRect(segment.x * gridSize, segment.y * gridSize, gridSize, gridSize);
            });
            
            // رسم الطعام
            ctx.fillStyle = '#FF5252';
            ctx.beginPath();
            ctx.arc(
                food.x * gridSize + gridSize/2, 
                food.y * gridSize + gridSize/2, 
                gridSize/2, 0, Math.PI * 2
            );
            ctx.fill();
            
            // رسم تأثير للطعام
            ctx.fillStyle = 'rgba(255, 82, 82, 0.5)';
            ctx.beginPath();
            ctx.arc(
                food.x * gridSize + gridSize/2, 
                food.y * gridSize + gridSize/2, 
                gridSize/2 + 2, 0, Math.PI * 2
            );
            ctx.fill();
        }

        // رسم الشبكة
        function drawGrid() {
            ctx.strokeStyle = 'rgba(255, 255, 255, 0.05)';
            ctx.lineWidth = 1;
            
            // الخطوط العمودية
            for (let x = 0; x <= canvas.width; x += gridSize) {
                ctx.beginPath();
                ctx.moveTo(x, 0);
                ctx.lineTo(x, canvas.height);
                ctx.stroke();
            }
            
            // الخطوط الأفقية
            for (let y = 0; y <= canvas.height; y += gridSize) {
                ctx.beginPath();
                ctx.moveTo(0, y);
                ctx.lineTo(canvas.width, y);
                ctx.stroke();
            }
        }

        // إنشاء الطعام في مكان عشوائي
        function generateFood() {
            const maxX = Math.floor(canvas.width / gridSize);
            const maxY = Math.floor(canvas.height / gridSize);
            
            food = {
                x: Math.floor(Math.random() * maxX),
                y: Math.floor(Math.random() * maxY)
            };
            
            // التأكد من أن الطعام لا يظهر على الدودة
            for (let segment of snake) {
                if (segment.x === food.x && segment.y === food.y) {
                    generateFood();
                    break;
                }
            }
        }

        // تحديث حالة اللعبة
        function update() {
            if (isPaused || isGameOver) return;
            
            // تحديث اتجاه الدودة
            direction = nextDirection;
            
            // حساب موضع الرأس الجديد
            const head = {...snake[0]};
            
            switch(direction) {
                case 'up':
                    head.y -= 1;
                    break;
                case 'down':
                    head.y += 1;
                    break;
                case 'left':
                    head.x -= 1;
                    break;
                case 'right':
                    head.x += 1;
                    break;
            }
            
            // التحقق من الاصطدام بالجدران
            if (
                head.x < 0 || 
                head.y < 0 || 
                head.x >= canvas.width / gridSize || 
                head.y >= canvas.height / gridSize
            ) {
                gameOver();
                return;
            }
            
            // التحقق من الاصطدام بالنفس
            for (let segment of snake) {
                if (head.x === segment.x && head.y === segment.y) {
                    gameOver();
                    return;
                }
            }
            
            // إضافة الرأس الجديد
            snake.unshift(head);
            
            // التحقق من أكل الطعام
            if (head.x === food.x && head.y === food.y) {
                // زيادة النقاط
                score += 10;
                scoreValue.textContent = score;
                
                // إنشاء طعام جديد
                generateFood();
                
                // زيادة السرعة تدريجياً
                if (score % 50 === 0 && gameSpeed > 50) {
                    gameSpeed -= 10;
                    clearInterval(gameInterval);
                    gameInterval = setInterval(gameLoop, gameSpeed);
                }
            } else {
                // إزالة الذيل إذا لم يتم أكل الطعام
                snake.pop();
            }
            
            // رسم اللعبة
            draw();
        }

        // حلقة اللعبة الرئيسية
        function gameLoop() {
            update();
        }

        // إنهاء اللعبة
        function gameOver() {
            isGameOver = true;
            clearInterval(gameInterval);
            
            // تحديث أفضل نتيجة
            if (score > highScore) {
                highScore = score;
                highScoreValue.textContent = highScore;
                localStorage.setItem('snakeHighScore', highScore);
            }
            
            // عرض شاشة انتهاء اللعبة
            finalScore.textContent = score;
            gameOverScreen.classList.add('active');
        }

        // بدء اللعبة
        function startGame() {
            if (gameInterval) {
                clearInterval(gameInterval);
            }
            
            isPaused = false;
            pauseBtn.textContent = 'إيقاف مؤقت';
            gameInterval = setInterval(gameLoop, gameSpeed);
        }

        // إيقاف/استئناف اللعبة
        function togglePause() {
            isPaused = !isPaused;
            pauseBtn.textContent = isPaused ? 'استئناف' : 'إيقاف مؤقت';
        }

        // إعادة تشغيل اللعبة
        function restartGame() {
            clearInterval(gameInterval);
            initGame();
            startGame();
        }

        // التحكم في اتجاه الدودة
        function changeDirection(newDirection) {
            // منع الحركة العكسية المباشرة
            if (
                (newDirection === 'up' && direction !== 'down') ||
                (newDirection === 'down' && direction !== 'up') ||
                (newDirection === 'left' && direction !== 'right') ||
                (newDirection === 'right' && direction !== 'left')
            ) {
                nextDirection = newDirection;
            }
        }

        // أحداث لوحة المفاتيح
        document.addEventListener('keydown', (e) => {
            switch(e.key) {
                case 'ArrowUp':
                    changeDirection('up');
                    break;
                case 'ArrowDown':
                    changeDirection('down');
                    break;
                case 'ArrowLeft':
                    changeDirection('left');
                    break;
                case 'ArrowRight':
                    changeDirection('right');
                    break;
                case ' ':
                    togglePause();
                    break;
            }
        });

        // أحداث الأزرار
        startBtn.addEventListener('click', startGame);
        pauseBtn.addEventListener('click', togglePause);
        restartBtn.addEventListener('click', restartGame);
        playAgainBtn.addEventListener('click', restartGame);

        // أحداث أزرار التحكم للهواتف
        upBtn.addEventListener('click', () => changeDirection('up'));
        leftBtn.addEventListener('click', () => changeDirection('left'));
        rightBtn.addEventListener('click', () => changeDirection('right'));
        downBtn.addEventListener('click', () => changeDirection('down'));

        // تهيئة اللعبة عند تحميل الصفحة
        window.addEventListener('load', () => {
            initGame();
            
            // ضبط حجم الـ canvas عند تغيير حجم النافذة
            window.addEventListener('resize', () => {
                canvas.width = canvas.offsetWidth;
                canvas.height = canvas.offsetHeight;
                draw();
            });
        });
    </script>
</body>
</html>
