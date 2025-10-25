# my-website
Made by armaan
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Money Monitoring System</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f9;
      margin: 20px;
      padding: 20px;
    }
    h1 {
      text-align: center;
      
      color: #333;
    }
    form {
      max-width: 400px;
      margin: 20px auto;
      padding: 20px;
      background: white;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
    }
    input, select, button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ddd;
      border-radius: 5px;
    }
    button {
      background-color: #28a745;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #218838;
    }
    table {
      width: 100%;
      margin-top: 20px;
      border-collapse: collapse;
    }
    th, td {
      border: 1px solid #ddd;
      padding: 10px;
      text-align: center;
    }
    th {
      background-color: #007bff;
      color: white;
    }
  </style>
</head>
<body>
  <h1>Money Monitoring System</h1>
  
  <form id="transactionForm">
    <label for="description">Description:</label>
    <input type="text" id="description" placeholder="e.g., Salary, Grocery" required>
    
    <label for="amount">Amount:</label>
    <input type="number" id="amount" placeholder="Enter amount" required>
    
    <label for="type">Type:</label>
    <select id="type" required>
      <option value="income">Income</option>
      <option value="expense">Expense</option>
    </select>
    
    <button type="button" onclick="addTransaction()">Add Transaction</button>
  </form>
  
  <table>
    <thead>
      <tr>
        <th>Description</th>
        <th>Type</th>
        <th>Amount</th>
        <th>Balance</th>
      </tr>
    </thead>
    <tbody id="transactionsTable">
      <!-- Transactions will be added here dynamically -->
    </tbody>
  </table>

  <script>
    let balance = 0;

    function addTransaction() {
      const description = document.getElementById('description').value;
      const amount = parseFloat(document.getElementById('amount').value);
      const type = document.getElementById('type').value;

      if (!description || !amount || isNaN(amount)) {
        alert("Please fill out all fields.");
        return;
      }

      // Update balance
      if (type === 'income') {
        balance += amount;
      } else if (type === 'expense') {
        balance -= amount;
      }

      // Add transaction to the table
      const table = document.getElementById('transactionsTable');
      const row = document.createElement('tr');
      row.innerHTML = `
        <td>${description}</td>
        <td>${type.charAt(0).toUpperCase() + type.slice(1)}</td>
        <td>${amount.toFixed(2)}</td>
        <td>${balance.toFixed(2)}</td>
      `;
      table.appendChild(row);

      // Clear form fields
      document.getElementById('description').value = '';
      document.getElementById('amount').value = '';
      document.getElementById('type').value = 'income';
    }
  </script>
</body>
</html>
