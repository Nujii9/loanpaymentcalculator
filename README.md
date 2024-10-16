<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Loan Payment Calculator</title>
    <link rel="stylesheet" href="https://pyscript.net/alpha/pyscript.css" />
    <script defer src="https://pyscript.net/alpha/pyscript.js"></script>

    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: url('money.png') repeat no-repeat;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        h1 {
            background-color: #e3e3e3;
            border-radius: 25px;
            width: 100%;
            justify-content: center;
            text-align: center;
        }

        .calculator-container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            width: 100%;
            text-align: center;
        }

        .calculator-container h1 {
            color: #4CAF50;
            margin-bottom: 20px;
        }

        label {
            font-size: 1rem;
            color: #333;
            margin-bottom: 5px;
            display: block;
        }

        input[type="number"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1rem;
        }

        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 1rem;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #45a049;
        }

        #result {
            margin-top: 20px;
            font-size: 1.2rem;
            color: #333;
        }

        @media (max-width: 500px) {
            .calculator-container {
                padding: 20px;
            }

            input[type="number"] {
                font-size: 0.9rem;
            }

            button {
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<body>
    <div class="calculator-container">
        <h1><b>Loan Payment Calculator</b></h1>

        <label for="loan">Enter the amount of loan: </label>
        <input type="number" id="loan" placeholder="Loan Amount" required>

        <label for="interest">Enter the interest rate as percentage: </label>
        <input type="number" id="interest" step="0.01" placeholder="Interest Rate" required>

        <label for="months">Enter the desired number of months: </label>
        <input type="number" id="months" placeholder="Months" required>

        <button id="calculate-button">Calculate</button>

        <div id="result"></div>
    </div>

    <py-script>
        def monthly_payment_amount(A, R, M):
            P = R * A / (1 - (1 + R) ** -M)
            return P

        def calculate_payment(event=None):
            loan = float(Element("loan").element.value)
            interest = float(Element("interest").element.value) / 100
            months = int(Element("months").element.value)
            payment_amount = monthly_payment_amount(loan, interest, months)
            Element("result").write(f"The monthly payment amount is: PHP {payment_amount:.2f}")

        Element("calculate-button").element.onclick = calculate_payment
    </py-script>
</body>
</html>
