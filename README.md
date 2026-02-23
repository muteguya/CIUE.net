<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>CIUE · mobile money deposit</title>
  <!-- Font Awesome 6 (free) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background: #eef2f7;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 16px;
    }

    /* phone frame */
    .phone {
      max-width: 390px;
      width: 100%;
      background-color: #ffffff;
      border-radius: 40px;
      box-shadow: 0 25px 60px rgba(0, 20, 30, 0.15), 0 8px 20px rgba(0, 40, 60, 0.1);
      overflow: hidden;
      padding: 20px 18px 12px 18px;
      transition: all 0.2s;
    }

    /* header */
    .welcome-section {
      margin-bottom: 28px;
    }

    .hello-tag {
      color: #006064;
      font-size: 0.85rem;
      font-weight: 600;
      letter-spacing: 0.8px;
      text-transform: uppercase;
      margin-bottom: 6px;
    }

    .main-headline {
      font-size: 1.9rem;
      font-weight: 700;
      line-height: 1.2;
      color: #0b2b3b;
    }

    .main-headline span {
      display: block;
      font-size: 1rem;
      font-weight: 400;
      color: #3f5e6b;
      margin-top: 6px;
      letter-spacing: -0.2px;
    }

    .divider {
      height: 2px;
      background: linear-gradient(90deg, #00bcd4 0%, #b2ebf2 70%, #e0f7fa 100%);
      width: 70px;
      margin: 18px 0 20px 0;
      border-radius: 4px;
    }

    /* collaboration text */
    .collab-text {
      font-size: 1.2rem;
      font-weight: 500;
      color: #1d4e5f;
      margin-bottom: 24px;
      line-height: 1.3;
    }

    .collab-text i {
      color: #00acc1;
      margin-right: 6px;
    }

    /* TASK HALL section – cards */
    .task-hall-label {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 18px;
    }

    .task-hall-label h3 {
      font-size: 1.5rem;
      font-weight: 700;
      color: #003d4d;
      letter-spacing: -0.3px;
    }

    .task-hall-label i {
      font-size: 1.6rem;
      color: #00bcd4;
      background: #e0f7fa;
      padding: 8px;
      border-radius: 18px;
    }

    .teaser-badge {
      background: #00838f;
      color: white;
      padding: 6px 14px;
      border-radius: 100px;
      font-size: 0.8rem;
      font-weight: 600;
      display: inline-block;
      margin-bottom: 12px;
      letter-spacing: 0.3px;
    }

    /* card grid */
    .card-grid {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 28px;
    }

    .reward-card {
      background: #f9fbfd;
      border-radius: 28px;
      padding: 16px 22px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid #d6e9ed;
      box-shadow: 0 5px 12px rgba(0, 140, 150, 0.06);
      transition: all 0.2s;
    }

    .reward-card:hover {
      background: #f0fafc;
      border-color: #4dd0e1;
    }

    .card-left {
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .card-icon {
      width: 48px;
      height: 48px;
      background: #d2f1f5;
      border-radius: 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #006a7a;
      font-size: 1.5rem;
    }

    .card-title {
      font-weight: 700;
      font-size: 1.2rem;
      color: #144f5c;
    }

    .card-value {
      font-weight: 800;
      font-size: 1.3rem;
      background: linear-gradient(145deg, #006a7a, #00b2c9);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      letter-spacing: 0.5px;
    }

    .card-value small {
      font-size: 0.8rem;
      font-weight: 500;
      color: #3f98a7;
      background: none;
      -webkit-text-fill-color: #3f98a7;
    }

    /* action row (recharge / withdraw / profile) */
    .action-row {
      display: flex;
      align-items: center;
      justify-content: space-around;
      background: #ecf7f9;
      padding: 12px 10px;
      border-radius: 60px;
      margin: 24px 0 20px 0;
    }

    .action-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 6px;
      color: #006b7a;
      font-weight: 500;
      font-size: 0.9rem;
      cursor: pointer;
      transition: all 0.2s;
    }

    .action-item i {
      font-size: 1.5rem;
      background: white;
      padding: 10px;
      border-radius: 40px;
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 10px rgba(0,150,160,0.15);
      color: #006a7a;
      transition: 0.15s;
    }

    .action-item:hover i {
      background: #00bcd4;
      color: white;
    }

    /* company profile line */
    .company-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: white;
      border: 1px solid #cae3e8;
      padding: 12px 18px;
      border-radius: 30px;
      margin-bottom: 22px;
    }

    .company-line span {
      font-weight: 600;
      color: #1b4e5b;
      font-size: 1rem;
    }

    .company-line i {
      color: #00a5b9;
      font-size: 1.3rem;
    }

    /* bottom nav */
    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      background: #ffffff;
      padding: 8px 0 6px 0;
      border-top: 2px solid #e3f0f3;
      margin-top: 12px;
    }

    .nav-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      color: #597e89;
      font-size: 0.75rem;
      font-weight: 500;
      gap: 4px;
      transition: 0.1s;
    }

    .nav-item i {
      font-size: 1.4rem;
      color: #89b8c5;
    }

    .nav-item.active {
      color: #006a7a;
    }

    .nav-item.active i {
      color: #00b2c9;
      text-shadow: 0 2px 6px #b0e6ee;
    }

    /* balance display */
    .balance-container {
      background: linear-gradient(135deg, #e0f7fa, #b2ebf2);
      border-radius: 30px;
      padding: 16px 20px;
      margin-bottom: 24px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid #80deea;
    }

    .balance-label {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .balance-label i {
      font-size: 2rem;
      color: #006064;
      background: white;
      padding: 10px;
      border-radius: 50%;
    }

    .balance-info h4 {
      color: #004d5a;
      font-size: 0.9rem;
      font-weight: 500;
    }

    .balance-info .amount {
      font-size: 2rem;
      font-weight: 800;
      color: #00363a;
      line-height: 1.2;
    }

    .balance-info .amount small {
      font-size: 0.9rem;
      font-weight: 500;
      color: #006a7a;
    }

    .history-btn {
      background: white;
      border: none;
      padding: 8px 16px;
      border-radius: 30px;
      color: #006a7a;
      font-weight: 600;
      cursor: pointer;
      box-shadow: 0 2px 8px rgba(0,100,110,0.2);
    }

    /* deposit modal */
    .modal-overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }

    .modal-content {
      background: white;
      max-width: 390px;
      width: 90%;
      border-radius: 40px;
      padding: 24px;
      box-shadow: 0 30px 60px rgba(0,50,60,0.4);
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .modal-header h2 {
      color: #006064;
      font-size: 1.6rem;
    }

    .close-btn {
      background: none;
      border: none;
      font-size: 1.8rem;
      color: #597e89;
      cursor: pointer;
    }

    /* recipient info */
    .recipient-card {
      background: #e0f7fa;
      border-radius: 20px;
      padding: 16px;
      margin-bottom: 24px;
      text-align: center;
      border: 2px dashed #00838f;
    }

    .recipient-card i {
      font-size: 2rem;
      color: #006064;
      margin-bottom: 8px;
    }

    .recipient-card .number {
      font-size: 1.5rem;
      font-weight: 800;
      color: #003d4d;
      letter-spacing: 1px;
    }

    .recipient-card .name {
      color: #006a7a;
      font-weight: 600;
      margin-top: 5px;
    }

    .recipient-card .warning {
      font-size: 0.8rem;
      color: #d32f2f;
      margin-top: 10px;
      background: #ffebee;
      padding: 5px;
      border-radius: 30px;
    }

    .deposit-option {
      background: #f0fafc;
      border: 2px solid #b2ebf2;
      border-radius: 20px;
      padding: 16px;
      margin-bottom: 16px;
      display: flex;
      align-items: center;
      gap: 15px;
      cursor: pointer;
      transition: all 0.2s;
    }

    .deposit-option:hover {
      background: #e0f7fa;
      border-color: #00bcd4;
      transform: scale(1.02);
    }

    .deposit-option i {
      font-size: 2.2rem;
      color: #006a7a;
      width: 50px;
      text-align: center;
    }

    .deposit-option .info h3 {
      color: #003d4d;
      margin-bottom: 4px;
    }

    .deposit-option .info p {
      color: #3f5e6b;
      font-size: 0.9rem;
    }

    .custom-amount {
      margin-top: 20px;
    }

    .custom-amount input {
      width: 100%;
      padding: 18px;
      border: 2px solid #b2ebf2;
      border-radius: 30px;
      font-size: 1.1rem;
      text-align: center;
      font-weight: 600;
      color: #006064;
    }

    .deposit-btn {
      background: linear-gradient(135deg, #006a7a, #00bcd4);
      color: white;
      border: none;
      width: 100%;
      padding: 18px;
      border-radius: 40px;
      font-size: 1.2rem;
      font-weight: 700;
      margin-top: 20px;
      cursor: pointer;
      transition: 0.2s;
    }

    .deposit-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(0,150,170,0.4);
    }

    .ussd-code {
      background: #f5f5f5;
      padding: 15px;
      border-radius: 20px;
      text-align: center;
      margin: 15px 0;
      font-size: 1.3rem;
      font-weight: 800;
      color: #003d4d;
      letter-spacing: 2px;
      border: 1px solid #00bcd4;
    }

    .transaction-history {
      margin-top: 20px;
      max-height: 200px;
      overflow-y: auto;
    }

    .transaction-item {
      display: flex;
      justify-content: space-between;
      padding: 12px;
      border-bottom: 1px solid #e0f0f3;
    }
  </style>
</head>
<body>
  <div class="phone">
    <!-- header with CIUE -->
    <div class="welcome-section">
      <div class="hello-tag"><i class="far fa-hand-peace" style="margin-right: 6px;"></i> CIUE · FRESH</div>
      <div class="main-headline">
        NEW OPPORTUNITIES <span>and challenges work together to create a better future</span>
      </div>
      <div class="divider"></div>
    </div>

    <!-- Collaboration belief line -->
    <div class="collab-text">
      <i class="fas fa-handshake"></i> Collaboration. We believe that every employee can:
    </div>

    <!-- BALANCE DISPLAY -->
    <div class="balance-container">
      <div class="balance-label">
        <i class="fas fa-wallet"></i>
        <div class="balance-info">
          <h4>Available Balance</h4>
          <div class="amount" id="balanceAmount">12,500 <small>UGX</small></div>
        </div>
      </div>
      <button class="history-btn" onclick="showHistory()"><i class="fas fa-history"></i> History</button>
    </div>

    <!-- Task Hall area -->
    <div class="task-hall-label">
      <i class="fas fa-clipboard-list"></i>
      <h3>Task Hall</h3>
    </div>
    <span class="teaser-badge">✨ TEASER · fresh tasks</span>

    <div class="card-grid">
      <!-- TEASER card -->
      <div class="reward-card">
        <div class="card-left">
          <div class="card-icon"><i class="fas fa-bolt"></i></div>
          <span class="card-title">TEASER</span>
        </div>
        <div class="card-value">+1,200 <small>UGX</small></div>
      </div>
      <!-- VAF card -->
      <div class="reward-card">
        <div class="card-left">
          <div class="card-icon"><i class="fas fa-chart-line"></i></div>
          <span class="card-title">VAF</span>
        </div>
        <div class="card-value">+1,200 <small>UGX</small></div>
      </div>
      <!-- Out of Ideas card -->
      <div class="reward-card">
        <div class="card-left">
          <div class="card-icon"><i class="fas fa-lightbulb"></i></div>
          <span class="card-title">Out of Ideas</span>
        </div>
        <div class="card-value">+1,200 <small>UGX</small></div>
      </div>
    </div>

    <!-- Action row with clickable recharge -->
    <div class="action-row">
      <div class="action-item" onclick="openDepositModal()">
        <i class="fas fa-wallet"></i>
        <span>Recharge</span>
      </div>
      <div class="action-item" onclick="alert('Withdraw feature coming soon!')">
        <i class="fas fa-hand-holding-usd"></i>
        <span>Withdraw</span>
      </div>
      <div class="action-item" onclick="alert('Company profile')">
        <i class="fas fa-building"></i>
        <span>Company</span>
      </div>
    </div>

    <!-- Company Profile line -->
    <div class="company-line">
      <span><i class="far fa-id-card" style="margin-right: 10px; color: #00838f;"></i> Company Profile</span>
      <i class="fas fa-chevron-right"></i>
    </div>

    <!-- bottom nav -->
    <div class="bottom-nav">
      <div class="nav-item active">
        <i class="fas fa-home"></i>
        <span>Home</span>
      </div>
      <div class="nav-item">
        <i class="fas fa-tasks"></i>
        <span>Task</span>
      </div>
      <div class="nav-item">
        <i class="fas fa-chart-simple"></i>
        <span>Level</span>
      </div>
      <div class="nav-item">
        <i class="fas fa-coins"></i>
        <span>Income</span>
      </div>
      <div class="nav-item">
        <i class="fas fa-user"></i>
        <span>Me</span>
      </div>
    </div>
  </div>

  <!-- DEPOSIT MODAL - with Mobile Money integration -->
  <div class="modal-overlay" id="depositModal">
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-mobile-alt"></i> Mobile Money</h2>
        <button class="close-btn" onclick="closeDepositModal()">&times;</button>
      </div>
      
      <!-- Recipient info (fixed to 0756673144 / NAMUHANGA VERONIC) -->
      <div class="recipient-card">
        <i class="fas fa-user-check"></i>
        <div class="number">0756 673 144</div>
        <div class="name">NAMUHANGA VERONIC</div>
        <div class="warning">
          <i class="fas fa-exclamation-triangle"></i> Send money to this number only
        </div>
      </div>

      <!-- Quick deposit options (these will auto-fill the amount) -->
      <div class="deposit-option" onclick="setDepositAmount(10000)">
        <i class="fas fa-bolt"></i>
        <div class="info">
          <h3>10,000 UGX</h3>
          <p>Quick deposit</p>
        </div>
      </div>
      
      <div class="deposit-option" onclick="setDepositAmount(50000)">
        <i class="fas fa-star"></i>
        <div class="info">
          <h3>50,000 UGX</h3>
          <p>Most popular</p>
        </div>
      </div>
      
      <div class="deposit-option" onclick="setDepositAmount(100000)">
        <i class="fas fa-crown"></i>
        <div class="info">
          <h3>100,000 UGX</h3>
          <p>Premium</p>
        </div>
      </div>
      
      <!-- Custom amount -->
      <div class="custom-amount">
        <input type="number" id="customAmount" placeholder="Enter amount (UGX)" min="1000" step="1000">
      </div>

      <!-- USSD Code Display (dynamic based on amount) -->
      <div class="ussd-code" id="ussdDisplay">
        *165*1*0756673144*<span id="amountDisplay">AMOUNT</span>#
      </div>
      
      <button class="deposit-btn" onclick="processDeposit()">
        <i class="fas fa-mobile-alt"></i> Pay with Mobile Money
      </button>
      
      <!-- Transaction history -->
      <div id="historySection" style="display: none;" class="transaction-history">
        <h3 style="color: #006064; margin-bottom: 10px;">Recent deposits</h3>
        <div id="transactionList"></div>
      </div>
    </div>
  </div>

  <script>
    // Balance and transaction data
    let currentBalance = 12500;
    let transactions = [
      { type: 'deposit', amount: 10000, date: '2024-01-15' },
      { type: 'deposit', amount: 2500, date: '2024-01-14' }
    ];
    
    // Fixed recipient details
    const RECIPIENT_NUMBER = '0756673144';
    const RECIPIENT_NAME = 'NAMUHANGA VERONIC';
    
    // Update balance display
    function updateBalanceDisplay() {
      document.getElementById('balanceAmount').innerHTML = currentBalance.toLocaleString() + ' <small>UGX</small>';
    }
    
    // Modal functions
    function openDepositModal() {
      document.getElementById('depositModal').style.display = 'flex';
      updateUssdCode(); // Update USSD with current amount
    }
    
    function closeDepositModal() {
      document.getElementById('depositModal').style.display = 'none';
    }
    
    // Set amount from quick options and update USSD
    function setDepositAmount(amount) {
      document.getElementById('customAmount').value = amount;
      updateUssdCode();
    }
    
    // Update USSD code based on entered amount
    function updateUssdCode() {
      let amount = document.getElementById('customAmount').value;
      if (!amount || amount < 1000) {
        amount = 'AMOUNT';
      } else {
        amount = parseInt(amount).toLocaleString() + ' UGX';
      }
      document.getElementById('amountDisplay').textContent = amount;
    }
    
    // Listen for custom amount changes
    document.getElementById('customAmount')?.addEventListener('input', updateUssdCode);
    
    // Process deposit - opens mobile money dialer with USSD
    function processDeposit() {
      let amount = parseInt(document.getElementById('customAmount').value);
      
      if (!amount || amount < 1000) {
        alert('❌ Please enter a valid amount (minimum 1000 UGX)');
        return;
      }
      
      // Confirm with user
      if (confirm(`Send ${amount.toLocaleString()} UGX to ${RECIPIENT_NUMBER} (${RECIPIENT_NAME})?\n\nYou will be redirected to mobile money.`)) {
        
        // Format USSD code for Uganda (MTN/Airtel)
        // Format: *165*1*0756673144*amount#
        const ussdCode = `*165*1*${RECIPIENT_NUMBER}*${amount}#`;
        
        // Try to open USSD dialer (works on most Android phones)
        window.location.href = `tel:${ussdCode}`;
        
        // Fallback for iOS/browsers that don't support tel: for USSD
        setTimeout(() => {
          alert(`📱 Dial ${ussdCode} manually to complete payment`);
        }, 500);
        
        // Record transaction locally (for demo purposes)
        currentBalance += amount;
        transactions.unshift({
          type: 'deposit',
          amount: amount,
          date: new Date().toLocaleDateString()
        });
        
        updateBalanceDisplay();
        
        // Don't close modal immediately - user needs to complete payment
        // Show confirmation but keep modal open
        alert(`⏳ Payment initiated!\n\nPlease complete the transaction on your phone.\n\nOnce payment is confirmed, your balance will update automatically.`);
      }
    }
    
    // Show transaction history
    function showHistory() {
      let historyDiv = document.getElementById('historySection');
      let transactionList = document.getElementById('transactionList');
      
      // Build transaction HTML
      let html = '';
      transactions.forEach(t => {
        html += `
          <div class="transaction-item">
            <span><i class="fas fa-arrow-down" style="color: #00a86b;"></i> +${t.amount.toLocaleString()} UGX</span>
            <span style="color: #597e89;">${t.date}</span>
          </div>
        `;
      });
      
      if (transactions.length === 0) {
        html = '<p style="color: #597e89; text-align: center;">No transactions yet</p>';
      }
      
      transactionList.innerHTML = html;
      
      // Toggle history display
      if (historyDiv.style.display === 'none') {
        historyDiv.style.display = 'block';
        // Open modal if closed
        document.getElementById('depositModal').style.display = 'flex';
      } else {
        historyDiv.style.display = 'none';
      }
    }
    
    // Close modal when clicking outside
    window.onclick = function(event) {
      let modal = document.getElementById('depositModal');
      if (event.target === modal) {
        modal.style.display = 'none';
      }
    }
    
    // Initialize balance and amount display
    updateBalanceDisplay();
  </script>

  <!-- publish instructions -->
  <div style="max-width:390px; margin:24px auto 0; text-align: center; font-size:0.8rem; background: #fff4e6; padding: 12px 14px; border-radius: 60px; color:#3a5e69;">
    <i class="fas fa-globe" style="margin-right: 8px;"></i> 
    <strong>How to publish (make it live):</strong> Save as index.html, upload to Netlify, Vercel, or any web host. When users click deposit, they'll be prompted to send money to 0756673144 (NAMUHANGA VERONIC).
  </div>
</body>
</html>
