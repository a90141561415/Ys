<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>線上預約 | 預約表單</title>
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

        /* 按鈕 */
        .btn-submit {
            background: #1f3b4c;
            color: white;
            border: none;
            width: 100%;
            padding: 1rem;
            font-size: 1.1rem;
            font-weight: 700;
            border-radius: 3rem;
            margin-top: 1rem;
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

                <!-- 右側欄位：預約細項 (服務時間改為時長選項，時段自行填寫，刪除人數與email) -->
                <div class="form-col">
                    <!-- 服務時間 (時長) 選項 更優雅的描述 -->
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

                    <!-- 預約時段：改為自行填寫 (文字輸入) -->
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

            <button type="submit" class="btn-submit">
                <span>✅</span> 確認預約
            </button>
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

        // 服務時長選項 (duration)
        const durationOptions = document.querySelectorAll('.duration-option');
        let selectedDurationValue = '';     // 儲存完整文字 (例如 "60分鐘 經典療程")

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

        // 初始化服務時長選擇 (預設選中 60分鐘 經典療程)
        function initDurationSelection() {
            // 預設第二個選項 (60分鐘) 更常用
            const defaultOption = durationOptions[1];
            if (defaultOption) {
                const radioInside = defaultOption.querySelector('input[type="radio"]');
                if (radioInside) {
                    radioInside.checked = true;
                    selectedDurationValue = radioInside.value;
                }
                defaultOption.classList.add('selected');
            } else if(durationOptions[0]){
                // fallback
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
                    // 清除所有樣式
                    durationOptions.forEach(opt => opt.classList.remove('selected'));
                    option.classList.add('selected');
                    radio.checked = true;
                    selectedDurationValue = radio.value;
                    // 更新即時摘要
                    updateSummaryPreview();
                });
            });
        }

        // 取得服務時間顯示文字
        function getDurationDisplayText() {
            if (!selectedDurationValue) return '未選擇服務時間';
            return selectedDurationValue;
        }

        // 取得項目/部位文字 (簡短呈現)
        function getServiceItemDisplay() {
            let raw = serviceItemTextarea.value.trim();
            if (!raw) return '尚未填寫';
            return raw.length > 35 ? raw.substring(0, 32) + '…' : raw;
        }

        // 更新下方即時摘要
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

        // 顯示浮動訊息
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

        // 表單驗證
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
            
            // 項目/部位 不能空白
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
            
            // 週日提醒 (選擇性)
            const selectedDate = new Date(dateInput.value);
            const dayOfWeek = selectedDate.getDay();
            if (dayOfWeek === 0) {
                if(!confirm('您選擇的是週日，部分服務可能需要確認營業時間，確定要預約嗎？')) {
                    return false;
                }
            }
            return true;
        }

        // 處理提交
        function handleSubmit(e) {
            e.preventDefault();
            if (!validateForm()) return;
            
            // 組合預約資料
            const bookingData = {
                id: 'BK' + Date.now(),
                name: nameInput.value.trim(),
                phone: phoneInput.value.trim(),
                serviceItem: serviceItemTextarea.value.trim(),
                duration: selectedDurationValue,
                date: dateInput.value,
                customTime: customTimeInput.value.trim(),
                createdTime: new Date().toLocaleString()
            };
            
            // 可選擇儲存至 localStorage (保留歷史)
            try {
                let history = localStorage.getItem('bookingHistory');
                let bookingsArray = history ? JSON.parse(history) : [];
                bookingsArray.unshift(bookingData);
                if(bookingsArray.length > 20) bookingsArray.pop();
                localStorage.setItem('bookingHistory', JSON.stringify(bookingsArray));
            } catch(e) { /* 靜默 */ }
            
            // 顯示成功訊息
            const serviceItemShort = bookingData.serviceItem.length > 25 ? bookingData.serviceItem.substring(0,22)+'…' : bookingData.serviceItem;
            const successMsg = `✅ 預約成功！\n\n📌 預約編號：${bookingData.id}\n👤 姓名：${bookingData.name}\n📞 電話：${bookingData.phone}\n📝 項目／部位：${bookingData.serviceItem}\n⏱️ 服務時間：${bookingData.duration}\n📅 預約日期：${bookingData.date}\n⏰ 預約時段：${bookingData.customTime}\n\n感謝您的預約，我們將盡快與您確認！`;
            
            alert(successMsg);
            showToast(`預約完成！編號 ${bookingData.id}`, false);
            
            // 選擇性保留表單內容，但可將時段與項目保留，方便再次預約但不清空。但為了使用者體驗，不強制全部清空，
            // 但可以將姓名/電話保留原樣，將焦點移到姓名方便繼續預約。不清除任何內容讓使用者手動調整。
            nameInput.focus();
        }
        
        // 綁定即時摘要更新事件
        function bindSummaryEvents() {
            const inputs = [nameInput, phoneInput, dateInput, customTimeInput, serviceItemTextarea];
            inputs.forEach(input => {
                input.addEventListener('input', updateSummaryPreview);
                input.addEventListener('change', updateSummaryPreview);
            });
            // 時長選擇事件已在 initDurationSelection 中透過點擊觸發更新摘要，但為了確保duration變更時摘要也更新
            // 在點擊事件內已經呼叫 updateSummaryPreview，另外再補一個自定義事件監聽但不用重複。
            updateSummaryPreview();
        }
        
        // 設定預設日期為明天 (提升便利性)
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
        
        // 設定預約時段 placeholder 提示
        function setCustomTimePlaceholder() {
            customTimeInput.placeholder = "例如：14:30、上午11點、15:00~16:00";
        }
        
        function init() {
            initDurationSelection();
            setDefaultDate();
            setCustomTimePlaceholder();
            bindSummaryEvents();
            form.addEventListener('submit', handleSubmit);
            // 再確保服務項目textarea也有即時更新
            updateSummaryPreview();
        }
        
        init();
    })();
</script>
</body>
</html>