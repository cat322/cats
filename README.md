<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لعبة اضرب الطائر!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f8ff;
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
        #bird {
            width: 40px;
            height: 40px;
            background-color: #ff6b6b;
            position: absolute;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s;
        }
        #score {
            font-size: 24px;
            color: #333;
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
        }
        button:hover {
            background-color: #3a7ba8;
        }
    </style>
</head>
<body>
    <h1>🎯 اضرب الطائر!</h1>
    <div id="score">النقاط: 0</div>
    <div id="game">
        <div id="bird"></div>
    </div>
    <button onclick="startGame()">ابدأ اللعبة</button>

    <script>
        let score = 0;
        const bird = document.getElementById("bird");
        const game = document.getElementById("game");
        const scoreDisplay = document.getElementById("score");

        function moveBird() {
            // حرك الطائر عشوائيًا داخل الصندوق
            const x = Math.random() * (game.offsetWidth - bird.offsetWidth);
            const y = Math.random() * (game.offsetHeight - bird.offsetHeight);
            
            bird.style.left = x + "px";
            bird.style.top = y + "px";
        }

        function startGame() {
            score = 0;
            scoreDisplay.textContent = "النقاط: " + score;
            
            // حرك الطائر كل ثانية
            const gameInterval = setInterval(moveBird, 1000);
            
            // اضرب الطائر عند النقر
            bird.onclick = function() {
                score++;
                scoreDisplay.textContent = "النقاط: " + score;
                moveBird(); // حركه مرة أخرى بعد الضربة
            };
        }
    </script>
</body>
</html>
