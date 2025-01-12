#<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لعبة الأعداد الدورية</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            padding: 50px;
        }
        .question {
            font-size: 24px;
            margin-bottom: 20px;
        }
        .answers {
            margin-top: 20px;
        }
        button {
            font-size: 18px;
            padding: 10px 20px;
            margin: 10px;
            cursor: pointer;
        }
        .correct {
            background-color: #4CAF50;
            color: white;
        }
        .incorrect {
            background-color: #f44336;
            color: white;
        }
        .result {
            font-size: 24px;
            margin-top: 30px;
        }
    </style>
</head>
<body>

    <h1>لعبة الأعداد الدورية</h1>
    <div class="question" id="question"></div>
    
    <div class="answers">
        <button id="answer1" onclick="checkAnswer(1)">إجابة 1</button>
        <button id="answer2" onclick="checkAnswer(2)">إجابة 2</button>
        <button id="answer3" onclick="checkAnswer(3)">إجابة 3</button>
    </div>

    <div class="result" id="result"></div>

    <script>
        let currentQuestion = 0;
        let score = 0;

        const questions = [
            {
                question: "هل العدد 0.3333... هو عدد دوري؟",
                answers: ["نعم", "لا", "لا أعرف"],
                correct: 1
            },
            {
                question: "ما هو الكسر الذي يعادل العدد 0.6666...؟",
                answers: ["1/3", "2/3", "1/2"],
                correct: 2
            },
            {
                question: "هل العدد 0.1(23) هو عدد دوري؟",
                answers: ["نعم", "لا", "لا أعرف"],
                correct: 1
            }
        ];

        function loadQuestion() {
            const question = questions[currentQuestion];
            document.getElementById("question").textContent = question.question;
            document.getElementById("answer1").textContent = question.answers[0];
            document.getElementById("answer2").textContent = question.answers[1];
            document.getElementById("answer3").textContent = question.answers[2];
        }

        function checkAnswer(selectedAnswer) {
            const correctAnswer = questions[currentQuestion].correct;
            const resultElement = document.getElementById("result");
            if (selectedAnswer === correctAnswer) {
                score++;
                resultElement.textContent = "إجابة صحيحة!";
                resultElement.className = "correct";
            } else {
                resultElement.textContent = "إجابة خاطئة!";
                resultElement.className = "incorrect";
            }
            currentQuestion++;
            if (currentQuestion < questions.length) {
                setTimeout(() => {
                    resultElement.textContent = "";
                    loadQuestion();
                }, 1000);
            } else {
                setTimeout(() => {
                    resultElement.textContent = `لقد حصلت على ${score} من ${questions.length} إجابات صحيحة!`;
                    resultElement.className = "";
                }, 1000);
            }
        }

        loadQuestion();
    </script>

</body>
</html>
 -
لعبة في الرياضيات عن العدد الدوري
