<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>فاتورة مبيعات - شركة النسيم</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            direction: rtl;
            text-align: right;
            margin: 0;
            padding: 10px;
            background-color: #f0f0f5;
        }
        .container {
            max-width: 100%;
            margin: auto;
            background-color: #fff;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }
        .header {
            text-align: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #eaeaea;
        }
        .author {
            text-align: left;
            color: #28a745;
            font-weight: bold;
            font-size: 16px;
            margin-bottom: 10px;
        }
        .company-name {
            font-size: 26px;
            font-weight: bold;
            margin: 10px 0 5px;
            color: #0055a5;
        }
        .distribution-center {
            font-size: 18px;
            margin: 5px 0;
            color: #555;
        }
        .invoice-title {
            font-size: 22px;
            font-weight: bold;
            margin: 10px 0;
            color: #007bff;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }
        .info-section {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            margin-bottom: 20px;
            gap: 10px;
            background-color: #f9f9f9;
            padding: 15px;
            border-radius: 8px;
        }
        .info-section label {
            flex: 1;
            min-width: 200px;
            font-weight: bold;
        }
        .info-section input {
            width: 100%;
            padding: 8px;
            border: 1px solid #ced4da;
            border-radius: 4px;
            transition: border-color 0.2s;
        }
        .info-section input:focus {
            border-color: #007bff;
            outline: none;
            box-shadow: 0 0 0 2px rgba(0,123,255,0.25);
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            box-shadow: 0 0 8px rgba(0,0,0,0.05);
        }
        th, td {
            border: 1px solid #dee2e6;
            padding: 10px;
            text-align: center;
        }
        th {
            background-color: #0055a5;
            color: white;
            font-weight: bold;
        }
        tr:nth-child(even) {
            background-color: #f2f2f2;
        }
        tr:hover {
            background-color: #e9f3ff;
        }
        /* تعديل عرض الأعمدة */
        table th:nth-child(3), table td:nth-child(3) {
            width: 15%; /* عمود الكمية */
        }
        table th:nth-child(4), table td:nth-child(4) {
            width: 15%; /* عمود السعر */
        }
        table th:last-child, table td:last-child {
            width: 5%; /* عمود الحذف */
        }
        input[type="text"], input[type="number"], input[type="date"] {
            width: calc(100% - 16px);
            padding: 8px;
            border: 1px solid #ced4da;
            border-radius: 4px;
            text-align: center;
            transition: all 0.2s;
        }
        input[type="text"]:focus, input[type="number"]:focus, input[type="date"]:focus {
            border-color: #007bff;
            box-shadow: 0 0 0 3px rgba(0,123,255,0.25);
            outline: none;
        }
        input[type="number"] {
            text-align: left;
            direction: ltr;
        }
        .total-section {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            margin: 20px 0;
            gap: 10px;
            padding: 15px;
            background-color: #f8f9fa;
            border-radius: 8px;
            border-right: 4px solid #0055a5;
        }
        .total-row {
            display: flex;
            justify-content: space-between;
            width: 100%;
            padding: 5px 0;
        }
        .total-label {
            font-weight: bold;
            color: #333;
        }
        .total-value {
            font-weight: bold;
            min-width: 120px;
            text-align: left;
            direction: ltr;
            color: #0055a5;
        }
        .amount-in-words {
            font-weight: bold;
            margin-top: 10px;
            padding: 10px;
            background-color: #e9ecef;
            border-radius: 4px;
            width: 100%;
            color: #28a745;
        }
        .button-group {
            display: flex;
            gap: 10px;
            margin-top: 20px;
            flex-wrap: wrap;
        }
        button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            flex: 1;
            min-width: 120px;
            transition: all 0.2s;
            font-weight: bold;
        }
        button:hover {
            background-color: #0069d9;
            transform: translateY(-2px);
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }
        button.print-btn {
            background-color: #28a745;
        }
        button.print-btn:hover {
            background-color: #218838;
        }
        button.clear-btn {
            background-color: #dc3545;
        }
        button.clear-btn:hover {
            background-color: #c82333;
        }
        button.manage-btn {
            background-color: #6c757d;
        }
        button.manage-btn:hover {
            background-color: #5a6268;
        }
        /* المرجع الذي تمت إضافته لتسريع البحث */
        #itemsList {
            max-height: 300px;
            overflow-y: auto;
            border: 1px solid #ced4da;
            border-radius: 4px;
            margin-top: 15px;
            padding: 10px;
            background-color: white;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .saved-items-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
            margin-bottom: 10px;
        }
        .items-title {
            font-weight: bold;
            font-size: 16px;
            color: #0055a5;
        }
        .item-option {
            padding: 8px;
            cursor: pointer;
            border-bottom: 1px solid #f2f2f2;
            display: flex;
            justify-content: space-between;
        }
        .item-option:hover {
            background-color: #f8f9fa;
        }
        .item-option span {
            font-weight: bold;
            color: #28a745;
        }
        .item-option button {
            padding: 2px 8px;
            min-width: auto;
            font-size: 12px;
        }
        .invoices-list {
            margin-top: 20px;
            padding: 15px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            display: none;
        }
        .invoice-card {
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #eee;
            border-radius: 4px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .invoice-card:hover {
            background-color: #f9f9f9;
        }
        .invoice-info {
            flex: 1;
        }
        .invoice-customer {
            font-weight: bold;
        }
        .invoice-date {
            font-size: 14px;
            color: #777;
        }
        .invoice-amount {
            font-weight: bold;
            color: #0055a5;
        }
        .invoice-actions {
            display: flex;
            gap: 5px;
        }
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            display: none;
        }
        .modal {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            width: 90%;
            max-width: 500px;
            max-height: 80vh;
            overflow-y: auto;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }
        .modal-title {
            font-size: 18px;
            font-weight: bold;
            color: #0055a5;
        }
        .close-btn {
            background: none;
            border: none;
            font-size: 20px;
            cursor: pointer;
            color: #777;
        }
        .invoice-number-section {
            margin-bottom: 15px;
        }
        /* التصميم المتجاوب */
        @media (max-width: 768px) {
            .info-section {
                flex-direction: column;
            }
            .info-section label {
                width: 100%;
            }
            .button-group {
                flex-direction: column;
            }
            .company-name {
                font-size: 20px;
            }
            .distribution-center, .invoice-title {
                font-size: 16px;
            }
            th, td {
                padding: 6px;
                font-size: 14px;
            }
            .total-section {
                padding: 10px;
            }
            .item-option {
                flex-direction: column;
            }
            .item-option button {
                margin-top: 5px;
                align-self: flex-end;
            }
        }
        /* أنماط الطباعة */
        @media print {
            body {
                background: white;
                padding: 0;
                margin: 0;
            }
            .container {
                box-shadow: none;
                padding: 0;
            }
            button, .button-group, #itemsList, .invoices-list {
                display: none !important;
            }
            .company-name, .distribution-center, .invoice-title {
                color: black !important;
            }
            th {
                background-color: #f0f0f0 !important;
                color: black !important;
            }
            .total-value, .amount-in-words {
                color: black !important;
            }
            .total-section {
                border-right: 1px solid #ddd;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="author">إعداد: م عيسى الزروق</div>
        <div class="header">
            <div class="company-name">شركة النسيم للصناعات الغذائية</div>
            <div class="distribution-center">مركز توزيع البيضاء</div>
            <div class="invoice-title">فاتورة مبيعات</div>
        </div>
        
        <div class="info-section">
            <label>رقم الفاتورة: <input type="text" id="invoiceNumber" placeholder="الرقم التسلسلي"></label>
            <label>التاريخ: <input type="date" id="invoiceDate"></label>
            <label>الاسم: <input type="text" id="customerName" placeholder="اسم العميل" list="customersList" autocomplete="off"></label>
            <label>العنوان: <input type="text" id="customerAddress" placeholder="عنوان العميل" list="addressesList" autocomplete="off"></label>
            <datalist id="customersList"></datalist>
            <datalist id="addressesList"></datalist>
        </div>
        
        <table id="invoiceTable">
            <thead>
                <tr>
                    <th>الرقم</th>
                    <th>الصنف</th>
                    <th>الكمية</th>
                    <th>السعر</th>
                    <th>الإجمالي</th>
                    <th>حذف</th>
                </tr>
            </thead>
            <tbody id="invoiceBody">
                <!-- سيتم إضافة الصفوف ديناميكيًا -->
            </tbody>
        </table>
        
        <button type="button" onclick="addNewRow()">إضافة صنف جديد</button>
        
        <div class="total-section">
            <div class="total-row">
                <span class="total-label">المجموع الأولي:</span>
                <span class="total-value" id="subtotal">0.000</span>
            </div>
            <div class="total-row">
                <span class="total-label">الخصم:</span>
                <div>
                    <input type="number" id="discountAmount" step="0.001" min="0" value="0" oninput="calculateTotals()">
                </div>
            </div>
            <div class="total-row">
                <span class="total-label">الإجمالي النهائي:</span>
                <span class="total-value" id="finalTotal">0.000</span>
            </div>
            <div class="amount-in-words" id="amountInWords">صفر دينار فقط لا غير</div>
        </div>
        
        <div class="button-group">
            <button type="button" onclick="saveInvoice()">حفظ الفاتورة</button>
            <button type="button" class="print-btn" onclick="printInvoice()">طباعة الفاتورة</button>
            <button type="button" class="manage-btn" onclick="toggleInvoicesList()">إدارة الفواتير</button>
            <button type="button" class="clear-btn" onclick="clearInvoice()">فاتورة جديدة</button>
        </div>
        
        <!-- قائمة الفواتير المحفوظة -->
        <div id="invoicesList" class="invoices-list">
            <div class="saved-items-header">
                <div class="items-title">الفواتير المحفوظة</div>
                <button class="clear-btn" onclick="toggleInvoicesList()">إغلاق</button>
            </div>
            <div id="invoicesContainer">
                <!-- سيتم إضافة الفواتير ديناميكيًا -->
            </div>
        </div>
        
        <!-- قائمة الأصناف المحفوظة -->
        <div id="itemsList">
            <div class="saved-items-header">
                <div class="items-title">الأصناف المحفوظة</div>
                <button class="clear-btn" onclick="clearAllItems()" title="حذف جميع الأصناف">مسح الكل</button>
            </div>
            <div id="savedItemsContainer">
                <!-- سيتم إضافة الأصناف ديناميكيًا -->
            </div>
        </div>
        
        <!-- نافذة إضافة/تعديل صنف -->
        <div id="itemModal" class="modal-overlay">
            <div class="modal">
                <div class="modal-header">
                    <div class="modal-title">إضافة/تعديل صنف</div>
                    <button class="close-btn" onclick="closeItemModal()">&times;</button>
                </div>
                <div class="modal-body">
                    <label>اسم الصنف: <input type="text" id="modalItemName"></label>
                    <label>السعر: <input type="number" id="modalItemPrice" step="0.001" min="0"></label>
                    <div class="button-group" style="margin-top: 15px;">
                        <button type="button" onclick="saveItemFromModal()">حفظ</button>
                        <button type="button" class="clear-btn" onclick="closeItemModal()">إلغاء</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // الأصناف المسجلة مسبقًا (من ملف الإكسيل)
        let defaultItems = [
            { name: "زبادي طبيعي", price: 29.00 },
            { name: "زبادي مزمزج", price: 33.50 },
            { name: "زبادي نكهات", price: 29.00 },
            { name: "زبادي بيوتي فروت", price: 45.50 },
            { name: "زبادي يوناني", price: 28.50 },
            { name: "شراب 1 لتر باكو", price: 61.00 },
            { name: "شراب بوستو 1 لتر", price: 36.50 },
            { name: "شراب بوستو 250 جم", price: 22.00 },
            { name: "شراب شيشة 180جم", price: 16.75 },
            { name: "شراب نصف لتر باكو", price: 33.50 },
            { name: "شراب بيوتي اب 1 لتر", price: 36.50 },
            { name: "شراب بيوتي اب 250 جم", price: 22.00 },
            { name: "لبن 1 لتر", price: 56.00 },
            { name: "لبن أصلي", price: 28.50 },
            { name: "لبن رايب", price: 30.00 },
            { name: "لبن عمران", price: 16.50 },
            { name: "لبن كوب", price: 18.50 },
            { name: "لبن نصف لتر", price: 31.00 },
            { name: "مولتو شكلاطة 48", price: 57.50 }
        ];
        
        // متغيرات التطبيق
        let savedItems = [];
        let savedInvoices = [];
        let rowCounter = 0;
        let currentEditItemIndex = -1;

        // قائمة العملاء والعناوين
        let savedCustomers = [];
        let savedAddresses = [];

        // تهيئة التطبيق عند التحميل
        window.onload = function() {
            const today = new Date().toISOString().split('T')[0];
            document.getElementById("invoiceDate").value = today;
            
            // تحميل الأصناف والفواتير المحفوظة
            loadSavedItems();
            loadSavedInvoices();
            loadCustomersAndAddresses();
            
            // إضافة الأصناف الافتراضية إذا لم تكن موجودة
            if (savedItems.length === 0) {
                savedItems = [...defaultItems];
                saveSavedItems();
            }
            
            // عرض الأصناف المحفوظة
            displaySavedItems();
            updateCustomersList();
            updateAddressesList();
            
            // إضافة رقم تسلسلي للفاتورة
            generateInvoiceNumber();
            
            // إضافة صف جديد للفاتورة
            addNewRow();
            
            // إضافة مستمعي الأحداث للاسم والعنوان
            document.getElementById('customerName').addEventListener('input', function() {
                filterCustomersList(this.value);
            });
            
            document.getElementById('customerAddress').addEventListener('input', function() {
                filterAddressesList(this.value);
            });
        };
        
        // تحميل العملاء والعناوين
        function loadCustomersAndAddresses() {
            const customers = localStorage.getItem('savedCustomers');
            const addresses = localStorage.getItem('savedAddresses');
            
            if (customers) {
                savedCustomers = JSON.parse(customers);
            }
            
            if (addresses) {
                savedAddresses = JSON.parse(addresses);
            }
        }
        
        // تحديث قائمة العملاء
        function updateCustomersList() {
            const dataList = document.getElementById('customersList');
            dataList.innerHTML = '';
            
            // إزالة التكرار والترتيب
            const uniqueCustomers = [...new Set(savedCustomers)].sort();
            
            uniqueCustomers.forEach(customer => {
                const option = document.createElement('option');
                option.value = customer;
                dataList.appendChild(option);
            });
        }
        
        // تحديث قائمة العناوين
        function updateAddressesList() {
            const dataList = document.getElementById('addressesList');
            dataList.innerHTML = '';
            
            // إزالة التكرار والترتيب
            const uniqueAddresses = [...new Set(savedAddresses)].sort();
            
            uniqueAddresses.forEach(address => {
                const option = document.createElement('option');
                option.value = address;
                dataList.appendChild(option);
            });
        }
        
        // تصفية قائمة العملاء
        function filterCustomersList(term) {
            if (!term || term.length < 2) return;
            
            const dataList = document.getElementById('customersList');
            dataList.innerHTML = '';
            
            const lowercaseTerm = term.toLowerCase();
            const matches = savedCustomers.filter(customer => 
                customer.toLowerCase().includes(lowercaseTerm)
            );
            
            matches.forEach(customer => {
                const option = document.createElement('option');
                option.value = customer;
                dataList.appendChild(option);
            });
        }
        
        // تصفية قائمة العناوين
        function filterAddressesList(term) {
            if (!term || term.length < 2) return;
            
            const dataList = document.getElementById('addressesList');
            dataList.innerHTML = '';
            
            const lowercaseTerm = term.toLowerCase();
            const matches = savedAddresses.filter(address => 
                address.toLowerCase().includes(lowercaseTerm)
            );
            
            matches.forEach(address => {
                const option = document.createElement('option');
                option.value = address;
                dataList.appendChild(option);
            });
        }

        // توليد رقم تسلسلي للفاتورة
        function generateInvoiceNumber() {
            // التاريخ الحالي كجزء من الرقم التسلسلي
            const now = new Date();
            const year = now.getFullYear().toString().slice(-2);
            const month = (now.getMonth() + 1).toString().padStart(2, '0');
            const day = now.getDate().toString().padStart(2, '0');
            
            // رقم تسلسلي يعتمد على عدد الفواتير المخزنة + 1
            const serial = (savedInvoices.length + 1).toString().padStart(3, '0');
            
            // تكوين الرقم التسلسلي بالصيغة: YYMMDD-XXX
            document.getElementById("invoiceNumber").value = `${year}${month}${day}-${serial}`;
        }

        // إضافة صف جديد للفاتورة
        function addNewRow() {
            rowCounter++;
            const tbody = document.getElementById("invoiceBody");
            const newRow = document.createElement("tr");
            newRow.id = `row-${rowCounter}`;
            
            // إنشاء قائمة منسدلة للأصناف
            const selectOptions = savedItems.map(item => 
                `<option value="${item.name}">${item.name}</option>`
            ).join('');
            
            newRow.innerHTML = `
                <td>${rowCounter}</td>
                <td>
                    <select class="item-name" onchange="updatePrice(this)">
                        <option value="">-- اختر الصنف --</option>
                        ${selectOptions}
                    </select>
                </td>
                <td><input type="number" class="item-quantity" value="1" step="0.001" min="0.001" oninput="calculateRowTotal(this)"></td>
                <td><input type="number" class="item-price" value="0" step="0.001" min="0" oninput="calculateRowTotal(this)"></td>
                <td class="row-total">0.000</td>
                <td><button type="button" class="clear-btn" onclick="deleteRow('${newRow.id}')">×</button></td>
            `;
            
            tbody.appendChild(newRow);
        }

        // حساب إجمالي الصف
        function calculateRowTotal(input) {
            const row = input.closest('tr');
            const quantity = parseFloat(row.querySelector('.item-quantity').value) || 0;
            const price = parseFloat(row.querySelector('.item-price').value) || 0;
            const total = quantity * price;
            
            row.querySelector('.row-total').textContent = formatNumber(total);
            calculateTotals();
        }

        // حساب جميع الإجماليات
        function calculateTotals() {
            let subtotal = 0;
            const rowTotals = document.querySelectorAll('.row-total');
            
            rowTotals.forEach(cell => {
                subtotal += parseFloat(cell.textContent.replace(/,/g, '')) || 0;
            });
            
            const discount = parseFloat(document.getElementById('discountAmount').value) || 0;
            const finalTotal = subtotal - discount;
            
            document.getElementById('subtotal').textContent = formatNumber(subtotal);
            document.getElementById('finalTotal').textContent = formatNumber(finalTotal);
            document.getElementById('amountInWords').textContent = convertToWords(finalTotal) + " دينار ليبي فقط لا غير";
        }

        // تنسيق الرقم بإضافة فواصل الآلاف
        function formatNumber(num) {
            return num.toFixed(3).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        }

        // البحث عن الأصناف المحفوظة أثناء الكتابة
        function findItems(input) {
            const term = input.value.toLowerCase();
            const dataList = input.nextElementSibling;
            
            // تفريغ قائمة الخيارات
            dataList.innerHTML = '';
            
            if (term.length < 2) return; // لا نبحث عن كلمات قصيرة جدًا
            
            // البحث في الأصناف المحفوظة
            const matches = savedItems.filter(item => 
                item.name.toLowerCase().includes(term)
            );
            
            // إضافة النتائج إلى القائمة
            matches.forEach(item => {
                const option = document.createElement('option');
                option.value = item.name;
                dataList.appendChild(option);
            });
        }

        // تحديث السعر عند اختيار صنف
        function updatePrice(input) {
            const itemName = input.value;
            const row = input.closest('tr');
            
            // البحث عن الصنف في القائمة المحفوظة
            const item = savedItems.find(item => item.name === itemName);
            
            if (item) {
                row.querySelector('.item-price').value = item.price;
            }
            
            calculateRowTotal(input);
            
            // إضافة الصنف إلى القائمة المحفوظة إذا لم يكن موجودًا
            if (!item && itemName.trim() !== '') {
                const price = parseFloat(row.querySelector('.item-price').value) || 0;
                savedItems.push({ name: itemName, price: price });
                saveSavedItems();
                displaySavedItems(); // تحديث قائمة الأصناف المعروضة
            }
        }

        // حذف صف من الفاتورة
        function deleteRow(rowId) {
            document.getElementById(rowId).remove();
            calculateTotals();
        }

        // تحويل الرقم إلى كلمات (تفقيط)
        function convertToWords(number) {
            const units = ['', 'واحد', 'اثنان', 'ثلاثة', 'أربعة', 'خمسة', 'ستة', 'سبعة', 'ثمانية', 'تسعة', 'عشرة',
                         'أحد عشر', 'اثنا عشر', 'ثلاثة عشر', 'أربعة عشر', 'خمسة عشر', 'ستة عشر', 'سبعة عشر', 'ثمانية عشر', 'تسعة عشر'];
            const tens = ['', '', 'عشرون', 'ثلاثون', 'أربعون', 'خمسون', 'ستون', 'سبعون', 'ثمانون', 'تسعون'];
            const hundreds = ['', 'مائة', 'مائتان', 'ثلاثمائة', 'أربعمائة', 'خمسمائة', 'ستمائة', 'سبعمائة', 'ثمانمائة', 'تسعمائة'];
            const thousands = ['', 'ألف', 'ألفان', 'آلاف', 'آلاف', 'آلاف', 'آلاف', 'آلاف', 'آلاف', 'آلاف', 'آلاف'];
            
            if (number === 0) return 'صفر';
            
            // فصل الرقم إلى جزء صحيح وجزء عشري
            const parts = number.toString().split('.');
            const integerPart = parseInt(parts[0]);
            
            // تقريب الجزء العشري إلى 3 أرقام بعد الفاصلة
            const decimalPart = parts.length > 1 ? Math.round(parseFloat('0.' + parts[1]) * 1000) / 1000 : 0;
            
            let result = '';
            
            // معالجة الجزء الصحيح
            if (integerPart > 0) {
                if (integerPart < 20) {
                    result = units[integerPart];
                } else if (integerPart < 100) {
                    const unit = integerPart % 10;
                    const ten = Math.floor(integerPart / 10);
                    
                    if (unit === 0) {
                        result = tens[ten];
                    } else {
                        result = units[unit] + ' و' + tens[ten];
                    }
                } else if (integerPart < 1000) {
                    const hundred = Math.floor(integerPart / 100);
                    const remainder = integerPart % 100;
                    
                    if (remainder === 0) {
                        result = hundreds[hundred];
                    } else if (remainder < 20) {
                        result = hundreds[hundred] + ' و' + units[remainder];
                    } else {
                        const unit = remainder % 10;
                        const ten = Math.floor(remainder / 10);
                        
                        if (unit === 0) {
                            result = hundreds[hundred] + ' و' + tens[ten];
                        } else {
                            result = hundreds[hundred] + ' و' + units[unit] + ' و' + tens[ten];
                        }
                    }
                } else {
                    // للأرقام أكبر من 999
                    const thousand = Math.floor(integerPart / 1000);
                    const remainder = integerPart % 1000;
                    
                    if (thousand === 1) {
                        result = 'ألف';
                    } else if (thousand === 2) {
                        result = 'ألفان';
                    } else if (thousand >= 3 && thousand <= 10) {
                        result = units[thousand] + ' ' + 'آلاف';
                    } else {
                        result = convertToWords(thousand) + ' ' + 'ألف';
                    }
                    
                    if (remainder > 0) {
                        result += ' و' + convertToWords(remainder);
                    }
                }
            }
            
            // معالجة الجزء العشري إذا وجد
            if (decimalPart > 0) {
                const decimalStr = Math.round(decimalPart * 1000).toString();
                result += ' و ' + decimalStr + ' مليم';
            }
            
            return result;
        }

        // حفظ الفاتورة
        function saveInvoice() {
            // جمع بيانات الفاتورة
            const invoiceNumber = document.getElementById('invoiceNumber').value;
            const invoiceDate = document.getElementById('invoiceDate').value;
            const customerName = document.getElementById('customerName').value;
            const customerAddress = document.getElementById('customerAddress').value;
            
            if (!invoiceNumber || !invoiceDate || !customerName) {
                alert('الرجاء إدخال رقم الفاتورة والتاريخ واسم العميل على الأقل!');
                return;
            }
            
            const items = [];
            const rows = document.querySelectorAll('#invoiceBody tr');
            
            rows.forEach(row => {
                const itemName = row.querySelector('.item-name').value;
                const quantity = parseFloat(row.querySelector('.item-quantity').value) || 0;
                const price = parseFloat(row.querySelector('.item-price').value) || 0;
                const total = parseFloat(row.querySelector('.row-total').textContent.replace(/,/g, '')) || 0;
                
                if (itemName && quantity > 0 && price > 0) {
                    items.push({
                        name: itemName,
                        quantity: quantity,
                        price: price,
                        total: total
                    });
                }
            });
            
            if (items.length === 0) {
                alert('الرجاء إضافة صنف واحد على الأقل!');
                return;
            }
            
            const subtotal = parseFloat(document.getElementById('subtotal').textContent.replace(/,/g, '')) || 0;
            const discount = parseFloat(document.getElementById('discountAmount').value) || 0;
            const finalTotal = parseFloat(document.getElementById('finalTotal').textContent.replace(/,/g, '')) || 0;
            
            const invoice = {
                id: Date.now().toString(), // معرف فريد للفاتورة
                number: invoiceNumber,
                date: invoiceDate,
                customerName: customerName,
                customerAddress: customerAddress,
                items: items,
                subtotal: subtotal,
                discount: discount,
                finalTotal: finalTotal,
                amountInWords: document.getElementById('amountInWords').textContent
            };
            
            // حفظ اسم العميل والعنوان لاستخدامهما لاحقًا
            if (customerName && !savedCustomers.includes(customerName)) {
                savedCustomers.push(customerName);
                localStorage.setItem('savedCustomers', JSON.stringify(savedCustomers));
                updateCustomersList();
            }
            
            if (customerAddress && !savedAddresses.includes(customerAddress)) {
                savedAddresses.push(customerAddress);
                localStorage.setItem('savedAddresses', JSON.stringify(savedAddresses));
                updateAddressesList();
            }
            
            // البحث عن فاتورة برقم مماثل
            const existingIndex = savedInvoices.findIndex(inv => inv.number === invoiceNumber);
            
            if (existingIndex >= 0) {
                // تحديث الفاتورة الموجودة
                savedInvoices[existingIndex] = invoice;
            } else {
                // إضافة فاتورة جديدة
                savedInvoices.push(invoice);
            }
            
            // حفظ الفواتير
            saveSavedInvoices();
            
            // حفظ الأصناف لاستخدامها لاحقًا
            saveSavedItems();
            
            alert('تم حفظ الفاتورة بنجاح!');
        }

        // حفظ قائمة الأصناف
        function saveSavedItems() {
            localStorage.setItem('savedItems', JSON.stringify(savedItems));
        }

        // تحميل قائمة الأصناف المحفوظة
        function loadSavedItems() {
            const items = localStorage.getItem('savedItems');
            if (items) {
                savedItems = JSON.parse(items);
            }
        }

        // عرض الأصناف المحفوظة
        function displaySavedItems() {
            const container = document.getElementById('savedItemsContainer');
            container.innerHTML = '';
            
            if (savedItems.length === 0) {
                container.innerHTML = '<div style="text-align:center;padding:10px;">لا توجد أصناف محفوظة</div>';
                return;
            }
            
            // ترتيب الأصناف أبجديًا
            const sortedItems = [...savedItems].sort((a, b) => a.name.localeCompare(b.name));
            
            sortedItems.forEach((item, index) => {
                const div = document.createElement('div');
                div.className = 'item-option';
                div.innerHTML = `
                    ${item.name} <span>${formatNumber(item.price)}</span>
                    <button type="button" class="clear-btn" onclick="editItem(${index})">تعديل</button>
                `;
                div.onclick = function(e) {
                    if (e.target.tagName !== 'BUTTON') {
                        addItemToInvoice(item);
                    }
                };
                container.appendChild(div);
            });
        }

        // إضافة صنف إلى الفاتورة
        function addItemToInvoice(item) {
            // البحث عن صف فارغ
            const rows = document.querySelectorAll('#invoiceBody tr');
            let emptyRow = null;
            
            for (let row of rows) {
                const itemName = row.querySelector('.item-name').value;
                if (!itemName) {
                    emptyRow = row;
                    break;
                }
            }
            
            // إذا لم يكن هناك صف فارغ، أضف صفًا جديدًا
            if (!emptyRow) {
                addNewRow();
                emptyRow = document.querySelector('#invoiceBody tr:last-child');
            }
            
            // ملء الصف بالبيانات
            emptyRow.querySelector('.item-name').value = item.name;
            emptyRow.querySelector('.item-price').value = item.price;
            
            // حساب الإجمالي
            calculateRowTotal(emptyRow.querySelector('.item-price'));
        }

        // فتح نافذة تعديل صنف
        function editItem(index) {
            currentEditItemIndex = index;
            const item = savedItems[index];
            
            document.getElementById('modalItemName').value = item.name;
            document.getElementById('modalItemPrice').value = item.price;
            
            document.getElementById('itemModal').style.display = 'flex';
        }

        // إغلاق نافذة تعديل صنف
        function closeItemModal() {
            document.getElementById('itemModal').style.display = 'none';
            currentEditItemIndex = -1;
        }

        // حفظ الصنف بعد التعديل
        function saveItemFromModal() {
            const name = document.getElementById('modalItemName').value;
            const price = parseFloat(document.getElementById('modalItemPrice').value) || 0;
            
            if (!name) {
                alert('الرجاء إدخال اسم الصنف!');
                return;
            }
            
            if (currentEditItemIndex >= 0) {
                // تعديل صنف موجود
                savedItems[currentEditItemIndex] = { name, price };
            } else {
                // إضافة صنف جديد
                savedItems.push({ name, price });
            }
            
            saveSavedItems();
            displaySavedItems();
            closeItemModal();
        }

        // مسح جميع الأصناف
        function clearAllItems() {
            if (confirm('هل أنت متأكد من مسح جميع الأصناف المحفوظة؟')) {
                savedItems = [];
                saveSavedItems();
                displaySavedItems();
            }
        }

        // حفظ الفواتير
        function saveSavedInvoices() {
            localStorage.setItem('savedInvoices', JSON.stringify(savedInvoices));
        }

        // تحميل الفواتير المحفوظة
        function loadSavedInvoices() {
            const invoices = localStorage.getItem('savedInvoices');
            if (invoices) {
                savedInvoices = JSON.parse(invoices);
            }
        }

        // عرض/إخفاء قائمة الفواتير
        function toggleInvoicesList() {
            const list = document.getElementById('invoicesList');
            
            if (list.style.display === 'block') {
                list.style.display = 'none';
            } else {
                displaySavedInvoices();
                list.style.display = 'block';
            }
        }

        // عرض الفواتير المحفوظة
        function displaySavedInvoices() {
            const container = document.getElementById('invoicesContainer');
            container.innerHTML = '';
            
            if (savedInvoices.length === 0) {
                container.innerHTML = '<div style="text-align:center;padding:10px;">لا توجد فواتير محفوظة</div>';
                return;
            }
            
            // ترتيب الفواتير بتاريخ تنازلي
            const sortedInvoices = [...savedInvoices].sort((a, b) => new Date(b.date) - new Date(a.date));
            
            sortedInvoices.forEach(invoice => {
                const div = document.createElement('div');
                div.className = 'invoice-card';
                
                // تنسيق التاريخ
                const dateParts = invoice.date.split('-');
                const formattedDate = `${dateParts[2]}/${dateParts[1]}/${dateParts[0]}`;
                
                div.innerHTML = `
                    <div class="invoice-info">
                        <div class="invoice-customer">${invoice.customerName}</div>
                        <div class="invoice-date">${formattedDate} - ${invoice.number}</div>
                    </div>
                    <div class="invoice-amount">${formatNumber(invoice.finalTotal)}</div>
                    <div class="invoice-actions">
                        <button type="button" onclick="loadInvoice('${invoice.id}')">تحميل</button>
                        <button type="button" class="clear-btn" onclick="deleteInvoice('${invoice.id}')">حذف</button>
                    </div>
                `;
                
                container.appendChild(div);
            });
        }

        // تحميل فاتورة من القائمة
        function loadInvoice(id) {
            const invoice = savedInvoices.find(inv => inv.id === id);
            if (!invoice) return;
            
            // تعبئة البيانات الأساسية
            document.getElementById('invoiceNumber').value = invoice.number;
            document.getElementById('invoiceDate').value = invoice.date;
            document.getElementById('customerName').value = invoice.customerName;
            document.getElementById('customerAddress').value = invoice.customerAddress || '';
            document.getElementById('discountAmount').value = invoice.discount;
            
            // مسح الصفوف الحالية
            document.getElementById('invoiceBody').innerHTML = '';
            rowCounter = 0;
            
            // إضافة الأصناف
            invoice.items.forEach(item => {
                addNewRow();
                const row = document.getElementById(`row-${rowCounter}`);
                row.querySelector('.item-name').value = item.name;
                row.querySelector('.item-quantity').value = item.quantity;
                row.querySelector('.item-price').value = item.price;
                row.querySelector('.row-total').textContent = formatNumber(item.total);
            });
            
            // تحديث الإجماليات
            calculateTotals();
            
            // إغلاق قائمة الفواتير
            toggleInvoicesList();
        }

        // حذف فاتورة
        function deleteInvoice(id) {
            if (confirm('هل أنت متأكد من حذف هذه الفاتورة؟')) {
                const index = savedInvoices.findIndex(inv => inv.id === id);
                if (index >= 0) {
                    savedInvoices.splice(index, 1);
                    saveSavedInvoices();
                    displaySavedInvoices();
                }
            }
        }

        // إنشاء فاتورة جديدة
        function clearInvoice() {
            if (confirm('هل أنت متأكد من إنشاء فاتورة جديدة؟ سيتم مسح البيانات الحالية.')) {
                document.getElementById('customerName').value = '';
                document.getElementById('customerAddress').value = '';
                document.getElementById('discountAmount').value = '0';
                document.getElementById('invoiceBody').innerHTML = '';
                rowCounter = 0;
                
                // توليد رقم فاتورة جديد
                generateInvoiceNumber();
                
                // إضافة صف جديد
                addNewRow();
                
                // تحديث الإجماليات
                calculateTotals();
            }
        }

        // طباعة الفاتورة
        function printInvoice() {
            window.print();
        }
    </script>
</body>
</html>
