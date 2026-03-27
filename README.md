# Es<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>優雅預約系統 | 線上預約表</title>
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
            backdrop-filter: blur(0px);
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

        /* 雙欄佈局 (桌面) */
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

        /* 服務項目樣式 (自定義radio樣式) */
        .service-group {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
            margin-top: 0.3rem;
        }

        .service-option {
            flex: 1 1 110px;
            background: #f8fafc;
            border: 1.5px solid #e2edf2;
            border-radius: 2rem;
            transition: all 0.2s;
            cursor: pointer;
            text-align: center;
            padding: 0.6rem 0.2rem;
        }

        .service-option.selected {
            background: #1f3b4c;
            border-color: #1f3b4c;
            color: white;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        .service-option.selected .service-name {
            color: white;
        }

        .service-name {
            font-weight: 600;
            font-size: 0.9rem;
            display: block;
        }

        .service-price {
            font-size: 0.7rem;
            opacity: 0.8;
            display: block;
        }

        input[type="radio"] {
            display: none;
        }

        /* 日期時間區域特別 */
        .datetime-row {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .datetime-row .input-group {
            flex: 1;
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

        /* 預約成功彈窗/訊息區塊 */
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
        }
    </style>
</head>
<body>

<div class="booking-card">
    <div class="hero">
        <h1>
            <span>📅</span> 線上預約系統
        </h1>
        <p>選擇服務 · 填寫資料 · 快速預約</p>
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
                        <label>✉️ 電子郵件</label>
                        <input type="email" id="email" name="email" placeholder="example@domain.com">
                    </div>
                    <div class="input-group">
                        <label>💬 備註 / 特殊需求</label>
                        <textarea id="notes" placeholder="例如: 需要無障礙空間、素食點心⋯"></textarea>
                    </div>
                </div>

                <!-- 右側欄位：預約細項 -->
                <div class="form-col">
                    <!-- 服務項目 (模擬radio風格) -->
                    <div class="input-group">
                        <label>✨ 服務項目 <span style="color:#e53e3e;">*</span></label>
                        <div class="service-group" id="serviceGroup">
                            <label class="service-option" data-value="consultation">
                                <input type="radio" name="service" value="專業諮詢 (60min)" hidden>
                                <span class="service-name">💬 專業諮詢</span>
                                <span class="service-price">NT$ 800</span>
                            </label>
                            <label class="service-option" data-value="beauty">
                                <input type="radio" name="service" value="精緻美容護理 (90min)" hidden>
                                <span class="service-name">🌸 精緻美容</span>
                                <span class="service-price">NT$ 1,500</span>
                            </label>
                            <label class="service-option" data-value="massage">
                                <input type="radio" name="service" value="深層放鬆按摩 (60min)" hidden>
                                <span class="service-name">💆 深層按摩</span>
                                <span class="service-price">NT$ 1,200</span>
                            </label>
                            <label class="service-option" data-value="hair">
                                <input type="radio" name="service" value="時尚髮型設計 (90min)" hidden>
                                <span class="service-name">✂️ 髮型設計</span>
                                <span class="service-price">NT$ 1,000</span>
                            </label>
                        </div>
                        <small style="color:#6b7a85; font-size:0.7rem; margin-top:6px;">點擊選項即可選擇服務</small>
                    </div>

                    <!-- 日期 + 時間 雙欄 -->
                    <div class="datetime-row">
                        <div class="input-group">
                            <label>📆 預約日期 <span style="color:#e53e3e;">*</span></label>
                            <input type="date" id="date" name="date" required>
                        </div>
                        <div class="input-group">
                            <label>⏰ 時段 <span style="color:#e53e3e;">*</span></label>
                            <select id="timeSlot" name="timeSlot" required>
                                <option value="" disabled selected>— 請選擇時段 —</option>
                                <option value="09:00~10:00">09:00 - 10:00</option>
                                <option value="10:00~11:00">10:00 - 11:00</option>
                                <option value="11:00~12:00">11:00 - 12:00</option>
                                <option value="13:00~14:00">13:00 - 14:00</option>
                                <option value="14:00~15:00">14:00 - 15:00</option>
                                <option value="15:00~16:00">15:00 - 16:00</option>
                                <option value="16:00~17:00">16:00 - 17:00</option>
                                <option value="17:00~18:00">17:00 - 18:00</option>
                            </select>
                        </div>
                    </div>
                    <div class="input-group">
                        <label>👥 人數</label>
                        <select id="guests" name="guests">
                            <option value="1">1 人</option>
                            <option value="2">2 人</option>
                            <option value="3">3 人</option>
                            <option value="4">4 人</option>
                            <option value="5+">5 人以上</option>
                        </select>
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
        const emailInput = document.getElementById('email');
        const dateInput = document.getElementById('date');
        const timeSelect = document.getElementById('timeSlot');
        const guestsSelect = document.getElementById('guests');
        const notesTextarea = document.getElementById('notes');
        const summaryDiv = document.getElementById('summaryText');

        // 服務項目的動態點選模擬 radio
        const serviceOptions = document.querySelectorAll('.service-option');
        let selectedServiceValue = '';     // 儲存目前選中的服務文字 (例如 "專業諮詢 (60min)")
        let selectedServicePrice = '';      // 可顯示價格用

        // 設定今日日期為 min，避免選到過去 (且未來開放3個月)
        const today = new Date();
        const yyyy = today.getFullYear();
        const mm = String(today.getMonth() + 1).padStart(2, '0');
        const dd = String(today.getDate()).padStart(2, '0');
        const minDate = `${yyyy}-${mm}-${dd}`;
        dateInput.setAttribute('min', minDate);
        // 設定最大日期 (3個月後)
        const maxDateObj = new Date();
        maxDateObj.setMonth(maxDateObj.getMonth() + 3);
        const maxY = maxDateObj.getFullYear();
        const maxM = String(maxDateObj.getMonth() + 1).padStart(2, '0');
        const maxD = String(maxDateObj.getDate()).padStart(2, '0');
        dateInput.setAttribute('max', `${maxY}-${maxM}-${maxD}`);

        // 設定服務項目點選邏輯
        function initServiceSelection() {
            // 預設選中第一個 (專業諮詢)
            const firstOption = serviceOptions[0];
            if (firstOption) {
                const radioInside = firstOption.querySelector('input[type="radio"]');
                if (radioInside) {
                    radioInside.checked = true;
                    selectedServiceValue = radioInside.value;
                    // 附加價格資訊給摘要使用 (可從span抓)
                    const priceSpan = firstOption.querySelector('.service-price');
                    if(priceSpan) selectedServicePrice = priceSpan.innerText;
                }
                firstOption.classList.add('selected');
            }

            serviceOptions.forEach(option => {
                option.addEventListener('click', (e) => {
                    // 防止點擊內部radio冒泡
                    e.stopPropagation();
                    const radio = option.querySelector('input[type="radio"]');
                    if (!radio) return;
                    // 清除所有selected樣式
                    serviceOptions.forEach(opt => opt.classList.remove('selected'));
                    option.classList.add('selected');
                    radio.checked = true;
                    selectedServiceValue = radio.value;
                    const priceSpan = option.querySelector('.service-price');
                    if(priceSpan) selectedServicePrice = priceSpan.innerText;
                    else selectedServicePrice = '';
                    // 觸發即時更新摘要
                    updateSummaryPreview();
                });
            });
        }

        // 取得服務顯示文字 (含價格風格)
        function getServiceDisplayText() {
            if (!selectedServiceValue) return '未選擇服務';
            let priceText = selectedServicePrice ? ` ${selectedServicePrice}` : '';
            return `${selectedServiceValue}${priceText}`;
        }

        // 更新下方即時摘要 (友善預覽)
        function updateSummaryPreview() {
            const customerName = nameInput.value.trim() || '(未填)';
            const phoneVal = phoneInput.value.trim() || '(未填)';
            const serviceText = getServiceDisplayText();
            const dateVal = dateInput.value;
            const timeVal = timeSelect.options[timeSelect.selectedIndex]?.value || '尚未選擇時段';
            const guestsVal = guestsSelect.value;
            let formattedDate = dateVal ? dateVal : '未選擇日期';
            if(dateVal) {
                // 轉成易讀格式 YYYY-MM-DD -> YYYY/MM/DD
                formattedDate = dateVal.replace(/-/g, '/');
            }
            let notesPreview = notesTextarea.value.trim();
            if(notesPreview) notesPreview = `備註：${notesPreview.substring(0, 40)}${notesPreview.length>40?'…':''}`;
            else notesPreview = '無備註';

            summaryDiv.innerHTML = `
                <div style="display:flex; flex-wrap:wrap; justify-content:space-between; gap:0.3rem;">
                    <span><strong>👤 姓名：</strong> ${escapeHtml(customerName)}</span>
                    <span><strong>📞 電話：</strong> ${escapeHtml(phoneVal)}</span>
                </div>
                <div><strong>✨ 服務：</strong> ${escapeHtml(serviceText)}</div>
                <div><strong>📅 日期：</strong> ${escapeHtml(formattedDate)} ｜ <strong>⏰ 時段：</strong> ${escapeHtml(timeVal)}</div>
                <div><strong>👥 人數：</strong> ${escapeHtml(guestsVal)} 人 ｜ <strong>📝 備註：</strong> ${escapeHtml(notesPreview)}</div>
            `;
        }

        // 簡易防XSS
        function escapeHtml(str) {
            if (!str) return '';
            return str.replace(/[&<>]/g, function(m) {
                if (m === '&') return '&amp;';
                if (m === '<') return '&lt;';
                if (m === '>') return '&gt;';
                return m;
            }).replace(/[\uD800-\uDBFF][\uDC00-\uDFFF]/g, function(c) {
                return c;
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
                // 恢復原本風格 (以免下次錯誤底色殘留)
                setTimeout(() => {
                    toast.style.background = "#1e2f3a";
                }, 300);
            }, 2800);
        }

        // 驗證表單完整性 (前端)
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
            // 簡單電話驗證 (數字、 dash)
            const phoneRegex = /^[\d\s\-+()]{8,20}$/;
            if (!phoneRegex.test(phone)) {
                showToast('請輸入有效的電話號碼 (8~20位數字/橫線)', true);
                phoneInput.focus();
                return false;
            }
            if (!selectedServiceValue) {
                showToast('請選擇一項服務項目', true);
                return false;
            }
            if (!dateInput.value) {
                showToast('請選擇預約日期', true);
                dateInput.focus();
                return false;
            }
            if (!timeSelect.value) {
                showToast('請選擇預約時段', true);
                timeSelect.focus();
                return false;
            }
            // 檢查日期不可為週日或過早 (基本營業: 可加但自由, 可加週六週日都可, 此處簡單提醒如果選週末)
            const selectedDate = new Date(dateInput.value);
            const dayOfWeek = selectedDate.getDay(); // 0周日 6周六
            if (dayOfWeek === 0) {
                // 只是溫馨提醒，不強制阻擋 (讓使用者決定)
                if(!confirm('您選擇的是週日，部分服務可能需確認營業時間，確定要預約嗎？')) {
                    return false;
                }
            }
            return true;
        }

        // 處理提交 (展示預約成功資訊)
        function handleSubmit(e) {
            e.preventDefault();
            if (!validateForm()) return;

            // 組合預約資料 (模擬儲存至後端)
            const bookingData = {
                id: 'BK' + Date.now(),
                name: nameInput.value.trim(),
                phone: phoneInput.value.trim(),
                email: emailInput.value.trim() || '未提供',
                service: selectedServiceValue,
                servicePrice: selectedServicePrice,
                date: dateInput.value,
                timeSlot: timeSelect.value,
                guests: guestsSelect.value,
                notes: notesTextarea.value.trim() || '無',
                createdTime: new Date().toLocaleString()
            };

            // 本地存檔 (可儲存至 localStorage 模擬歷史紀錄，但主要展示預約成功訊息)
            try {
                let history = localStorage.getItem('bookingHistory');
                let bookingsArray = history ? JSON.parse(history) : [];
                bookingsArray.unshift(bookingData);
                // 保留最近10筆避免過大
                if(bookingsArray.length > 20) bookingsArray.pop();
                localStorage.setItem('bookingHistory', JSON.stringify(bookingsArray));
            } catch(e) { /* 靜默 */ }

            // 顯示完整預約明細 (漂亮的成功彈窗)
            const serviceShow = `${selectedServiceValue} ${selectedServicePrice ? '('+selectedServicePrice+')' : ''}`;
            const successMsg = `✅ 預約成功！\n\n📌 預約編號：${bookingData.id}\n👤 姓名：${bookingData.name}\n📞 電話：${bookingData.phone}\n✨ 服務：${serviceShow}\n📆 日期：${bookingData.date}\n⏰ 時段：${bookingData.timeSlot}\n👥 人數：${bookingData.guests}人\n📝 備註：${bookingData.notes !== '無' ? bookingData.notes : '－'}\n\n📧 確認信已發送至${bookingData.email || '未提供信箱'} (模擬)\n感謝您的預約！`;

            // 跳出更精緻的 alert 但更優雅可使用自訂modal，此處用 alert 但為了體驗採用模擬對話框，但較直觀
            // 使用自訂模擬 alert 會破壞簡單性，直接 alert 搭配但為了高級感，使用彈窗風格替代: 但是為了通用，仍用 alert 但文字漂亮。
            // 但為了提升體驗 使用 showToast 並搭配 console，但最好顯示完整資訊：改用 confirm 風格？alert 會被阻擋, 使用自訂彈窗較費工，但仍做小modal？
            // 為保持簡潔且資訊完整，我們採用內置彈出視窗: 用 alert 但將文字排版換行
            alert(successMsg);
            // 顯示短toast
            showToast(`預約完成！編號 ${bookingData.id}`, false);
            // 可選擇重置表單 (部分保留不清除? 保留姓名電話清空? 設計上僅輕微重置但不強迫 選擇保留部分? 提供重置按鈕較佳, 但提供重置所有但不清除姓名)
            // 依照使用者體驗，提交後不自動清空所有，而是讓使用者手動清除; 但為了防止重複提交，可重置服務項目保持，但不清除姓名等；但使用者可能需要重新填寫另一筆，建議提供重置小按鈕？無需複雜，但可以讓表單保留或重置部分，但最好將日期及時間保留但可讓客戶繼續，不過為了避免重複提交後續, 保留表單內容讓他們手動修改。
            // 只是預約demo，不用重置。但可讓日期、時段保留目前選項方便再次預約，但為保險，不自動重置，符合預期。
            // 但使用者若想再約一次可手動改, 也可以提供一個「清除表單」小功能，但省略保持清爽。
            // 額外加一個小彩蛋: 聚焦到姓名 方便新增
            nameInput.focus();
        }

        // 監聽所有輸入欄位更新摘要
        function bindSummaryEvents() {
            const inputs = [nameInput, phoneInput, emailInput, dateInput, timeSelect, guestsSelect, notesTextarea];
            inputs.forEach(input => {
                input.addEventListener('input', updateSummaryPreview);
                input.addEventListener('change', updateSummaryPreview);
            });
            // 服務初始變更時更新摘要 (因為上面點選已經觸發update)
            // 再加上手動調用一次
            updateSummaryPreview();
        }

        // 設定日期預設為明天? (為了UI更好，預設設為明天+ 不強迫)
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

        // 初始化所有
        function init() {
            initServiceSelection();
            setDefaultDate();
            bindSummaryEvents();
            form.addEventListener('submit', handleSubmit);
            // 額外確保如果點擊標籤也會更新
            updateSummaryPreview();
        }

        init();
    })();
</script>
</body>
</html>