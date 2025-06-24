<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لعبة اضرب بنين!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f8ff;
            padding: 20px;
        }
        #game {
            width: 300px;
            height: 200px;
            background-color: #4b9cd3;
            margin: 20px auto;
            position: relative;
            overflow: hidden;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        #target {
            width: 60px;
            height: 60px;
            background-color: #ff6b6b;
            position: absolute;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
            font-size: 16px;
        }
        #score {
            font-size: 24px;
            color: #333;
            margin: 10px;
        }
        #timer {
            font-size: 24px;
            color: #e74c3c;
            margin: 10px;
        }
        button {
            background-color: #4b9cd3;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            margin: 5px;
        }
        button:hover {
            background-color: #3a7ba8;
        }
        #result {
            font-size: 20px;
            margin: 10px;
            color: #2ecc71;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>🎯 اضرب بنين خلال 10 ثوانٍ!</h1>
    <div id="timer">الوقت المتبقي: 10</div>
    <div id="score">النقاط: 0</div>
    <div id="result"></div>
    <div id="game">
        <div id="target">بنين</div>
    </div>
    <button onclick="startGame()">ابدأ اللعبة</button>
    <button onclick="resetGame()">إعادة التشغيل</button>

    <script>
        let score = 0;
        let timeLeft = 10;
        let gameInterval;
        let timerInterval;
        const target = document.getElementById("target");
        const game = document.getElementById("game");
        const scoreDisplay = document.getElementById("score");
        const timerDisplay = document.getElementById("timer");
        const resultDisplay = document.getElementById("result");

        function moveTarget() {
            const x = Math.random() * (game.offsetWidth - target.offsetWidth);
            const y = Math.random() * (game.offsetHeight - target.offsetHeight);
            target.style.left = x + "px";
            target.style.top = y + "px";
        }

        function updateTimer() {
            timeLeft--;
            timerDisplay.textContent = "الوقت المتبقي: " + timeLeft;
            
            if (timeLeft <= 0) {
                endGame();
            }
        }

        function startGame() {
            // إعادة تعيين اللعبة
            score = 0;
            timeLeft = 10;
            scoreDisplay.textContent = "النقاط: " + score;
            timerDisplay.textContent = "الوقت المتبقي: " + timeLeft;
            resultDisplay.textContent = "";
            
            // تفعيل النقر على الهدف
            target.onclick = function() {
                score++;
                scoreDisplay.textContent = "النقاط: " + score;
                moveTarget();
            };
            
            // بدء المؤقت وحركة الهدف
            moveTarget();
            gameInterval = setInterval(moveTarget, 800); // أسرع حركة
            timerInterval = setInterval(updateTimer, 1000);
        }

        function endGame() {
            clearInterval(gameInterval);
            clearInterval(timerInterval);
            target.onclick = null; // تعطيل النقر بعد انتهاء الوقت
            resultDisplay.textContent = "🎉 انتهى الوقت! نقاطك: " + score;
        }

        function resetGame() {
            clearInterval(gameInterval);
            clearInterval(timerInterval);
            score = 0;
            timeLeft = 10;
            scoreDisplay.textContent = "النقاط: " + score;
            timerDisplay.textContent = "الوقت المتبقي: " + timeLeft;
            resultDisplay.textContent = "";
            target.style.left = "0px";
            target.style.top = "0px";
            target.onclick = null;
        }
    </script>
</body>
</html>
