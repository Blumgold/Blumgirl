<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Расчет электрической мощности</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 20px;
            background: linear-gradient(to right, #ff7e5f, #feb47b);
            color: #333;
        }
        h1 {
            text-align: center;
            color: #fff;
            text-shadow: 2px 2px #333;
        }
        .container {
            max-width: 400px;
            margin: 30px auto;
            padding: 20px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            transition: transform 0.2s;
        }
        .container:hover {
            transform: scale(1.03);
        }
        label {
            font-weight: bold;
            display: block;
            margin-top: 10px;
        }
        input {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        button {
            padding: 12px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #218838;
        }
        .result {
            margin-top: 20px;
            font-weight: bold;
            font-size: 1.2em;
            text-align: center;
            color: #333;
        }
        @media (max-width: 500px) {
            .container {
                width: 90%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Энергия и мощность</h1>
        <label for="constant">Постоянная счетчика (имп/кВтч):</label>
        <input type="number" id="constant" placeholder="Введите значение" required>
        
        <label for="time">Время замера (секунды):</label>
        <input type="number" id="time" placeholder="Введите время в секундах" required>
        <label for="pulses">Количество импульсов:</label>
        <input type="number" id="pulses" placeholder="Введите количество импульсов" required>
        <button onclick="calculatePower()">Рассчитать мощность</button>
        
        <div class="result" id="result"></div>
    </div>
    <script>
        function calculatePower() {
            const constant = parseFloat(document.getElementById('constant').value);
            const time = parseInt(document.getElementById('time').value);
            const pulses = parseInt(document.getElementById('pulses').value);
            
            if (isNaN(constant) || isNaN(time) || isNaN(pulses) || time <= 0 || constant <= 0) {
                document.getElementById('result').innerText = 'Пожалуйста, введите корректные данные.';
                return;
            }
            const power = (3600 * pulses) / (constant * time); // Рассчитываем мощность в кВт
            document.getElementById('result').innerText = `Мощность: ${power.toFixed(2)} кВт`;
        }
    </script>
</body>
</html>
