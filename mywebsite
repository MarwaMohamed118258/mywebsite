<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>تطبيق تحويل العملات</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      text-align: center;
      padding: 50px;
    }

    .container {
      background: white;
      padding: 20px;
      border-radius: 10px;
      max-width: 500px;
      margin: auto;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    input, select, button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      font-size: 16px;
    }

    .result {
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>تطبيق تحويل العملات</h1>
    <div class="currency-converter">
      <label for="amount">المبلغ:</label>
      <input type="number" id="amount" placeholder="أدخل المبلغ" min="1">
      
      <label for="from-currency">من العملة:</label>
      <select id="from-currency"></select>

      <label for="to-currency">إلى العملة:</label>
      <select id="to-currency"></select>

      <button id="convert-btn">تحويل</button>

      <div class="result">
        <p>النتيجة: <span id="result"></span></p>
      </div>
    </div>
  </div>

  <script>
    const currencies = ["USD", "EUR", "EGP", "SAR"];
    const rates = {
      "USD": 1,
      "EUR": 0.93,
      "EGP": 47,
      "SAR": 3.75
    };

    const fromSelect = document.getElementById('from-currency');
    const toSelect = document.getElementById('to-currency');
    const amountInput = document.getElementById('amount');
    const resultSpan = document.getElementById('result');

    // إضافة العملات للاختيارات
    currencies.forEach(currency => {
      const option1 = document.createElement('option');
      option1.value = currency;
      option1.text = currency;
      fromSelect.add(option1);

      const option2 = document.createElement('option');
      option2.value = currency;
      option2.text = currency;
      toSelect.add(option2);
    });

    document.getElementById('convert-btn').addEventListener('click', () => {
      const from = fromSelect.value;
      const to = toSelect.value;
      const amount = parseFloat(amountInput.value);

      if (isNaN(amount) || amount <= 0) {
        resultSpan.innerText = "أدخل مبلغًا صحيحًا.";
        return;
      }

      const converted = (amount / rates[from]) * rates[to];
      resultSpan.innerText = ${converted.toFixed(2)} ${to};
    });
  </script>

</body>
</html>
