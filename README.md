<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wooden Racks - Payment Tracker</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --wood-dark: #5D4037;
            --wood-medium: #8D6E63;
            --wood-light: #D7CCC8;
            --accent: #3E2723;
            --white: #FFFFFF;
            --black: #212121;
            --gray-light: #F5F5F5;
            --gray-medium: #E0E0E0;
            --success: #4CAF50;
            --danger: #F44336;
            --gold: #FFD700;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --shadow-lg: 0 10px 25px rgba(0, 0, 0, 0.15);
        }

        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #e4e8ed 100%);
            color: var(--black);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            line-height: 1.6;
        }

        .container {
            max-width: 1800px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Improved Header Styles */
        header {
            background: linear-gradient(135deg, var(--wood-dark) 0%, var(--accent) 100%);
            padding: 0;
            border-bottom: none;
            box-shadow: var(--shadow-lg);
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--gold), #FFA000, var(--gold));
            z-index: 2;
        }

        .header-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 20px 0;
            position: relative;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .logo-image {
            width: 80px;
            height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 16px;
            overflow: hidden;
            background: linear-gradient(135deg, var(--wood-light) 0%, var(--wood-medium) 100%);
            border: 3px solid rgba(255, 255, 255, 0.3);
            box-shadow: var(--shadow);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .logo-image:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
        }

        .logo-image img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            padding: 8px;
        }

        .logo-text {
            color: var(--white);
        }

        .logo-text h1 {
            font-size: 32px;
            font-weight: 700;
            margin-bottom: 5px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
            letter-spacing: 0.5px;
        }

        .logo-text p {
            font-size: 16px;
            color: var(--wood-light);
            opacity: 0.9;
            font-weight: 500;
        }

        .header-stats {
            display: flex;
            gap: 30px;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px 25px;
            border-radius: 12px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .stat-item {
            text-align: center;
            color: var(--white);
        }

        .stat-value {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 5px;
            color: var(--gold);
        }

        .stat-label {
            font-size: 14px;
            opacity: 0.9;
        }

        /* Main Content Styles */
        main {
            flex: 1;
            padding: 40px 0;
        }

        .dashboard-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            flex-wrap: wrap;
            gap: 20px;
        }

        .dashboard-title {
            font-size: 28px;
            color: var(--wood-dark);
            font-weight: 600;
        }

        .controls {
            display: flex;
            justify-content: space-between;
            margin-bottom: 25px;
            flex-wrap: wrap;
            gap: 15px;
        }

        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s ease;
            font-size: 15px;
            box-shadow: var(--shadow);
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--wood-medium) 0%, var(--wood-dark) 100%);
            color: var(--white);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(93, 64, 55, 0.4);
        }

        .btn-secondary {
            background: var(--white);
            color: var(--wood-dark);
            border: 1px solid var(--wood-light);
        }

        .btn-secondary:hover {
            background: var(--gray-light);
            transform: translateY(-2px);
        }

        .btn-success {
            background: linear-gradient(135deg, var(--success) 0%, #3d8b40 100%);
            color: var(--white);
        }

        .btn-success:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(76, 175, 80, 0.4);
        }

        .sheet-container {
            background-color: var(--white);
            border-radius: 12px;
            box-shadow: var(--shadow-lg);
            overflow: hidden;
            border: 1px solid var(--gray-medium);
            margin-bottom: 30px;
        }

        .sheet-header {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr 1fr 1.5fr 2fr 2fr 80px;
            background: linear-gradient(135deg, var(--wood-medium) 0%, var(--wood-dark) 100%);
            color: var(--white);
            font-weight: 600;
            border-bottom: 1px solid var(--accent);
        }

        .sheet-header-cell {
            padding: 18px 12px;
            text-align: center;
            border-right: 1px solid rgba(255, 255, 255, 0.2);
            font-size: 15px;
        }

        .sheet-header-cell:last-child {
            border-right: none;
        }

        .sheet-body {
            max-height: 500px;
            overflow-y: auto;
        }

        .sheet-row {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr 1fr 1.5fr 2fr 2fr 80px;
            border-bottom: 1px solid var(--gray-medium);
            transition: all 0.3s ease;
        }

        .sheet-row:hover {
            background-color: rgba(141, 110, 99, 0.05);
            transform: translateY(-1px);
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
        }

        .sheet-cell {
            padding: 15px 12px;
            border-right: 1px solid var(--gray-medium);
            display: flex;
            align-items: center;
        }

        .sheet-cell:last-child {
            border-right: none;
            justify-content: center;
        }

        .sheet-cell input, .sheet-cell textarea {
            width: 100%;
            border: none;
            padding: 10px 8px;
            background: transparent;
            font-size: 14px;
            resize: none;
            transition: background-color 0.2s;
        }

        .sheet-cell input:focus, .sheet-cell textarea:focus {
            outline: none;
            background-color: var(--gray-light);
            border-radius: 4px;
        }

        .action-btn {
            background: none;
            border: none;
            cursor: pointer;
            padding: 8px;
            border-radius: 6px;
            transition: all 0.2s;
            color: var(--wood-medium);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .action-btn:hover {
            background-color: var(--gray-medium);
            transform: scale(1.1);
        }

        .delete-btn {
            color: var(--danger);
        }

        .details-btn {
            color: var(--wood-dark);
        }

        .totals-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
            margin-bottom: 30px;
        }

        .total-card {
            background: linear-gradient(135deg, var(--white) 0%, #f9f9f9 100%);
            border-radius: 12px;
            padding: 25px;
            box-shadow: var(--shadow);
            border-left: 5px solid var(--wood-medium);
            transition: transform 0.3s ease;
        }

        .total-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
        }

        .total-card h3 {
            color: var(--wood-dark);
            margin-bottom: 15px;
            font-size: 18px;
            font-weight: 600;
        }

        .total-amount {
            font-size: 32px;
            font-weight: 700;
            color: var(--accent);
        }

        .data-management {
            background: linear-gradient(135deg, var(--white) 0%, #f9f9f9 100%);
            border-radius: 12px;
            padding: 25px;
            box-shadow: var(--shadow);
            border: 1px solid var(--gray-medium);
        }

        .data-management h3 {
            color: var(--wood-dark);
            margin-bottom: 20px;
            font-size: 20px;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .data-management h3 i {
            color: var(--wood-medium);
        }

        .data-controls {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }

        .data-input {
            flex: 1;
            min-width: 250px;
            padding: 12px 15px;
            border: 1px solid var(--gray-medium);
            border-radius: 8px;
            font-size: 15px;
            transition: all 0.3s;
        }

        .data-input:focus {
            outline: none;
            border-color: var(--wood-medium);
            box-shadow: 0 0 0 3px rgba(141, 110, 99, 0.2);
        }

        .saved-files {
            margin-top: 20px;
        }

        .saved-files h4 {
            color: var(--wood-dark);
            margin-bottom: 15px;
            font-size: 18px;
            font-weight: 600;
        }

        .file-list {
            max-height: 200px;
            overflow-y: auto;
            border: 1px solid var(--gray-medium);
            border-radius: 8px;
            padding: 15px;
            background-color: var(--gray-light);
        }

        .file-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 15px;
            border-bottom: 1px solid var(--gray-medium);
            transition: background-color 0.2s;
        }

        .file-item:hover {
            background-color: rgba(255, 255, 255, 0.7);
        }

        .file-item:last-child {
            border-bottom: none;
        }

        .file-info {
            flex: 1;
        }

        .file-name {
            font-weight: 600;
            color: var(--wood-dark);
            margin-bottom: 5px;
        }

        .file-date {
            font-size: 13px;
            color: var(--wood-medium);
        }

        .file-actions {
            display: flex;
            gap: 10px;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.6);
            z-index: 1000;
            align-items: center;
            justify-content: center;
            backdrop-filter: blur(5px);
        }

        .modal-content {
            background-color: var(--white);
            padding: 30px;
            border-radius: 12px;
            box-shadow: var(--shadow-lg);
            width: 90%;
            max-width: 700px;
            max-height: 80vh;
            overflow-y: auto;
            animation: modalAppear 0.3s ease;
        }

        @keyframes modalAppear {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--gray-medium);
        }

        .modal-title {
            font-size: 22px;
            color: var(--wood-dark);
            font-weight: 600;
        }

        .close-modal {
            background: none;
            border: none;
            font-size: 28px;
            cursor: pointer;
            color: var(--wood-medium);
            transition: color 0.2s;
        }

        .close-modal:hover {
            color: var(--accent);
        }

        .modal-body {
            margin-bottom: 25px;
        }

        .modal-footer {
            display: flex;
            justify-content: flex-end;
            gap: 15px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--wood-dark);
        }

        .form-group input, .form-group textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid var(--gray-medium);
            border-radius: 8px;
            font-size: 15px;
            transition: all 0.3s;
        }

        .form-group input:focus, .form-group textarea:focus {
            outline: none;
            border-color: var(--wood-medium);
            box-shadow: 0 0 0 3px rgba(141, 110, 99, 0.2);
        }

        .form-group textarea {
            min-height: 100px;
            resize: vertical;
        }

        .client-details-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        .full-width {
            grid-column: 1 / -1;
        }

        /* Improved Footer Styles */
        footer {
            background: linear-gradient(135deg, var(--wood-dark) 0%, var(--accent) 100%);
            padding: 40px 0 20px;
            color: var(--wood-light);
            margin-top: 50px;
            position: relative;
        }

        footer::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--gold), #FFA000, var(--gold));
        }

        .footer-content {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr;
            gap: 40px;
            margin-bottom: 30px;
        }

        .footer-section h3 {
            color: var(--white);
            margin-bottom: 20px;
            font-size: 20px;
            font-weight: 600;
            position: relative;
            padding-bottom: 10px;
        }

        .footer-section h3::after {
            content: '';
            position: absolute;
            left: 0;
            bottom: 0;
            width: 40px;
            height: 3px;
            background: var(--gold);
            border-radius: 2px;
        }

        .footer-section p {
            margin-bottom: 15px;
            line-height: 1.7;
            opacity: 0.9;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 12px;
        }

        .footer-links a {
            color: var(--wood-light);
            text-decoration: none;
            transition: color 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .footer-links a:hover {
            color: var(--gold);
        }

        .contact-info {
            list-style: none;
        }

        .contact-info li {
            margin-bottom: 15px;
            display: flex;
            align-items: flex-start;
            gap: 12px;
        }

        .contact-info i {
            color: var(--gold);
            font-size: 18px;
            margin-top: 2px;
        }

        .footer-bottom {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 14px;
            opacity: 0.8;
        }

        /* Responsive Design */
        @media (max-width: 2000px) {
            .sheet-header, .sheet-row {
                grid-template-columns: 2fr 1fr 1fr 1fr 1fr 1.5fr 80px;
            }
            
            .sheet-header-cell:nth-child(8),
            .sheet-cell:nth-child(8) {
                display: none;
            }
        }

        @media (max-width: 1200px) {
            .footer-content {
                grid-template-columns: 1fr 1fr;
            }
            
            .header-stats {
                display: none;
            }
        }

        @media (max-width: 992px) {
            .sheet-header, .sheet-row {
                grid-template-columns: 2fr 1fr 1fr 1fr 1.5fr 80px;
            }
            
            .sheet-header-cell:nth-child(7),
            .sheet-cell:nth-child(7) {
                display: none;
            }
            
            .footer-content {
                grid-template-columns: 1fr;
                gap: 30px;
            }
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
                gap: 20px;
            }
            
            .logo {
                margin-bottom: 0;
            }
            
            .sheet-header, .sheet-row {
                grid-template-columns: 1fr 1fr 1fr;
            }
            
            .sheet-header-cell:nth-child(n+4),
            .sheet-cell:nth-child(n+4) {
                display: none;
            }
            
            .totals-section {
                grid-template-columns: 1fr;
            }
            
            .controls {
                flex-direction: column;
            }
            
            .data-controls {
                flex-direction: column;
            }
            
            .client-details-grid {
                grid-template-columns: 1fr;
            }
            
            .footer-content {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <div class="logo-image">
                        <img src="https://i.postimg.cc/Tp5m4YKd/logo.jpg" alt="Wooden Racks Logo" onerror="this.style.display='none'; this.parentNode.innerHTML='<div style=\"width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg, #D7CCC8 0%, #8D6E63 100%);color:#5D4037;font-weight:bold;font-size:20px;border-radius:16px;\">WR</div>';">
                    </div>
                    <div class="logo-text">
                        <h1>Wooden Racks</h1>
                        <p>Professional Payment Tracking System</p>
                    </div>
                </div>
                <div class="header-stats">
                    <div class="stat-item">
                        <div class="stat-value" id="header-total-down">₱0.00</div>
                        <div class="stat-label">Down Payments</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value" id="header-total-full">₱0.00</div>
                        <div class="stat-label">Full Payments</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value" id="header-total-clients">0</div>
                        <div class="stat-label">Active Clients</div>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <main>
        <div class="container">
            <div class="dashboard-header">
                <h2 class="dashboard-title">Payment Tracking Dashboard</h2>
                <div class="data-controls">
                    <button class="btn btn-success" id="save-file-btn">
                        <i class="fas fa-save"></i> Save As New File
                    </button>
                    <button class="btn btn-secondary" id="load-file-btn">
                        <i class="fas fa-folder-open"></i> Load File
                    </button>
                </div>
            </div>
            
            <div class="controls">
                <button class="btn btn-primary" id="add-row-btn">
                    <i class="fas fa-plus"></i> Add New Client
                </button>
            </div>
            
            <div class="sheet-container">
                <div class="sheet-header">
                    <div class="sheet-header-cell">Client Name</div>
                    <div class="sheet-header-cell">Date</div>
                    <div class="sheet-header-cell">Down Payment</div>
                    <div class="sheet-header-cell">Full Payment</div>
                    <div class="sheet-header-cell">Total</div>
                    <div class="sheet-header-cell">Contact</div>
                    <div class="sheet-header-cell">Address</div>
                    <div class="sheet-header-cell">Order Details</div>
                    <div class="sheet-header-cell">Actions</div>
                </div>
                <div class="sheet-body" id="sheet-body">
                    <!-- Rows will be added here dynamically -->
                </div>
            </div>
            
            <div class="totals-section">
                <div class="total-card">
                    <h3><i class="fas fa-money-bill-wave"></i> Total Down Payments</h3>
                    <div class="total-amount" id="total-downpayment">₱0.00</div>
                </div>
                <div class="total-card">
                    <h3><i class="fas fa-wallet"></i> Total Full Payments</h3>
                    <div class="total-amount" id="total-fullpayment">₱0.00</div>
                </div>
            </div>

            <div class="data-management">
                <h3><i class="fas fa-database"></i> Data Management</h3>
                <p>Current Data File: <strong id="current-file-name">Unsaved Data</strong></p>
                <div class="data-controls">
                    <input type="text" id="file-name-input" class="data-input" placeholder="Enter file name for saving">
                    <button class="btn btn-success" id="save-named-btn">
                        <i class="fas fa-save"></i> Save with Name
                    </button>
                </div>
                
                <div class="saved-files">
                    <h4><i class="fas fa-folder"></i> Saved Files</h4>
                    <div class="file-list" id="file-list">
                        <!-- Saved files will appear here -->
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Modal for file operations -->
    <div class="modal" id="file-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="modal-title">Save As New File</h3>
                <button class="close-modal" id="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <p id="modal-message">Enter a name for your new data file. This will create a fresh sheet:</p>
                <input type="text" id="modal-file-name" class="data-input" placeholder="File name">
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="modal-cancel">Cancel</button>
                <button class="btn btn-primary" id="modal-confirm">Save As New</button>
            </div>
        </div>
    </div>

    <!-- Modal for client details -->
    <div class="modal" id="client-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="client-modal-title">Client Details</h3>
                <button class="close-modal" id="close-client-modal">&times;</button>
            </div>
            <div class="modal-body">
                <div class="client-details-grid">
                    <div class="form-group">
                        <label for="detail-client-name">Client Name</label>
                        <input type="text" id="detail-client-name" class="data-input">
                    </div>
                    <div class="form-group">
                        <label for="detail-date">Date</label>
                        <input type="date" id="detail-date" class="data-input">
                    </div>
                    <div class="form-group">
                        <label for="detail-contact">Contact Number</label>
                        <input type="text" id="detail-contact" class="data-input" placeholder="Phone number">
                    </div>
                    <div class="form-group full-width">
                        <label for="detail-address">Address</label>
                        <textarea id="detail-address" class="data-input" placeholder="Full address"></textarea>
                    </div>
                    <div class="form-group full-width">
                        <label for="detail-order">Order Details</label>
                        <textarea id="detail-order" class="data-input" placeholder="Description of products ordered"></textarea>
                    </div>
                    <div class="form-group">
                        <label for="detail-downpayment">Down Payment</label>
                        <input type="number" id="detail-downpayment" class="data-input" step="0.01" min="0">
                    </div>
                    <div class="form-group">
                        <label for="detail-fullpayment">Full Payment</label>
                        <input type="number" id="detail-fullpayment" class="data-input" step="0.01" min="0">
                    </div>
                    <div class="form-group">
                        <label for="detail-total">Total</label>
                        <input type="text" id="detail-total" class="data-input" readonly>
                    </div>
                </div>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" id="client-modal-cancel">Cancel</button>
                <button class="btn btn-primary" id="client-modal-save">Save Changes</button>
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>Wooden Racks</h3>
                    <p>Professional payment tracking system for managing client transactions, down payments, and full payments with ease and efficiency.</p>
                    <p>Streamline your business finances with our intuitive tracking solution.</p>
                </div>
                <div class="footer-section">
                    <h3>Quick Links</h3>
                    <ul class="footer-links">
                        <li><a href="#"><i class="fas fa-home"></i> Dashboard</a></li>
                        <li><a href="#"><i class="fas fa-users"></i> Clients</a></li>
                        <li><a href="#"><i class="fas fa-chart-bar"></i> Reports</a></li>
                        <li><a href="#"><i class="fas fa-cog"></i> Settings</a></li>
                    </ul>
                </div>
                <div class="footer-section">
                    <h3>Contact Info</h3>
                    <ul class="contact-info">
                        <li>
                            <i class="fas fa-map-marker-alt"></i>
                            <span>123 Business Ave, Suite 100<br>Manila, Philippines</span>
                        </li>
                        <li>
                            <i class="fas fa-phone"></i>
                            <span>+63 912 345 6789</span>
                        </li>
                        <li>
                            <i class="fas fa-envelope"></i>
                            <span>info@woodenracks.com</span>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2023 Wooden Racks Payment Tracker. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const sheetBody = document.getElementById('sheet-body');
            const addRowBtn = document.getElementById('add-row-btn');
            const saveFileBtn = document.getElementById('save-file-btn');
            const loadFileBtn = document.getElementById('load-file-btn');
            const saveNamedBtn = document.getElementById('save-named-btn');
            const fileNameInput = document.getElementById('file-name-input');
            const fileList = document.getElementById('file-list');
            const currentFileName = document.getElementById('current-file-name');
            const totalDownpaymentEl = document.getElementById('total-downpayment');
            const totalFullpaymentEl = document.getElementById('total-fullpayment');
            
            // Header stats elements
            const headerTotalDown = document.getElementById('header-total-down');
            const headerTotalFull = document.getElementById('header-total-full');
            const headerTotalClients = document.getElementById('header-total-clients');
            
            // Modal elements
            const fileModal = document.getElementById('file-modal');
            const modalTitle = document.getElementById('modal-title');
            const modalMessage = document.getElementById('modal-message');
            const modalFileName = document.getElementById('modal-file-name');
            const modalCancel = document.getElementById('modal-cancel');
            const modalConfirm = document.getElementById('modal-confirm');
            const closeModal = document.getElementById('close-modal');
            
            // Client details modal elements
            const clientModal = document.getElementById('client-modal');
            const clientModalTitle = document.getElementById('client-modal-title');
            const detailClientName = document.getElementById('detail-client-name');
            const detailDate = document.getElementById('detail-date');
            const detailContact = document.getElementById('detail-contact');
            const detailAddress = document.getElementById('detail-address');
            const detailOrder = document.getElementById('detail-order');
            const detailDownpayment = document.getElementById('detail-downpayment');
            const detailFullpayment = document.getElementById('detail-fullpayment');
            const detailTotal = document.getElementById('detail-total');
            const closeClientModal = document.getElementById('close-client-modal');
            const clientModalCancel = document.getElementById('client-modal-cancel');
            const clientModalSave = document.getElementById('client-modal-save');
            
            let clients = JSON.parse(localStorage.getItem('woodenRacksClients')) || [];
            let currentFileId = localStorage.getItem('currentFileId') || 'default';
            let currentEditingClientId = null;
            
            // Initialize the sheet with saved data
            function initSheet() {
                sheetBody.innerHTML = '';
                
                if (clients.length === 0) {
                    addNewRow();
                } else {
                    clients.forEach(client => {
                        addRowToSheet(client);
                    });
                }
                
                updateTotals();
                updateCurrentFileName();
                loadFileList();
            }
            
            // Add a new empty row
            function addNewRow() {
                const newClient = {
                    id: Date.now(),
                    name: '',
                    date: new Date().toISOString().split('T')[0],
                    contact: '',
                    address: '',
                    orderDetails: '',
                    downpayment: 0,
                    fullpayment: 0,
                    total: 0
                };
                
                clients.push(newClient);
                addRowToSheet(newClient);
                updateTotals();
            }
            
            // Add a row to the sheet
            function addRowToSheet(client) {
                const row = document.createElement('div');
                row.className = 'sheet-row';
                row.setAttribute('data-id', client.id);
                
                row.innerHTML = `
                    <div class="sheet-cell">
                        <input type="text" class="client-name" value="${client.name}" placeholder="Client name">
                    </div>
                    <div class="sheet-cell">
                        <input type="date" class="client-date" value="${client.date}">
                    </div>
                    <div class="sheet-cell">
                        <input type="number" class="client-downpayment" value="${client.downpayment}" step="0.01" min="0">
                    </div>
                    <div class="sheet-cell">
                        <input type="number" class="client-fullpayment" value="${client.fullpayment}" step="0.01" min="0">
                    </div>
                    <div class="sheet-cell client-total">₱${client.total.toFixed(2)}</div>
                    <div class="sheet-cell">
                        <input type="text" class="client-contact" value="${client.contact}" placeholder="Contact number">
                    </div>
                    <div class="sheet-cell">
                        <textarea class="client-address" placeholder="Address">${client.address}</textarea>
                    </div>
                    <div class="sheet-cell">
                        <textarea class="client-order" placeholder="Order details">${client.orderDetails}</textarea>
                    </div>
                    <div class="sheet-cell">
                        <button class="action-btn details-btn" title="View Full Details">
                            <i class="fas fa-expand"></i>
                        </button>
                        <button class="action-btn delete-btn" title="Delete row">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                `;
                
                sheetBody.appendChild(row);
                
                // Add event listeners to inputs
                const nameInput = row.querySelector('.client-name');
                const dateInput = row.querySelector('.client-date');
                const contactInput = row.querySelector('.client-contact');
                const addressInput = row.querySelector('.client-address');
                const orderInput = row.querySelector('.client-order');
                const downpaymentInput = row.querySelector('.client-downpayment');
                const fullpaymentInput = row.querySelector('.client-fullpayment');
                const detailsBtn = row.querySelector('.details-btn');
                const deleteBtn = row.querySelector('.delete-btn');
                
                nameInput.addEventListener('input', function() {
                    updateClient(client.id, 'name', this.value);
                });
                
                dateInput.addEventListener('change', function() {
                    updateClient(client.id, 'date', this.value);
                });
                
                contactInput.addEventListener('input', function() {
                    updateClient(client.id, 'contact', this.value);
                });
                
                addressInput.addEventListener('input', function() {
                    updateClient(client.id, 'address', this.value);
                });
                
                orderInput.addEventListener('input', function() {
                    updateClient(client.id, 'orderDetails', this.value);
                });
                
                downpaymentInput.addEventListener('input', function() {
                    updateClient(client.id, 'downpayment', parseFloat(this.value) || 0);
                    updateRowTotal(row, client.id);
                    updateTotals();
                });
                
                fullpaymentInput.addEventListener('input', function() {
                    updateClient(client.id, 'fullpayment', parseFloat(this.value) || 0);
                    updateRowTotal(row, client.id);
                    updateTotals();
                });
                
                detailsBtn.addEventListener('click', function() {
                    openClientDetails(client.id);
                });
                
                deleteBtn.addEventListener('click', function() {
                    deleteClient(client.id);
                    row.remove();
                    updateTotals();
                });
            }
            
            // Open client details modal
            function openClientDetails(clientId) {
                const client = clients.find(c => c.id === clientId);
                if (client) {
                    currentEditingClientId = clientId;
                    clientModalTitle.textContent = `Client Details: ${client.name || 'Unnamed Client'}`;
                    detailClientName.value = client.name || '';
                    detailDate.value = client.date || '';
                    detailContact.value = client.contact || '';
                    detailAddress.value = client.address || '';
                    detailOrder.value = client.orderDetails || '';
                    detailDownpayment.value = client.downpayment || 0;
                    detailFullpayment.value = client.fullpayment || 0;
                    updateDetailTotal();
                    
                    clientModal.style.display = 'flex';
                }
            }
            
            // Update client data
            function updateClient(id, field, value) {
                const client = clients.find(c => c.id === id);
                if (client) {
                    client[field] = value;
                }
            }
            
            // Update row total
            function updateRowTotal(row, id) {
                const client = clients.find(c => c.id === id);
                if (client) {
                    client.total = (parseFloat(client.downpayment) || 0) + (parseFloat(client.fullpayment) || 0);
                    const totalCell = row.querySelector('.client-total');
                    totalCell.textContent = `₱${client.total.toFixed(2)}`;
                }
            }
            
            // Update detail total
            function updateDetailTotal() {
                const downpayment = parseFloat(detailDownpayment.value) || 0;
                const fullpayment = parseFloat(detailFullpayment.value) || 0;
                const total = downpayment + fullpayment;
                detailTotal.value = `₱${total.toFixed(2)}`;
            }
            
            // Delete client
            function deleteClient(id) {
                clients = clients.filter(client => client.id !== id);
            }
            
            // Update totals
            function updateTotals() {
                const totalDownpayment = clients.reduce((sum, client) => sum + (parseFloat(client.downpayment) || 0), 0);
                const totalFullpayment = clients.reduce((sum, client) => sum + (parseFloat(client.fullpayment) || 0), 0);
                const totalClients = clients.filter(client => client.name.trim() !== '').length;
                
                totalDownpaymentEl.textContent = `₱${totalDownpayment.toFixed(2)}`;
                totalFullpaymentEl.textContent = `₱${totalFullpayment.toFixed(2)}`;
                
                // Update header stats
                headerTotalDown.textContent = `₱${totalDownpayment.toFixed(2)}`;
                headerTotalFull.textContent = `₱${totalFullpayment.toFixed(2)}`;
                headerTotalClients.textContent = totalClients;
            }
            
            // Save data to localStorage with a specific name (creates new file)
            function saveNamedData(fileName) {
                if (!fileName.trim()) {
                    alert('Please enter a file name');
                    return;
                }
                
                const fileId = 'file_' + Date.now();
                const fileData = {
                    id: fileId,
                    name: fileName,
                    data: clients,
                    timestamp: new Date().toISOString()
                };
                
                // Get existing files
                const savedFiles = JSON.parse(localStorage.getItem('woodenRacksFiles')) || [];
                
                // Add new file
                savedFiles.push(fileData);
                
                // Save to localStorage
                localStorage.setItem('woodenRacksFiles', JSON.stringify(savedFiles));
                localStorage.setItem('currentFileId', fileId);
                currentFileId = fileId;
                
                updateCurrentFileName();
                loadFileList();
                
                alert(`New file "${fileName}" created successfully!`);
            }
            
            // Save as new file (clears current data)
            function saveAsNewFile(fileName) {
                if (!fileName.trim()) {
                    alert('Please enter a file name');
                    return;
                }
                
                const fileId = 'file_' + Date.now();
                // Create empty data for new file
                const fileData = {
                    id: fileId,
                    name: fileName,
                    data: [],
                    timestamp: new Date().toISOString()
                };
                
                // Get existing files
                const savedFiles = JSON.parse(localStorage.getItem('woodenRacksFiles')) || [];
                
                // Add new file
                savedFiles.push(fileData);
                
                // Save to localStorage
                localStorage.setItem('woodenRacksFiles', JSON.stringify(savedFiles));
                localStorage.setItem('currentFileId', fileId);
                currentFileId = fileId;
                
                // Clear current data and initialize new sheet
                clients = [];
                localStorage.setItem('woodenRacksClients', JSON.stringify(clients));
                initSheet();
                
                updateCurrentFileName();
                loadFileList();
                
                alert(`New file "${fileName}" created with a fresh sheet!`);
            }
            
            // Load data from a saved file
            function loadData(fileId) {
                const savedFiles = JSON.parse(localStorage.getItem('woodenRacksFiles')) || [];
                const fileToLoad = savedFiles.find(file => file.id === fileId);
                
                if (fileToLoad) {
                    clients = fileToLoad.data;
                    currentFileId = fileId;
                    localStorage.setItem('currentFileId', fileId);
                    localStorage.setItem('woodenRacksClients', JSON.stringify(clients));
                    initSheet();
                    alert(`Loaded "${fileToLoad.name}"`);
                } else {
                    alert('File not found');
                }
            }
            
            // Delete a saved file
            function deleteFile(fileId) {
                if (confirm('Are you sure you want to delete this file?')) {
                    const savedFiles = JSON.parse(localStorage.getItem('woodenRacksFiles')) || [];
                    const updatedFiles = savedFiles.filter(file => file.id !== fileId);
                    
                    localStorage.setItem('woodenRacksFiles', JSON.stringify(updatedFiles));
                    
                    // If we're deleting the current file, reset to default
                    if (fileId === currentFileId) {
                        clients = [];
                        currentFileId = 'default';
                        localStorage.removeItem('currentFileId');
                        localStorage.removeItem('woodenRacksClients');
                        initSheet();
                    }
                    
                    loadFileList();
                }
            }
            
            // Update the current file name display
            function updateCurrentFileName() {
                if (currentFileId === 'default') {
                    currentFileName.textContent = 'Unsaved Data';
                    return;
                }
                
                const savedFiles = JSON.parse(localStorage.getItem('woodenRacksFiles')) || [];
                const currentFile = savedFiles.find(file => file.id === currentFileId);
                
                if (currentFile) {
                    currentFileName.textContent = currentFile.name;
                } else {
                    currentFileName.textContent = 'Unsaved Data';
                }
            }
            
            // Load the list of saved files
            function loadFileList() {
                const savedFiles = JSON.parse(localStorage.getItem('woodenRacksFiles')) || [];
                fileList.innerHTML = '';
                
                if (savedFiles.length === 0) {
                    fileList.innerHTML = '<p>No saved files yet</p>';
                    return;
                }
                
                savedFiles.forEach(file => {
                    const fileItem = document.createElement('div');
                    fileItem.className = 'file-item';
                    
                    const fileDate = new Date(file.timestamp).toLocaleDateString();
                    
                    fileItem.innerHTML = `
                        <div class="file-info">
                            <div class="file-name">${file.name}</div>
                            <div class="file-date">Saved: ${fileDate}</div>
                        </div>
                        <div class="file-actions">
                            <button class="action-btn load-file-btn" data-id="${file.id}" title="Load File">
                                <i class="fas fa-folder-open"></i>
                            </button>
                            <button class="action-btn delete-file-btn" data-id="${file.id}" title="Delete File">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    `;
                    
                    fileList.appendChild(fileItem);
                });
                
                // Add event listeners to file actions
                document.querySelectorAll('.load-file-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        const fileId = this.getAttribute('data-id');
                        loadData(fileId);
                    });
                });
                
                document.querySelectorAll('.delete-file-btn').forEach(btn => {
                    btn.addEventListener('click', function() {
                        const fileId = this.getAttribute('data-id');
                        deleteFile(fileId);
                    });
                });
            }
            
            // Show modal for file operations
            function showModal(title, message, confirmText, confirmAction) {
                modalTitle.textContent = title;
                modalMessage.textContent = message;
                modalConfirm.textContent = confirmText;
                modalFileName.value = '';
                fileModal.style.display = 'flex';
                
                // Set up confirm action
                modalConfirm.onclick = confirmAction;
            }
            
            // Event listeners
            addRowBtn.addEventListener('click', addNewRow);
            
            saveFileBtn.addEventListener('click', function() {
                showModal(
                    'Save As New File', 
                    'Enter a name for your new data file. This will create a fresh sheet:', 
                    'Save As New',
                    function() {
                        const fileName = modalFileName.value.trim();
                        if (fileName) {
                            saveAsNewFile(fileName);
                            fileModal.style.display = 'none';
                        } else {
                            alert('Please enter a file name');
                        }
                    }
                );
            });
            
            saveNamedBtn.addEventListener('click', function() {
                const fileName = fileNameInput.value.trim();
                saveNamedData(fileName);
                fileNameInput.value = '';
            });
            
            loadFileBtn.addEventListener('click', function() {
                // Just refresh the file list
                loadFileList();
            });
            
            // Modal event listeners
            closeModal.addEventListener('click', function() {
                fileModal.style.display = 'none';
            });
            
            modalCancel.addEventListener('click', function() {
                fileModal.style.display = 'none';
            });
            
            // Client modal event listeners
            closeClientModal.addEventListener('click', function() {
                clientModal.style.display = 'none';
            });
            
            clientModalCancel.addEventListener('click', function() {
                clientModal.style.display = 'none';
            });
            
            clientModalSave.addEventListener('click', function() {
                if (currentEditingClientId) {
                    const client = clients.find(c => c.id === currentEditingClientId);
                    if (client) {
                        client.name = detailClientName.value;
                        client.date = detailDate.value;
                        client.contact = detailContact.value;
                        client.address = detailAddress.value;
                        client.orderDetails = detailOrder.value;
                        client.downpayment = parseFloat(detailDownpayment.value) || 0;
                        client.fullpayment = parseFloat(detailFullpayment.value) || 0;
                        client.total = client.downpayment + client.fullpayment;
                        
                        // Update the row in the table
                        const row = document.querySelector(`.sheet-row[data-id="${currentEditingClientId}"]`);
                        if (row) {
                            row.querySelector('.client-name').value = client.name;
                            row.querySelector('.client-date').value = client.date;
                            row.querySelector('.client-contact').value = client.contact;
                            row.querySelector('.client-address').value = client.address;
                            row.querySelector('.client-order').value = client.orderDetails;
                            row.querySelector('.client-downpayment').value = client.downpayment;
                            row.querySelector('.client-fullpayment').value = client.fullpayment;
                            row.querySelector('.client-total').textContent = `₱${client.total.toFixed(2)}`;
                        }
                        
                        updateTotals();
                        clientModal.style.display = 'none';
                    }
                }
            });
            
            // Update detail total when payment values change
            detailDownpayment.addEventListener('input', updateDetailTotal);
            detailFullpayment.addEventListener('input', updateDetailTotal);
            
            // Close modals when clicking outside
            window.addEventListener('click', function(event) {
                if (event.target === fileModal) {
                    fileModal.style.display = 'none';
                }
                if (event.target === clientModal) {
                    clientModal.style.display = 'none';
                }
            });
            
            // Initialize the sheet
            initSheet();
        });
    </script>
</body>
</html>
