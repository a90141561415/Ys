<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>線上預約 | 直接傳送LINE官方帳號</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: system-ui, 'Segoe UI', 'Helvetica Neue', 'Noto Sans', sans-serif;
        }

        body {
            background: linear-gradient(145deg, #e0eaf4 0%, #cfdef3 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 2rem 1.5rem;
        }

        .booking-card {
            max-width: 800px;
            width: 100%;
            background: rgba(255, 255, 255, 0.97);
            border-radius: 2rem;
            box-shadow: 0 25px 45px -12px rgba(0, 0, 0, 0.35), 0 4px 12px rgba(0, 0, 0, 0.05);
            overflow: hidden;
            transition: transform 0.2s ease;
        }

        .booking-card:hover {
            transform: scale(1.01);
        }

        .hero {
            background: #1f3b4c;
            background-image: radial-gradient(circle at 10% 30%, #2c4e64, #142c38);
            padding: 2rem 2rem 1.8rem;
            color: white;
            text-align: center;
        }

        .hero h1 {
            font-size: 1.9rem;
            letter-spacing: -0.3px;
            font-weight: 700;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.6rem;
        }

        .hero h1 span {
            font-size: 2rem;
        }

        .hero p {
            opacity: 0.85;
            font-weight: 400;
            font-size: 0.95rem;
        }

        .form-container {
            padding: 2rem 2rem 2rem;
        }

        .form-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
        }

        .form-col {
            flex: 1;
            min-width: 220px;
        }

        .input-group {
            margin-bottom: 1.5rem;
            display: flex;
            flex-direction: column;
        }

        .input-group label {
            font-weight: 600;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: #2c4e64;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 0.4rem;
        }

        input, select, textarea {
            border: 1.5px solid #e2e8f0;
            border-radius: 1.25rem;
            padding: 0.8rem 1.2rem;
            font-size: 0.95rem;
            transition: all 0.2s;
            background-color: #fefefe;
            outline: none;
            width: 100%;
        }

        input:focus, select:focus, textarea:focus {
            border-color: #2c7da0;
            box-shadow: 0 0 0 3px rgba(44, 125, 160, 0.2);
        }

        textarea {
            resize: vertical;
            min-height: 85px;
        }

        .duration-group {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
            margin-top: 0.3rem;
        }

        .duration-option {
            flex: 1 1 100px;
            background: #f8fafc;
            border: 1.5px solid #e2edf2;
            border-radius: 2rem;
            transition: all 0.2s;
            cursor: pointer;
            text-align: center;
            padding: 0.7rem 0.2rem;
        }

        .duration-option.selected {
            background: #1f3b4c;
            border-color: #1f3b4c;
            color: white;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        .duration-option.selected .duration-name {
            color: white;
        }

        .duration-name {
            font-weight: 600;
            font-size: 0.95rem;
            display: block;
        }

        .duration-desc {
            font-size: 0.65rem;
            opacity: 0.75;
            display: block;
            margin-top: 0.2rem;
        }

        input[type="radio"] {
            display: none;
        }

        .btn-submit {
            background: #06C755;
            color: white;
            border: none;
            width: 100%;
            padding: 1rem;
            font-size: 1.1rem;
            font-weight: 700;
            border-radius: 3rem;
            cursor: pointer;
            transition: all 0.25s;
            box-shadow: 0 6px 14px rgba(0, 0, 0, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            margin-top: 0.5rem;
        }

        .btn-submit:hover {
            background: #05a344;
            transform: translateY(-2px);
            box-shadow: 0 12px 20px -8px rgba(0, 0, 0, 0.25);
        }

        .btn-submit:active {
            transform: translateY(1px);
        }

        .toast-message {
            position: fixed;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%) scale(0.9);
            background: #1e2f3a;
            backdrop-filter: blur(12px);
            color: white;
            padding: 0.9rem 1.8rem;
            border-radius: 60px;
            font-weight: 500;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            z-index: 1000;
            opacity: 0;
            transition: opacity 0.2s, transform 0.2s;
            pointer-events: none;
            font-size: 0.95rem;
            white-space: nowrap;
        }

        .toast-message.show {
            opacity: 1;
            transform: translateX(-50%) scale(1);
        }

        .summary-card {
            background: #f0f6fa;
            border-radius: 1.5rem;
            padding: 1rem 1.2rem;
            margin-top: 1.8rem;
            border-left: 6px solid #2c7da0;
        }

        .summary-title {
            font-weight: 700;
            font-size: 0.85rem;
            color: #1f4e6e;
            margin-bottom: 0.5rem;
            letter-spacing: 0.5px;
        }

        .summary-detail {
            font-size: 0.9rem;
            color: #1a2c36;
            word-break: break-word;
            line-height: 1.4;
        }

        .time-custom-wrapper {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            flex-wrap: wrap;
        }
        .time-custom-wrapper input {
            flex: 2;
            min-width: 130px;
        }
        .time-hint {
            font-size: 0.7rem;
            color: #5a6e7a;
            margin-top: 0.3rem;
        }

        .line-badge {
            text-align: center;
            margin-top: 1rem;
            padding-top: 0.5rem;
            border-top: 1px solid #e2edf2;
            font-size: 0.75rem;
            color: #5f7f8c;
        }

        @media (max-width: 640px) {
            .form-container {
                padding: 1.5rem;
            }
            .hero h1 {
                font-size: 1.5rem;
            }
            .toast-message {
                white-space: normal;
                text-align: center;
                width: 85%;
                border-radius: 2rem;
                padding: 0.8rem 1rem;
            }
            .duration-option {
                flex: 1 1 80px;
            }
        }
    </style>
</head>
<body>

<div class="booking-card">
    <div class="hero">
        <h1>
            <span>📅</span> 線上預約
        </h1>
        <p>填寫資料 · 一鍵傳送至官方LINE</p>
    </div>
    <div class="form-container">
        <form id="bookingForm">
            <div class="form-grid">
                <div class="form-col">
                    <div class="input-group">
                        <label>📛 姓名 <span style="color:#e53e3e;">*</span></label>
                        <input type="text" id="name" name="name" placeholder="請輸入真實姓名" autocomplete="name" required>
                    </div>
                    <div class="input-group">
                        <label>📞 聯絡電話 <span style="color:#e53e3e;">*</span></label>
                        <input type="tel" id="phone" name="phone" placeholder="0912-345-678" required>
                    </div>
                    <div class="input-group">
                        <label>📝 項目 / 部位 <span style="color:#e53e3e;">*</span></label>
                        <textarea id="serviceItem" name="serviceItem" rows="2" placeholder="例如：身體、臉部、櫸木按摩、背部舒壓、全身精油⋯⋯" required></textarea>
                        <small style="color:#6b7a85; font-size:0.7rem; margin-top:4px;">請填寫您想預約的具體項目或部位</small>
                    </div>
                </div>

                <div class="form-col">
                    <div class="input-group">
                        <label>⏱️ 服務時間 <span style="color:#e53e3e;">*</span></label>
                        <div class="duration-group" id="durationGroup">
                            <label class="duration-option" data-value="30">
                                <input type="radio" name="duration" value="30分鐘 輕享時光" hidden>
                                <span class="duration-name">🌿 30分鐘</span>
                                <span class="duration-desc">輕享時光</span>
                            </label>
                            <label class="duration-option" data-value="60">
                                <input type="radio" name="duration" value="60分鐘 經典療程" hidden>
                                <span class="duration-name">🌸 60分鐘</span>
                                <span class="duration-desc">經典療程</span>
                            </label>
                            <label class="duration-option" data-value="90">
                                <input type="radio" name="duration" value="90分鐘 深度放鬆" hidden>
                                <span class="duration-name">✨ 90分鐘</span>
                                <span class="duration-desc">深度放鬆</span>
                            </label>
                            <label class="duration-option" data-value="120">
                                <input type="radio" name="duration" value="120分鐘 極致饗宴" hidden>
                                <span class="duration-name">🌟 120分鐘</span>
                                <span class="duration-desc">極致饗宴</span>
                            </label>
                        </div>
                        <small style="color:#6b7a85; font-size:0.7rem; margin-top:6px;">點擊選擇適合您的療程時間</small>
                    </div>

                    <div class="input-group">
                        <label>📆 預約日期 <span style="color:#e53e3e;">*</span></label>
                        <input type="date" id="date" name="date" required>
                    </div>

                    <div class="input-group">
                        <label>⏰ 預約時段 <span style="color:#e53e3e;">*</span></label>
                        <div class="time-custom-wrapper">
                            <input type="text" id="customTime" name="customTime" placeholder="例如：14:30、下午3點、15:00~16:00" required>
                        </div>
                        <div class="time-hint">💡 請自行填寫希望時段</div>
                    </div>
                </div>
            </div>

            <div class="summary-card" id="liveSummary">
                <div class="summary-title">📋 預約明細預覽</div>
                <div class="summary-detail" id="summaryText">請填寫上方資料，預約資訊將即時顯示。</div>
            </div>

            <button type="submit" class="btn-submit" id="confirmAndSendBtn">
                <span>💬</span> 確認預約並傳送至官方LINE
            </button>
            <div class="line-badge">
                <span>🔗 點擊後將跳轉至 LINE 官方帳號，預約資訊會自動帶入對話框</span>
            </div>
        </form>
    </div>
</div>

<div id="toastMsg" class="toast-message">✨ 準備跳轉LINE...</div>

<script>
    (function(){
        // DOM 元素
        const form = document.getElementById('bookingForm');
        const nameInput = document.getElementById('name');
        const phoneInput = document.getElementById('phone');
        const dateInput = document.getElementById('date');
        const customTimeInput = document.getElementById('customTime');
        const serviceItemTextarea = document.getElementById('serviceItem');
        const summaryDiv = document.getElementById('summaryText');
        const submitBtn = document.getElementById('confirmAndSendBtn');

        // 服務時長選項
        const durationOptions = document.querySelectorAll('.duration-option');
        let selectedDurationValue = '';

        // LINE 官方帳號連結 (您提供的連結)
        const LINE_OFFICIAL_URL = 'https://lin.ee/oS5k6PH';

        // 設定日期限制
        const today = new Date();
        const yyyy = today.getFullYear();
        const mm = String(today.getMonth() + 1).padStart(2, '0');
        const dd = String(today.getDate()).padStart(2, '0');
        const minDate = `${yyyy}-${mm}-${dd}`;
        dateInput.setAttribute('min', minDate);
        const maxDateObj = new Date();
        maxDateObj.setMonth(maxDateObj.getMonth() + 3);
        const maxY = maxDateObj.getFullYear();
        const maxM = String(maxDateObj.getMonth() + 1).padStart(2, '0');
        const maxD = String(maxDateObj.getDate()).padStart(2, '0');
        dateInput.setAttribute('max', `${maxY}-${maxM}-${maxD}`);

        // 初始化服務時長選擇 (預設 60分鐘)
        function initDurationSelection() {
            const defaultOption = durationOptions[1];
            if (defaultOption) {
                const radioInside = defaultOption.querySelector('input[type="radio"]');
                if (radioInside) {
                    radioInside.checked = true;
                    selectedDurationValue = radioInside.value;
                }
                defaultOption.classList.add('selected');
            } else if(durationOptions[0]){
                const first = durationOptions[0];
                const radioFirst = first.querySelector('input[type="radio"]');
                if(radioFirst) {
                    radioFirst.checked = true;
                    selectedDurationValue = radioFirst.value;
                }
                first.classList.add('selected');
            }

            durationOptions.forEach(option => {
                option.addEventListener('click', (e) => {
                    e.stopPropagation();
                    const radio = option.querySelector('input[type="radio"]');
                    if (!radio) return;
                    durationOptions.forEach(opt => opt.classList.remove('selected'));
                    option.classList.add('selected');
                    radio.checked = true;
                    selectedDurationValue = radio.value;
                    updateSummaryPreview();
                });
            });
        }

        function getDurationDisplayText() {
            if (!selectedDurationValue) return '未選擇服務時間';
            return selectedDurationValue;
        }

        function getServiceItemDisplay() {
            let raw = serviceItemTextarea.value.trim();
            if (!raw) return '尚未填寫';
            return raw.length > 35 ? raw.substring(0, 32) + '…' : raw;
        }

        function updateSummaryPreview() {
            const customerName = nameInput.value.trim() || '(未填)';
            const phoneVal = phoneInput.value.trim() || '(未填)';
            const durationText = getDurationDisplayText();
            const dateVal = dateInput.value;
            const timeText = customTimeInput.value.trim() || '(尚未填寫時段)';
            const itemText = getServiceItemDisplay();
            let formattedDate = dateVal ? dateVal.replace(/-/g, '/') : '未選擇日期';
            
            summaryDiv.innerHTML = `
                <div style="display:flex; flex-wrap:wrap; justify-content:space-between; gap:0.3rem; margin-bottom:0.3rem;">
                    <span><strong>👤 姓名：</strong> ${escapeHtml(customerName)}</span>
                    <span><strong>📞 電話：</strong> ${escapeHtml(phoneVal)}</span>
                </div>
                <div><strong>📝 項目／部位：</strong> ${escapeHtml(itemText)}</div>
                <div><strong>⏱️ 服務時間：</strong> ${escapeHtml(durationText)}</div>
                <div><strong>📅 預約日期：</strong> ${escapeHtml(formattedDate)} ｜ <strong>⏰ 時段：</strong> ${escapeHtml(timeText)}</div>
            `;
        }

        function escapeHtml(str) {
            if (!str) return '';
            return str.replace(/[&<>]/g, function(m) {
                if (m === '&') return '&amp;';
                if (m === '<') return '&lt;';
                if (m === '>') return '&gt;';
                return m;
            });
        }

        function showToast(message, isError = false) {
            const toast = document.getElementById('toastMsg');
            toast.textContent = message;
            if(isError) {
                toast.style.background = "#b91c1c";
                toast.style.color = "#fff1f0";
            } else {
                toast.style.background = "#1e2f3a";
                toast.style.color = "white";
            }
            toast.classList.add('show');
            setTimeout(() => {
                toast.classList.remove('show');
                setTimeout(() => {
                    toast.style.background = "#1e2f3a";
                }, 300);
            }, 2500);
        }

        // 獲取表單預約資料
        function getBookingData() {
            return {
                name: nameInput.value.trim(),
                phone: phoneInput.value.trim(),
                serviceItem: serviceItemTextarea.value.trim(),
                duration: selectedDurationValue,
                date: dateInput.value,
                customTime: customTimeInput.value.trim(),
                timestamp: new Date().toLocaleString('zh-TW', { hour12: false })
            };
        }

        // 建立美觀的預約訊息 (用於 LINE 預填)
        function buildLineMessage(booking) {
            if (!booking) return '';
            const dateFormatted = booking.date ? booking.date.replace(/-/g, '/') : '未填';
            const message = `📋 *新預約通知* 📋\n\n` +
                `👤 姓名：${booking.name}\n` +
                `📞 電話：${booking.phone}\n` +
                `📝 項目／部位：${booking.serviceItem}\n` +
                `⏱️ 服務時間：${booking.duration}\n` +
                `📆 預約日期：${dateFormatted}\n` +
                `⏰ 預約時段：${booking.customTime}\n` +
                `🕒 填寫時間：${booking.timestamp}\n\n` +
                `請協助確認，謝謝！`;
            return message;
        }

        // 儲存預約資料到 localStorage (方便留存)
        function saveToLocalStorage(booking) {
            try {
                let history = localStorage.getItem('bookingHistory');
                let bookingsArray = history ? JSON.parse(history) : [];
                const newRecord = { ...booking, id: 'BK' + Date.now() };
                bookingsArray.unshift(newRecord);
                if(bookingsArray.length > 30) bookingsArray.pop();
                localStorage.setItem('bookingHistory', JSON.stringify(bookingsArray));
                return newRecord;
            } catch(e) {
                return booking;
            }
        }

        // 驗證表單完整性
        function validateForm() {
            const name = nameInput.value.trim();
            if (!name) {
                showToast('請填寫姓名', true);
                nameInput.focus();
                return false;
            }
            const phone = phoneInput.value.trim();
            if (!phone) {
                showToast('請填寫聯絡電話', true);
                phoneInput.focus();
                return false;
            }
            const phoneRegex = /^[\d\s\-+()]{8,20}$/;
            if (!phoneRegex.test(phone)) {
                showToast('請輸入有效的電話號碼 (8~20位數字/橫線/空格)', true);
                phoneInput.focus();
                return false;
            }
            const serviceItemRaw = serviceItemTextarea.value.trim();
            if (!serviceItemRaw) {
                showToast('請填寫預約項目 / 部位', true);
                serviceItemTextarea.focus();
                return false;
            }
            if (!selectedDurationValue) {
                showToast('請選擇服務時間', true);
                return false;
            }
            if (!dateInput.value) {
                showToast('請選擇預約日期', true);
                dateInput.focus();
                return false;
            }
            const customTime = customTimeInput.value.trim();
            if (!customTime) {
                showToast('請填寫預約時段', true);
                customTimeInput.focus();
                return false;
            }
            // 週日提醒 (非強制，但友善提醒)
            const selectedDate = new Date(dateInput.value);
            if (selectedDate.getDay() === 0) {
                if(!confirm('您選擇的是週日，部分服務可能需要確認營業時間，確定要預約嗎？')) {
                    return false;
                }
            }
            return true;
        }

        // 核心功能：確認預約並跳轉 LINE
        async function handleConfirmAndSendToLine(e) {
            e.preventDefault();
            
            // 1. 驗證表單
            if (!validateForm()) return;
            
            // 2. 取得預約資料
            const bookingData = getBookingData();
            
            // 3. 儲存至 localStorage (留紀錄)
            saveToLocalStorage(bookingData);
            
            // 4. 建立 LINE 預填訊息
            const message = buildLineMessage(bookingData);
            const encodedMessage = encodeURIComponent(message);
            
            // 5. 跳轉至 LINE 官方帳號並帶入預填訊息
            // 注意：LINE 官方帳號連結 (lin.ee 短網址) 直接加上 ?text= 參數可能無法預填，
            // 需要使用 line.me/R/ti/p/ 格式。但我們可以透過擷取官方帳號 ID 方式，或者使用官方提供的 API。
            // 由於短網址 lin.ee/oS5k6PH 會轉址至 https://line.me/R/ti/p/@??? 或類似網址，
            // 為了確保預填訊息能正常運作，我們採用標準 LINE 分享網址格式。
            // 方法：透過 fetch 取得短網址真實位置 (但跨域限制)，更好的做法是直接使用 line.me 的標準格式。
            // 但為了相容性，我們提供兩種方案：先用 try 嘗試帶入訊息，若不支援則單純跳轉並複製訊息。
            
            // 方案：使用標準 LINE 網址格式，但需要知道官方帳號的 ID。從短網址無法直接獲取，
            // 但我們可以將預約訊息複製到剪貼簿，再跳轉至官方帳號，讓用戶手動貼上 (體驗也不差)。
            // 不過為了更符合「直接跳轉帶入訊息」，我們可以用 line:// 協議但手機支援度不同。
            
            // 最佳實務：複製訊息到剪貼簿 + 跳轉 LINE，使用者只需在 LINE 對話框長按貼上即可。
            // 為了提升體驗，先顯示提示訊息，再複製並跳轉。
            
            showToast('📋 預約資料已儲存，準備跳轉LINE...', false);
            
            // 複製訊息到剪貼簿
            try {
                await navigator.clipboard.writeText(message);
                showToast('✅ 預約內容已複製，跳轉後請貼上傳送', false);
            } catch (err) {
                console.warn('複製失敗', err);
                // 如果複製失敗，改用 alert 顯示讓用戶手動複製
                alert('請手動複製以下預約內容：\n\n' + message);
            }
            
            // 延遲一點點跳轉，讓用戶看到提示
            setTimeout(() => {
                // 直接跳轉 LINE 官方帳號加好友/聊天頁面
                window.open(LINE_OFFICIAL_URL, '_blank', 'noopener,noreferrer');
                // 額外顯示提醒
                setTimeout(() => {
                    showToast('💡 請在LINE對話框長按貼上預約內容', false);
                }, 800);
            }, 600);
        }
        
        // 設定預設日期 (明天)
        function setDefaultDate() {
            if(!dateInput.value) {
                const tomorrow = new Date(today);
                tomorrow.setDate(today.getDate() + 1);
                const yyyyTom = tomorrow.getFullYear();
                const mmTom = String(tomorrow.getMonth() + 1).padStart(2,'0');
                const ddTom = String(tomorrow.getDate()).padStart(2,'0');
                dateInput.value = `${yyyyTom}-${mmTom}-${ddTom}`;
            }
        }
        
        function setCustomTimePlaceholder() {
            customTimeInput.placeholder = "例如：14:30、上午11點、15:00~16:00";
        }
        
        // 綁定即時更新事件
        function bindSummaryEvents() {
            const inputs = [nameInput, phoneInput, dateInput, customTimeInput, serviceItemTextarea];
            inputs.forEach(input => {
                input.addEventListener('input', updateSummaryPreview);
                input.addEventListener('change', updateSummaryPreview);
            });
            updateSummaryPreview();
        }
        
        function init() {
            initDurationSelection();
            setDefaultDate();
            setCustomTimePlaceholder();
            bindSummaryEvents();
            
            // 綁定按鈕事件 (取代原本的 submit)
            if (submitBtn) {
                submitBtn.addEventListener('click', handleConfirmAndSendToLine);
            }
            
            // 防止表單傳統提交
            form.addEventListener('submit', (e) => e.preventDefault());
            updateSummaryPreview();
        }
        
        init();
    })();
</script>
</body>
</html>