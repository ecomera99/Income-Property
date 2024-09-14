<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Real Estate Deal Analyzer</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        .calculator { max-width: 600px; margin: auto; }
        label { display: block; margin-top: 10px; }
        input { width: 100%; padding: 8px; }
        button { margin-top: 20px; padding: 10px 20px; }
        .result { background-color: #f0f0f0; padding: 10px; margin-top: 20px; }
        .result h3 { margin-top: 20px; }
    </style>
</head>
<body>
    <div class="calculator">
        <h1>Real Estate Deal Analyzer</h1>
        <form id="dealForm">
            <label for="purchasePrice">Purchase Price ($):</label>
            <input type="number" id="purchasePrice" required>

            <label for="downPayment">Down Payment (%):</label>
            <input type="number" id="downPayment" required>

            <label for="interestRate">Interest Rate (%):</label>
            <input type="number" id="interestRate" required>

            <label for="loanTerm">Loan Term (Years):</label>
            <input type="number" id="loanTerm" required>

            <label for="annualIncome">Gross Annual Rental Income ($):</label>
            <input type="number" id="annualIncome" required>

            <label for="annualExpenses">Total Annual Operating Expenses ($):</label>
            <input type="number" id="annualExpenses" required>

            <button type="button" onclick="calculate()">Calculate</button>
        </form>

        <div class="result" id="results" style="display: none;">
            <h2>Income Breakdown & Metrics</h2>
            <div>
                <h3>Net Operating Income (NOI)</h3>
                <p><strong>Income:</strong> $<span id="incomeDisplay"></span></p>
                <p><strong>Expenses:</strong> $<span id="expensesDisplay"></span></p>
                <p><strong>Net Operating Income:</strong> $<span id="noiDisplay"></span></p>
            </div>
            <div>
                <h3>Cash Flow Per Year</h3>
                <p><strong>Net Operating Income:</strong> $<span id="noiDisplay2"></span></p>
                <p><strong>Less: Mortgage Payment:</strong> $<span id="mortgagePaymentDisplay"></span></p>
                <p><strong>Annual Cash Flow:</strong> $<span id="annualCashFlowDisplay"></span></p>
            </div>
            <div>
                <h3>Cash on Cash Return</h3>
                <p><strong>Annual Cash Flow:</strong> $<span id="annualCashFlowDisplay2"></span></p>
                <p><strong>Down Payment:</strong> $<span id="downPaymentAmountDisplay"></span></p>
                <p><strong>Cash on Cash Return:</strong> <span id="cashOnCashReturnDisplay"></span>%</p>
            </div>
            <div>
                <h3>Cap Rate</h3>
                <p><strong>Net Operating Income:</strong> $<span id="noiDisplay3"></span></p>
                <p><strong>Purchase Price:</strong> $<span id="purchasePriceDisplay"></span></p>
                <p><strong>Cap Rate:</strong> <span id="capRateDisplay"></span>%</p>
            </div>
            <div>
                <h3>Expense Ratio</h3>
                <p><strong>Total Expenses:</strong> $<span id="expensesDisplay2"></span></p>
                <p><strong>Total Revenue:</strong> $<span id="incomeDisplay2"></span></p>
                <p><strong>Operating Expense %:</strong> <span id="expenseRatioDisplay"></span>%</p>
            </div>
            <div>
                <h3>Gross Annual Return</h3>
                <p><strong>Gross Annual Rental Income:</strong> $<span id="incomeDisplay3"></span></p>
                <p><strong>Purchase Price:</strong> $<span id="purchasePriceDisplay2"></span></p>
                <p><strong>Gross Annual Return:</strong> <span id="grossAnnualReturnDisplay"></span>%</p>
            </div>
        </div>
    </div>

    <script>
        function calculate() {
            // Get input values
            var purchasePrice = parseFloat(document.getElementById('purchasePrice').value);
            var downPaymentPercent = parseFloat(document.getElementById('downPayment').value) / 100;
            var interestRatePercent = parseFloat(document.getElementById('interestRate').value) / 100;
            var loanTermYears = parseFloat(document.getElementById('loanTerm').value);
            var annualIncome = parseFloat(document.getElementById('annualIncome').value);
            var annualExpenses = parseFloat(document.getElementById('annualExpenses').value);

            // Calculations
            var downPaymentAmount = purchasePrice * downPaymentPercent;
            var loanAmount = purchasePrice - downPaymentAmount;

            // Mortgage Payment Calculation
            var monthlyInterestRate = interestRatePercent / 12;
            var numberOfPayments = loanTermYears * 12;
            var monthlyMortgagePayment = (loanAmount * monthlyInterestRate) / (1 - Math.pow(1 + monthlyInterestRate, -numberOfPayments));
            var annualMortgagePayment = monthlyMortgagePayment * 12;

            // Net Operating Income (NOI)
            var noi = annualIncome - annualExpenses;

            // Annual Cash Flow
            var annualCashFlow = noi - annualMortgagePayment;

            // Cash on Cash Return
            var cashOnCashReturn = (annualCashFlow / downPaymentAmount) * 100;

            // Cap Rate
            var capRate = (noi / purchasePrice) * 100;

            // Expense Ratio
            var expenseRatio = (annualExpenses / annualIncome) * 100;

            // Gross Annual Return
            var grossAnnualReturn = (annualIncome / purchasePrice) * 100;

            // Display the results
            document.getElementById('incomeDisplay').textContent = annualIncome.toFixed(2);
            document.getElementById('expensesDisplay').textContent = annualExpenses.toFixed(2);
            document.getElementById('noiDisplay').textContent = noi.toFixed(2);

            document.getElementById('noiDisplay2').textContent = noi.toFixed(2);
            document.getElementById('mortgagePaymentDisplay').textContent = annualMortgagePayment.toFixed(2);
            document.getElementById('annualCashFlowDisplay').textContent = annualCashFlow.toFixed(2);

            document.getElementById('annualCashFlowDisplay2').textContent = annualCashFlow.toFixed(2);
            document.getElementById('downPaymentAmountDisplay').textContent = downPaymentAmount.toFixed(2);
            document.getElementById('cashOnCashReturnDisplay').textContent = cashOnCashReturn.toFixed(2);

            document.getElementById('noiDisplay3').textContent = noi.toFixed(2);
            document.getElementById('purchasePriceDisplay').textContent = purchasePrice.toFixed(2);
            document.getElementById('capRateDisplay').textContent = capRate.toFixed(2);

            document.getElementById('expensesDisplay2').textContent = annualExpenses.toFixed(2);
            document.getElementById('incomeDisplay2').textContent = annualIncome.toFixed(2);
            document.getElementById('expenseRatioDisplay').textContent = expenseRatio.toFixed(2);

            document.getElementById('incomeDisplay3').textContent = annualIncome.toFixed(2);
            document.getElementById('purchasePriceDisplay2').textContent = purchasePrice.toFixed(2);
            document.getElementById('grossAnnualReturnDisplay').textContent = grossAnnualReturn.toFixed(2);

            // Show the results section
            document.getElementById('results').style.display = 'block';
        }
    </script>
</body>
</html>
