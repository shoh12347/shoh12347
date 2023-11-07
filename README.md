<!DOCTYPE html>
<html>
<head>
    <title>Средняя длина слова</title>
    <style>
        body {
    background-color: #f7f7f7;
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
    text-align: center;
    margin: 0;
    padding: 0;
}

h1 {
    font-size: 36px;
    color: #333;
}

textarea {
    width: 80%;
    max-width: 400px;
    height: 100px;
    font-size: 16px;
    border: 2px solid #d1d1d1;
    padding: 10px;
    margin: 10px;
    border-radius: 8px;
}

button {
    background-color: #0070c9;
    color: #fff;
    font-size: 18px;
    border: none;
    padding: 10px 20px;
    border-radius: 8px;
    cursor: pointer;
}

button:hover {
    background-color: #0050a7;
}

p {
    font-size: 18px;
    color: #333;
}

span {
    font-weight: bold;
    color: #0070c9;
}

    </style>
</head>
<body>
    <h1>Далимов Шохрухбек Улугбек угли </h1>
    <h1>Средняя длина слова в строке</h1>
    <textarea id="inputText" placeholder="Введите текст"></textarea>
    <button id="calculateButton">Рассчитать</button>
    <p>Средняя длина слова: <span id="averageLength"></span></p>
    <p>Слова этой длины: <span id="wordsOfLength"></span></p>

    <script >
        document.addEventListener("DOMContentLoaded", function() {
    const inputText = document.getElementById("inputText");
    const calculateButton = document.getElementById("calculateButton");
    const averageLengthSpan = document.getElementById("averageLength");
    const wordsOfLengthSpan = document.getElementById("wordsOfLength");

    calculateButton.addEventListener("click", function() {
        const text = inputText.value;
        const words = text.split(/\s+/); // Разбиваем текст на слова по пробелам

        let totalLength = 0;
        let wordCount = 0;
        let wordsOfTargetLength = [];

        words.forEach(function(word) {
            // Удаляем знаки пунктуации и пробелы в начале и конце слова
            word = word.replace(/[.,\/#!$%^&*;:{}=\-_`~()]/g, "").trim();
            if (word.length > 0) {
                totalLength += word.length;
                wordCount++;
                if (!wordsOfTargetLength[word.length]) {
                    wordsOfTargetLength[word.length] = [];
                }
                wordsOfTargetLength[word.length].push(word);
            }
        });

        if (wordCount > 0) {
            const averageLength = totalLength / wordCount;
            averageLengthSpan.textContent = averageLength.toFixed(2);
        } else {
            averageLengthSpan.textContent = "N/A";
        }

        wordsOfLengthSpan.textContent = "";
        for (let i = 1; i < wordsOfTargetLength.length; i++) {
            if (wordsOfTargetLength[i]) {
                if (wordsOfLengthSpan.textContent !== "") {
                    wordsOfLengthSpan.textContent += ", ";
                }
                wordsOfLengthSpan.textContent += (${i}): ${wordsOfTargetLength[i].join(", ")};
            }
        }
    });
});

    </script>
</body>
</html>
