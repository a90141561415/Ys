<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>線上預約 | LINE傳送 + Google日曆同步</title>
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
            max-width: 850px;
            width: 100%;
            background: rgba(255, 255, 255, 0.97);
            border-radius: 2rem;
            box-shadow: 0 25px 45px -12px rgba(0, 0, 0, 0.35), 0 4px 12px rgba(0, 0, 0, 0.05);
            overflow: hidden;
        }

        .hero {
            background: linear-gradient(135deg, #1f3b4c 0%, #142c38 100%);
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

        .hero p {
            opacity: 0.85;
            font-size: 0.95rem;
        }

        .form-container {
            padding: 2rem;
        }

        .form-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
        }

        .form-col {
            flex: 1;
            min-width: 240px;
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
            flex: 1 1 90px;
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

        .duration-name {
            font-weight: 600;
            font-size: 0.9rem;
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

        .action-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .btn-primary {
            flex: 2;
            background: #06C755;
            color: white;
            border: none;
            padding: 1rem;
            font-size: 1rem;
            font-weight: 700;
            border-radius: 3rem;
            cursor: pointer;
            transition: all 0.25s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }

        .btn-primary:hover {
            background: #05a344;
            transform: translateY(-2px);
        }

        .btn-secondary {
            flex: 1;
            background: #4285F4;
            color: white;
            border: none;
            padding: 1rem;
            font-size: 1rem;
            font-weight: 600;
            border-radius: 3rem;
            cursor: pointer;
            transition: all 0.25s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .btn-secondary:hover {
            background: #3367d6;
            transform: translateY(-2px);
        }

        .toast-message {
            position: fixed;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%) scale(0.9);
            background: #1e2f3a;
            color: white;
            padding: 0.9rem 1.8rem;
            border-radius: 60px;
            font-weight: 500;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            z-index: 1000;
            opacity: 0;
            transition: opacity 0.2s, transform 0.2s;
            pointer-events: none;
            font-size: 0.9rem;
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
            margin: 1.5rem 0 0.5rem;
            border-left: 6px solid #2c7da0;
        }

        .summary-title {
            font-weight: 700;
            font-size: 0.85rem;
            color: #1f4e6e;
            margin-bottom: 0.5rem;
        }

        .summary-detail {
            font-size: 0.9rem;
            color: #1a2c36;
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

        .info-badge {
            text-align: center;
            margin-top: 1rem;
            padding-top: 0.8rem;
            border-top: 1px solid #e2edf2;
            font-size: 0.7rem;
            color: #5f7f8c;
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            flex-wrap: wrap;
        }

        @media (max-width: 640px) {
            .form-container { padding: 1.5rem; }
            .hero h1 { font-size: 1.5rem; }
            .toast-message { white-space: normal; width: 85%; text-align: center; border-radius: 2rem; }
            .action-buttons { flex-direction: column; }
            .btn-primary, .btn-secondary { width: 100%; }
        }
    </style>
</head>
<body>

<div class="booking-card">
    <div class="hero">
        <h1>
            <span>📅</span> 線上預約
        </h1>
        <p>填寫資料 · 傳送LINE · 加入Google日曆</p>
    </div>
    <div class="form-container">
        <form id="bookingForm">
            <div class="form-grid">
                <div class="form-col">
                    <div class="input-group">
                        <label>📛 姓名 <span style="color:#e53e3e;">*</span></label>
                        <input type="text" id="name" placeholder="請輸入真實姓名" autocomplete="name" required>
                    </div>
                    <div class="input-group">
                        <label>📞 聯絡電話 <span style="color:#e53e3e;">*</span></label>
                        <input type="tel" id="phone" placeholder="0912-345-678" required>
                    </div>
                    <div class="input-group">
                        <label>📝 項目 / 部位 <span style="color:#e53e3e;">*</span></label>
                        <textarea id="serviceItem" rows="2" placeholder="例如：身體、臉部、櫸木按摩、背部舒壓、全身精油⋯⋯" required></textarea>
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
                    </div>

                    <div class="input-group">
                        <label>📆 預約日期 <span style="color:#e53e3e;">*</span></label>
                        <input type="date" id="date" required>
                    </div>

                    <div class="input-group">
                        <label>⏰ 預約時段 <span style="color:#e53e3e;">*</span></label>
                        <div class="time-custom-wrapper">
                            <input type="text" id="customTime" placeholder="例如：14:30、下午3點、15:00~16:00" required>
                        </div>
                        <div class="time-hint">💡 請填寫希望時段 (用於LINE通知，Google日曆需使用標準時間格式)</div>
                    </div>
                </div>
            </div>

            <div class="summary-card">
                <div class="summary-title">📋 預約明細預覽</div>
                <div class="summary-detail" id="summaryText">請填寫上方資料</div>
            </div>

            <div class="action-buttons">
                <button type="button" class="btn-primary" id="sendToLineBtn">
                    <span>💬</span> 確認預約 · 傳送LINE
                </button>
                <button type="button" class="btn-secondary" id="addToCalendarBtn">
                    <span>📆</span> 加入Google日曆
                </button>
            </div>
            <div class="info-badge">
                <span>🔹 點擊「傳送LINE」會複製預約內容並跳轉官方帳號</span>
                <span>🔹 點擊「加入Google日曆」可將預約時間存入日曆</span>
            </div>
        </form>
    </div>
</div>

<div id="toastMsg" class="toast-message">✨ 操作提示</div>

<script>
    (function(){
        // DOM 元素
        const nameInput = document.getElementById('name');
        const phoneInput = document.getElementById('phone');
        const dateInput = document.getElementById('date');
        const customTimeInput = document.getElementById('customTime');
        const serviceItemTextarea = document.getElementById('serviceItem');
        const summaryDiv = document.getElementById('summaryText');
        const sendToLineBtn = document.getElementById('sendToLineBtn');
        const addToCalendarBtn = document.getElementById('addToCalendarBtn');

        // 服務時長
        const durationOptions = document.querySelectorAll('.duration-option');
        let selectedDurationValue = '60分鐘 經典療程';

        // LINE 官方帳號連結
        const LINE_OFFICIAL_URL = 'https://lin.ee/oS5k6PH';

        // 設定日期限制
        const today = new Date();
        const yyyy = today.getFullYear();
        const mm = String(today.getMonth() + 1).padStart(2, '0');
        const dd = String(today.getDate()).padStart(2, '0');
        dateInput.setAttribute('min', `${yyyy}-${mm}-${dd}`);
        const maxDateObj = new Date();
        maxDateObj.setMonth(maxDateObj.getMonth() + 3);
        dateInput.setAttribute('max', `${maxDateObj.getFullYear()}-${String(maxDateObj.getMonth()+1).padStart(2,'0')}-${String(maxDateObj.getDate()).padStart(2,'0')}`);

        // 初始化服務時長
        function initDurationSelection() {
            const defaultOption = durationOptions[1];
            if (defaultOption) {
                const radio = defaultOption.querySelector('input');
                if (radio) {
                    radio.checked = true;
                    selectedDurationValue = radio.value;
                }
                defaultOption.classList.add('selected');
            }
            durationOptions.forEach(opt => {
                opt.addEventListener('click', (e) => {
                    e.stopPropagation();
                    const radio = opt.querySelector('input');
                    if (!radio) return;
                    durationOptions.forEach(o => o.classList.remove('selected'));
                    opt.classList.add('selected');
                    radio.checked = true;
                    selectedDurationValue = radio.value;
                    updateSummary();
                });
            });
        }

        function getDurationText() { return selectedDurationValue || '未選擇'; }
        function getServiceItemShort() {
            let raw = serviceItemTextarea.value.trim();
            if (!raw) return '尚未填寫';
            return raw.length > 32 ? raw.substring(0, 29) + '…' : raw;
        }

        function updateSummary() {
            const name = nameInput.value.trim() || '(未填)';
            const phone = phoneInput.value.trim() || '(未填)';
            const item = getServiceItemShort();
            const duration = getDurationText();
            const dateVal = dateInput.value;
            const timeVal = customTimeInput.value.trim() || '(未填)';
            const formattedDate = dateVal ? dateVal.replace(/-/g, '/') : '未選擇';
            summaryDiv.innerHTML = `
                <div style="display:flex; flex-wrap:wrap; gap:0.5rem; margin-bottom:0.3rem;">
                    <span><strong>👤</strong> ${escapeHtml(name)}</span>
                    <span><strong>📞</strong> ${escapeHtml(phone)}</span>
                </div>
                <div><strong>📝</strong> ${escapeHtml(item)}</div>
                <div><strong>⏱️</strong> ${escapeHtml(duration)}</div>
                <div><strong>📅</strong> ${escapeHtml(formattedDate)} ｜ <strong>⏰</strong> ${escapeHtml(timeVal)}</div>
            `;
        }

        function escapeHtml(str) { if (!str) return ''; return str.replace(/[&<>]/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;'}[m])); }

        function showToast(msg, isError = false) {
            const toast = document.getElementById('toastMsg');
            toast.textContent = msg;
            toast.style.background = isError ? '#b91c1c' : '#1e2f3a';
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 2500);
        }

        // 獲取完整預約資料
        function getBookingData() {
            return {
                name: nameInput.value.trim(),
                phone: phoneInput.value.trim(),
                serviceItem: serviceItemTextarea.value.trim(),
                duration: selectedDurationValue,
                date: dateInput.value,
                customTime: customTimeInput.value.trim(),
                timestamp: new Date().toLocaleString('zh-TW')
            };
        }

        // 驗證表單
        function validateForm() {
            const name = nameInput.value.trim();
            if (!name) { showToast('請填寫姓名', true); nameInput.focus(); return false; }
            const phone = phoneInput.value.trim();
            if (!phone) { showToast('請填寫電話', true); phoneInput.focus(); return false; }
            if (!/^[\d\s\-+()]{8,20}$/.test(phone)) { showToast('請輸入有效電話', true); phoneInput.focus(); return false; }
            if (!serviceItemTextarea.value.trim()) { showToast('請填寫項目/部位', true); serviceItemTextarea.focus(); return false; }
            if (!selectedDurationValue) { showToast('請選擇服務時間', true); return false; }
            if (!dateInput.value) { showToast('請選擇日期', true); dateInput.focus(); return false; }
            if (!customTimeInput.value.trim()) { showToast('請填寫預約時段', true); customTimeInput.focus(); return false; }
            const selectedDate = new Date(dateInput.value);
            if (selectedDate.getDay() === 0 && !confirm('週日營業時間可能調整，確定要預約嗎？')) return false;
            return true;
        }

        // 儲存至 localStorage
        function saveToLocal(booking) {
            try {
                let history = localStorage.getItem('bookingHistory');
                let arr = history ? JSON.parse(history) : [];
                arr.unshift({ ...booking, id: 'BK' + Date.now() });
                if (arr.length > 30) arr.pop();
                localStorage.setItem('bookingHistory', JSON.stringify(arr));
            } catch(e) {}
        }

        // ========== 1. LINE 傳送功能 (複製訊息 + 跳轉) ==========
        function buildLineMessage(booking) {
            const dateFormatted = booking.date ? booking.date.replace(/-/g, '/') : '未填';
            return `📋 新預約通知 📋\n\n` +
                `👤 姓名：${booking.name}\n` +
                `📞 電話：${booking.phone}\n` +
                `📝 項目：${booking.serviceItem}\n` +
                `⏱️ 服務時間：${booking.duration}\n` +
                `📆 預約日期：${dateFormatted}\n` +
                `⏰ 時段：${booking.customTime}\n` +
                `🕒 填寫時間：${booking.timestamp}\n\n` +
                `請協助確認，謝謝！`;
        }

        async function handleSendToLine() {
            if (!validateForm()) return;
            const booking = getBookingData();
            saveToLocal(booking);
            const message = buildLineMessage(booking);
            
            // 複製到剪貼簿
            try {
                await navigator.clipboard.writeText(message);
                showToast('✅ 預約內容已複製，準備跳轉LINE');
            } catch (err) {
                alert('請手動複製以下內容：\n\n' + message);
            }
            
            setTimeout(() => {
                window.open(LINE_OFFICIAL_URL, '_blank', 'noopener,noreferrer');
                setTimeout(() => {
                    showToast('💡 請在LINE對話框長按貼上預約內容', false);
                }, 800);
            }, 400);
        }

        // ========== 2. Google 日曆功能 (自動解析時間並建立事件) ==========
        // 將使用者填寫的時段文字轉換為標準時間格式 (嘗試解析)
        // 支援格式: "14:30", "下午2點半", "14:00~15:00", "上午10點", "09:00-10:00"
        function parseTimeStringToHourMin(timeStr) {
            if (!timeStr) return null;
            // 嘗試匹配 HH:MM 格式
            let match = timeStr.match(/(\d{1,2}):(\d{2})/);
            if (match) {
                return { hour: parseInt(match[1]), minute: parseInt(match[2]) };
            }
            // 匹配 "下午2點半" 或 "上午10點" 之類
            const ampmMatch = timeStr.match(/(上午|下午|早上|晚上)?\s*(\d{1,2})\s*點\s*(半|(\d{1,2})分)?/);
            if (ampmMatch) {
                let hour = parseInt(ampmMatch[2]);
                let minute = 0;
                if (ampmMatch[3] === '半') minute = 30;
                else if (ampmMatch[4]) minute = parseInt(ampmMatch[4]);
                const period = ampmMatch[1];
                if (period === '下午' || period === '晚上') {
                    if (hour !== 12) hour += 12;
                } else if (period === '上午' && hour === 12) hour = 0;
                return { hour, minute };
            }
            // 嘗試 "14點30分"
            const cnMatch = timeStr.match(/(\d{1,2})\s*點\s*(\d{1,2})\s*分/);
            if (cnMatch) {
                return { hour: parseInt(cnMatch[1]), minute: parseInt(cnMatch[2]) };
            }
            return null;
        }

        // 根據服務時長字串取得分鐘數
        function getDurationMinutes(durationStr) {
            if (durationStr.includes('30')) return 30;
            if (durationStr.includes('60')) return 60;
            if (durationStr.includes('90')) return 90;
            if (durationStr.includes('120')) return 120;
            return 60; // 預設60分鐘
        }

        // 建立 Google Calendar 連結 (可新增事件)
        function buildGoogleCalendarUrl(booking) {
            const dateStr = booking.date; // YYYY-MM-DD
            if (!dateStr) return null;
            
            // 解析時段
            const parsedTime = parseTimeStringToHourMin(booking.customTime);
            let startDateTime = null;
            let endDateTime = null;
            
            if (parsedTime) {
                // 建立開始時間
                const startDate = new Date(dateStr);
                startDate.setHours(parsedTime.hour, parsedTime.minute, 0);
                if (!isNaN(startDate.getTime())) {
                    startDateTime = startDate;
                    // 結束時間 = 開始 + 服務時長
                    const durationMinutes = getDurationMinutes(booking.duration);
                    const endDate = new Date(startDate.getTime() + durationMinutes * 60000);
                    endDateTime = endDate;
                }
            }
            
            // 標題
            const title = `預約：${booking.serviceItem} (${booking.duration})`;
            const details = `客戶：${booking.name}\n電話：${booking.phone}\n項目：${booking.serviceItem}\n服務時間：${booking.duration}\n預約時段：${booking.customTime}`;
            const location = "依店家安排";
            
            let startFormat = '', endFormat = '';
            if (startDateTime && endDateTime && !isNaN(startDateTime.getTime())) {
                // 格式: YYYYMMDDTHHMMSSZ (使用本地時間轉ISO但去除時區標示，Google會視為本地時間)
                const formatDate = (d) => {
                    return d.getFullYear() +
                        String(d.getMonth() + 1).padStart(2, '0') +
                        String(d.getDate()).padStart(2, '0') +
                        'T' +
                        String(d.getHours()).padStart(2, '0') +
                        String(d.getMinutes()).padStart(2, '0') +
                        '00';
                };
                startFormat = formatDate(startDateTime);
                endFormat = formatDate(endDateTime);
            } else {
                // 無法解析時段則設為全天事件，並在說明中標註時段
                startFormat = dateStr.replace(/-/g, '');
                endFormat = dateStr.replace(/-/g, '');
            }
            
            const baseUrl = 'https://calendar.google.com/calendar/render';
            const params = new URLSearchParams();
            params.append('action', 'TEMPLATE');
            params.append('text', title);
            params.append('details', details);
            params.append('location', location);
            if (startFormat && endFormat) {
                params.append('dates', `${startFormat}/${endFormat}`);
            }
            return `${baseUrl}?${params.toString()}`;
        }

        async function handleAddToCalendar() {
            if (!validateForm()) return;
            const booking = getBookingData();
            saveToLocal(booking);
            
            const calendarUrl = buildGoogleCalendarUrl(booking);
            if (!calendarUrl) {
                showToast('無法建立日曆事件，請確認日期格式正確', true);
                return;
            }
            
            // 顯示預覽提醒，並跳轉
            const confirmMsg = `即將建立 Google 日曆事件：\n\n📌 ${booking.serviceItem}\n📅 ${booking.date} ${booking.customTime}\n⏱️ ${booking.duration}\n\n點擊確定後將開啟 Google 日曆頁面，可編輯後儲存。`;
            if (confirm(confirmMsg)) {
                window.open(calendarUrl, '_blank', 'noopener,noreferrer');
                showToast('已開啟 Google 日曆，請填寫詳細資訊後儲存');
            }
        }

        // 設定預設日期為明天
        function setDefaultDate() {
            if (!dateInput.value) {
                const tomorrow = new Date(today);
                tomorrow.setDate(today.getDate() + 1);
                dateInput.value = `${tomorrow.getFullYear()}-${String(tomorrow.getMonth()+1).padStart(2,'0')}-${String(tomorrow.getDate()).padStart(2,'0')}`;
            }
        }
        
        function bindEvents() {
            const inputs = [nameInput, phoneInput, dateInput, customTimeInput, serviceItemTextarea];
            inputs.forEach(input => {
                input.addEventListener('input', updateSummary);
                input.addEventListener('change', updateSummary);
            });
            sendToLineBtn.addEventListener('click', handleSendToLine);
            addToCalendarBtn.addEventListener('click', handleAddToCalendar);
        }
        
        function init() {
            initDurationSelection();
            setDefaultDate();
            bindEvents();
            updateSummary();
            // 自定義時段提示
            customTimeInput.placeholder = "例如：14:30、下午3點、15:00~16:00";
        }
        
        init();
    })();
</script>
</body>
</html>