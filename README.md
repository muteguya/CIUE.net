here<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>CIUE · Register & Earn</title>
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

    /* Balance Display */
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

    /* Welcome header */
    .welcome-section {
      margin-bottom: 22px;
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
    }

    .action-item:hover i {
      background: #00bcd4;
      color: white;
    }

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
    }

    .logout-btn {
      background: none;
      border: 1px solid #cae3e8;
      color: #006a7a;
      padding: 8px 15px;
      border-radius: 30px;
      cursor: pointer;
      font-size: 0.9rem;
      transition: all 0.2s;
    }

    .logout-btn:hover {
      background: #fff0e0;
      border-color: #ff9800;
      color: #ff9800;
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

    <!-- MAIN DASHBOARD (hidden initially) -->
    <div id="mainDashboard">
      <!-- header with user greeting -->
      <div class="welcome-section">
        <div class="hello-tag" id="userGreeting">
          <i class="far fa-hand-peace" style="margin-right: 6px;"></i> 
          WELCOME BACK, <span id="userName">USER</span>
        </div>
        <div class="main-headline">
          NEW OPPORTUNITIES <span>Collaborate and earn together</span>
        </div>
        <div class="divider"></div>
      </div>

      <!-- Balance Display -->
      <div class="balance-container">
        <div class="balance-label">
          <i class="fas fa-wallet"></i>
          <div class="balance-info">
            <h4>Available Balance</h4>
            <div class="amount" id="balanceAmount">12,500 <small>UGX</small></div>
          </div>
        </div>
        <button class="logout-btn" onclick="logout()">
          <i class="fas fa-sign-out-alt"></i> Logout
        </button>
      </div>

      <!-- Task Hall area -->
      <div class="task-hall-label">
        <i class="fas fa-clipboard-list"></i>
        <h3>Task Hall</h3>
      </div>
      <span class="teaser-badge">✨ TEASER · fresh tasks</span>

      <div class="card-grid">
        <div class="reward-card">
          <div class="card-left">
            <div class="card-icon"><i class="fas fa-bolt"></i></div>
            <span class="card-title">TEASER</span>
          </div>
          <div class="card-value">+1,200 <small>UGX</small></div>
        </div>
        <div class="reward-card">
          <div class="card-left">
            <div class="card-icon"><i class="fas fa-chart-line"></i></div>
            <span class="card-title">VAF</span>
          </div>
          <div class="card-value">+1,200 <small>UGX</small></div>
        </div>
        <div class="reward-card">
          <div class="card-left">
            <div class="card-icon"><i class="fas fa-lightbulb"></i></div>
            <span class="card-title">Out of Ideas</span>
          </div>
          <div class="card-value">+1,200 <small>UGX</small></div>
        </div>
      </div>

      <!-- Action row -->
      <div class="action-row">
        <div class="action-item" onclick="alert('Deposit feature coming soon!')">
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
      
      // Get form values
      const fullName = document.getElementById('regFullName').value.trim();
      const phone = document.getElementById('regPhone').value.trim();
      const country = document.getElementById('regCountry').value;
      const password = document.getElementById('regPassword').value;
      const confirmPass = document.getElementById('regConfirmPassword').value;
      
      // Validate
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
      
      // Check if user already exists in localStorage
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      
      if (users[phone]) {
        showMessage('This phone number is already registered. Please login.', false);
        switchAuthTab('login');
        return;
      }
      
      // Save user
      users[phone] = {
        fullName: fullName,
        phone: phone,
        country: country,
        password: password,
        registeredDate: new Date().toISOString(),
        balance: 12500 // Starting balance
      };
      
      localStorage.setItem('cueUsers', JSON.stringify(users));
      
      // Auto login after registration
      localStorage.setItem('currentUser', phone);
      
      showMessage('Registration successful! Welcome to CIUE!');
      
      // Show dashboard
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
      
      // Get users from localStorage
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[phone];
      
      if (!user || user.password !== password) {
        showMessage('Invalid phone number or password', false);
        return;
      }
      
      // Save current user
      localStorage.setItem('currentUser', phone);
      
      showMessage('Login successful! Welcome back!');
      
      // Show dashboard
      setTimeout(() => {
        showDashboard(phone);
      }, 1000);
    }

    // Show dashboard with user info
    function showDashboard(phone) {
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      const user = users[phone];
      
      if (!user) return;
      
      // Update greeting
      document.getElementById('userName').textContent = user.fullName.split(' ')[0];
      document.getElementById('balanceAmount').innerHTML = `${user.balance.toLocaleString()} <small>UGX</small>`;
      
      // Hide auth, show dashboard
      document.getElementById('authContainer').style.display = 'none';
      document.getElementById('mainDashboard').style.display = 'block';
    }

    // Logout function
    function logout() {
      localStorage.removeItem('currentUser');
      document.getElementById('authContainer').style.display = 'block';
      document.getElementById('mainDashboard').style.display = 'none';
      switchAuthTab('login');
      
      // Clear forms
      document.getElementById('loginPhone').value = '';
      document.getElementById('loginPassword').value = '';
    }

    // Check if user is already logged in on page load
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
      
      // Add country flags mapping
      const countryFlags = {
        'UG': '🇺🇬 Uganda',
        'KE': '🇰🇪 Kenya',
        'TZ': '🇹🇿 Tanzania',
        'BI': '🇧🇮 Burundi',
        'SS': '🇸🇸 South Sudan'
      };
    }

    // Demo accounts for testing
    function createDemoAccounts() {
      const users = JSON.parse(localStorage.getItem('cueUsers') || '{}');
      
      // Add demo account if none exists
      if (Object.keys(users).length === 0) {
        users['0756673144'] = {
          fullName: 'NAMUHANGA VERONIC',
          phone: '0756673144',
          country: 'UG',
          password: '123456',
          registeredDate: new Date().toISOString(),
          balance: 12500
        };
        localStorage.setItem('cueUsers', JSON.stringify(users));
      }
    }
    
    // Create demo account on first load
    createDemoAccounts();
  </script>
</body>
</html>
