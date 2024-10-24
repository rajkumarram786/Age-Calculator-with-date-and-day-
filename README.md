# Age-Calculator-with-date-and-day-
Age Calculator with date and day 



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-image: url('https://www.w3schools.com/w3images/mountains.jpg'); /* Example background image */
            background-size: cover;
            background-position: center;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            color: white;
            backdrop-filter: blur(8px); /* Slight blur to make text readable */
        }

        .container {
            background-color: rgba(0, 0, 0, 0.7); /* Semi-transparent background */
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.5);
            text-align: center;
            animation: fadeIn 1.5s ease-in-out; /* Container fade-in animation */
        }

        @keyframes fadeIn {
            0% {
                opacity: 0;
                transform: translateY(-30px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }

        h1 {
            margin-bottom: 20px;
            font-size: 36px;
        }

        label, p {
            font-size: 18px;
        }

        input {
            margin: 10px 0;
            padding: 10px;
            font-size: 16px;
            width: 100%;
            max-width: 300px;
            border-radius: 5px;
            border: none;
        }

        button {
            padding: 10px 20px;
            font-size: 16px;
            background-color: #28a745;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            transition: background-color 0.3s ease, transform 0.2s ease;
            position: relative;
            overflow: hidden;
        }

        button:hover {
            background-color: #218838;
            transform: scale(1.05);
        }

        button::before {
            content: '';
            position: absolute;
            left: 50%;
            top: 50%;
            width: 300%;
            height: 300%;
            background: rgba(255, 255, 255, 0.2);
            transform: translate(-50%, -50%) rotate(45deg);
            transition: width 0.3s ease, height 0.3s ease;
            border-radius: 50%;
            z-index: 1;
        }

        button:hover::before {
            width: 0;
            height: 0;
        }

        button span {
            position: relative;
            z-index: 2;
        }

        #result {
            margin-top: 20px;
            font-size: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Age Calculator</h1>
        <label for="dob">Enter your Date of Birth:</label>
        <input type="date" id="dob">
        <button onclick="calculateAge()"><span>Calculate Age</span></button>
        <p id="result"></p>
    </div>

    <script>
        function calculateAge() {
            const dob = document.getElementById("dob").value;
            const resultElement = document.getElementById("result");

            if (!dob) {
                resultElement.textContent = "Please select your date of birth!";
                return;
            }

            const birthDate = new Date(dob);
            const currentDate = new Date();

            let years = currentDate.getFullYear() - birthDate.getFullYear();
            let months = currentDate.getMonth() - birthDate.getMonth();
            let days = currentDate.getDate() - birthDate.getDate();

            if (days < 0) {
                months--;
                days += new Date(currentDate.getFullYear(), currentDate.getMonth(), 0).getDate();
            }

            if (months < 0) {
                years--;
                months += 12;
            }

            resultElement.textContent = `You are ${years} years, ${months} months, and ${days} days old.`;
        }
    </script>
</body>
</html>
