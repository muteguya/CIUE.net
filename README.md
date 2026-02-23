<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>CIUE · Welcome</title>
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
      background: #ffffff;
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
      box-shadow: 0 25px 60px rgba(0, 20, 30, 0.15);
      overflow: hidden;
      padding: 30px 20px 20px 20px;
    }

    /* Auth Pages */
    .auth-container {
      padding: 10px 0;
    }

    .logo-area {
      text-align: center;
      margin-bottom: 25px;
    }

    .logo-icon {
      width: 80px;
      height: 80px;
      background: linear-gradient(135deg, #006a7a, #00bcd4);
      border-radius: 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 15px;
      color: white;
      font-size: 2.5rem;
      box-shadow: 0 10px 25px rgba(0,150,170,0.3);
    }

    .logo-area h1 {
      color: #003d4d;
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 5px;
    }

    .logo-area p {
      color: #597e89;
      font-size: 0.9rem;
    }

    .auth-tabs {
      display: flex;
      background: #ecf7f9;
      border-radius: 60px;
      padding: 5px;
      margin-bottom: 25px;
    }

    .auth-tab {
      flex: 1;
      text-align: center;
      padding: 12px;
      border-radius: 60px;
      font-weight: 600;
      color: #006a7a;
      cursor: pointer;
      transition: all 0.2s;
    }

    .auth-tab.active {
      background: white;
      color: #003d4d;
      box-shadow: 0 4px 10px rgba(0,150,160,0.15);
    }

    .auth-form {
      display: none;
    }

    .auth-form.active {
      display: block;
    }

    .form-group {
      margin-bottom: 20px;
    }

    .form-group label {
      display: block;
      color: #003d4d;
      font-weight: 600;
      margin-bottom: 8px;
      font-size: 0.9rem;
    }

    .input-icon {
      position: relative;
      display: flex;
      align-items: center;
    }

    .input-icon i {
      position: absolute;
      left: 15px;
      color: #00acc1;
      font-size: 1.1rem;
    }

    .input-icon input,
    .input-icon select {
      width: 100%;
      padding: 15px 15px 15px 45px;
      border: 2px solid #e0f0f3;
      border-radius: 30px;
      font-size: 1rem;
      outline: none;
      transition: all 0.2s;
      background: white;
    }

    .input-icon input:focus,
    .input-icon select:focus {
      border-color: #00bcd4;
      box-shadow: 0 0 0 3px rgba(0,188,212,0.1);
    }

    .country-select {
      width: 100%;
      padding: 15px 15px 15px 45px;
      border: 2px solid #e0f0f3;
      border-radius: 30px;
      font-size: 1rem;
      outline: none;
      background: white;
      color: #003d4d;
      cursor: pointer;
    }

    .password-hint {
      font-size: 0.8rem;
      color: #597e89;
      margin-top: 5px;
    }

    .auth-btn {
      background: linear-gradient(135deg, #006a7a, #00bcd4);
      color: white;
      border: none;
      width: 100%;
      padding: 18px;
      border-radius: 40px;
      font-size: 1.2rem;
      font-weight: 700;
      margin: 20px 0 15px;
      cursor: pointer;
      transition: 0.2s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }

    .auth-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(0,150,170,0.4);
    }

    .auth-footer {
      text-align: center;
      color: #597e89;
      font-size: 0.9rem;
    }

    .auth-footer a {
      color: #006a7a;
      font-weight: 600;
      text-decoration: none;
    }

    .terms {
      text-align: center;
      font-size: 0.8rem;
      color: #89b8c5;
      margin-top: 20px;
    }

    .terms a {
      color: #006a7a;
      text-decoration: none;
    }

    /* Success Message */
    .success-message {
      background: #d4edda;
      color: #155724;
      padding: 15px;
      border-radius: 30px;
      text-align: center;
      margin-bottom: 20px;
      border: 2px solid #c3e6cb;
      display: none;
    }

    .success-message i {
      margin-right: 8px;
    }

    /* Main Dashboard (hidden initially) */
    #mainDashboard {
      display: none;
    }

    /* Welcome Section - REDESIGNED to match image */
    .welcome-section {
      margin-bottom: 30px;
    }

    .welcome-title {
      font-size: 2.2rem;
      font-weight: 700;
      color: #000000;
      line-height: 1.2;
      margin-bottom: 5px;
    }

    .welcome-subtitle {
      font-size: 1rem;
      font-weight: 400;
      color: #333333;
      line-height: 1.4;
      margin-bottom: 20px;
      max-width: 90%;
    }

    .divider-line {
      width: 100%;
      height: 1px;
      background-color: #e0e0e0;
      margin: 15px 0;
    }

    /* Collaboration Text */
    .collab-title {
      font-size: 1.1rem;
      font-weight: 600;
      color: #000000;
      margin-bottom: 20px;
    }

    .collab-title i {
      color: #006a7a;
      margin-right: 8px;
    }

    /* Task Hall Section */
    .task-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 20px;
    }

    .task-header h3 {
      font-size: 1.5rem;
      font-weight: 700;
      color: #000000;
    }

    .teaser-badge {
      background: #333333;
      color: white;
      padding: 6px 16px;
      border-radius: 30px;
      font-size: 0.8rem;
      font-weight: 600;
      display: inline-block;
      letter-spacing: 0.5px;
    }

    /* Card Grid - Redesigned to match image */
    .card-grid {
      display: flex;
      flex-direction: column;
      gap: 15px;
      margin-bottom: 30px;
    }

    .reward-card {
      background: #ffffff;
      border-radius: 0;
      padding: 15px 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid #f0f0f0;
    }

    .card-left {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .card-title {
      font-weight: 600;
      font-size: 1.1rem;
      color: #000000;
    }

    .card-value {
      font-weight: 700;
      font-size: 1.1rem;
      color: #000000;
    }

    .card-value small {
      font-size: 0.8rem;
      font-weight: 400;
      color: #666666;
      margin-left: 2px;
    }

    /* Action Row - Redesigned to match image */
    .action-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin: 25px 0 20px 0;
    }

    .action-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 5px;
      color: #000000;
      font-weight: 500;
      font-size: 0.9rem;
      cursor: pointer;
    }

    .action-item i {
      font-size: 1.3rem;
      color: #000000;
    }

    .company-line {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: white;
      padding: 15px 0;
      border-bottom: 1px solid #f0f0f0;
      margin-bottom: 20px;
    }

    .company-line span {
      font-weight: 500;
      color: #000000;
      font-size: 1rem;
    }

    .company-line i {
      color: #000000;
      font-size: 1rem;
    }

    /* Bottom Navigation - Redesigned to match image */
    .bottom-nav {
      display: flex;
      align-items: center;
      justify-content: space-around;
      background: #ffffff;
      padding: 15px 0 10px 0;
      border-top: 1px solid #f0f0f0;
      margin-top: 10px;
    }

    .nav-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      color: #999999;
      font-size: 0.75rem;
      font-weight: 500;
      gap: 4px;
    }

    .nav-item i {
      font-size: 1.3rem;
      color: #999999;
    }

    .nav-item.active {
      color: #000000;
    }

    .nav-item.active i {
      color: #000000;
    }

    /* Balance Display - Keep for functionality but style simply */
    .balance-container {
      background: #f9f9f9;
      border-radius: 10px;
      padding: 15px;
      margin-bottom: 25px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border: 1px solid #eaeaea;
    }

    .balance-label {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .balance-label i {
      font-size: 1.5rem;
      color: #333;
    }

    .balance-info h4 {
      color: #666;
      font-size: 0.8rem;
      font-weight: 400;
    }

    .balance-info .amount {
      font-size: 1.5rem;
      font-weight: 700;
      color: #000;
      line-height: 1.2;
    }

    .balance-info .amount small {
      font-size: 0.8rem;
      font-weight: 400;
      color: #666;
    }

    .history-btn {
      background: none;
      border: 1px solid #ddd;
      padding: 8px 12px;
      border-radius: 20px;
      color: #333;
      font-weight: 500;
      cursor: pointer;
      font-size: 0.8rem;
    }

    .logout-btn {
      background: none;
      border: 1px solid #ddd;
      color: #333;
      padding: 8px 15px;
      border-radius: 20px;
      cursor: pointer;
      font-size: 0.9rem;
    }

    .logout-btn:hover {
      background: #f5f5f5;
    }

    /* Deposit Modal Styles */
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
      border-radius: 30px;
      padding: 24px;
      box-shadow: 0 30px 60px rgba(0,0,0,0.2);
      max-height: 90vh;
      overflow-y: auto;
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .modal-header h2 {
      color: #000;
      font-size: 1.4rem;
    }

    .close-btn {
      background: none;
      border: none;
      font-size: 1.8rem;
      color: #999;
      cursor: pointer;
    }

    .recipient-card {
      background: #f9f9f9;
      border-radius: 15px;
      padding: 16px;
      margin-bottom: 20px;
      text-align: center;
      border: 1px solid #eaeaea;
    }

    .recipient-card .number {
      font-size: 1.3rem;
      font-weight: 700;
      color: #000;
    }

    .recipient-card .name {
      color: #666;
      font-weight: 500;
      margin-top: 5px;
    }

    .deposit-option {
      background: #f9f9f9;
      border: 1px solid #eaeaea;
      border-radius: 15px;
      padding: 15px;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 15px;
      cursor: pointer;
    }

    .deposit-option:hover {
      background: #f0f0f0;
    }

    .deposit-option i {
      font-size: 1.8rem;
      color: #333;
    }

    .deposit-option .info h3 {
      color: #000;
      font-size: 1.1rem;
      margin-bottom: 3px;
    }

    .deposit-option .info p {
      color: #666;
      font-size: 0.8rem;
    }

    .custom-amount input {
      width: 100%;
      padding: 15px;
      border: 1px solid #ddd;
      border-radius: 15px;
      font-size: 1rem;
      text-align: center;
    }

    .ussd-code {
      background: #f5f5f5;
      padding: 15px;
      border-radius: 15px;
      text-align: center;
      margin: 15px 0;
      font-size: 1.1rem;
      font-weight: 600;
      color: #000;
      border: 1px solid #ddd;
    }

    .deposit-btn {
      background: #000;
      color: white;
      border: none;
      width: 100%;
      padding: 16px;
      border-radius: 30px;
      font-size: 1.1rem;
      font-weight: 600;
      margin-top: 15px;
      cursor: pointer;
    }

    .deposit-btn:hover {
      background: #333;
    }
  </style>
</head>
<body>
  <div class="phone">
    <!-- AUTHENTICATION SECTION -->
    <div id="authContainer" class="auth-container">
      <div class="logo-area">
        <div class="logo-icon">
          <i class="fas fa-hand-holding-heart"></i>
        </div>
        <h1>CIUE</h1>
        <p>Mobile Money • Earn • Task Hall</p>
      </div>

      <!-- Success/Error Message -->
      <div id="messageBox" class="success-message">
        <i class="fas fa-check-circle"></i> <span id="messageText"></span>
      </div>

      <!-- Auth Tabs -->
      <div class="auth-tabs">
        <div class="auth-tab active" onclick="switchAuthTab('login')" id="loginTab">Login</div>
        <div class="auth-tab" onclick="switchAuthTab('register')" id="registerTab">Register</div>
      </div>

      <!-- LOGIN FORM -->
      <div id="loginForm" class="auth-form active">
        <form onsubmit="handleLogin(event)">
          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-icon">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="loginPhone" placeholder="0756 673 144" required>
            </div>
          </div>

          <div class="form-group">
            <label>Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="loginPassword" placeholder="••••••••" required>
            </div>
          </div>

          <button type="submit" class="auth-btn">
            <i class="fas fa-sign-in-alt"></i> Login
          </button>

          <div class="auth-footer">
            Don't have an account? <a href="#" onclick="switchAuthTab('register'); return false;">Register now</a>
          </div>
        </form>
      </div>

      <!-- REGISTRATION FORM -->
      <div id="registerForm" class="auth-form">
        <form onsubmit="handleRegister(event)">
          <div class="form-group">
            <label>Full Names</label>
            <div class="input-icon">
              <i class="fas fa-user"></i>
              <input type="text" id="regFullName" placeholder="Enter your full names" required>
            </div>
          </div>

          <div class="form-group">
            <label>Phone Number</label>
            <div class="input-icon">
              <i class="fas fa-phone-alt"></i>
              <input type="tel" id="regPhone" placeholder="0756 673 144" required>
            </div>
          </div>

          <div class="form-group">
            <label>Country</label>
            <div class="input-icon">
              <i class="fas fa-globe-africa"></i>
              <select id="regCountry" class="country-select" required>
                <option value="">Select your country</option>
                <option value="UG">Uganda 🇺🇬</option>
                <option value="KE">Kenya 🇰🇪</option>
                <option value="TZ">Tanzania 🇹🇿</option>
                <option value="BI">Burundi 🇧🇮</option>
                <option value="SS">South Sudan 🇸🇸</option>
              </select>
            </div>
          </div>

          <div class="form-group">
            <label>Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="regPassword" placeholder="Create a password" required>
            </div>
            <div class="password-hint">Minimum 6 characters</div>
          </div>

          <div class="form-group">
            <label>Confirm Password</label>
            <div class="input-icon">
              <i class="fas fa-lock"></i>
              <input type="password" id="regConfirmPassword" placeholder="Confirm your password" required>
            </div>
          </div>

          <button type="submit" class="auth-btn">
            <i class="fas fa-user-plus"></i> Register
          </button>

          <div class="auth-footer">
            Already have an account? <a href="#" onclick="switchAuthTab('login'); return false;">Login here</a>
          </div>

          <div class="terms">
            By registering, you agree to our <a href="#">Terms</a> and <a href="#">Privacy Policy</a>
          </div>
        </form>
      </div>
    </div>

    <!-- MAIN DASHBOARD - REDESIGNED TO MATCH IMAGE -->
    <div id="mainDashboard">
      <!-- Welcome header exactly as in image -->
      <div class="welcome-section">
        <div class="welcome-title">WELCOME</div>
        <div class="welcome-subtitle">NEW OPPORTUNITIES AND CHALLENGES WORK TOGETHER TO CREATE A BETTER FUTURE</div>
        <div class="divider-line"></div>
      </div>

      <!-- Balance Display (functional but minimal) -->
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

      <!-- Collaboration text as in image -->
      <div class="collab-title">
        <i class="fas fa-handshake"></i> Collaboration. We Believe That Every Employee Can:
      </div>

      <!-- Task Hall section as in image -->
      <div class="task-header">
        <h3>Task Hall</h3>
        <span class="teaser-badge">TEASER</span>
      </div>

      <!-- Cards exactly as in image -->
      <div class="card-grid">
        <div class="reward-card">
          <div class="card-left">
            <span class="card-title">TEASER</span>
          </div>
          <div class="card-value">+1200.00 <small>UGX</small></div>
        </div>
        
        <div class="reward-card">
          <div class="card-left">
            <span class="card-title">VAF</span>
          </div>
          <div class="card-value">+1200.00 <small>UGX</small></div>
        </div>
        
        <div class="reward-card">
          <div class="card-left">
            <span class="card-title">Out of Ideas</span>
          </div>
          <div class="card-value">+1200.00 <small>UGX</small></div>
        </div>
      </div>

      <!-- Action row exactly as in image (bullet points) -->
      <div class="action-row">
        <div class="action-item" onclick="openDepositModal()">
          <span>• Recharge</span>
        </div>
        <div class="action-item" onclick="alert('Withdraw feature coming soon!')">
          <span>• Withdraw</span>
        </div>
        <div class="action-item" onclick="alert('Company profile')">
          <span>• Company Profile</span>
        </div>
      </div>

      <!-- Company Profile line (simple) -->
      <div class="company-line">
        <span>Company Profile</span>
        <i class="fas fa-chevron-right"></i>
      </div>

      <!-- Bottom navigation exactly as in image -->
      <div class="bottom-nav">
        <div class="nav-item active">
          <span>Home</span>
        </div>
        <div class="nav-item">
          <span>Task</span>
        </div>
        <div class="nav-item">
          <span>Level</span>
        </div>
        <div class="nav-item">
          <span>Income</span>
        </div>
        <div class="nav-item">
          <span>Me</span>
        </div>
      </div>
      
      <!-- Logout button -->
      <div style="text-align: center; margin-top: 20px;">
        <button class="logout-btn" onclick="logout()">
          <i class="fas fa-sign-out-alt"></i> Logout
        </button>
      </div>
    </div>
  </div>

  <!-- DEPOSIT MODAL -->
  <div class="modal-overlay" id="depositModal">
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-mobile-alt"></i> Mobile Money</h2>
        <button class="close-btn" onclick="closeDepositModal()">&times;</button>
      </div>
      
      <!-- Recipient info -->
      <div class="recipient-card">
        <div class="number">0756 673 144</div>
        <div class="name">NAMUHANGA VERONIC</div>
      </div>

      <!-- Quick deposit options -->
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

      <!-- USSD Code Display -->
      <div class="ussd-code" id="ussdDisplay">
        *165*1*0756673144*<span id="amountDisplay">AMOUNT</span>#
      </div>
      
      <button class="deposit-btn" onclick="processDeposit()">
        <i class="fas fa-mobile-alt"></i> Pay with Mobile Money
      </button>
      
      <!-- Transaction history -->
      <div id="historySection" style="display: none;" class="transaction-history">
        <h3 style="margin-bottom: 10px;">Recent deposits</h3>
        <div id="transactionList"></div>
      </div>
    </div>
  </div>

  <script>
    // Show message function
    function showMessage(text, isSuccess = true) {
      const msgBox = document.getElementById('messageBox');
      const msgText = document.getElementById('messageText');
      msgText.textContent = text;
      msgBox.style.display = 'block';
      msgBox.style.background = isSuccess ? '#d4edda' : '#f8d7da';
      msgBox.style.color = isSuccess ? '#155724' : '#721c24';
      msgBox.style.borderColor = isSuccess ? '#c3e6cb' : '#f5c6cb';
      
      setTimeout(() => {
        msgBox.style.display = 'none';
      }, 3000);
    }

    // Switch between login and register tabs
    function switchAuthTab(tab) {
      const loginForm = document.getElementById('loginForm');
      const registerForm = document.getElementById('registerForm');
      const loginTab = document.getElementById('loginTab');
      const registerTab = document.getElementById('registerTab');
      
      if (tab === 'login') {
        loginForm.classList.add('active');
        registerForm.classList.remove('active');
        loginTab.classList.add('active');
        registerTab.classList.remove('active');
      } else {
        registerForm.classList.add('active');
        loginForm.classList.remove('active');
        registerTab.classList.add('active');
        loginTab.classList.remove('active');
      }
    }

    // Handle Registration
    function handleRegister(event) {
      event.preventDefault();
      
      const fullName = document.getElementById('regFullName').value.trim();
      const phone = document.getElementById('regPhone').value.trim();
      const country = document.getElementById('regCountry').value;
      const password = document.getElementById('regPassword').value;
      const confirmPass = document.getElementById('regConfirmPassword').value;
      
      if (!fullName || !phone || !country || !password || !confirmPass) {
        showMessage('Please fill in all fields', false);
        return;
      }
      
      if (password.length < 6) {
        showMessage('Password must be at least 6 characters', false);
        return;
      }
      
      if (password !== confirmPass) {
        showMessage('Passwords do not match', false);
        return;
      }
      
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      
      if (users[phone]) {
        showMessage('This phone number is already registered. Please login.', false);
        switchAuthTab('login');
        return;
      }
      
      users[phone] = {
        fullName: fullName,
        phone: phone,
        country: country,
        password: password,
        registeredDate: new Date().toISOString(),
        balance: 12500,
        transactions: [
          { type: 'deposit', amount: 10000, date: '2024-01-15' },
          { type: 'deposit', amount: 2500, date: '2024-01-14' }
        ]
      };
      
      localStorage.setItem('cueUsers', JSON.stringify(users));
      localStorage.setItem('currentUser', phone);
      
      showMessage('Registration successful! Welcome to CIUE!');
      
      setTimeout(() => {
        showDashboard(phone);
      }, 1000);
    }

    // Handle Login
    function handleLogin(event) {
      event.preventDefault();
      
      const phone = document.getElementById('loginPhone').value.trim();
      const password = document.getElementById('loginPassword').value;
      
      if (!phone || !password) {
        showMessage('Please enter phone number and password', false);
        return;
      }
      
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[phone];
      
      if (!user || user.password !== password) {
        showMessage('Invalid phone number or password', false);
        return;
      }
      
      localStorage.setItem('currentUser', phone);
      
      showMessage('Login successful! Welcome back!');
      
      setTimeout(() => {
        showDashboard(phone);
      }, 1000);
    }

    // Show dashboard with user info
    function showDashboard(phone) {
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[phone];
      
      if (!user) return;
      
      document.getElementById('balanceAmount').innerHTML = `${(user.balance || 12500).toLocaleString()} <small>UGX</small>`;
      window.currentUserPhone = phone;
      
      document.getElementById('authContainer').style.display = 'none';
      document.getElementById('mainDashboard').style.display = 'block';
    }

    // Logout function
    function logout() {
      localStorage.removeItem('currentUser');
      document.getElementById('authContainer').style.display = 'block';
      document.getElementById('mainDashboard').style.display = 'none';
      switchAuthTab('login');
      
      document.getElementById('loginPhone').value = '';
      document.getElementById('loginPassword').value = '';
    }

    // DEPOSIT MODAL FUNCTIONS
    const RECIPIENT_NUMBER = '0756673144';
    const RECIPIENT_NAME = 'NAMUHANGA VERONIC';
    
    function openDepositModal() {
      document.getElementById('depositModal').style.display = 'flex';
      updateUssdCode();
    }
    
    function closeDepositModal() {
      document.getElementById('depositModal').style.display = 'none';
    }
    
    function setDepositAmount(amount) {
      document.getElementById('customAmount').value = amount;
      updateUssdCode();
    }
    
    function updateUssdCode() {
      let amount = document.getElementById('customAmount').value;
      if (!amount || amount < 1000) {
        amount = 'AMOUNT';
      } else {
        amount = parseInt(amount).toLocaleString() + ' UGX';
      }
      document.getElementById('amountDisplay').textContent = amount;
    }
    
    function processDeposit() {
      let amount = parseInt(document.getElementById('customAmount').value);
      
      if (!amount || amount < 1000) {
        alert('❌ Please enter a valid amount (minimum 1000 UGX)');
        return;
      }
      
      if (confirm(`Send ${amount.toLocaleString()} UGX to ${RECIPIENT_NUMBER} (${RECIPIENT_NAME})?`)) {
        
        const ussdCode = `*165*1*${RECIPIENT_NUMBER}*${amount}#`;
        window.location.href = `tel:${ussdCode}`;
        
        setTimeout(() => {
          alert(`📱 Dial ${ussdCode} manually to complete payment`);
        }, 500);
        
        const currentUser = localStorage.getItem('currentUser');
        if (currentUser) {
          const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
          if (users[currentUser]) {
            users[currentUser].balance = (users[currentUser].balance || 12500) + amount;
            if (!users[currentUser].transactions) users[currentUser].transactions = [];
            users[currentUser].transactions.unshift({
              type: 'deposit',
              amount: amount,
              date: new Date().toLocaleDateString()
            });
            localStorage.setItem('cueUsers', JSON.stringify(users));
            
            document.getElementById('balanceAmount').innerHTML = `${users[currentUser].balance.toLocaleString()} <small>UGX</small>`;
          }
        }
        
        alert(`⏳ Payment initiated!\n\nPlease complete the transaction on your phone.`);
      }
    }
    
    function showHistory() {
      let historyDiv = document.getElementById('historySection');
      let transactionList = document.getElementById('transactionList');
      
      const currentUser = localStorage.getItem('currentUser');
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[currentUser];
      const transactions = user?.transactions || [];
      
      let html = '';
      transactions.forEach(t => {
        html += `
          <div style="display:flex; justify-content:space-between; padding:8px 0; border-bottom:1px solid #eee;">
            <span>+${t.amount.toLocaleString()} UGX</span>
            <span style="color:#666;">${t.date}</span>
          </div>
        `;
      });
      
      if (transactions.length === 0) {
        html = '<p style="color:#666; text-align:center;">No transactions yet</p>';
      }
      
      transactionList.innerHTML = html;
      
      if (historyDiv.style.display === 'none') {
        historyDiv.style.display = 'block';
        openDepositModal();
      } else {
        historyDiv.style.display = 'none';
      }
    }
    
    window.onclick = function(event) {
      let modal = document.getElementById('depositModal');
      if (event.target === modal) {
        modal.style.display = 'none';
      }
    }
    
    document.getElementById('customAmount')?.addEventListener('input', updateUssdCode);

    window.onload = function() {
      const currentUser = localStorage.getItem('currentUser');
      
      if (currentUser) {
        const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
        if (users[currentUser]) {
          showDashboard(currentUser);
        } else {
          localStorage.removeItem('currentUser');
        }
      }
      
      // Create demo account if none exists
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      if (Object.keys(users).length === 0) {
        users['0756673144'] = {
          fullName: 'NAMUHANGA VERONIC',
          phone: '0756673144',
          country: 'UG',
          password: '123456',
          registeredDate: new Date().toISOString(),
          balance: 12500,
          transactions: [
            { type: 'deposit', amount: 10000, date: '2024-01-15' },
            { type: 'deposit', amount: 2500, date: '2024-01-14' }
          ]
        };
        localStorage.setItem('cueUsers', JSON.stringify(users));
      }
    }
  </script>
</body>
</html>
