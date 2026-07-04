<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Our Special Date ❤️</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #ffe3e3 0%, #fff0f0 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            padding: 20px;
        }

        .card {
            background: white;
            padding: 40px;
            border-radius: 24px;
            box-shadow: 0 10px 40px rgba(255, 75, 92, 0.15);
            max-width: 480px;
            width: 100%;
            text-align: center;
            transition: all 0.4s ease;
        }

        .step {
            display: none;
        }

        .step.active {
            display: block;
            animation: fadeIn 0.5s ease forward;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1, h2 {
            color: #ff4b5c;
            margin-bottom: 20px;
        }

        .gif-container img {
            width: 140px;
            height: 140px;
            margin-bottom: 15px;
            object-fit: contain;
        }

        /* Buttons & Interactions */
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 25px;
            position: relative;
            height: 50px;
        }

        button {
            padding: 12px 28px;
            font-size: 1rem;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .btn-primary {
            background-color: #ff4b5c;
            color: white;
            box-shadow: 0 4px 15px rgba(255, 75, 92, 0.3);
        }

        .btn-primary:hover {
            transform: scale(1.05);
            background-color: #e03e4f;
        }

        #noBtn {
            background-color: #888;
            color: white;
            position: absolute;
            left: 55%;
        }

        /* Food Grid Selection */
        .menu-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin: 20px 0;
        }

        .menu-item {
            border: 2px solid #eee;
            border-radius: 15px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .menu-item:hover {
            border-color: #ff4b5c;
            background-color: #fff8f8;
        }

        .menu-item.selected {
            border-color: #ff4b5c;
            background-color: #ffe8ea;
        }

        .menu-item span {
            font-size: 2rem;
            display: block;
            margin-bottom: 5px;
        }

        /* Inputs */
        .form-group {
            margin: 20px 0;
            text-align: left;
        }

        label {
            display: block;
            font-weight: 600;
            color: #555;
            margin-bottom: 8px;
        }

        input[type="date"], input[type="time"] {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.2s;
        }

        input[type="date"]:focus, input[type="time"]:focus {
            border-color: #ff4b5c;
        }

        .error-msg {
            color: #d9534f;
            font-size: 0.9rem;
            margin-top: 5px;
            display: none;
            text-align: left;
        }

        /* Highlight Selection Box */
        .summary-box {
            background: #fff5f5;
            border-left: 4px solid #ff4b5c;
            padding: 15px;
            border-radius: 8px;
            margin: 20px 0;
            text-align: left;
        }

        .summary-box p {
            margin: 5px 0;
            color: #444;
        }
    </style>
</head>
<body>

    <div class="card">
        <div id="step1" class="step active">
            <div class="gif-container">
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbWdtcm9wa2V6OXN2Z3I1M29icWFsYzg0Mms5cmYwNm90Mm90Z3V6ciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/v6aOjy0Qo1fIA/giphy.gif" alt="Cute Bear">
            </div>
            <h1>Will you go out with me? ❤️</h1>
            <div class="btn-container">
                <button class="btn-primary" onclick="nextStep(2)">Yes!</button>
                <button id="noBtn">No</button>
            </div>
        </div>

        <div id="step2" class="step">
            <div class="gif-container">
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExM3Z0NTh3b3NpeWw5b3Q4bms2ZW95Y3A0am9pY3B5bXptczN6NzhwMiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/Qs7KuhzSl6IokmI6nN/giphy.gif" alt="Hungry Cute Bear">
            </div>
            <h2>What would you like to eat? 🍕</h2>
            <p style="color: #666;">Pick your favorite treat!</p>
            
            <div class="menu-grid">
                <div class="menu-item" onclick="toggleSelectFood(this, 'Pizza & Pasta')">
                    <span>🍕</span> Pizza & Pasta
                </div>
                <div class="menu-item" onclick="toggleSelectFood(this, 'Sushi Date')">
                    <span>🍣</span> Sushi
                </div>
                <div class="menu-item" onclick="toggleSelectFood(this, 'Burgers & Fries')">
                    <span>🍔</span> Burgers & Fries
                </div>
                <div class="menu-item" onclick="toggleSelectFood(this, 'Sweet Desserts')">
                    <span>🍰</span> Just Desserts
                </div>
            </div>
            <p id="foodError" class="error-msg">Please pick at least one option before continuing!</p>
            <button class="btn-primary" style="width: 100%;" onclick="validateFoodAndNext()">Next: Pick a Time ➔</button>
        </div>

        <div id="step3" class="step">
            <div class="gif-container">
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbWc0ZXI5NzdmaXN3cHltMXE0cjZ0eWpsYnc1azEwNHB5MG9idG44dyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/3ohs7K86VLeIP1re9O/giphy.gif" alt="Clock Bear">
            </div>
            <h2>When are you free? 📅</h2>
            
            <div class="form-group">
                <label for="dateInput">Select Date:</label>
                <input type="date" id="dateInput">
                <p id="dateError" class="error-msg">Please select a valid upcoming date!</p>
            </div>

            <div class="form-group">
                <label for="timeInput">Select Time:</label>
                <input type="time" id="timeInput">
                <p id="timeError" class="error-msg">Please select a time!</p>
            </div>

            <button class="btn-primary" style="width: 100%;" onclick="validateDateTimeAndNext()">Lock Date & Time ➔</button>
        </div>

        <div id="step4" class="step">
            <div class="gif-container">
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHY1YTI4cXN0ZmdvNnI0N3V5MDZ6YmN5MXRrcnRkZ3p0Z3RsczZxeSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9cw/c7QVDasajO0I8/giphy.gif" alt="Dancing Happy Bear">
            </div>
            <h2>It's an official date! 🎉</h2>
            
            <div class="summary-box">
                <p><strong>🍴 Menu Choice:</strong> <span id="finalFood"></span></p>
                <p><strong>📅 Date scheduled:</strong> <span id="finalDate"></span></p>
                <p><strong>⏰ Pickup Time:</strong> <span id="finalTime"></span></p>
            </div>

            <h3 style="color: #ff4b5c; margin-top: 20px;">Be ready on <span id="finalTimeText"></span>, I will pick you up! 🚘💨</h3>
        </div>
    </div>

    <script>
        let selectedFood = "";
        const noBtn = document.getElementById('noBtn');

        // 1. Runaway No Button Logic
        function moveNoButton() {
            const padding = 50;
            const maxX = window.innerWidth - noBtn.offsetWidth - padding;
            const maxY = window.innerHeight - noBtn.offsetHeight - padding;
            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);

            noBtn.style.position = 'fixed';
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
        }
        noBtn.addEventListener('mouseover', moveNoButton);
        noBtn.addEventListener('touchstart', (e) => { e.preventDefault(); moveNoButton(); });

        // 2. Navigation Steps
        function nextStep(stepNumber) {
            document.querySelectorAll('.step').forEach(step => step.classList.remove('active'));
            document.getElementById(`step${stepNumber}`).classList.add('active');
        }

        // 3. Food Choice Engine
        function toggleSelectFood(element, foodName) {
            document.querySelectorAll('.menu-item').forEach(item => item.classList.remove('selected'));
            element.classList.add('selected');
            selectedFood = foodName;
            document.getElementById('foodError').style.display = 'none';
        }

        function validateFoodAndNext() {
            if (!selectedFood) {
                document.getElementById('foodError').style.display = 'block';
            } else {
                // Set the default minimum date value to "today" for better UX validation rules
                const today = new Date().toISOString().split('T')[0];
                document.getElementById('dateInput').setAttribute('min', today);
                nextStep(3);
            }
        }

        // 4. Date & Time Validation Engine
        function validateDateTimeAndNext() {
            const dateInput = document.getElementById('dateInput').value;
            const timeInput = document.getElementById('timeInput').value;
            let isValid = true;

            // Reset errors
            document.getElementById('dateError').style.display = 'none';
            document.getElementById('timeError').style.display = 'none';

            if (!dateInput) {
                document.getElementById('dateError').style.display = 'block';
                isValid = false;
            }
            if (!timeInput) {
                document.getElementById('timeError').style.display = 'block';
                isValid = false;
            }

            if (isValid) {
                // Format date look (e.g., 2026-07-04 -> July 4, 2026)
                const dateOptions = { year: 'numeric', month: 'long', day: 'numeric' };
                const structuredDate = new Date(dateInput).toLocaleDateString(undefined, dateOptions);
                
                // Format 24hr to readable 12hr time format
                const [hours, minutes] = timeInput.split(':');
                const ampm = hours >= 12 ? 'PM' : 'AM';
                const formattedHours = hours % 12 || 12;
                const structuredTime = `${formattedHours}:${minutes} ${ampm}`;

                // Populate final text fields dynamically
                document.getElementById('finalFood').innerText = selectedFood;
                document.getElementById('finalDate').innerText = structuredDate;
                document.getElementById('finalTime').innerText = structuredTime;
                document.getElementById('finalTimeText').innerText = `${structuredDate} at ${structuredTime}`;

                nextStep(4);
            }
        }
    </script>
</body>
</html>
