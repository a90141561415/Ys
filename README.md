<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="default" />
  <meta name="apple-mobile-web-app-title" content="森呼吸芳療塔羅" />
  <title>森呼吸・塔羅芳療身心處方</title>
  <style>
    :root {
      --bg-cream: #F7F5F0;
      --bg-card: #FFFFFF;
      --sage-dark: #2C4238;
      --sage-main: #4A6B5D;
      --sage-light: #E4ECE7;
      --sage-muted: #8FA398;
      --gold-accent: #B89768;
      --gold-light: #F3ECE0;
      --text-main: #2D3330;
      --text-sub: #636E68;
      --border-soft: #E2DDD3;
      --shadow-soft: 0 12px 32px rgba(44, 66, 56, 0.08);
      --shadow-card: 0 8px 20px rgba(44, 66, 56, 0.14);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "PingFang TC", "Microsoft JhengHei", "Noto Sans TC", sans-serif;
      background-color: var(--bg-cream);
      color: var(--text-main);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      overflow-x: hidden;
      background-image:
        radial-gradient(circle at 12% 18%, rgba(74, 107, 93, 0.06) 0%, transparent 45%),
        radial-gradient(circle at 88% 82%, rgba(184, 151, 104, 0.08) 0%, transparent 45%);
    }

    /* 頂部導覽列 */
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 18px 24px;
      max-width: 1024px;
      width: 100%;
      margin: 0 auto;
      z-index: 10;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 600;
      font-size: 1.05rem;
      color: var(--sage-dark);
      letter-spacing: 0.08em;
    }

    .brand-icon {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background: var(--sage-main);
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.95rem;
      flex-shrink: 0;
    }

    .btn-ghost {
      background: rgba(255, 255, 255, 0.75);
      border: 1px solid var(--border-soft);
      color: var(--sage-dark);
      padding: 8px 14px;
      border-radius: 20px;
      font-size: 0.85rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: all 0.2s ease;
    }

    .btn-ghost:hover {
      background: #fff;
      border-color: var(--sage-main);
    }

    /* 主容器 */
    main {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 12px 20px 36px;
      max-width: 1024px;
      width: 100%;
      margin: 0 auto;
    }

    .screen {
      display: none;
      width: 100%;
      animation: fadeIn 0.55s ease forwards;
    }

    .screen.active {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* 第一步：靜心迎賓畫面 */
    .welcome-box {
      text-align: center;
      max-width: 540px;
      padding: 24px 16px;
    }

    .breath-circle-wrap {
      position: relative;
      width: 150px;
      height: 150px;
      margin: 0 auto 32px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .breath-ring {
      position: absolute;
      width: 100%;
      height: 100%;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(74, 107, 93, 0.18) 0%, rgba(74, 107, 93, 0.03) 70%);
      animation: breathe 6s ease-in-out infinite;
    }

    .breath-ring:nth-child(2) {
      width: 78%;
      height: 78%;
      border: 1px solid rgba(74, 107, 93, 0.28);
      animation-delay: 0.4s;
    }

    .breath-core {
      width: 84px;
      height: 84px;
      border-radius: 50%;
      background: var(--sage-main);
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.95rem;
      letter-spacing: 0.12em;
      box-shadow: 0 8px 24px rgba(74, 107, 93, 0.25);
      z-index: 2;
    }

    @keyframes breathe {
      0%, 100% { transform: scale(0.92); opacity: 0.75; }
      50% { transform: scale(1.14); opacity: 1; }
    }

    .welcome-subtitle {
      font-size: 0.85rem;
      color: var(--gold-accent);
      letter-spacing: 0.18em;
      text-transform: uppercase;
      margin-bottom: 10px;
      font-weight: 600;
    }

    .welcome-title {
      font-size: 1.85rem;
      color: var(--sage-dark);
      font-weight: 600;
      line-height: 1.4;
      margin-bottom: 16px;
      letter-spacing: 0.04em;
    }

    .welcome-desc {
      font-size: 1rem;
      color: var(--text-sub);
      line-height: 1.8;
      margin-bottom: 34px;
    }

    .btn-primary {
      background: var(--sage-dark);
      color: #fff;
      border: none;
      padding: 16px 40px;
      border-radius: 32px;
      font-size: 1.05rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      cursor: pointer;
      box-shadow: 0 10px 24px rgba(44, 66, 56, 0.22);
      transition: all 0.25s ease;
    }

    .btn-primary:hover {
      background: var(--sage-main);
      transform: translateY(-2px);
    }

    .btn-primary:active {
      transform: scale(0.98);
    }

    /* 第二步：78張抽牌區 */
    .draw-header {
      text-align: center;
      margin-bottom: 18px;
    }

    .draw-header h2 {
      font-size: 1.45rem;
      color: var(--sage-dark);
      margin-bottom: 6px;
      letter-spacing: 0.05em;
    }

    .draw-header p {
      font-size: 0.92rem;
      color: var(--text-sub);
    }

    .deck-controls {
      display: flex;
      gap: 12px;
      margin-bottom: 16px;
    }

    .deck-scroll-hint {
      font-size: 0.82rem;
      color: var(--sage-muted);
      margin-bottom: 10px;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .cards-rail-wrapper {
      width: 100%;
      overflow-x: auto;
      padding: 26px 24px 36px;
      -webkit-overflow-scrolling: touch;
      scrollbar-width: thin;
      scrollbar-color: var(--sage-muted) transparent;
    }

    .cards-rail-wrapper::-webkit-scrollbar {
      height: 6px;
    }

    .cards-rail-wrapper::-webkit-scrollbar-thumb {
      background: rgba(74, 107, 93, 0.3);
      border-radius: 3px;
    }

    .cards-rail {
      display: flex;
      align-items: center;
      min-width: max-content;
      padding: 0 20px;
    }

    .tarot-back {
      width: 108px;
      height: 176px;
      border-radius: 12px;
      background: linear-gradient(145deg, #324B40 0%, #22352C 100%);
      border: 2px solid #C8AD7F;
      box-shadow: -4px 6px 16px rgba(0, 0, 0, 0.16);
      margin-left: -46px;
      cursor: pointer;
      position: relative;
      transition: transform 0.28s cubic-bezier(0.22, 1, 0.36, 1), box-shadow 0.28s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      user-select: none;
    }

    .tarot-back:first-child {
      margin-left: 0;
    }

    .tarot-back::before {
      content: "";
      position: absolute;
      inset: 7px;
      border: 1px solid rgba(200, 173, 127, 0.45);
      border-radius: 7px;
      pointer-events: none;
    }

    .tarot-back-motif {
      width: 44px;
      height: 44px;
      border: 1px solid rgba(200, 173, 127, 0.65);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #D8C094;
      font-size: 1.1rem;
    }

    .tarot-back.shuffling {
      animation: shuffleCard 0.45s ease-in-out;
    }

    @keyframes shuffleCard {
      0% { transform: translateY(0) rotate(0deg); }
      50% { transform: translateY(-14px) rotate(3deg); }
      100% { transform: translateY(0) rotate(0deg); }
    }

    /* 第三步：結果處方籤 */
    .result-container {
      width: 100%;
      max-width: 860px;
      display: grid;
      grid-template-columns: 260px 1fr;
      gap: 28px;
      background: var(--bg-card);
      border-radius: 24px;
      padding: 32px;
      box-shadow: var(--shadow-soft);
      border: 1px solid var(--border-soft);
    }

    /* 牌面視覺卡片 */
    .revealed-card-wrap {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .revealed-card {
      width: 220px;
      height: 340px;
      border-radius: 16px;
      background: linear-gradient(165deg, #FCFBF8 0%, #EFECE4 100%);
      border: 2px solid var(--gold-accent);
      box-shadow: var(--shadow-card);
      padding: 16px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      text-align: center;
      position: relative;
      animation: flipReveal 0.65s cubic-bezier(0.22, 1, 0.36, 1) forwards;
    }

    @keyframes flipReveal {
      0% { opacity: 0; transform: rotateY(80deg) scale(0.92); }
      100% { opacity: 1; transform: rotateY(0deg) scale(1); }
    }

    .revealed-card::before {
      content: "";
      position: absolute;
      inset: 8px;
      border: 1px solid rgba(184, 151, 104, 0.4);
      border-radius: 10px;
      pointer-events: none;
    }

    .card-arcana-tag {
      font-size: 0.75rem;
      letter-spacing: 0.14em;
      color: var(--gold-accent);
      font-weight: 600;
      margin-top: 4px;
    }

    .card-emblem {
      width: 96px;
      height: 96px;
      border-radius: 50%;
      background: var(--sage-light);
      border: 1px solid rgba(74, 107, 93, 0.25);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: var(--sage-dark);
      font-size: 2rem;
    }

    .card-element-badge {
      font-size: 0.72rem;
      color: var(--sage-main);
      margin-top: 4px;
      font-weight: 500;
    }

    .card-title-box h3 {
      font-size: 1.35rem;
      color: var(--sage-dark);
      letter-spacing: 0.06em;
      margin-bottom: 4px;
    }

    .card-title-box span {
      font-size: 0.78rem;
      color: var(--text-sub);
    }

    /* 右側處方解析 */
    .prescription-content {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .rx-badge-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 14px;
    }

    .badge {
      padding: 5px 12px;
      border-radius: 20px;
      font-size: 0.78rem;
      font-weight: 600;
    }

    .badge-formula {
      background: var(--gold-light);
      color: #8C6B3B;
    }

    .badge-quadrant {
      background: var(--sage-light);
      color: var(--sage-dark);
    }

    .rx-section-title {
      font-size: 0.85rem;
      color: var(--sage-main);
      font-weight: 600;
      letter-spacing: 0.08em;
      margin-bottom: 8px;
    }

    .rx-reading {
      font-size: 1.05rem;
      line-height: 1.8;
      color: var(--text-main);
      margin-bottom: 22px;
      background: #FAF9F5;
      padding: 16px 18px;
      border-radius: 14px;
      border-left: 3px solid var(--sage-main);
    }

    .oil-card {
      background: linear-gradient(135deg, #2F473C 0%, #3F5E50 100%);
      color: #fff;
      border-radius: 16px;
      padding: 20px;
      margin-bottom: 16px;
    }

    .oil-card-label {
      font-size: 0.78rem;
      color: #D8C094;
      letter-spacing: 0.14em;
      margin-bottom: 6px;
    }

    .oil-name {
      font-size: 1.45rem;
      font-weight: 600;
      letter-spacing: 0.05em;
      margin-bottom: 10px;
    }

    .oil-chemistry {
      font-size: 0.9rem;
      line-height: 1.65;
      color: rgba(255, 255, 255, 0.9);
      padding-top: 10px;
      border-top: 1px solid rgba(255, 255, 255, 0.16);
    }

    /* 氣味微調區 */
    .swap-box {
      background: var(--bg-cream);
      border-radius: 12px;
      padding: 12px 16px;
      font-size: 0.86rem;
      color: var(--text-sub);
      margin-bottom: 20px;
    }

    .swap-toggle {
      color: var(--sage-dark);
      font-weight: 600;
      cursor: pointer;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 8px;
    }

    .swap-details {
      display: none;
      margin-top: 10px;
      padding-top: 10px;
      border-top: 1px dashed var(--border-soft);
      line-height: 1.6;
      color: var(--text-main);
    }

    .swap-details.open {
      display: block;
    }

    .action-row {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
    }

    .btn-secondary {
      background: #fff;
      border: 1px solid var(--sage-main);
      color: var(--sage-dark);
      padding: 12px 22px;
      border-radius: 26px;
      font-size: 0.92rem;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.2s;
    }

    .btn-secondary:hover {
      background: var(--sage-light);
    }

    /* 芳療師速查彈窗 (Modal) */
    .modal-backdrop {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(28, 38, 33, 0.55);
      backdrop-filter: blur(4px);
      z-index: 100;
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .modal-backdrop.open {
      display: flex;
    }

    .modal-box {
      background: #fff;
      width: 100%;
      max-width: 820px;
      max-height: 86vh;
      border-radius: 20px;
      display: flex;
      flex-direction: column;
      overflow: hidden;
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.25);
    }

    .modal-header {
      padding: 18px 24px;
      background: var(--sage-dark);
      color: #fff;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
    }

    .modal-header h3 {
      font-size: 1.1rem;
      letter-spacing: 0.06em;
    }

    .modal-close {
      background: none;
      border: none;
      color: #fff;
      font-size: 1.5rem;
      cursor: pointer;
      line-height: 1;
      padding: 4px 8px;
    }

    .modal-tabs {
      display: flex;
      background: var(--bg-cream);
      border-bottom: 1px solid var(--border-soft);
    }

    .modal-tab {
      flex: 1;
      padding: 12px;
      border: none;
      background: none;
      font-size: 0.9rem;
      font-weight: 600;
      color: var(--text-sub);
      cursor: pointer;
    }

    .modal-tab.active {
      color: var(--sage-dark);
      background: #fff;
      border-bottom: 2px solid var(--sage-dark);
    }

    .modal-body {
      padding: 20px 24px;
      overflow-y: auto;
      flex: 1;
    }

    .quadrant-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 14px;
    }

    .q-card {
      border: 1px solid var(--border-soft);
      border-radius: 14px;
      padding: 16px;
      background: #FAF9F6;
    }

    .q-card h4 {
      color: var(--sage-dark);
      margin-bottom: 6px;
      font-size: 1rem;
    }

    .q-card .q-chem {
      font-size: 0.8rem;
      color: var(--gold-accent);
      font-weight: 600;
      margin-bottom: 8px;
    }

    .q-card p {
      font-size: 0.86rem;
      color: var(--text-sub);
      line-height: 1.6;
    }

    .search-input {
      width: 100%;
      padding: 10px 14px;
      border: 1px solid var(--border-soft);
      border-radius: 10px;
      margin-bottom: 14px;
      font-size: 0.92rem;
    }

    .db-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.85rem;
    }

    .db-table th, .db-table td {
      text-align: left;
      padding: 10px 8px;
      border-bottom: 1px solid var(--border-soft);
    }

    .db-table th {
      color: var(--sage-dark);
      background: var(--bg-cream);
      position: sticky;
      top: 0;
    }

    .db-row-btn {
      background: var(--sage-light);
      color: var(--sage-dark);
      border: none;
      padding: 6px 12px;
      border-radius: 12px;
      font-size: 0.78rem;
      cursor: pointer;
    }

    /* =====================================
       森呼吸・塔羅芳療
       Responsive Design RWD
       手機 / 平板 / 桌機
    ===================================== */

    /* 全裝置基礎設定 */
    html {
      width: 100%;
      min-height: 100%;
      scroll-behavior: smooth;
      -webkit-text-size-adjust: 100%;
    }

    body {
      width: 100%;
      min-width: 320px;
      min-height: 100vh;
      overflow-x: hidden;
    }

    button {
      min-height: 42px;
      touch-action: manipulation;
    }

    img {
      max-width: 100%;
      height: auto;
    }

    /* 主內容區 */
    main {
      width: 100%;
      max-width: 1200px;
      padding-left: clamp(12px, 3vw, 32px);
      padding-right: clamp(12px, 3vw, 32px);
    }

    /* 頂部導覽 */
    header {
      width: 100%;
      max-width: 1200px;
      gap: 12px;
    }

    .brand {
      white-space: nowrap;
    }

    .btn-ghost {
      white-space: normal;
      justify-content: center;
    }

    /* 抽牌區 */
    .cards-rail-wrapper {
      width: 100%;
      max-width: 100%;
      overscroll-behavior-x: contain;
      scroll-snap-type: x proximity;
    }

    .tarot-back {
      scroll-snap-align: center;
      flex-shrink: 0;
    }

    /* 結果區 */
    .result-container {
      width: 100%;
      max-width: 1100px;
      grid-template-columns: minmax(200px, 260px) minmax(0, 1fr);
    }

    .prescription-content {
      min-width: 0;
    }

    .rx-reading {
      overflow-wrap: anywhere;
    }

    .oil-card {
      overflow-wrap: anywhere;
    }

    /* 速查表 */
    .modal-box {
      width: min(100%, 900px);
    }

    .modal-body {
      min-width: 0;
      overflow-x: auto;
      -webkit-overflow-scrolling: touch;
    }

    .db-table {
      min-width: 540px;
    }

    .quadrant-grid {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    /* 平板：768px～1023px */
    @media screen and (min-width: 768px) and (max-width: 1023px) {
      header {
        padding: 16px 20px;
      }

      main {
        padding-top: 24px;
      }

      .result-container {
        grid-template-columns: 220px minmax(0, 1fr);
        gap: 20px;
        padding: 24px;
      }

      .revealed-card {
        width: 200px;
        height: 310px;
      }

      .quadrant-grid {
        grid-template-columns: repeat(2, 1fr);
      }

      .tarot-back {
        width: 96px;
        height: 160px;
        margin-left: -40px;
      }
    }

    /* 手機：767px 以下 */
    @media screen and (max-width: 767px) {
      header {
        padding: 12px 14px;
        flex-wrap: wrap;
        justify-content: space-between;
      }

      .brand {
        font-size: 0.95rem;
      }

      header .btn-ghost {
        font-size: 0.75rem;
        padding: 8px 10px;
      }

      main {
        padding: 12px 12px 28px;
        justify-content: flex-start;
      }

      .welcome-box {
        padding: 20px 8px;
      }

      .welcome-title {
        font-size: clamp(1.45rem, 6vw, 1.85rem);
      }

      .welcome-desc {
        font-size: 0.92rem;
      }

      .breath-circle-wrap {
        width: 125px;
        height: 125px;
      }

      .breath-core {
        width: 72px;
        height: 72px;
        font-size: 0.82rem;
      }

      .draw-header h2 {
        font-size: 1.2rem;
      }

      .draw-header p {
        font-size: 0.82rem;
        line-height: 1.6;
      }

      .deck-controls {
        width: 100%;
        flex-wrap: wrap;
        justify-content: center;
      }

      .deck-controls button {
        flex: 1;
        min-width: 135px;
        font-size: 0.82rem;
        padding: 9px;
      }

      .deck-scroll-hint {
        font-size: 0.75rem;
        justify-content: center;
        text-align: center;
      }

      .cards-rail-wrapper {
        padding: 24px 12px 30px;
      }

      .cards-rail {
        padding: 0 12px;
      }

      .tarot-back {
        width: 88px;
        height: 145px;
        margin-left: -34px;
        border-radius: 10px;
      }

      .tarot-back-motif {
        width: 34px;
        height: 34px;
      }

      /* 結果處方改成上下排列 */
      .result-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 24px;
        padding: 22px 14px;
        border-radius: 18px;
      }

      .revealed-card {
        width: 190px;
        height: 295px;
      }

      .card-emblem {
        width: 82px;
        height: 82px;
      }

      .prescription-content {
        width: 100%;
      }

      .rx-reading {
        font-size: 0.95rem;
        padding: 14px;
      }

      .oil-card {
        padding: 17px;
      }

      .oil-name {
        font-size: 1.25rem;
      }

      .action-row {
        flex-direction: column;
      }

      .action-row button {
        width: 100%;
      }

      /* 彈出視窗 */
      .modal-backdrop {
        padding: 8px;
        align-items: center;
      }

      .modal-box {
        width: 100%;
        max-height: 92vh;
        border-radius: 16px;
      }

      .modal-header {
        padding: 14px;
      }

      .modal-header h3 {
        font-size: 0.88rem;
        line-height: 1.5;
      }

      .modal-tabs {
        flex-wrap: wrap;
      }

      .modal-tab {
        font-size: 0.78rem;
        padding: 12px 5px;
      }

      .modal-body {
        padding: 14px;
      }

      .quadrant-grid {
        grid-template-columns: 1fr;
      }

      .q-card {
        padding: 14px;
      }

      .search-input {
        font-size: 16px;
      }
    }

    /* 小尺寸手機：480px 以下 */
    @media screen and (max-width: 480px) {
      header {
        align-items: flex-start;
      }

      .brand {
        font-size: 0.85rem;
      }

      header .btn-ghost {
        max-width: 155px;
      }

      .welcome-title {
        font-size: 1.45rem;
      }

      .welcome-desc {
        font-size: 0.88rem;
        line-height: 1.8;
      }

      .btn-primary {
        width: 100%;
        padding: 15px 20px;
      }

      .tarot-back {
        width: 80px;
        height: 132px;
        margin-left: -30px;
      }

      .result-container {
        padding: 18px 12px;
      }

      .revealed-card {
        width: 180px;
        height: 280px;
      }

      .rx-badge-row {
        gap: 6px;
      }

      .badge {
        font-size: 0.72rem;
      }

      .oil-chemistry {
        font-size: 0.82rem;
      }
    }

    /* 電腦滑鼠效果 */
    @media (hover: hover) and (pointer: fine) {
      .tarot-back:hover {
        transform: translateY(-18px) scale(1.04);
        box-shadow: 0 14px 26px rgba(44, 66, 56, 0.28);
        z-index: 20;
      }

      button:hover {
        transition: all 0.2s ease;
      }
    }

    /* 減少動態效果：照顧對動畫敏感的使用者 */
    @media (prefers-reduced-motion: reduce) {
      *,
      *::before,
      *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        scroll-behavior: auto !important;
        transition-duration: 0.01ms !important;
      }
    }
  </style>
</head>
<body>

  <!-- 頂部導覽 -->
  <header>
    <div class="brand">
      <div class="brand-icon">🌿</div>
      <span>森呼吸・塔羅芳療</span>
    </div>
    <button class="btn-ghost" onclick="openReferenceModal()">
      <span>📋 芳療師速查表 (78牌/四象限)</span>
    </button>
  </header>

  <main>
    <!-- 畫面 1：靜心迎賓 -->
    <section id="screen-welcome" class="screen active">
      <div class="welcome-box">
        <div class="breath-circle-wrap">
          <div class="breath-ring"></div>
          <div class="breath-ring"></div>
          <div class="breath-core">深呼吸</div>
        </div>
        <div class="welcome-subtitle">Aromatherapy × Tarot Ritual</div>
        <h1 class="welcome-title">傾聽身體的聲音<br>尋找今日的命定香氣</h1>
        <p class="welcome-desc">
          請先喝一口溫熱的迎賓茶，輕輕閉上眼睛深呼吸三次。<br>
          在心中默想：<strong>「我現在的身心，最需要什麼樣的照顧？」</strong><br>
          準備好後，憑直覺為自己抽取一張專屬處方牌。
        </p>
        <button class="btn-primary" onclick="goToDrawScreen()">開始直覺選牌</button>
      </div>
    </section>

    <!-- 畫面 2：78張橫向牌陣 -->
    <section id="screen-draw" class="screen">
      <div class="draw-header">
        <h2>請憑直覺，點選一張吸引你的牌</h2>
        <p>共 78 張完整牌組（大阿爾克那深層複方 × 小阿爾克那精準單方）</p>
      </div>

      <div class="deck-controls">
        <button class="btn-ghost" onclick="shuffleDeckAnimation()">🔀 重新洗牌</button>
        <button class="btn-ghost" onclick="drawRandomCard()">✨ 幫我隨機感應一張</button>
      </div>

      <div class="deck-scroll-hint">👈 左右滑動瀏覽牌陣，點擊任一張牌面揭曉 👉</div>

      <div class="cards-rail-wrapper" id="rail-wrapper">
        <div class="cards-rail" id="cards-rail"></div>
      </div>
    </section>

    <!-- 畫面 3：今日身心處方籤 -->
    <section id="screen-result" class="screen">
      <div class="result-container">
        <!-- 左側牌面 -->
        <div class="revealed-card-wrap">
          <div class="revealed-card" id="revealed-card-box">
            <div class="card-arcana-tag" id="res-arcana-tag">MAJOR ARCANA</div>
            <div class="card-emblem">
              <div id="res-icon">🌿</div>
              <div class="card-element-badge" id="res-element">火元素</div>
            </div>
            <div class="card-title-box">
              <h3 id="res-name">0. 愚人</h3>
              <span id="res-sub">The Fool</span>
            </div>
          </div>
        </div>

        <!-- 右側精油處方 -->
        <div class="prescription-content">
          <div>
            <div class="rx-badge-row">
              <span class="badge badge-formula" id="res-type-badge">大阿爾克那・深層複方</span>
              <span class="badge badge-quadrant" id="res-quadrant-badge">膽汁型－乾火</span>
            </div>

            <div class="rx-section-title">✦ 當下身心狀態解讀</div>
            <div class="rx-reading" id="res-reading"></div>

            <div class="oil-card">
              <div class="oil-card-label">TODAY'S ESSENTIAL OIL PRESCRIPTION｜今日專屬精油配方</div>
              <div class="oil-name" id="res-oil">甜橙 ＋ 尤加利</div>
              <div class="oil-chemistry" id="res-chem"></div>
            </div>

            <div class="swap-box">
              <div class="swap-toggle" onclick="toggleSwapDetails()">
                <span>👃 現場試聞後想微調香氣？（點此查看同象限替換建議）</span>
                <span id="swap-arrow">▼</span>
              </div>
              <div class="swap-details" id="swap-details"></div>
            </div>
          </div>

          <div class="action-row">
            <button class="btn-primary" onclick="goToDrawScreen()">重新抽一張牌</button>
            <button class="btn-secondary" onclick="goToWelcomeScreen()">回到迎賓首頁</button>
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- 芳療師速查表彈窗 -->
  <div class="modal-backdrop" id="ref-modal" onclick="closeModalOnBackdrop(event)">
    <div class="modal-box">
      <div class="modal-header">
        <h3>🌿 芳療師後台速查（《L'Aromathérapie Exactement》四象限 × 78牌庫）</h3>
        <button class="modal-close" onclick="closeReferenceModal()">&times;</button>
      </div>
      <div class="modal-tabs">
        <button class="modal-tab active" id="tab-quad" onclick="switchModalTab('quad')">法系四象限與14支核心油</button>
        <button class="modal-tab" id="tab-list" onclick="switchModalTab('list')">78 張完整牌庫一覽</button>
      </div>
      <div class="modal-body" id="modal-body-quad">
        <div class="quadrant-grid">
          <div class="q-card">
            <h4>1. 神經型－土（陰／涼／負電｜親油性）</h4>
            <div class="q-chem">官能基：酯類、倍半萜烯｜對應：錢幣牌組</div>
            <p><strong>狀態：</strong>神經緊繃、肌肉僵硬痙攣、工作過勞、難以真正放鬆。<br>
               <strong>工作室核心油：</strong>真正薰衣草、快樂鼠尾草、羅馬洋甘菊、大西洋雪松、岩蘭草。</p>
          </div>
          <div class="q-card">
            <h4>2. 淋巴型－水（陰／涼／負電｜親水性）</h4>
            <div class="q-chem">官能基：醛類、酮類、內酯/香豆素｜對應：聖杯牌組</div>
            <p><strong>狀態：</strong>情緒鬱結、心火旺煩躁、水腫循環差、思緒混亂需降溫。<br>
               <strong>工作室核心油：</strong>山雞椒（馬告）、佛手柑（搭配真正薰衣草、玫瑰天竺葵）。</p>
          </div>
          <div class="q-card">
            <h4>3. 多血型－風（陽／熱／正電｜親水性）</h4>
            <div class="q-chem">官能基：單萜醇、倍半萜醇｜對應：寶劍牌組</div>
            <p><strong>狀態：</strong>用腦過度、能量耗盡、手腳冰冷、缺乏底氣與防護力。<br>
               <strong>工作室核心油：</strong>芳樟、玫瑰天竺葵、甜馬鬱蘭、澳洲檀香（倍半萜醇居中調和）。</p>
          </div>
          <div class="q-card">
            <h4>4. 膽汁型－乾火（陽／熱／正電｜親油性）</h4>
            <div class="q-chem">官能基：單萜烯、氧化物、醚類｜對應：權杖牌組</div>
            <p><strong>狀態：</strong>肩頸氣血瘀滯、胸悶呼吸淺、無力感、需要腎上腺素支持與動力。<br>
               <strong>工作室核心油：</strong>甜橙、黑雲杉、澳洲尤加利（搭配甜馬鬱蘭疏通肌肉）。</p>
          </div>
        </div>
      </div>
      <div class="modal-body" id="modal-body-list" style="display:none;">
        <input type="text" class="search-input" id="db-search" placeholder="搜尋牌名、精油名稱或關鍵字（例如：薰衣草、肩頸、高塔）..." oninput="renderDbTable()" />
        <table class="db-table">
          <thead>
            <tr>
              <th>牌名</th>
              <th>類型</th>
              <th>推薦精油</th>
              <th>操作</th>
            </tr>
          </thead>
          <tbody id="db-table-body"></tbody>
        </table>
      </div>
    </div>
  </div>

  <script>
    // 四象限替換建議對照表
    const QUADRANT_SWAPS = {
      "神經型－土": "同屬「神經型－土（酯類／倍半萜烯）」的替換選項：大西洋雪松、岩蘭草、真正薰衣草、快樂鼠尾草、羅馬洋甘菊。若客人覺得泥土或草本味太重，可微調為大西洋雪松或真正薰衣草。",
      "淋巴型－水": "同屬「淋巴型－水（醛類／香豆素／花香調）」的替換選項：佛手柑、山雞椒、真正薰衣草、玫瑰天竺葵。想更清新可選山雞椒，想更甜美安撫可選佛手柑或天竺葵。",
      "多血型－風": "同屬「多血型－風（單萜醇／倍半萜醇）」的替換選項：芳樟、玫瑰天竺葵、甜馬鬱蘭、澳洲檀香。親膚性極高，適合喜歡溫潤木質花香的客人。",
      "膽汁型－乾火": "同屬「膽汁型－乾火（單萜烯／氧化物）」的替換選項：甜橙、黑雲杉、澳洲尤加利、甜馬鬱蘭。喜歡果香選甜橙，喜歡森林浴選黑雲杉，喜歡清涼通暢選尤加利。",
      "全象限深度調和": "大阿爾克那為「雙重／三重深層複方」。現場試聞時，可保留其中一支主調精油，另一支依客人當下嗅覺偏好，從「真正薰衣草、佛手柑、甜橙、大西洋雪松」中任選一支搭配。"
    };

    // 完整 78 張塔羅牌資料庫（22大牌複方 + 56小牌單方）
    const TAROT_DB = [
      // === 22 張大阿爾克那（複方） ===
      { id: 0, name: "0. 愚人", en: "The Fool", arcana: "大阿爾克那", formula: "深層複方", element: "風 / 新生能量", icon: "🍃", quadrant: "膽汁型－乾火",
        reading: "你的靈魂正渴望一場輕盈的呼吸。近期可能背負了太多「應該」，身體需要卸下重擔，找回純粹的自由與彈性。",
        oil: "甜橙 ＋ 澳洲尤加利",
        chem: "單萜烯 ＋ 氧化物：如清晨森林的微風，清空沉重思緒，打開胸腔呼吸空間，帶來輕盈愉悅感。" },
      { id: 1, name: "I. 魔術師", en: "The Magician", arcana: "大阿爾克那", formula: "深層複方", element: "風 / 創造顯化", icon: "✨", quadrant: "淋巴型－水",
        reading: "你的腦袋正高速運轉、充滿想法，但也容易因此感到肩頸與太陽穴緊繃。今天適合把飄在空中的能量，溫柔地帶回身體裡。",
        oil: "山雞椒 ＋ 芳樟",
        chem: "醛類 ＋ 單萜醇：幫過熱的大腦降溫，同時溫和補氣，讓思緒清晰而不焦躁。" },
      { id: 2, name: "II. 女祭司", en: "The High Priestess", arcana: "大阿爾克那", formula: "深層複方", element: "水 / 內在直覺", icon: "🌙", quadrant: "神經型－土",
        reading: "你最近接收了太多外界的聲音，內心需要一片安靜的湖水。這是一張邀請你向內傾聽、好好與自己獨處的牌。",
        oil: "澳洲檀香 ＋ 真正薰衣草",
        chem: "倍半萜醇 ＋ 酯類：深層安撫神經系統，帶領意識回到平靜的內在中心。" },
      { id: 3, name: "III. 皇后", en: "The Empress", arcana: "大阿爾克那", formula: "深層複方", element: "土 / 豐盛滋養", icon: "🌸", quadrant: "多血型－風",
        reading: "你一直在照顧身邊的人，現在輪到你被好好滋養了。身體渴望溫暖的包覆與寵愛，讓緊繃的肌膚與心靈都軟化下來。",
        oil: "玫瑰天竺葵 ＋ 甜橙",
        chem: "單萜醇 ＋ 單萜烯：平衡荷爾蒙與情緒，帶來如同被溫暖擁抱的豐盛療癒感。" },
      { id: 4, name: "IV. 皇帝", en: "The Emperor", arcana: "大阿爾克那", formula: "深層複方", element: "火 / 穩固支撐", icon: "🏔️", quadrant: "膽汁型－乾火",
        reading: "你扛起了許多責任，習慣凡事撐住，連肌肉都在不知不覺中武裝起來。今天請允許自己卸下盔甲，把重量交給按摩床。",
        oil: "黑雲杉 ＋ 大西洋雪松",
        chem: "單萜烯 ＋ 倍半萜烯：給疲憊的腎上腺「類可體松」支持，同時深層鬆開僵硬背肌。" },
      { id: 5, name: "V. 教皇", en: "The Hierophant", arcana: "大阿爾克那", formula: "深層複方", element: "土 / 安定呼吸", icon: "🕯️", quadrant: "多血型－風",
        reading: "內心有些自我要求或規則讓你感到喘不過氣。身體需要一種穩定、被支持的安全感，幫助你釋放胸口的悶脹。",
        oil: "澳洲檀香 ＋ 佛手柑",
        chem: "倍半萜醇 ＋ 酯類與香豆素：加深呼吸深度，化解內在的拘謹與無形壓力。" },
      { id: 6, name: "VI. 戀人", en: "The Lovers", arcana: "大阿爾克那", formula: "深層複方", element: "風 / 心輪和諧", icon: "🕊️", quadrant: "多血型－風",
        reading: "你正在尋找身與心的和諧共鳴。也許最近在關係或選擇上有些微的拉扯，需要讓心輪重新打開、恢復柔軟的流動。",
        oil: "玫瑰天竺葵 ＋ 快樂鼠尾草",
        chem: "單萜醇 ＋ 酯類：協調自律神經與情感波動，讓身心回到溫柔的平衡點。" },
      { id: 7, name: "VII. 戰車", en: "The Chariot", arcana: "大阿爾克那", formula: "深層複方", element: "水 / 動能調節", icon: "🧭", quadrant: "神經型－土",
        reading: "你像一輛高速行駛的車，衝勁十足卻忘了進站保養。雙腿與下背可能累積了不少緊繃，需要幫身體踩個溫柔的煞車。",
        oil: "甜馬鬱蘭 ＋ 岩蘭草",
        chem: "單萜醇 ＋ 倍半萜烯：極佳的肌肉鬆弛與接地組合，讓浮躁的動能平穩沉澱下來。" },
      { id: 8, name: "VIII. 力量", en: "Strength", arcana: "大阿爾克那", formula: "深層複方", element: "火 / 溫柔接納", icon: "🦁", quadrant: "淋巴型－水",
        reading: "外表看起來很堅強的你，內在其實有點累了。真正的力量來自於溫柔地接納自己的疲憊，今天讓雙手替你揉開深層的結。",
        oil: "佛手柑 ＋ 真正薰衣草",
        chem: "酯類 ＋ 香豆素：安撫緊繃的神經末梢，用陽光般的香氣融化內在的硬撐。" },
      { id: 9, name: "IX. 隱士", en: "The Hermit", arcana: "大阿爾克那", formula: "深層複方", element: "土 / 深度靜心", icon: "🏮", quadrant: "神經型－土",
        reading: "你需要暫時關掉外界的喧囂，給自己一段不被打擾的修復時光。這是一張適合深度靜心、釋放深層疲勞的牌。",
        oil: "大西洋雪松 ＋ 澳洲檀香",
        chem: "倍半萜烯 ＋ 倍半萜醇：深沉木質調，把向外耗散的能量全部收攝回體內修復。" },
      { id: 10, name: "X. 命運之輪", en: "Wheel of Fortune", arcana: "大阿爾克那", formula: "深層複方", element: "火 / 節奏對齊", icon: "☸️", quadrant: "膽汁型－乾火",
        reading: "生活正處於一個節奏轉換的路口，身體可能因為適應變化而感到微微失衡。順應流動，讓今天的按摩幫你重新對齊節奏。",
        oil: "甜橙 ＋ 甜馬鬱蘭",
        chem: "單萜烯 ＋ 單萜醇：暢通氣血循環，協助身體順暢地度過季節或生活轉折。" },
      { id: 11, name: "XI. 正義", en: "Justice", arcana: "大阿爾克那", formula: "深層複方", element: "風 / 思緒歸零", icon: "⚖️", quadrant: "神經型－土",
        reading: "你花了很多心力在衡量、思考與維持平衡，大腦與肩頸處於過度緊繃的狀態。現在不需要再分析對錯，只需要單純地放鬆。",
        oil: "快樂鼠尾草 ＋ 佛手柑",
        chem: "高比例酯類 ＋ 香豆素：強力抗痙攣與平衡神經，幫過度理性的大腦按下暫停鍵。" },
      { id: 12, name: "XII. 倒吊人", en: "The Hanged Man", arcana: "大阿爾克那", formula: "深層複方", element: "水 / 蓄力流動", icon: "🌊", quadrant: "膽汁型－乾火",
        reading: "感覺有些事情卡住了，或是身體正處於「動彈不得」的沉重期。換個視角休息一下吧，這段停滯期其實是身體在為你蓄力。",
        oil: "澳洲尤加利 ＋ 大西洋雪松",
        chem: "氧化物 ＋ 倍半萜烯：打開受限的呼吸空間，促進淋巴與末梢循環流動。" },
      { id: 13, name: "XIII. 死神", en: "Death", arcana: "大阿爾克那", formula: "深層複方", element: "水 / 代謝重啟", icon: "🦋", quadrant: "膽汁型－乾火",
        reading: "舊的疲憊與情緒毒素正準備離開你的身體，這是一個「徹底代謝與重啟」的時刻。放心地把累積的痠痛都代謝掉吧。",
        oil: "黑雲杉 ＋ 大西洋雪松",
        chem: "單萜烯 ＋ 倍半萜烯：清理停滯的能量與乳酸堆積，迎接身心煥然一新。" },
      { id: 14, name: "XIV. 節制", en: "Temperance", arcana: "大阿爾克那", formula: "深層複方", element: "火 / 溫潤調和", icon: "🏺", quadrant: "多血型－風",
        reading: "你的身體正在努力尋找自我修復的平衡點。這是一張非常溫和的療癒牌，適合用如流水般順暢的手法，調和體內的水分與氣場。",
        oil: "芳樟 ＋ 真正薰衣草",
        chem: "單萜醇 ＋ 酯類：最溫和親膚的黃金比例，如春雨般滋潤疲憊的身心。" },
      { id: 15, name: "XV. 惡魔", en: "The Devil", arcana: "大阿爾克那", formula: "深層複方", element: "土 / 深層鬆綁", icon: "⛓️", quadrant: "神經型－土",
        reading: "身體被長期的壓力、熬夜或執念緊緊束縛住了，肩頸與腰背可能有明顯的氣結。今天讓我們一起把這些沉重的枷鎖鬆綁。",
        oil: "岩蘭草 ＋ 山雞椒",
        chem: "倍半萜烯 ＋ 醛類：岩蘭草深層接地排濁，山雞椒打破沉悶鬱結，釋放深層壓力。" },
      { id: 16, name: "XVI. 高塔", en: "The Tower", arcana: "大阿爾克那", formula: "深層複方", element: "火 / 張力釋放", icon: "⚡", quadrant: "神經型－土",
        reading: "累積已久的壓力似乎到了臨界點，身體正在發出「需要徹底釋放」的訊號。別擔心，打破緊繃之後，迎來的是前所未有的輕鬆。",
        oil: "羅馬洋甘菊 ＋ 甜橙",
        chem: "酯類 ＋ 單萜烯：洋甘菊擁有極強的安撫與釋放張力效果，溫柔接住突如其來的疲憊。" },
      { id: 17, name: "XVII. 星星", en: "The Star", arcana: "大阿爾克那", formula: "深層複方", element: "風 / 清澈微光", icon: "⭐", quadrant: "淋巴型－水",
        reading: "經過一段時間的忙碌，你終於迎來了療癒與希望的微光。今天的按摩將像星光灑落一樣，為你注入純淨、清澈的新能量。",
        oil: "佛手柑 ＋ 芳樟",
        chem: "酯類 ＋ 單萜醇：清澈透亮的香氣，撫平過去的勞累，帶來平靜與希望感。" },
      { id: 18, name: "XVIII. 月亮", en: "The Moon", arcana: "大阿爾克那", formula: "深層複方", element: "水 / 潛意識安撫", icon: "🌕", quadrant: "神經型－土",
        reading: "潛意識裡可能藏著一些說不出口的不安或敏感，連帶影響了睡眠品質與腸胃。在這個安全的空間裡，你可以完全放下戒備。",
        oil: "羅馬洋甘菊 ＋ 快樂鼠尾草",
        chem: "高比例酯類：深度安撫敏感的神經系統與腹部緊繃，幫助夜晚深層好眠。" },
      { id: 19, name: "XIX. 太陽", en: "The Sun", arcana: "大阿爾克那", formula: "深層複方", element: "火 / 生命力回升", icon: "☀️", quadrant: "膽汁型－乾火",
        reading: "你的生命力正在回升，或正準備迎接充滿活力的新階段！今天的精油將為你點燃內在的小太陽，讓全身氣血暢通、充滿暖意。",
        oil: "甜橙 ＋ 黑雲杉",
        chem: "高比例單萜烯：充滿陽光與森林正電能量的組合，提振精神、消除倦怠。" },
      { id: 20, name: "XX. 審判", en: "Judgement", arcana: "大阿爾克那", formula: "深層複方", element: "火 / 自癒力喚醒", icon: "🎺", quadrant: "膽汁型－乾火",
        reading: "身體正在喚醒沉睡已久的自癒力。這是一個身心重新開機、找回輕盈感的重要時刻，深呼吸，迎接全新的自己。",
        oil: "澳洲尤加利 ＋ 玫瑰天竺葵",
        chem: "氧化物 ＋ 單萜醇：清新的呼吸感搭配花香的滋養，喚醒身體每一個細胞的活力。" },
      { id: 21, name: "XXI. 世界", en: "The World", arcana: "大阿爾克那", formula: "深層複方", element: "土 / 身心圓滿", icon: "🌍", quadrant: "全象限深度調和",
        reading: "恭喜你完成了一段不簡單的旅程，現在是犒賞自己、享受完整與圓滿的時刻。讓這場全身的香氣之旅，為你畫下最完美的句點。",
        oil: "澳洲檀香 ＋ 佛手柑 ＋ 甜橙",
        chem: "倍半萜醇 ＋ 酯類 ＋ 單萜烯：兼具穩定、安撫與愉悅的完美交響，帶來全方位的身心圓滿。" },

      // === 權杖牌組 14 張（單方） ===
      { id: 22, name: "權杖 Ace", en: "Ace of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "內心正燃起一股新的熱情與動力，身體也準備好迎接新開始。需要一點陽光的能量，幫你點燃活力。",
        oil: "甜橙（單方）", chem: "單萜烯：帶來溫暖愉悅的陽光能量，活絡全身氣血循環。" },
      { id: 23, name: "權杖 2", en: "Two of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "站在規劃與展望的十字路口，眼神看著遠方，肩膀卻不自覺微微聳起。先深呼吸，把力量收回到當下。",
        oil: "黑雲杉（單方）", chem: "單萜烯：像高聳的針葉林般給予脊柱支撐力，穩定心神。" },
      { id: 24, name: "權杖 3", en: "Three of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "多血型－風",
        reading: "事情正在推進中，你付出了許多心力等待成果。雙腿與下背有些微的奔波感，適合好好舒展筋骨。",
        oil: "甜馬鬱蘭（單方）", chem: "單萜醇：溫熱舒緩奔波後的肌肉緊繃，讓身體重新暖起來。" },
      { id: 25, name: "權杖 4", en: "Four of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "階段性的忙碌告一段落，現在是享受安定與喜悅的時刻。讓甜美的香氣陪你一起慶祝這份輕鬆。",
        oil: "甜橙（單方）", chem: "單萜烯：放大身心的愉悅與放鬆感，享受無憂無慮的片刻。" },
      { id: 26, name: "權杖 5", en: "Five of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "外界似乎有些雜音或小競爭讓你感到微躁，體內有一股悶熱的火氣。需要清涼的微風幫你理順氣場。",
        oil: "澳洲尤加利（單方）", chem: "氧化物：疏通胸口鬱悶的熱氣，讓呼吸重新變得寬敞順暢。" },
      { id: 27, name: "權杖 6", en: "Six of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "你剛剛打了一場漂亮的勝仗，精神亢奮但肌肉其實已經很累了。現在可以安心把光環卸下，交給雙手照顧。",
        oil: "黑雲杉（單方）", chem: "單萜烯：補充腎上腺能量，幫助亢奮的神經系統平穩降落。" },
      { id: 28, name: "權杖 7", en: "Seven of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "多血型－風",
        reading: "感覺最近一直在防禦、應付各種突發狀況，上背部與肩胛骨特別僵硬。在這裡很安全，不用再武裝自己了。",
        oil: "甜馬鬱蘭（單方）", chem: "單萜醇：軟化長期處於防禦狀態的僵硬背肌，帶來安全感。" },
      { id: 29, name: "權杖 8", en: "Eight of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "淋巴型－水",
        reading: "生活節奏快得像一陣風，訊息與任務接踵而來，連呼吸都變得急促。讓香氣幫你把快轉鍵按回正常速度。",
        oil: "山雞椒（單方）", chem: "醛類：快速幫高速運轉的躁動感降溫，理清混亂節奏。" },
      { id: 30, name: "權杖 9", en: "Nine of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "雖然已經很疲憊了，但責任感讓你還在咬牙撐著最後一哩路。這是一張提醒你「該中場休息充電」的溫柔訊號。",
        oil: "黑雲杉（單方）", chem: "單萜烯：深層滋養透支的體力，為疲憊的身體注入森林元氣。" },
      { id: 31, name: "權杖 10", en: "Ten of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "多血型－風",
        reading: "身上背負了太多不屬於你的責任，肩膀沉重得快喘不過氣。今天把所有的重擔都放在門外，單純享受被照顧。",
        oil: "甜馬鬱蘭（單方）", chem: "單萜醇：深度鬆開如石頭般堅硬的肩頸斜方肌，卸下重擔。" },
      { id: 32, name: "權杖侍者", en: "Page of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "對生活充滿好奇與躍躍欲試的能量，但偶爾會有點三分鐘熱度或小急躁。保持這份純真，同時讓身體穩下來。",
        oil: "甜橙（單方）", chem: "單萜烯：滋養純粹的快樂與創造力，讓氣血順暢流動。" },
      { id: 33, name: "權杖騎士", en: "Knight of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "一股腦往前衝的行動派，能量集中在頭部與上半身，容易感到燥熱或緊繃。讓清新的草本幫你平衡衝勁。",
        oil: "澳洲尤加利（單方）", chem: "氧化物：引導過旺的火氣向下流動，帶來清爽的呼吸空間。" },
      { id: 34, name: "權杖皇后", en: "Queen of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "多血型－風",
        reading: "充滿魅力與熱情的照顧者，總是用溫暖照亮別人，卻忘了留一點光給自己。今天換你享受女王般的寵愛。",
        oil: "玫瑰天竺葵（單方）", chem: "單萜醇：平衡內在的付出與接收，溫柔滋養女性與心輪能量。" },
      { id: 35, name: "權杖國王", en: "King of Wands", arcana: "小阿爾克那・權杖", formula: "精準單方", element: "火元素", icon: "🔥", quadrant: "膽汁型－乾火",
        reading: "擁有強大的領導力與決斷力，但長期處於高壓決策狀態，容易讓神經與血管緊繃。讓深沉的森林香氣為你減壓。",
        oil: "黑雲杉（單方）", chem: "單萜烯：給予王者般的沉穩支持，深層釋放累積的操勞。" },

      // === 聖杯牌組 14 張（單方） ===
      { id: 36, name: "聖杯 Ace", en: "Ace of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "淋巴型－水",
        reading: "心輪正在溫柔地敞開，適合接納愛、善意與純粹的放鬆。讓如清泉般的香氣流過全身，滋潤乾涸的身心。",
        oil: "佛手柑（單方）", chem: "酯類＋香豆素：如陽光灑落湖面，帶來充滿希望的溫柔安撫。" },
      { id: 37, name: "聖杯 2", en: "Two of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "多血型－風",
        reading: "渴望身與心、自我與他人之間的和諧共鳴。今天的按摩將是一場你與自己身體最溫柔的深度對話。",
        oil: "玫瑰天竺葵（單方）", chem: "單萜醇：協調身心的平衡頻率，帶來被理解與被呵護的感受。" },
      { id: 38, name: "聖杯 3", en: "Three of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "淋巴型－水",
        reading: "內心渴望輕鬆愉快的交流與陪伴，適合釋放平日的拘謹，讓心情像微醺般輕盈放鬆。",
        oil: "佛手柑（單方）", chem: "酯類＋香豆素：掃去內心的陰霾與拘謹，喚起純粹的喜悅感。" },
      { id: 39, name: "聖杯 4", en: "Four of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "淋巴型－水",
        reading: "對日常感到有些提不起勁、情緒微微悶著，身體也容易覺得懶洋洋或水腫。需要一點清新的香氣喚醒感官。",
        oil: "山雞椒（單方）", chem: "醛類：像一顆檸檬糖般打破沉悶的情緒死水，提振低落氣場。" },
      { id: 40, name: "聖杯 5", en: "Five of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "神經型－土",
        reading: "心中還留著一點對過去的遺憾或失落，胸口感覺有些微酸澀緊縮。沒關係，允許情緒隨著呼吸慢慢流走。",
        oil: "真正薰衣草（單方）", chem: "酯類：如母親般溫柔包容的香氣，撫平內心的委屈與皺褶。" },
      { id: 41, name: "聖杯 6", en: "Six of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "神經型－土",
        reading: "內在小孩正在呼喚你，渴望回到單純、無憂無慮、被無條件呵護的狀態。安心閉上眼睛，享受這份純粹的照顧。",
        oil: "羅馬洋甘菊（單方）", chem: "酯類：最溫柔的安撫力量，給內在小孩一個溫暖安全的擁抱。" },
      { id: 42, name: "聖杯 7", en: "Seven of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "多血型－風",
        reading: "腦海中有太多想像、願望或未決定的事，讓能量有點飄浮不定。需要把分散的思緒收攏，重新回到身體裡。",
        oil: "芳樟（單方）", chem: "單萜醇：溫和定心，幫飄在雲端的思緒找到安穩的落腳處。" },
      { id: 43, name: "聖杯 8", en: "Eight of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "神經型－土",
        reading: "準備好揮別消耗你的人事物，踏上尋找內在平靜的旅程。這是一個斷捨離的時刻，讓身體把舊的情緒代謝掉。",
        oil: "真正薰衣草（單方）", chem: "酯類：清理殘留的情緒疲勞，平靜地迎接下一個階段。" },
      { id: 44, name: "聖杯 9", en: "Nine of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "多血型－風",
        reading: "內心感到滿足與富足，身體也處於相當不錯的狀態。今天是一場純粹的感官饗宴，盡情享受這份寵愛吧！",
        oil: "玫瑰天竺葵（單方）", chem: "單萜醇：放大內在的豐盛感與幸福感，讓肌膚與心情都發光。" },
      { id: 45, name: "聖杯 10", en: "Ten of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "淋巴型－水",
        reading: "渴望全方位的安穩、幸福與歸屬感。讓溫暖花香與柑橘調的氣息包圍你，感受身心靈合一的圓滿平靜。",
        oil: "佛手柑（單方）", chem: "酯類＋香豆素：溫暖、陽光、包容，帶來如家一般的安心感。" },
      { id: 46, name: "聖杯侍者", en: "Page of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "多血型－風",
        reading: "內心細膩敏感，容易察覺環境中細微的情緒變化。保護好這份珍貴的感受力，同時用香氣為自己建立溫柔防護罩。",
        oil: "芳樟（單方）", chem: "單萜醇：增強身心防護力，溫柔守護敏感細膩的靈魂。" },
      { id: 47, name: "聖杯騎士", en: "Knight of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "多血型－風",
        reading: "浪漫、重感情，總是把別人的感受放在前面，容易因此感到心累。今天不需要討好任何人，只需要討好你自己。",
        oil: "玫瑰天竺葵（單方）", chem: "單萜醇：把向外流淌的愛收回來滋養自己，平衡情感耗損。" },
      { id: 48, name: "聖杯皇后", en: "Queen of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "淋巴型－水",
        reading: "擁有極強的同理心與包容力，但可能默默吸收了太多周遭的負能量。讓流動的按摩手法幫你排出身體的情緒濕氣。",
        oil: "山雞椒（單方）", chem: "醛類：疏通情緒與淋巴的滯留感，還原清澈輕盈的自己。" },
      { id: 49, name: "聖杯國王", en: "King of Cups", arcana: "小阿爾克那・聖杯", formula: "精準單方", element: "水元素", icon: "💧", quadrant: "神經型－土",
        reading: "習慣在人前保持情緒穩定、成熟冷靜，把所有壓力都往心裡吞。在這個私密的空間裡，你可以安心卸下所有防備。",
        oil: "真正薰衣草（單方）", chem: "酯類：深層鬆開壓抑已久的神經與胸口緊繃，釋放無聲的壓力。" },

      // === 寶劍牌組 14 張（單方） ===
      { id: 50, name: "寶劍 Ace", en: "Ace of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "膽汁型－乾火",
        reading: "腦袋裡有許多新想法正在醞釀，思緒銳利但容易讓頭部與眉心緊繃。需要清涼的空氣感，讓靈感順暢流動。",
        oil: "澳洲尤加利（單方）", chem: "氧化物：提升大腦含氧量，帶來清澈透亮的呼吸與思緒。" },
      { id: 51, name: "寶劍 2", en: "Two of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "神經型－土",
        reading: "心裡似乎有兩個聲音在拉扯，讓你處於一種微微僵持、不敢放鬆的狀態。暫時把選擇題放一邊，先讓身體休息。",
        oil: "快樂鼠尾草（單方）", chem: "酯類：解除內在的糾結與神經痙攣，讓緊繃的身體軟化下來。" },
      { id: 52, name: "寶劍 3", en: "Three of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "神經型－土",
        reading: "心中藏著一點隱隱的刺痛或委屈，可能連帶讓胸口與上背感到緊縮。讓溫柔的香氣像暖流一樣，慢慢融化這份不適。",
        oil: "羅馬洋甘菊（單方）", chem: "酯類：極致的安撫與鎮靜，溫柔撫平心輪的酸澀與緊繃。" },
      { id: 53, name: "寶劍 4", en: "Four of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "神經型－土",
        reading: "這是一張最直接的「深度休眠牌」！你的大腦與神經已經過載，身體強烈渴望一場不受打擾的徹底關機與修復。",
        oil: "真正薰衣草（單方）", chem: "酯類：引導腦波進入深層放鬆狀態，最適合在按摩中好好睡一覺。" },
      { id: 54, name: "寶劍 5", en: "Five of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "多血型－風",
        reading: "最近可能經歷了一些溝通上的摩擦或無力感，讓你覺得心煩意亂。深吸一口氣，把外界的是非都留在門外。",
        oil: "芳樟（單方）", chem: "單萜醇：溫和淨化煩躁氣場，讓心緒重新回到平靜與從容。" },
      { id: 55, name: "寶劍 6", en: "Six of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "多血型－風",
        reading: "正在離開一段混亂或高壓的時期，朝著平靜的水域前進。身體還在慢慢適應放鬆的節奏，需要溫和的陪伴與支持。",
        oil: "芳樟（單方）", chem: "單萜醇：如平靜的微風推著小船前行，安撫過渡期的疲憊。" },
      { id: 56, name: "寶劍 7", en: "Seven of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "神經型－土",
        reading: "習慣用頭腦去應對各種複雜狀況，精神總是處於高度警覺。今天不需要再動腦想策略了，讓身體單純地感受觸碰。",
        oil: "快樂鼠尾草（單方）", chem: "酯類：讓過度警覺的交感神經休息，啟動副交感神經的修復模式。" },
      { id: 57, name: "寶劍 8", en: "Eight of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "膽汁型－乾火",
        reading: "感覺被自己的擔憂或完美主義困住了，肩頸像被無形的繩索綁緊。其實你隨時可以鬆開手，呼吸自由的空氣。",
        oil: "澳洲尤加利（單方）", chem: "氧化物：打破窒息般的緊繃感，打開胸廓，找回自由呼吸的空間。" },
      { id: 58, name: "寶劍 9", en: "Nine of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "神經型－土",
        reading: "深夜裡容易想太多、擔心還沒發生的事，導致睡眠品質受影響。今晚讓這支充滿安撫力的精油，陪你一夜好眠。",
        oil: "羅馬洋甘菊（單方）", chem: "酯類：專攻焦慮型失眠與神經緊繃，帶來深沉安穩的睡眠品質。" },
      { id: 59, name: "寶劍 10", en: "Ten of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "神經型－土",
        reading: "體力與腦力都到達了一個徹底耗盡的谷底——好消息是，從這一刻起，一切都將觸底反彈、重新開始充電！",
        oil: "真正薰衣草（單方）", chem: "酯類：在能量最低點給予最溫柔的修復，陪伴身心重新蓄力。" },
      { id: 60, name: "寶劍侍者", en: "Page of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "膽汁型－乾火",
        reading: "觀察力敏銳、資訊接收量大，但也容易因此感到精神緊繃、眼睛疲勞。讓清新的香氣幫你過濾掉多餘的雜訊。",
        oil: "澳洲尤加利（單方）", chem: "氧化物：消除用眼與用腦過度的疲勞感，讓頭腦恢復清爽。" },
      { id: 61, name: "寶劍騎士", en: "Knight of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "神經型－土",
        reading: "說話與做事都講求效率，精神總是處於衝刺狀態，容易忽略身體發出的痠痛警訊。今天幫自己安排一場慢下來的儀式。",
        oil: "快樂鼠尾草（單方）", chem: "酯類：幫高速運轉的思緒踩煞車，鬆開緊繃的頸部與頭皮。" },
      { id: 62, name: "寶劍皇后", en: "Queen of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "神經型－土",
        reading: "獨立、理性、習慣自己扛起一切，很少在別人面前示弱。今天請允許自己當一個單純被照顧的小孩，安心依靠。",
        oil: "羅馬洋甘菊（單方）", chem: "酯類：融化理性堅強的外殼，溫柔安撫內在深處的疲憊。" },
      { id: 63, name: "寶劍國王", en: "King of Swords", arcana: "小阿爾克那・寶劍", formula: "精準單方", element: "風元素", icon: "🌬️", quadrant: "多血型－風",
        reading: "每天需要做出許多專業判斷，大腦長期處於高壓運作。讓純淨的木質花香幫你清空記憶體，找回內在的寧靜。",
        oil: "芳樟（單方）", chem: "單萜醇：兼顧清晰與放鬆，讓高壓的決策者獲得深層精神休息。" },

      // === 錢幣牌組 14 張（單方） ===
      { id: 64, name: "錢幣 Ace", en: "Ace of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "神經型－土",
        reading: "身體正準備好吸收滿滿的滋養與能量！這是一張非常適合做深層肌肉保養的牌，讓大地精華為你打好健康基礎。",
        oil: "大西洋雪松（單方）", chem: "倍半萜烯：紮實穩定的大地能量，深層滋養疲憊的肌肉與筋膜。" },
      { id: 65, name: "錢幣 2", en: "Two of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "多血型－風",
        reading: "最近在工作與生活之間忙得團團轉，努力維持著平衡，雙腳與腰背也跟著忙碌不停。需要幫身體重新找回穩定的重心。",
        oil: "甜馬鬱蘭（單方）", chem: "單萜醇：調和忙碌帶來的循環失衡，舒緩久站或久坐的腰腿痠痛。" },
      { id: 66, name: "錢幣 3", en: "Three of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "神經型－土",
        reading: "專注在自己的專業與工作上，長時間維持同一個姿勢（如看電腦、低頭），容易造成局部肌肉僵硬。讓雙手幫你精準鬆綁。",
        oil: "大西洋雪松（單方）", chem: "倍半萜烯：促進局部淋巴與循環流動，化解長時間固定姿勢的僵硬。" },
      { id: 67, name: "錢幣 4", en: "Four of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "神經型－土",
        reading: "習慣把責任與壓力緊緊抓在手裡，身體也跟著變得緊繃、缺乏彈性。試著隨著吐氣慢慢鬆開拳頭，你會發現一切都很安全。",
        oil: "岩蘭草（單方）", chem: "倍半萜烯：極致的「接地（Grounding）」力量，幫助緊繃的身心徹底放下戒備。" },
      { id: 68, name: "錢幣 5", en: "Five of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "神經型－土",
        reading: "感覺身體有些虛寒、疲憊，或是最近耗費了太多體力卻沒時間好好吃飯休息。現在你需要最溫暖、厚實的能量包覆。",
        oil: "岩蘭草（單方）", chem: "倍半萜烯：如厚實的大地毯子般溫暖身體，深層補充耗損的元氣。" },
      { id: 69, name: "錢幣 6", en: "Six of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "多血型－風",
        reading: "你在生活中付出了許多時間與精力，現在輪到宇宙透過這場按摩，把同等份量的滋養與愛回饋給你了。",
        oil: "澳洲檀香（單方）", chem: "倍半萜醇：溫潤醇厚的木質香氣，帶來被珍視、被滋養的幸福感。" },
      { id: 70, name: "錢幣 7", en: "Seven of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "神經型－土",
        reading: "辛苦耕耘了一段時間，身體正處於「需要耐心等待恢復」的緩衝期。別急著趕路，今天就在這裡好好休養生息。",
        oil: "大西洋雪松（單方）", chem: "倍半萜烯：穩定耐心的木質能量，陪伴身體慢慢代謝累積的疲勞。" },
      { id: 71, name: "錢幣 8", en: "Eight of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "多血型－風",
        reading: "非常認真、一絲不苟地完成手邊每件事，但也因此讓手臂、肩膀與背部累積了不少職業疲勞。今天讓專業的雙手為你代勞。",
        oil: "甜馬鬱蘭（單方）", chem: "單萜醇：專攻勞損型肌肉痠痛，溫熱活絡辛勤工作的四肢與背肌。" },
      { id: 72, name: "錢幣 9", en: "Nine of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "多血型－風",
        reading: "獨立自主、懂得照顧自己，今天這場按摩正是你送給自己的質感犒賞！盡情享受這段純粹屬於你的優雅時光。",
        oil: "澳洲檀香（單方）", chem: "倍半萜醇：高雅沉靜的香氣，襯托你懂得愛自己的質感與從容。" },
      { id: 73, name: "錢幣 10", en: "Ten of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "神經型－土",
        reading: "渴望長久、穩固的健康與安適感。讓深沉的大地根部與木質精油，為你的身體打下最安穩、放鬆的根基。",
        oil: "岩蘭草（單方）", chem: "倍半萜烯：深層安定神經與肌肉張力，帶來由內而外的踏實感。" },
      { id: 74, name: "錢幣侍者", en: "Page of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "神經型－土",
        reading: "腳踏實地、認真感受身體的每一個微小變化。這是一張非常適合重新建立身體覺察、好好保養自己的牌。",
        oil: "大西洋雪松（單方）", chem: "倍半萜烯：喚醒身體的感知力，讓每一次呼吸與按壓都更有感。" },
      { id: 75, name: "錢幣騎士", en: "Knight of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "多血型－風",
        reading: "雖然步調不快，但每天都在穩定地承受壓力，肌肉裡可能藏著不少「陳年舊痠」。需要深層而穩定的力道慢慢推開。",
        oil: "甜馬鬱蘭（單方）", chem: "單萜醇：溫和滲透深層肌理，軟化累積已久的頑固緊繃。" },
      { id: 76, name: "錢幣皇后", en: "Queen of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "多血型－風",
        reading: "務實、溫暖、總能把生活打理得井井有條，但往往把自己排在最後一位。今天請把所有照顧都留給自己，享受大地母親般的擁抱。",
        oil: "澳洲檀香（單方）", chem: "倍半萜醇：極致溫潤與滋養，撫慰長期照顧他人的辛勞身心。" },
      { id: 77, name: "錢幣國王", en: "King of Pentacles", arcana: "小阿爾克那・錢幣", formula: "精準單方", element: "土元素", icon: "🌱", quadrant: "神經型－土",
        reading: "扛起了家庭或事業的穩重支柱，習慣把所有重量往自己肩上放。在這裡你不需要當任何人的靠山，讓按摩床成為你的靠山。",
        oil: "岩蘭草（單方）", chem: "倍半萜烯：「寧靜之油」，深層卸除頂天立地的重壓，帶來深沉好眠。" }
    ];

    let shuffledDeck = [...TAROT_DB];

    // 畫面切換
    function switchScreen(screenId) {
      document.querySelectorAll(".screen").forEach(el => el.classList.remove("active"));
      document.getElementById(screenId).classList.add("active");
      window.scrollTo({ top: 0, behavior: "smooth" });
    }

    function goToWelcomeScreen() {
      switchScreen("screen-welcome");
    }

    function goToDrawScreen() {
      shuffleArray(shuffledDeck);
      renderCardRail();
      switchScreen("screen-draw");
      const wrapper = document.getElementById("rail-wrapper");
      setTimeout(() => {
        wrapper.scrollTo({ left: (wrapper.scrollWidth - wrapper.clientWidth) / 2, behavior: "smooth" });
      }, 100);
    }

    // Fisher-Yates 洗牌演算法
    function shuffleArray(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
    }

    // 渲染 78 張牌背
    function renderCardRail() {
      const rail = document.getElementById("cards-rail");
      rail.innerHTML = "";
      shuffledDeck.forEach((card, index) => {
        const el = document.createElement("div");
        el.className = "tarot-back";
        el.title = `第 ${index + 1} 張牌`;
        el.innerHTML = `<div class="tarot-back-motif">✦</div>`;
        el.onclick = () => revealCard(card);
        rail.appendChild(el);
      });
    }

    // 洗牌視覺動畫
    function shuffleDeckAnimation() {
      shuffleArray(shuffledDeck);
      renderCardRail();
      const cards = document.querySelectorAll(".tarot-back");
      cards.forEach((c, idx) => {
        setTimeout(() => c.classList.add("shuffling"), (idx % 12) * 25);
      });
    }

    // 隨機感應抽牌
    function drawRandomCard() {
      const randomCard = shuffledDeck[Math.floor(Math.random() * shuffledDeck.length)];
      revealCard(randomCard);
    }

    // 揭曉結果
    function revealCard(card) {
      document.getElementById("res-arcana-tag").textContent = card.arcana;
      document.getElementById("res-icon").textContent = card.icon;
      document.getElementById("res-element").textContent = card.element;
      document.getElementById("res-name").textContent = card.name;
      document.getElementById("res-sub").textContent = card.en;

      document.getElementById("res-type-badge").textContent = `${card.arcana}・${card.formula}`;
      document.getElementById("res-quadrant-badge").textContent = `法系體質：${card.quadrant}`;
      document.getElementById("res-reading").textContent = card.reading;
      document.getElementById("res-oil").textContent = card.oil;
      document.getElementById("res-chem").textContent = card.chem;

      // 設定同象限微調提示
      const swapText = QUADRANT_SWAPS[card.quadrant] || QUADRANT_SWAPS["全象限深度調和"];
      document.getElementById("swap-details").textContent = swapText;
      document.getElementById("swap-details").classList.remove("open");
      document.getElementById("swap-arrow").textContent = "▼";

      // 重新觸發翻牌動畫
      const cardBox = document.getElementById("revealed-card-box");
      cardBox.style.animation = "none";
      cardBox.offsetHeight;
      cardBox.style.animation = null;

      switchScreen("screen-result");
    }

    function toggleSwapDetails() {
      const details = document.getElementById("swap-details");
      const arrow = document.getElementById("swap-arrow");
      const isOpen = details.classList.toggle("open");
      arrow.textContent = isOpen ? "▲" : "▼";
    }

    // 芳療師速查彈窗邏輯
    function openReferenceModal() {
      renderDbTable();
      document.getElementById("ref-modal").classList.add("open");
    }

    function closeReferenceModal() {
      document.getElementById("ref-modal").classList.remove("open");
    }

    function closeModalOnBackdrop(e) {
      if (e.target.id === "ref-modal") closeReferenceModal();
    }

    function switchModalTab(tab) {
      document.getElementById("tab-quad").classList.toggle("active", tab === "quad");
      document.getElementById("tab-list").classList.toggle("active", tab === "list");
      document.getElementById("modal-body-quad").style.display = tab === "quad" ? "block" : "none";
      document.getElementById("modal-body-list").style.display = tab === "list" ? "block" : "none";
    }

    function renderDbTable() {
      const keyword = (document.getElementById("db-search").value || "").trim().toLowerCase();
      const tbody = document.getElementById("db-table-body");
      tbody.innerHTML = "";

      TAROT_DB.filter(c =>
        c.name.toLowerCase().includes(keyword) ||
        c.oil.toLowerCase().includes(keyword) ||
        c.reading.toLowerCase().includes(keyword) ||
        c.quadrant.toLowerCase().includes(keyword)
      ).forEach(card => {
        const tr = document.createElement("tr");
        tr.innerHTML = `
          <td><strong>${card.name}</strong></td>
          <td>${card.formula}</td>
          <td>${card.oil}</td>
          <td><button class="db-row-btn" onclick="selectFromModal(${card.id})">預覽處方</button></td>
        `;
        tbody.appendChild(tr);
      });
    }

    function selectFromModal(id) {
      const card = TAROT_DB.find(c => c.id === id);
      if (card) {
        closeReferenceModal();
        revealCard(card);
      }
    }
  </script>
</body>
</html>
