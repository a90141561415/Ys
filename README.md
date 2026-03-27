<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>線上預約 | 傳送至LINE官方帳號</title>
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

        /* 主卡片容器 */
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

        /* 頁首裝飾 */
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

        /* 表單主體 */
        .form-container {
            padding: 2rem 2rem 2rem;
        }

        /* 雙欄佈局 */
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

        .input-group label i {
            font-style: normal;
            font-weight: normal;
            font-size: 1rem;
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

        /* 服務時間樣式 (自定義選項卡片) */
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

        /* 按鈕區塊 - 雙按鈕設計 */
        .action-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-top: 1rem;
        }

        .btn-submit {
            background: #1f3b4c;
            color: white;
            border: none;
            flex: 2;
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
        }

        .btn-submit:hover {
            background: #0e2a38;
            transform: translateY(-2px);
            box-shadow: 0 12px 20px -8px rgba(0, 0, 0, 0.25);
        }

        .btn-submit:active {
            transform: translateY(1px);
        }

        .line-btn-wrapper {
            flex: 1;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .line-btn-wrapper a {
            display: inline-block;
            text-decoration: none;
            transition: transform 0.2s ease;
        }

        .line-btn-wrapper a:hover {
            transform: scale(1.02);
        }

        .line-btn-wrapper img {
            height: 48px;
            border-radius: 28px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        /* 提示訊息 */
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
            white-space: nowrap;
            font-size: 0.95rem;
        }

        .toast-message.show {
            opacity: 1;
            transform: translateX(-50%) scale(1);
        }

        /* 預約總覽卡片 */
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

        hr {
            margin: 0.7rem 0;
            border: 0;
            height: 1px;
            background: #cbdde6;
        }

        /* 自訂時段輸入輔助 */
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
            .action-buttons {
                flex-direction: column;
            }
            .line-btn-wrapper img {
                height: 44px;
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
        <p>填寫資料 · 快速預約您的專屬時段</p>
    </div>
    <div class="form-container">
        <form id="bookingForm">
            <div class="form-grid">
                <!-- 左側欄位：顧客基本資料 -->
                <div class="form-col">
                    <div class="input-group">
                        <label>📛 姓名 <span style="color:#e53e3e;">*</span></label>
                        <input type="text" id="name" name="name" placeholder="請輸入真實姓名" autocomplete="name" required>
                    </div>
                    <div class="input-group">
                        <label>📞 聯絡電話 <span style="color:#e53e3e;">*</span></label>
                        <input type="tel" id="phone" name="phone" placeholder="0912-345-678" pattern="[0-9]{2,4}-?[0-9]{3,4}-?[0-9]{3,4}" required>
                    </div>
                    <div class="input-group">
                        <label>📝 項目 / 部位 <span style="color:#e53e3e;">*</span></label>
                        <textarea id="serviceItem" name="serviceItem" rows="2" placeholder="例如：身體、臉部、櫸木按摩、背部舒壓、全身精油⋯⋯" required></textarea>
                        <small style="color:#6b7a85; font-size:0.7rem; margin-top:4px;">請填寫您想預約的具體項目或部位</small>
                    </div>
                </div>

                <!-- 右側欄位：預約細項 -->
                <div class="form-col">
                    <!-- 服務時間 (時長) 選項 -->
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

                    <!-- 預約日期 -->
                    <div class="input-group">
                        <label>📆 預約日期 <span style="color:#e53e3e;">*</span></label>
                        <input type="date" id="date" name="date" required>
                    </div>

                    <!-- 預約時段：自行填寫 -->
                    <div class="input-group">
                        <label>⏰ 預約時段 <span style="color:#e53e3e;">*</span></label>
                        <div class="time-custom-wrapper">
                            <input type="text" id="customTime" name="customTime" placeholder="例如：14:30、下午3點、15:00~16:00" required>
                        </div>
                        <div class="time-hint">💡 請自行填寫希望時段 (範例：10:30 / 14:00-15:00 / 上午11點)</div>
                    </div>
                </div>
            </div>

            <!-- 預約摘要即時顯示 -->
            <div class="summary-card" id="liveSummary">
                <div class="summary-title">📋 預約明細預覽</div>
                <div class="summary-detail" id="summaryText">請填寫上方資料，預約資訊將即時顯示。</div>
            </div>

            <!-- 雙按鈕區塊：確認預約 + 傳送到LINE -->
            <div class="action-buttons">
                <button type="submit" class="btn-submit" id="confirmBookingBtn">
                    <span>✅</span> 確認預約
                </button>
                <div class="line-btn-wrapper">
                    <a href="https://lin.ee/oS5k6PH" target="_blank" id="lineShareBtn" rel="noopener noreferrer">
                        <img src="https://scdn.line-apps.com/n/line_add_friends/btn/zh-Hant.png" alt="加入好友 傳送預約" height="48" border="0">
                    </a>
                </div>
            </div>
            <p style="font-size: 0.7rem; text-align: center; margin-top: 1rem; color: #5f7f8c;">
                💡 點擊「確認預約」儲存資料後，可透過LINE按鈕傳送預約資訊給官方帳號。
            </p>
        </form>
    </div>
</div>

<!-- 浮動提示 -->
<div id="toastMsg" class="toast-message">✨ 預約已送出</div>

<script>
    (function(){
        // ---------- DOM 元素 ----------
        const form = document.getElementById('bookingForm');
        const nameInput = document.getElementById('name');
        const phoneInput = document.getElementById('phone');
        const dateInput = document.getElementById('date');
        const customTimeInput = document.getElementById('customTime');
        const serviceItemTextarea = document.getElementById('serviceItem');
        const summaryDiv = document.getElementById('summaryText');
        const lineBtn = document.getElementById('lineShareBtn');

        // 服務時長選項
        const durationOptions = document.querySelectorAll('.duration-option');
        let selectedDurationValue = '';     // 完整文字 (例如 "60分鐘 經典療程")
        
        // 儲存當前有效的預約資料物件 (用於LINE傳送)
        let currentBookingData = null;

        // 設定日期限制: 不選過去, 未來三個月
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

        // 初始化服務時長選擇 (預設選中 60分鐘)
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

        // 更新即時摘要
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
            }, 2800);
        }

        // 從表單獲取預約資料物件
        function getBookingDataFromForm() {
            return {
                name: nameInput.value.trim(),
                phone: phoneInput.value.trim(),
                serviceItem: serviceItemTextarea.value.trim(),
                duration: selectedDurationValue,
                date: dateInput.value,
                customTime: customTimeInput.value.trim(),
                timestamp: new Date().toLocaleString()
            };
        }

        // 驗證表單 (回傳 true/false，並自動聚焦)
        function validateFormForData() {
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
                showToast('請填寫預約項目 / 部位 (例如：身體、臉部、櫸木⋯)', true);
                serviceItemTextarea.focus();
                return false;
            }
            if (!selectedDurationValue) {
                showToast('請選擇服務時間 (30/60/90/120分鐘)', true);
                return false;
            }
            if (!dateInput.value) {
                showToast('請選擇預約日期', true);
                dateInput.focus();
                return false;
            }
            const customTime = customTimeInput.value.trim();
            if (!customTime) {
                showToast('請填寫預約時段 (例如：14:30 / 上午10點)', true);
                customTimeInput.focus();
                return false;
            }
            // 週日提醒
            const selectedDate = new Date(dateInput.value);
            if (selectedDate.getDay() === 0) {
                if(!confirm('您選擇的是週日，部分服務可能需要確認營業時間，確定要預約嗎？')) {
                    return false;
                }
            }
            return true;
        }

        // 儲存至 localStorage 並更新 currentBookingData
        function saveBookingToLocalAndCache(bookingData) {
            try {
                let history = localStorage.getItem('bookingHistory');
                let bookingsArray = history ? JSON.parse(history) : [];
                // 加上簡易id
                const newRecord = { ...bookingData, id: 'BK' + Date.now() };
                bookingsArray.unshift(newRecord);
                if(bookingsArray.length > 20) bookingsArray.pop();
                localStorage.setItem('bookingHistory', JSON.stringify(bookingsArray));
                // 更新 currentBookingData 為最新紀錄 (含id)
                currentBookingData = newRecord;
                return newRecord;
            } catch(e) { 
                console.warn(e);
                currentBookingData = { ...bookingData, id: 'BK' + Date.now() };
                return currentBookingData;
            }
        }

        // 製作 LINE 傳送訊息 (純文字格式，適合貼在官方帳號對話框)
        function buildLineMessage(booking) {
            if (!booking) return '';
            const header = '📋 新預約通知 📋\n';
            const nameLine = `👤 姓名：${booking.name || '未填'}\n`;
            const phoneLine = `📞 電話：${booking.phone || '未填'}\n`;
            const serviceLine = `📝 項目／部位：${booking.serviceItem || '未填'}\n`;
            const durationLine = `⏱️ 服務時間：${booking.duration || '未填'}\n`;
            const dateLine = `📆 預約日期：${booking.date || '未填'}\n`;
            const timeLine = `⏰ 預約時段：${booking.customTime || '未填'}\n`;
            const timeStampLine = `🕒 填寫時間：${booking.timestamp || new Date().toLocaleString()}\n`;
            const footer = `\n請儘快與顧客確認，謝謝！`;
            return header + nameLine + phoneLine + serviceLine + durationLine + dateLine + timeLine + timeStampLine + footer;
        }

        // 處理「確認預約」按鈕：驗證、儲存、顯示快訊、更新currentBookingData
        function handleConfirmBooking(e) {
            e.preventDefault();  // 防止表單默認提交刷新頁面
            if (!validateFormForData()) return;
            
            // 獲取當前資料
            const bookingRaw = getBookingDataFromForm();
            const savedRecord = saveBookingToLocalAndCache(bookingRaw);
            
            // 顯示成功訊息
            const durationShow = savedRecord.duration || '';
            const successMsg = `✅ 預約資料已暫存！\n\n📌 預約編號：${savedRecord.id}\n👤 姓名：${savedRecord.name}\n📞 電話：${savedRecord.phone}\n📝 項目：${savedRecord.serviceItem}\n⏱️ 服務時間：${durationShow}\n📅 日期：${savedRecord.date}\n⏰ 時段：${savedRecord.customTime}\n\n可點選右側「LINE按鈕」將預約內容傳送至官方帳號。`;
            alert(successMsg);
            showToast(`預約資料已儲存，可傳送至LINE`, false);
            
            // 更新摘要 (保持即時)
            updateSummaryPreview();
        }
        
        // 處理LINE按鈕點擊：先確保有 currentBookingData，若無則提示或自動儲存當前有效表單內容
        function handleLineClick(e) {
            // 如果還沒有 currentBookingData 或者表單內容已經變更與 currentBookingData 不同，則先驗證並儲存最新資料
            const currentFormData = getBookingDataFromForm();
            let needToSave = false;
            
            // 簡易比對：若無 currentBookingData 或者 關鍵欄位不一致，則重新儲存
            if (!currentBookingData) {
                needToSave = true;
            } else {
                if (currentBookingData.name !== currentFormData.name ||
                    currentBookingData.phone !== currentFormData.phone ||
                    currentBookingData.serviceItem !== currentFormData.serviceItem ||
                    currentBookingData.duration !== currentFormData.duration ||
                    currentBookingData.date !== currentFormData.date ||
                    currentBookingData.customTime !== currentFormData.customTime) {
                    needToSave = true;
                }
            }
            
            if (needToSave) {
                // 先驗證表單是否填寫完整
                if (!validateFormForData()) {
                    // 驗證失敗時阻止 LINE 跳轉，讓使用者先補齊資料
                    e.preventDefault();
                    showToast('請先完整填寫預約資料，再傳送至LINE', true);
                    return false;
                }
                // 驗證通過，儲存最新資料至 currentBookingData
                const freshData = getBookingDataFromForm();
                const saved = saveBookingToLocalAndCache(freshData);
                currentBookingData = saved;
                showToast('已更新預約資料，即將開啟LINE', false);
            }
            
            if (!currentBookingData) {
                // 防呆
                if (!validateFormForData()) {
                    e.preventDefault();
                    showToast('請填寫完整預約資訊', true);
                    return false;
                }
                const fallbackData = getBookingDataFromForm();
                const savedFallback = saveBookingToLocalAndCache(fallbackData);
                currentBookingData = savedFallback;
            }
            
            // 建立訊息文字
            const messageText = buildLineMessage(currentBookingData);
            // 編碼訊息
            const encodedMsg = encodeURIComponent(messageText);
            // 官方 LINE 連結: https://lin.ee/oS5k6PH 是加入好友連結，若要傳送訊息需搭配 ?text= 參數，
            // 但官方帳號通常需要先加入好友，點擊後會開啟該官方帳號對話視窗，若使用 ?text= 參數可以在手機LINE預填訊息 (僅支援LINE內建)
            // 注意: 官方帳號連結加入好友後若要帶入訊息，可以使用 https://line.me/R/ti/p/@帳號?text=xxx 格式，但此為「@帳號」方式。
            // 但提供的連結 lin.ee/oS5k6PH 為 LINE 官方帳號加好友短網址，轉址後為 https://line.me/R/ti/p/ 開頭，支援 ?text= 預填訊息。
            // 為了讓顧客傳送預約內容，我們組合出帶有預填訊息的加好友+訊息連結。
            // 方法: 將原本的 href 改為加好友連結並帶上 text 參數。
            const lineBaseUrl = 'https://lin.ee/oS5k6PH';
            // 由於短網址無法直接附加參數，但LINE短網址最終會導向至 line.me/R/ti/p/xxx，建議使用完整格式: https://line.me/R/ti/p/@??? 但短網址仍可透過額外處理，
            // 為了確保預填訊息，改採直接使用 line.me 官方格式: 先獲取官方帳號ID 但短網址無法得知真實ID，但用戶原本需求是「傳送到官方LINE」並使用提供的按鈕圖。
            // 提供最佳方案: 點選LINE按鈕時，打開新視窗，並且在新視窗中將訊息複製到剪貼簿(提醒貼上)，或者改為彈出視窗複製訊息。
            // 為符合友善體驗，採用另開視窗並自動複製預約文字，使用者可直接貼到官方LINE對話框。
            e.preventDefault();
            
            // 複製訊息到剪貼簿
            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(messageText).then(() => {
                    showToast('📋 預約內容已複製，請貼到LINE官方帳號傳送', false);
                }).catch(() => {
                    alert('請手動複製預約內容：\n\n' + messageText);
                });
            } else {
                alert('請手動複製預約內容並傳送至官方LINE：\n\n' + messageText);
            }
            
            // 再開啟LINE官方帳號連結 (加入好友/聊天)
            window.open(lineBaseUrl, '_blank', 'noopener,noreferrer');
            return false;
        }
        
        // 綁定LINE按鈕事件
        function bindLineButton() {
            if (lineBtn) {
                lineBtn.addEventListener('click', handleLineClick);
            }
        }
        
        // 綁定即時摘要更新事件
        function bindSummaryEvents() {
            const inputs = [nameInput, phoneInput, dateInput, customTimeInput, serviceItemTextarea];
            inputs.forEach(input => {
                input.addEventListener('input', updateSummaryPreview);
                input.addEventListener('change', updateSummaryPreview);
            });
            updateSummaryPreview();
        }
        
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
        
        function init() {
            initDurationSelection();
            setDefaultDate();
            setCustomTimePlaceholder();
            bindSummaryEvents();
            // 綁定確認預約按鈕 (取代原本 form submit)
            const confirmBtn = document.getElementById('confirmBookingBtn');
            if (confirmBtn) {
                confirmBtn.addEventListener('click', handleConfirmBooking);
            }
            bindLineButton();
            // 避免表單傳統提交刷新
            form.addEventListener('submit', (e) => e.preventDefault());
            updateSummaryPreview();
        }
        
        init();
    })();
</script>
</body>
</html>