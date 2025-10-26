
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
        }

        body {
            background-color: var(--gray-light);
            color: var(--black);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        .container {
            max-width: 1800px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Styles */
        header {
            background-color: var(--wood-dark);
            padding: 15px 0;
            border-bottom: 3px solid var(--accent);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .header-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo-image {
            width: 60px;
            height: 60px;
            margin-right: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 8px;
            overflow: hidden;
            background-color: var(--wood-light);
            border: 2px solid var(--accent);
        }

        .logo-image img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        .logo-text h1 {
            font-size: 28px;
            color: var(--white);
        }

        .logo-text p {
            font-size: 14px;
            color: var(--wood-light);
        }

        /* Main Content Styles */
        main {
            flex: 1;
            padding: 30px 0;
        }

        .sheet-container {
            background-color: var(--white);
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            border: 1px solid var(--gray-medium);
        }

        .sheet-header {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr 1fr 1.5fr 2fr 2fr 80px;
            background-color: var(--wood-medium);
            color: var(--white);
            font-weight: bold;
            border-bottom: 1px solid var(--accent);
        }

        .sheet-header-cell {
            padding: 15px 10px;
            text-align: center;
            border-right: 1px solid var(--accent);
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
            transition: background-color 0.2s;
        }

        .sheet-row:hover {
            background-color: var(--gray-light);
        }

        .sheet-cell {
            padding: 12px 10px;
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
            padding: 8px 5px;
            background: transparent;
            font-size: 14px;
            resize: none;
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
            padding: 5px;
            border-radius: 4px;
            transition: background-color 0.2s;
            color: var(--wood-medium);
        }

        .action-btn:hover {
            background-color: var(--gray-medium);
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
            gap: 20px;
            margin-top: 30px;
        }

        .total-card {
            background-color: var(--white);
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            border-left: 4px solid var(--wood-medium);
        }

        .total-card h3 {
            color: var(--wood-dark);
            margin-bottom: 10px;
            font-size: 18px;
        }

        .total-amount {
            font-size: 28px;
            font-weight: bold;
            color: var(--accent);
        }

        .controls {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.2s;
        }

        .btn-primary {
            background-color: var(--wood-medium);
            color: var(--white);
        }

        .btn-primary:hover {
            background-color: var(--wood-dark);
        }

        .btn-secondary {
            background-color: var(--gray-medium);
            color: var(--black);
        }

        .btn-secondary:hover {
            background-color: var(--gray-light);
        }

        .btn-success {
            background-color: var(--success);
            color: var(--white);
        }

        .btn-success:hover {
            background-color: #3d8b40;
        }

        .data-management {
            background-color: var(--white);
            border-radius: 8px;
            padding: 20px;
            margin-top: 20px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            border: 1px solid var(--gray-medium);
        }

        .data-management h3 {
            color: var(--wood-dark);
            margin-bottom: 15px;
            font-size: 18px;
        }

        .data-controls {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 15px;
        }

        .data-input {
            flex: 1;
            min-width: 200px;
            padding: 10px;
            border: 1px solid var(--gray-medium);
            border-radius: 4px;
            font-size: 14px;
        }

        .saved-files {
            margin-top: 15px;
        }

        .file-list {
            max-height: 150px;
            overflow-y: auto;
            border: 1px solid var(--gray-medium);
            border-radius: 4px;
            padding: 10px;
            background-color: var(--gray-light);
        }

        .file-item {
            display: flex;
            justify-content: space-between;
            padding: 8px;
            border-bottom: 1px solid var(--gray-medium);
        }

        .file-item:last-child {
            border-bottom: none;
        }

        .file-actions {
            display: flex;
            gap: 5px;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background-color: var(--white);
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            width: 90%;
            max-width: 700px;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .modal-title {
            font-size: 20px;
            color: var(--wood-dark);
        }

        .close-modal {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--wood-medium);
        }

        .modal-body {
            margin-bottom: 20px;
        }

        .modal-footer {
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            color: var(--wood-dark);
        }

        .form-group input, .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--gray-medium);
            border-radius: 4px;
            font-size: 14px;
        }

        .form-group textarea {
            min-height: 80px;
            resize: vertical;
        }

        .client-details-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .full-width {
            grid-column: 1 / -1;
        }

        /* Footer Styles */
        footer {
            background-color: var(--wood-dark);
            padding: 15px 0;
            border-top: 3px solid var(--accent);
            text-align: center;
            color: var(--wood-light);
            margin-top: 30px;
        }

        /* Responsive Design */
        @media (max-width: 1200px) {
            .sheet-header, .sheet-row {
                grid-template-columns: 2fr 1fr 1fr 1fr 1fr 1.5fr 80px;
            }
            
            .sheet-header-cell:nth-child(8),
            .sheet-cell:nth-child(8) {
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
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            .logo {
                margin-bottom: 15px;
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
        }
    </style>
</head>
<body>
<header>
    <div class="container">
        <div class="header-content">
            <div class="logo">
                <div class="logo-image">
                    <!-- Your actual logo - will work on all devices -->
                    <img src="https://i.postimg.cc/Tp5m4YKd/logo.jpg" alt="Wooden Racks Logo" onerror="this.style.display='none'; this.parentNode.innerHTML='<div style=\width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg, #D7CCC8 0%, #8D6E63 100%);color:#5D4037;font-weight:bold;font-size:14px;text-align:center;\>WR</div>';">
                </div>
                <div class="logo-text">
                    <h1>Wooden Racks</h1>
                    <p>Payment Tracking Sheet</p>
                </div>
            </div>
        </div>
    </div>
</header>
    <main>
        <div class="container">
            <div class="controls">
                <button class="btn btn-primary" id="add-row-btn">
                    <i class="fas fa-plus"></i> Add New Client
                </button>
                <div class="data-controls">
                    <button class="btn btn-success" id="save-file-btn">
                        <i class="fas fa-save"></i> Save As New File
                    </button>
                    <button class="btn btn-secondary" id="load-file-btn">
                        <i class="fas fa-folder-open"></i> Load File
                    </button>
                </div>
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
                    <h3>Total Down Payments</h3>
                    <div class="total-amount" id="total-downpayment">₱0.00</div>
                </div>
                <div class="total-card">
                    <h3>Total Full Payments</h3>
                    <div class="total-amount" id="total-fullpayment">₱0.00</div>
                </div>
            </div>

            <div class="data-management">
                <h3>Current Data File: <span id="current-file-name">Unsaved Data</span></h3>
                <div class="data-controls">
                    <input type="text" id="file-name-input" class="data-input" placeholder="Enter file name">
                    <button class="btn btn-success" id="save-named-btn">
                        <i class="fas fa-save"></i> Save with Name
                    </button>
                </div>
                
                <div class="saved-files">
                    <h4>Saved Files</h4>
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
                
                totalDownpaymentEl.textContent = `₱${totalDownpayment.toFixed(2)}`;
                totalFullpaymentEl.textContent = `₱${totalFullpayment.toFixed(2)}`;
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
                        <div>
                            <strong>${file.name}</strong>
                            <div style="font-size: 12px; color: #666;">Saved: ${fileDate}</div>
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
