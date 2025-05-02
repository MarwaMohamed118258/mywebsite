<div class="container">
  <h1>تطبيق تحويل العملات</h1>
  <div class="currency-converter">
    <label for="amount">المبلغ:</label>
    <input type="number" id="amount" placeholder="أدخل المبلغ" min="1">
    
    <label for="from-currency">من العملة:</label>
    <select id="from-currency">
      <!-- سيتم إضافة الخيارات بواسطة JavaScript -->
    </select>

    <label for="to-currency">إلى العملة:</label>
    <select id="to-currency">
      <!-- سيتم إضافة الخيارات بواسطة JavaScript -->
    </select>

    <button id="convert-btn">تحويل</button>

    <div class="result">
      <p>النتيجة: <span id="result"></span></p>
    </div>
  </div>
</div>
const fromCurrency = document.getElementById('from-currency');
const toCurrency = document.getElementById('to-currency');
const amountInput = document.getElementById('amount');
const result = document.getElementById('result');
const convertButton = document.getElementById('convert-btn');

const currencies = [
  { name: 'دولار أمريكي', code: 'USD' },
  { name: 'يورو', code: 'EUR' },
  { name: 'جنيه إسترليني', code: 'GBP' },
  { name: 'ين ياباني', code: 'JPY' },
  { name: 'ريال سعودي', code: 'SAR' },
  { name: 'دولار كندي', code: 'CAD' },
  { name: 'فرنك سويسري', code: 'CHF' },
  { name: 'دولار أسترالي', code: 'AUD' },
  { name: 'روبل روسي', code: 'RUB' },
  { name: 'درهم إماراتي', code: 'AED' },
  { name: 'جنيه مصري', code: 'EGP' },
  { name: 'ريال قطري', code: 'QAR' },
  { name: 'راند جنوب أفريقي', code: 'ZAR' },
  { name: 'بيزو مكسيكي', code: 'MXN' }
];

currencies.forEach(currency => {
  const optionFrom = document.createElement('option');
  optionFrom.value = currency.code;
  optionFrom.textContent = `${currency.name} (${currency.code})`;
  fromCurrency.appendChild(optionFrom);

  const optionTo = document.createElement('option');
  optionTo.value = currency.code;
  optionTo.textContent = `${currency.name} (${currency.code})`;
  toCurrency.appendChild(optionTo);
});

convertButton.addEventListener('click', async () => {
  const from = fromCurrency.value;
  const to = toCurrency.value;
  const amount = parseFloat(amountInput.value);

  if (!amount || from === to) {
    result.textContent = 'يرجى إدخال قيمة صحيحة.';
    return;
  }

  try {
    const response = await fetch(`https://api.exchangerate-api.com/v4/latest/${from}`);
    const data = await response.json();

    const exchangeRate = data.rates[to];
    const convertedAmount = amount * exchangeRate;

    result.textContent = `${amount} ${from} = ${convertedAmount.toFixed(2)} ${to}`;
  } catch (error) {
    result.textContent = 'حدث خطأ أثناء جلب البيانات. حاول مرة أخرى.';
  }
});
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Arial', sans-serif;
  background-color: #f7f7f7;
  color: #333;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.container {
  background-color: #fff;
  padding: 30px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 500px;
}

h1 {
  text-align: center;
  color: #4CAF50;
  font-size: 28px;
  margin-bottom: 20px;
}

.currency-converter {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

label {
  font-size: 16px;
}

input, select, button {
  padding: 10px;
  font-size: 16px;
  border-radius: 6px;
  border: 1px solid #ddd;
  margin-top: 5px;
}

button {
  background-color: #4CAF50;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #45a049;
}

.result {
  text-align: center;
  font-size: 18px;
  font-weight: bold;
  color: #4CAF50;
}

select, input {
  width: 100%;
}
