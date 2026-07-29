# fazaahamdanremotejobs.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>fazaahamdanremotejobs</title>
  <script src="https://js.stripe.com/v3/"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');
    
    body {
      font-family: 'Inter', sans-serif;
      margin: 0;
      background: #f8fafc;
      color: #1f2937;
    }
    .header {
      background: linear-gradient(135deg, #1e40af, #3b82f6);
      color: white;
      padding: 25px 20px;
      text-align: center;
    }
    .header h1 {
      margin: 0;
      font-size: 26px;
      font-weight: 700;
    }
    .container {
      max-width: 600px;
      margin: 20px auto;
      padding: 20px;
      background: white;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    }
    h2 {
      font-size: 22px;
      margin-bottom: 20px;
      color: #1e40af;
    }
    h3 {
      font-size: 18px;
      color: #1e40af;
      margin-top: 20px;
    }
    input, select, textarea, button {
      width: 100%;
      padding: 15px;
      margin: 10px 0;
      border: 1px solid #e5e7eb;
      border-radius: 12px;
      font-size: 16px;
      box-sizing: border-box;
    }
    button {
      background: #2563eb;
      color: white;
      font-weight: 600;
      cursor: pointer;
      border: none;
    }
    button:active {
      background: #1e40af;
    }
    button:disabled {
      background: #94a3b8;
      cursor: not-allowed;
    }
    .step {
      display: none;
    }
    .step.active {
      display: block;
    }
    .progress {
      display: flex;
      justify-content: space-between;
      margin-bottom: 30px;
    }
    .progress div {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background: #e5e7eb;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
    }
    .progress div.active {
      background: #2563eb;
      color: white;
    }
    .upload-box {
      border: 2px dashed #94a3b8;
      padding: 20px;
      text-align: center;
      border-radius: 12px;
      margin: 10px 0;
      background: #f8fafc;
    }
    .plan-option {
      border: 2px solid #e5e7eb;
      padding: 15px;
      margin: 10px 0;
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.3s;
    }
    .plan-option.selected {
      border-color: #2563eb;
      background: #f0f9ff;
    }
    .plan-option.vip.selected {
      border-color: #f59e0b;
      background: #fffbeb;
    }
    .price {
      font-size: 24px;
      font-weight: 700;
      color: #1e40af;
    }
    .price.vip {
      color: #b45309;
    }
    .stripe-card {
      border: 1px solid #e5e7eb;
      padding: 15px;
      border-radius: 12px;
      background: #fafafa;
      min-height: 50px;
    }
    .form-row {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
    }
    .note {
      font-size: 14px;
      color: #64748b;
      margin: 10px 0;
    }
    .badge {
      display: inline-block;
      padding: 2px 8px;
      border-radius: 6px;
      font-size: 12px;
      font-weight: 600;
    }
    .badge-vip {
      background: #fef3c7;
      color: #b45309;
    }
    .badge-premium {
      background: #dbeafe;
      color: #1e40af;
    }
    .badge-free {
      background: #e5e7eb;
      color: #4b5563;
    }
    /* Dashboard styles */
    .dashboard {
      display: none;
    }
    .dashboard.active {
      display: block;
    }
    .stat-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      margin-bottom: 20px;
    }
    .stat-card {
      background: #f8fafc;
      border: 1px solid #e5e7eb;
      border-radius: 12px;
      padding: 16px;
      text-align: center;
    }
    .stat-card .label {
      font-size: 13px;
      color: #64748b;
      margin-bottom: 4px;
    }
    .stat-card .value {
      font-size: 22px;
      font-weight: 700;
      color: #1e40af;
    }
    .stat-card .value.bonus {
      color: #059669;
    }
    .stat-card .sub {
      font-size: 12px;
      color: #94a3b8;
      margin-top: 4px;
    }
    .earnings-table {
      width: 100%;
      border-collapse: collapse;
      margin: 15px 0;
      font-size: 14px;
    }
    .earnings-table th, .earnings-table td {
      padding: 10px 8px;
      text-align: left;
      border-bottom: 1px solid #e5e7eb;
    }
    .earnings-table th {
      background: #f1f5f9;
      font-weight: 600;
      color: #475569;
    }
    .earnings-table tr.current-tier {
      background: #eff6ff;
      font-weight: 600;
    }
    .countdown-box {
      background: #fef3c7;
      border: 1px solid #fcd34d;
      border-radius: 12px;
      padding: 16px;
      text-align: center;
      margin: 15px 0;
    }
    .countdown-box .timer {
      font-size: 28px;
      font-weight: 700;
      color: #b45309;
      font-variant-numeric: tabular-nums;
    }
    .info-box {
      background: #f0f9ff;
      border: 1px solid #bae6fd;
      border-radius: 12px;
      padding: 14px;
      margin: 12px 0;
      font-size: 14px;
      color: #0369a1;
    }
    .warning-box {
      background: #fef2f2;
      border: 1px solid #fecaca;
      border-radius: 12px;
      padding: 14px;
      margin: 12px 0;
      font-size: 14px;
      color: #b91c1c;
    }
    .success-box {
      background: #ecfdf5;
      border: 1px solid #a7f3d0;
      border-radius: 12px;
      padding: 14px;
      margin: 12px 0;
      font-size: 14px;
      color: #047857;
    }
    .locked-overlay {
      opacity: 0.55;
      pointer-events: none;
      position: relative;
    }
    .locked-badge {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: rgba(0,0,0,0.75);
      color: white;
      padding: 8px 16px;
      border-radius: 8px;
      font-size: 13px;
      font-weight: 600;
      z-index: 2;
    }
    .job-list {
      list-style: none;
      padding: 0;
      margin: 0;
    }
    .job-item {
      border: 1px solid #e5e7eb;
      border-radius: 10px;
      padding: 12px 14px;
      margin: 8px 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: relative;
    }
    .job-item .job-title {
      font-weight: 600;
      font-size: 15px;
    }
    .job-item .job-rate {
      font-size: 13px;
      color: #059669;
      font-weight: 600;
    }
    .btc-note {
      font-size: 13px;
      color: #b45309;
      margin-top: 4px;
    }
    .section-divider {
      border: none;
      border-top: 1px solid #e5e7eb;
      margin: 24px 0;
    }
  </style>
</head>
<body>
  <div class="header">
    <h1>info.remotejobs.com</h1>
  </div>

  <div class="container">
    <!-- ==================== ONBOARDING FLOW ==================== -->
    <div id="onboarding">
      <div class="progress" id="progress">
        <div class="active">1</div>
        <div>2</div>
        <div>3</div>
        <div>4</div>
        <div>5</div>
      </div>

      <!-- Step 1: Account Creation -->
      <div class="step active" id="step1">
        <h2>Create Your Account</h2>
        <input type="text" id="fullName" placeholder="Full Name" required>
        <input type="email" id="email" placeholder="Email Address" required>
        <input type="password" id="password" placeholder="Create Password" required>
        <button onclick="nextStep(2)">Continue</button>
      </div>

      <!-- Step 2: Job Categories -->
      <div class="step" id="step2">
        <h2>Select Jobs You Are Familiar With</h2>
        <div id="categoriesContainer" style="margin-bottom: 20px;"></div>
        <button onclick="nextStep(3)">Next</button>
      </div>

      <!-- Step 3: Qualifications -->
      <div class="step" id="step3">
        <h2>Your Qualifications</h2>
        <textarea id="experience" rows="4" placeholder="Describe your experience..."></textarea>
        <input type="text" id="skills" placeholder="Skills (comma separated)">
        <button onclick="nextStep(4)">Next</button>
      </div>

      <!-- Step 4: ID Upload -->
      <div class="step" id="step4">
        <h2>Upload Your ID Card (Front & Back)</h2>
        <div class="upload-box">
          <p><strong>ID Front Side</strong></p>
          <input type="file" accept="image/*" id="idFront">
        </div>
        <div class="upload-box">
          <p><strong>ID Back Side</strong></p>
          <input type="file" accept="image/*" id="idBack">
        </div>
        <button onclick="nextStep(5)">Next</button>
      </div>

      <!-- Step 5: Subscription & Payment -->
      <div class="step" id="step5">
        <h2>Choose Your Plan</h2>
        
        <div id="planOptions">
          <!-- Populated by JS -->
        </div>

        <!-- Premium Payment Section (shown only for premium) -->
        <div id="premiumPayment" style="display: none; margin-top: 25px;">
          <h3>Payment Details (Card)</h3>
          <p class="note">Subscription fee will be charged via Stripe. $20/month or $190/year.</p>
          
          <div class="form-row">
            <input type="text" id="cardName" placeholder="Full Name on Card" required>
            <input type="email" id="paymentEmail" placeholder="Billing Email" value="" required>
          </div>

          <div id="card-element" class="stripe-card">
            <!-- Stripe Card Element will be mounted here -->
          </div>
          <div id="card-errors" style="color: #ef4444; font-size: 14px; margin-top: 8px;"></div>

          <div class="form-row">
            <input type="text" id="address" placeholder="Address" required>
            <input type="text" id="suburb" placeholder="Suburb">
          </div>
          <div class="form-row">
            <input type="text" id="city" placeholder="City" required>
            <input type="text" id="state" placeholder="State" required>
          </div>
          <input type="text" id="postalCode" placeholder="Postal Code" required>

          <div style="margin: 20px 0;">
            <label>
              <input type="checkbox" id="tos" required> I agree to the <a href="#" style="color:#2563eb;">Terms of Service</a> and <a href="#" style="color:#2563eb;">Privacy Policy</a>
            </label>
          </div>
        </div>

        <!-- VIP / BTC Payment Section -->
        <div id="vipPayment" style="display: none; margin-top: 25px;">
          <h3>VIP Payment (Bitcoin)</h3>
          <p class="note">One-time VIP upgrade: <strong>$499 USD</strong> paid in BTC. After payment is confirmed on-chain by our backend, your <code>upgradeCompleted</code> flag will be set and VIP jobs unlock.</p>
          <div class="info-box">
            Send exactly the amount shown to the address below. Do not send other amounts or tokens.
          </div>
          <input type="text" id="btcAddress" value="bc1qexamplevippaymentaddress000000000000" readonly style="font-family: monospace; font-size: 13px;">
          <p class="btc-note">Amount due: ≈ 0.00725 BTC (rate locked at checkout — illustrative)</p>
          <input type="text" id="btcTxId" placeholder="Paste your BTC Transaction ID (TXID) after sending">
          <div style="margin: 16px 0;">
            <label>
              <input type="checkbox" id="tosVip" required> I agree to the <a href="#" style="color:#2563eb;">Terms of Service</a> and <a href="#" style="color:#2563eb;">Privacy Policy</a>
            </label>
          </div>
        </div>

        <!-- Withdrawal Info (for all users) -->
        <h3 style="margin-top: 30px;">Bank Card for Withdrawal</h3>
        <div class="upload-box">
          <p><strong>Bank Card Front</strong></p>
          <input type="file" accept="image/*" id="bankFront">
        </div>
        <div class="upload-box">
          <p><strong>Bank Card Back</strong></p>
          <input type="file" accept="image/*" id="bankBack">
        </div>
        <select id="paymentMethod">
          <option value="">Select Withdrawal Method</option>
          <option value="bank">Bank Transfer</option>
          <option value="paypal">PayPal</option>
        </select>
        <input type="text" id="bankName" placeholder="Preferred Bank Name">

        <button onclick="completeSetup()" style="margin-top: 20px;" id="completeBtn">Complete Setup & Pay (if applicable)</button>
      </div>
    </div>

    <!-- ==================== DASHBOARD ==================== -->
    <div id="dashboard" class="dashboard">
      <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom: 8px;">
        <h2 style="margin:0;">Your Dashboard</h2>
        <span id="tierBadge" class="badge badge-free">Free</span>
      </div>
      <p class="note" id="welcomeMsg">Welcome back!</p>

      <!-- Stats -->
      <div class="stat-grid">
        <div class="stat-card">
          <div class="label">Available Balance</div>
          <div class="value" id="balanceValue">$0.00</div>
          <div class="sub">Withdrawable when unlocked</div>
        </div>
        <div class="stat-card">
          <div class="label">Welcome Bonus</div>
          <div class="value bonus" id="bonusValue">$25.00</div>
          <div class="sub">Non-withdrawable</div>
        </div>
        <div class="stat-card">
          <div class="label">Your Rate</div>
          <div class="value" id="rateValue">$8/hr</div>
          <div class="sub" id="rateSub">Free tier</div>
        </div>
        <div class="stat-card">
          <div class="label">Jobs Access</div>
          <div class="value" id="jobsAccessValue" style="font-size:18px;">Limited</div>
          <div class="sub" id="jobsAccessSub">Upgrade for more</div>
        </div>
      </div>

      <!-- Earnings rates per tier -->
      <h3>Earnings Rates by Tier</h3>
      <table class="earnings-table">
        <thead>
          <tr>
            <th>Tier</th>
            <th>Hourly Rate</th>
            <th>Jobs Access</th>
            <th>Priority</th>
          </tr>
        </thead>
        <tbody>
          <tr id="row-free">
            <td>Free</td>
            <td>$8 / hr</td>
            <td>Limited (5 jobs)</td>
            <td>Standard</td>
          </tr>
          <tr id="row-premium">
            <td>Premium</td>
            <td>$15 / hr</td>
            <td>100+ jobs</td>
            <td>Priority support</td>
          </tr>
          <tr id="row-vip">
            <td>VIP <span class="badge badge-vip">BTC</span></td>
            <td>$35 / hr</td>
            <td>All VIP jobs</td>
            <td>Highest + dedicated</td>
          </tr>
        </tbody>
      </table>

      <!-- Withdraw countdown (shown after VIP upgrade) -->
      <div id="withdrawCountdownSection" style="display: none;">
        <h3>Withdrawal Availability</h3>
        <div class="countdown-box">
          <div style="font-size:14px; color:#92400e; margin-bottom:6px;">Withdrawals unlock in</div>
          <div class="timer" id="countdownTimer">48:00:00</div>
          <div class="note" style="margin-top:8px; color:#92400e;">Security hold after VIP upgrade. Countdown starts only after backend sets <code>upgradeCompleted = true</code>.</div>
        </div>
      </div>

      <!-- Identity verification required for withdrawal (UI only) -->
      <div id="identityVerifySection">
        <h3>Identity Verification Required for Withdrawal</h3>
        <div class="warning-box">
          Before any withdrawal can be processed, identity verification must be completed. This is a UI placeholder — real verification is handled by your backend.
        </div>
        <div class="upload-box">
          <p><strong>Government ID (Front)</strong></p>
          <input type="file" accept="image/*" id="verifyIdFront">
        </div>
        <div class="upload-box">
          <p><strong>Government ID (Back)</strong></p>
          <input type="file" accept="image/*" id="verifyIdBack">
        </div>
        <div class="upload-box">
          <p><strong>Selfie holding ID</strong></p>
          <input type="file" accept="image/*" id="verifySelfie">
        </div>
        <button type="button" onclick="submitIdentityVerification()">Submit for Verification</button>
        <div id="verifyStatus" class="info-box" style="display:none;"></div>
      </div>

      <hr class="section-divider">

      <!-- Jobs section (VIP gated) -->
      <h3>Available Jobs</h3>
      <div id="jobsListContainer">
        <ul class="job-list" id="jobList">
          <!-- Populated by JS -->
        </ul>
      </div>

      <hr class="section-divider">

      <!-- Withdraw section -->
      <h3>Request Withdrawal</h3>
      <div id="withdrawLockedMsg" class="warning-box" style="display:none;">
        Withdrawals are locked until the security countdown finishes and identity verification is approved.
      </div>
      <input type="number" id="withdrawAmount" placeholder="Amount (USD)" min="10" step="0.01">
      <button id="withdrawBtn" onclick="requestWithdraw()" disabled>Request Withdrawal</button>
      <p class="note">Welcome bonus is non-withdrawable and cannot be included in any payout.</p>

      <!-- Demo controls (simulate backend) -->
      <hr class="section-divider">
      <h3 style="color:#64748b; font-size:15px;">Demo / Backend Simulation</h3>
      <p class="note">In production these flags are set only by your real backend after payment & verification.</p>
      <button type="button" onclick="simulateBackendVipUpgrade()" style="background:#b45309;">Simulate Backend: VIP upgradeCompleted = true</button>
      <button type="button" onclick="simulateIdentityApproved()" style="background:#047857; margin-top:8px;">Simulate Backend: Identity Verified</button>
    </div>
  </div>

  <script>
    // ========== STATE ==========
    let currentStep = 1;
    let selectedPlan = 'free';
    let stripe;
    let card;

    // User state (in production these come from your backend after auth)
    const userState = {
      name: '',
      email: '',
      plan: 'free',                 // 'free' | 'premium' | 'vip'
      upgradeCompleted: false,      // set ONLY after real backend verification
      identityVerified: false,      // set ONLY after real backend verification
      welcomeBonus: 25.00,          // non-withdrawable
      balance: 0.00,                // earned balance (withdrawable when unlocked)
      vipUpgradeTimestamp: null,    // when upgradeCompleted became true
      withdrawHoldHours: 48         // countdown duration after VIP upgrade
    };

    // Earnings rates per tier
    const TIER_RATES = {
      free:    { hourly: 8,  jobsLabel: 'Limited', jobsCount: 5,   priority: 'Standard' },
      premium: { hourly: 15, jobsLabel: '100+',    jobsCount: 100, priority: 'Priority support' },
      vip:     { hourly: 35, jobsLabel: 'All VIP', jobsCount: 999, priority: 'Highest + dedicated' }
    };

    // Sample jobs (VIP jobs gated by upgradeCompleted)
    const ALL_JOBS = [
      { id: 1, title: 'Data Entry Specialist', rate: 8,  tier: 'free' },
      { id: 2, title: 'Customer Support Chat', rate: 10, tier: 'free' },
      { id: 3, title: 'Content Writer', rate: 12, tier: 'premium' },
      { id: 4, title: 'Virtual Assistant', rate: 14, tier: 'premium' },
      { id: 5, title: 'Social Media Manager', rate: 16, tier: 'premium' },
      { id: 6, title: 'Senior Full-Stack Developer', rate: 35, tier: 'vip' },
      { id: 7, title: 'AI Prompt Engineer', rate: 40, tier: 'vip' },
      { id: 8, title: 'Crypto Research Analyst', rate: 38, tier: 'vip' },
      { id: 9, title: 'Technical Project Lead', rate: 45, tier: 'vip' }
    ];

    const categories = ['Software Development', 'Customer Service', 'Writing & Content', 'Graphic Design', 'Digital Marketing', 'Data Entry', 'Virtual Assistance', 'Sales'];

    // Populate categories
    const container = document.getElementById('categoriesContainer');
    categories.forEach(cat => {
      const div = document.createElement('div');
      div.style.margin = '8px 0';
      div.innerHTML = `<label style="font-size:16px"><input type="checkbox" value="${cat}"> ${cat}</label>`;
      container.appendChild(div);
    });

    // ========== PLAN SELECTOR ==========
    function populatePlans() {
      const planContainer = document.getElementById('planOptions');
      planContainer.innerHTML = `
        <div class="plan-option selected" id="plan-free" onclick="selectPlan('free')">
          <strong>Free Plan</strong><br>
          <span style="font-size:14px; color:#64748b;">Access to limited jobs • $8/hr</span><br>
          <span class="price">$0</span>
        </div>
        
        <div class="plan-option" id="plan-premium" onclick="selectPlan('premium')">
          <strong>Premium Plan</strong><br>
          <span style="font-size:14px; color:#64748b;">Access to 100+ jobs • $15/hr • Priority support</span><br>
          <span class="price">$20<span style="font-size:14px; font-weight:400;">/month</span></span><br>
          <small>or $190/year (save ~21%)</small>
        </div>

        <div class="plan-option vip" id="plan-vip" onclick="selectPlan('vip')">
          <strong>VIP Plan <span class="badge badge-vip">BTC</span></strong><br>
          <span style="font-size:14px; color:#64748b;">All VIP jobs • $35/hr • Highest priority</span><br>
          <span class="price vip">$499<span style="font-size:14px; font-weight:400;"> one-time (BTC)</span></span><br>
          <small>Paid in Bitcoin • Upgrade unlocked only after backend confirmation</small>
        </div>
      `;
    }

    function selectPlan(plan) {
      selectedPlan = plan;
      
      document.querySelectorAll('.plan-option').forEach(el => {
        el.classList.remove('selected');
      });
      
      document.getElementById('premiumPayment').style.display = 'none';
      document.getElementById('vipPayment').style.display = 'none';

      if (plan === 'free') {
        document.getElementById('plan-free').classList.add('selected');
      } else if (plan === 'premium') {
        document.getElementById('plan-premium').classList.add('selected');
        document.getElementById('premiumPayment').style.display = 'block';
        const userEmail = document.getElementById('email').value;
        if (userEmail) document.getElementById('paymentEmail').value = userEmail;
      } else if (plan === 'vip') {
        document.getElementById('plan-vip').classList.add('selected');
        document.getElementById('vipPayment').style.display = 'block';
      }
    }

    function nextStep(step) {
      document.getElementById(`step${currentStep}`).classList.remove('active');
      document.getElementById(`step${step}`).classList.add('active');
      currentStep = step;
      updateProgress();
      
      if (step === 5) {
        populatePlans();
        initStripe();
      }
    }

    function updateProgress() {
      const progress = document.getElementById('progress');
      for (let i = 0; i < 5; i++) {
        progress.children[i].classList.toggle('active', i < currentStep);
      }
    }

    // Initialize Stripe
    function initStripe() {
      if (typeof Stripe === 'undefined') {
        console.warn("Stripe script not loaded");
        return;
      }
      
      // Replace with your real Publishable Key in production
      stripe = Stripe('pk_test_YOUR_TEST_KEY_HERE'); 
      
      if (!card) {
        const elements = stripe.elements();
        card = elements.create('card', {
          style: {
            base: {
              fontSize: '16px',
              color: '#1f2937',
            }
          }
        });
        card.mount('#card-element');
      }
    }

    async function completeSetup() {
      const name = document.getElementById('fullName').value || "User";
      const email = document.getElementById('email').value || "";
      userState.name = name;
      userState.email = email;
      userState.plan = selectedPlan;

      // IMPORTANT: upgradeCompleted is NEVER set true on the client alone.
      // For VIP, we only record intent; real backend must verify BTC payment
      // and then set upgradeCompleted = true (simulated via demo button below).
      if (selectedPlan === 'vip') {
        const txid = document.getElementById('btcTxId').value.trim();
        if (!txid) {
          alert("Please paste your BTC Transaction ID after sending payment.");
          return;
        }
        if (!document.getElementById('tosVip').checked) {
          alert("Please agree to the Terms of Service.");
          return;
        }
        // Client-side: plan is selected as vip, but upgradeCompleted stays false
        // until backend confirms the on-chain payment.
        userState.upgradeCompleted = false;
        userState.balance = 50; // example starting balance after signup
        alert(`✅ VIP payment submitted!\n\nWelcome ${name}!\n\nYour BTC TXID has been recorded.\n\nVIP job access and withdrawal unlock will activate only after our backend verifies the payment on-chain and sets upgradeCompleted = true.\n\nYou can simulate that with the demo button on the dashboard.`);
      } else if (selectedPlan === 'premium') {
        const cardName = document.getElementById('cardName').value;
        const address = document.getElementById('address').value;
        if (!cardName || !address) {
          alert("Please fill in all billing information.");
          return;
        }
        // Premium does not require the same upgradeCompleted gate as VIP jobs
        userState.upgradeCompleted = true; // premium is immediately active in this UI demo
        userState.balance = 20;
        alert(`✅ Payment Successful!\n\nWelcome ${name}!\n\nYou are now a Premium member.\nYou have access to 100+ remote jobs.`);
      } else {
        userState.upgradeCompleted = true; // free has no upgrade gate
        userState.balance = 0;
        alert(`✅ Success!\n\nWelcome ${name}!\n\nYour Free account on info.remotejobs.com is ready.`);
      }

      // Show dashboard
      document.getElementById('onboarding').style.display = 'none';
      document.getElementById('dashboard').classList.add('active');
      renderDashboard();
    }

    // ========== DASHBOARD LOGIC ==========
    function renderDashboard() {
      const plan = userState.plan;
      const rates = TIER_RATES[plan] || TIER_RATES.free;

      // Badge
      const badge = document.getElementById('tierBadge');
      badge.className = 'badge';
      if (plan === 'vip') {
        badge.classList.add('badge-vip');
        badge.textContent = userState.upgradeCompleted ? 'VIP' : 'VIP (Pending)';
      } else if (plan === 'premium') {
        badge.classList.add('badge-premium');
        badge.textContent = 'Premium';
      } else {
        badge.classList.add('badge-free');
        badge.textContent = 'Free';
      }

      document.getElementById('welcomeMsg').textContent = `Welcome, ${userState.name || 'User'}!`;
      document.getElementById('balanceValue').textContent = `$${userState.balance.toFixed(2)}`;
      document.getElementById('bonusValue').textContent = `$${userState.welcomeBonus.toFixed(2)}`;
      document.getElementById('rateValue').textContent = `$${rates.hourly}/hr`;
      document.getElementById('rateSub').textContent = `${plan.charAt(0).toUpperCase() + plan.slice(1)} tier`;
      document.getElementById('jobsAccessValue').textContent = rates.jobsLabel;
      document.getElementById('jobsAccessSub').textContent = rates.priority;

      // Highlight current tier row
      ['free', 'premium', 'vip'].forEach(t => {
        const row = document.getElementById(`row-${t}`);
        if (row) row.classList.toggle('current-tier', t === plan);
      });

      // Withdraw countdown (only after VIP upgradeCompleted)
      const countdownSection = document.getElementById('withdrawCountdownSection');
      if (plan === 'vip' && userState.upgradeCompleted && userState.vipUpgradeTimestamp) {
        countdownSection.style.display = 'block';
        startWithdrawCountdown();
      } else if (plan === 'vip' && !userState.upgradeCompleted) {
        countdownSection.style.display = 'block';
        document.getElementById('countdownTimer').textContent = 'Pending backend';
      } else {
        countdownSection.style.display = 'none';
      }

      renderJobs();
      updateWithdrawButton();
    }

    function renderJobs() {
      const list = document.getElementById('jobList');
      list.innerHTML = '';

      ALL_JOBS.forEach(job => {
        const li = document.createElement('li');
        li.className = 'job-item';

        // Gate VIP jobs behind upgradeCompleted
        const isVipJob = job.tier === 'vip';
        const canAccess =
          (job.tier === 'free') ||
          (job.tier === 'premium' && (userState.plan === 'premium' || userState.plan === 'vip')) ||
          (isVipJob && userState.plan === 'vip' && userState.upgradeCompleted === true);

        if (!canAccess) {
          li.classList.add('locked-overlay');
        }

        li.innerHTML = `
          <div>
            <div class="job-title">${job.title}</div>
            <div style="font-size:12px; color:#64748b;">Tier: ${job.tier.toUpperCase()}</div>
          </div>
          <div class="job-rate">$${job.rate}/hr</div>
          ${!canAccess ? '<div class="locked-badge">' + (isVipJob && userState.plan === 'vip' && !userState.upgradeCompleted ? 'Awaiting upgrade verification' : 'Upgrade required') + '</div>' : ''}
        `;
        list.appendChild(li);
      });
    }

    // ========== WITHDRAW COUNTDOWN ==========
    let countdownInterval = null;

    function startWithdrawCountdown() {
      if (countdownInterval) clearInterval(countdownInterval);

      const endTime = userState.vipUpgradeTimestamp + (userState.withdrawHoldHours * 60 * 60 * 1000);

      function tick() {
        const now = Date.now();
        let remaining = Math.max(0, endTime - now);

        if (remaining <= 0) {
          document.getElementById('countdownTimer').textContent = '00:00:00';
          clearInterval(countdownInterval);
          updateWithdrawButton();
          return;
        }

        const hours = Math.floor(remaining / 3600000);
        const mins = Math.floor((remaining % 3600000) / 60000);
        const secs = Math.floor((remaining % 60000) / 1000);
        document.getElementById('countdownTimer').textContent =
          `${String(hours).padStart(2, '0')}:${String(mins).padStart(2, '0')}:${String(secs).padStart(2, '0')}`;
      }

      tick();
      countdownInterval = setInterval(tick, 1000);
    }

    function isWithdrawUnlocked() {
      // Must have identity verified
      if (!userState.identityVerified) return false;

      // Free / Premium: no VIP hold (in this UI demo)
      if (userState.plan !== 'vip') return true;

      // VIP: require upgradeCompleted + countdown finished
      if (!userState.upgradeCompleted || !userState.vipUpgradeTimestamp) return false;
      const endTime = userState.vipUpgradeTimestamp + (userState.withdrawHoldHours * 60 * 60 * 1000);
      return Date.now() >= endTime;
    }

    function updateWithdrawButton() {
      const btn = document.getElementById('withdrawBtn');
      const msg = document.getElementById('withdrawLockedMsg');
      const unlocked = isWithdrawUnlocked();
      btn.disabled = !unlocked;
      msg.style.display = unlocked ? 'none' : 'block';
    }

    function requestWithdraw() {
      if (!isWithdrawUnlocked()) {
        alert('Withdrawals are still locked.');
        return;
      }
      const amount = parseFloat(document.getElementById('withdrawAmount').value);
      if (isNaN(amount) || amount < 10) {
        alert('Minimum withdrawal is $10.');
        return;
      }
      if (amount > userState.balance) {
        alert('Insufficient withdrawable balance. Welcome bonus is non-withdrawable.');
        return;
      }
      // In production: send request to backend
      userState.balance -= amount;
      document.getElementById('balanceValue').textContent = `$${userState.balance.toFixed(2)}`;
      alert(`Withdrawal request of $${amount.toFixed(2)} submitted.\nWelcome bonus ($${userState.welcomeBonus.toFixed(2)}) remains non-withdrawable.`);
    }

    // ========== IDENTITY VERIFICATION (UI only) ==========
    function submitIdentityVerification() {
      const front = document.getElementById('verifyIdFront').files[0];
      const back = document.getElementById('verifyIdBack').files[0];
      const selfie = document.getElementById('verifySelfie').files[0];
      if (!front || !back || !selfie) {
        alert('Please upload all three documents.');
        return;
      }
      // UI only — real verification is backend
      const status = document.getElementById('verifyStatus');
      status.style.display = 'block';
      status.className = 'info-box';
      status.textContent = 'Documents submitted. Status: Pending review by backend. Use the demo button below to simulate approval.';
    }

    // ========== DEMO: Simulate backend ==========
    function simulateBackendVipUpgrade() {
      if (userState.plan !== 'vip') {
        alert('Select VIP plan first (complete setup with VIP).');
        return;
      }
      // This is the ONLY place upgradeCompleted becomes true in this demo.
      // In production your backend sets this after confirming the BTC payment.
      userState.upgradeCompleted = true;
      userState.vipUpgradeTimestamp = Date.now();
      userState.balance = Math.max(userState.balance, 100);
      alert('Backend simulated: upgradeCompleted = true.\nVIP jobs unlocked. Withdraw countdown started (48h).');
      renderDashboard();
    }

    function simulateIdentityApproved() {
      userState.identityVerified = true;
      const status = document.getElementById('verifyStatus');
      status.style.display = 'block';
      status.className = 'success-box';
      status.textContent = 'Identity verified (simulated). Withdrawals may unlock once any countdown has finished.';
      updateWithdrawButton();
    }

    // Initialize
    updateProgress();
  </script>
</body>
</html>
