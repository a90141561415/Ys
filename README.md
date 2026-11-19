<html lang="zh-TW">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="default" />
  <meta name="apple-mobile-web-app-title" content="森呼吸芳療塔羅" />
  <title>森呼吸芳療塔羅｜BOTANICAL TAROT & AROMATHERAPY</title>

  <!-- LINE / Facebook / 社群傳網址自動顯示預覽圖卡設定 -->
  <meta property="og:type" content="website" />
  <meta property="og:title" content="森呼吸芳療塔羅｜專屬身心與精油處方籤" />
  <meta property="og:description" content="靜心深呼吸，憑直覺抽取今日的命定塔羅牌，為您調配專屬的法系芳療與植萃精油配方。" />
  <!-- 請在 GitHub 倉庫上傳一張名為 cover.jpg 的封面圖，並將下方網址改為你的實際網址 -->
  <meta property="og:image" content="https://a90141561415.github.io/Ys/cover.jpg" />
  <meta property="og:url" content="https://a90141561415.github.io/Ys/" />

  <style>
    :root {
      --bg-cream: #F6F4EE;
      --bg-surface: #FFFFFF;
      --sage-deep: #2B4236;
      --sage-mid: #466656;
      --sage-soft: #E5ECE7;
      --sage-border: #D2DDD6;
      --gold-warm: #B8986A;
      --gold-pale: #F3ECE0;
      --text-primary: #27302B;
      --text-secondary: #636F68;
      --text-muted: #8E9A93;
      --shadow-elevated: 0 14px 36px rgba(43, 66, 54, 0.08);
      --shadow-card: 0 10px 24px rgba(43, 66, 54, 0.14);
    }

    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    html, body {
      width: 100% !important;
      max-width: 100vw !important;
      min-height: 100%;
      overflow-x: hidden !important;
      scroll-behavior: smooth;
      -webkit-text-size-adjust: 100%;
      font-family: -apple-system, BlinkMacSystemFont, "PingFang TC", "Noto Sans TC", "Microsoft JhengHei", sans-serif;
      background-color: var(--bg-cream);
      color: var(--text-primary);
    }

    .app-shell {
      width: 100%;
      max-width: 100%;
      min-height: 100vh;
      overflow-x: hidden;
      display: flex;
      flex-direction: column;
      background-color: var(--bg-cream);
      background-image:
        radial-gradient(circle at 10% 15%, rgba(70, 102, 86, 0.06) 0%, transparent 45%),
        radial-gradient(circle at 90% 85%, rgba(184, 152, 106, 0.08) 0%, transparent 45%);
    }

    button {
      min-height: 40px;
      touch-action: manipulation;
      font-family: inherit;
    }

    header {
      width: 100%;
      max-width: 1140px;
      margin: 0 auto;
      padding: 14px 16px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
      z-index: 10;
    }

    .brand-group {
      display: flex;
      align-items: center;
      gap: 10px;
      min-width: 0;
      flex: 1;
      cursor: pointer;
    }

    .brand-emblem {
      width: 38px;
      height: 38px;
      border-radius: 50%;
      background: var(--sage-soft);
      border: 1px solid var(--sage-border);
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--sage-deep);
      flex-shrink: 0;
    }

    .brand-titles {
      display: flex;
      flex-direction: column;
      min-width: 0;
    }

    .brand-titles .zh-title {
      font-size: 1rem;
      font-weight: 600;
      color: var(--sage-deep);
      letter-spacing: 0.06em;
      line-height: 1.25;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    .brand-titles .en-subtitle {
      font-size: 0.6rem;
      color: var(--text-secondary);
      letter-spacing: 0.1em;
      text-transform: uppercase;
      margin-top: 2px;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    .btn-ref {
      background: rgba(255, 255, 255, 0.9);
      border: 1px solid var(--sage-border);
      color: var(--sage-deep);
      padding: 7px 13px;
      border-radius: 22px;
      font-size: 0.8rem;
      font-weight: 500;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 5px;
      flex-shrink: 0;
      white-space: nowrap;
      transition: all 0.2s ease;
    }

    main {
      flex: 1;
      width: 100%;
      max-width: 1140px;
      min-width: 0;
      margin: 0 auto;
      padding: 8px 14px 32px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }

    .view-section {
      display: none;
      width: 100%;
      max-width: 100%;
      min-width: 0;
      animation: gentleFade 0.45s ease forwards;
    }

    .view-section.active {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    @keyframes gentleFade {
      from { opacity: 0; transform: translateY(8px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* === 畫面 1：靜心迎賓 === */
    .welcome-card {
      text-align: center;
      width: 100%;
      max-width: 520px;
      padding: 20px 10px;
    }

    .breath-orb-container {
      position: relative;
      width: 136px;
      height: 136px;
      margin: 0 auto 26px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .breath-aura {
      position: absolute;
      inset: 0;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(70, 102, 86, 0.18) 0%, rgba(70, 102, 86, 0.02) 70%);
      animation: calmBreath 6s ease-in-out infinite;
    }

    .breath-aura-inner {
      position: absolute;
      inset: 14px;
      border-radius: 50%;
      border: 1px solid rgba(70, 102, 86, 0.28);
      animation: calmBreath 6s ease-in-out infinite 0.5s;
    }

    .breath-center {
      width: 76px;
      height: 76px;
      border-radius: 50%;
      background: var(--sage-deep);
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.88rem;
      letter-spacing: 0.12em;
      box-shadow: 0 8px 24px rgba(43, 66, 54, 0.24);
      z-index: 2;
    }

    @keyframes calmBreath {
      0%, 100% { transform: scale(0.92); opacity: 0.72; }
      50% { transform: scale(1.12); opacity: 1; }
    }

    .eyebrow-tag {
      font-size: 0.72rem;
      font-weight: 600;
      letter-spacing: 0.16em;
      color: var(--gold-warm);
      text-transform: uppercase;
      margin-bottom: 8px;
    }

    .welcome-heading {
      font-size: clamp(1.45rem, 5.5vw, 1.85rem);
      font-weight: 600;
      color: var(--sage-deep);
      line-height: 1.4;
      margin-bottom: 14px;
      letter-spacing: 0.04em;
    }

    .welcome-copy {
      font-size: 0.94rem;
      color: var(--text-secondary);
      line-height: 1.8;
      margin-bottom: 30px;
    }

    .btn-sage-solid {
      background: var(--sage-deep);
      color: #fff;
      border: none;
      padding: 14px 34px;
      border-radius: 30px;
      font-size: 0.98rem;
      font-weight: 500;
      letter-spacing: 0.08em;
      cursor: pointer;
      box-shadow: 0 10px 24px rgba(43, 66, 54, 0.2);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      transition: all 0.25s ease;
    }

    .btn-sage-solid:active {
      transform: scale(0.98);
    }

    /* === 畫面 2：78 張橫向滑動牌陣 === */
    .deck-header {
      text-align: center;
      width: 100%;
      max-width: 560px;
      padding: 0 8px;
      margin-bottom: 14px;
    }

    .deck-header h2 {
      font-size: clamp(1.18rem, 4.5vw, 1.42rem);
      font-weight: 600;
      color: var(--sage-deep);
      line-height: 1.45;
      margin-bottom: 6px;
    }

    .deck-header p {
      font-size: 0.84rem;
      color: var(--text-secondary);
      line-height: 1.55;
    }

    .deck-toolbar {
      width: 100%;
      max-width: 560px;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 10px;
      margin-bottom: 12px;
      padding: 0 4px;
    }

    .pill-hint {
      background: var(--gold-pale);
      color: #7D6138;
      padding: 7px 14px;
      border-radius: 22px;
      font-size: 0.8rem;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      text-align: center;
    }

    .deck-carousel-wrap {
      width: 100%;
      max-width: 100%;
      min-width: 0;
      overflow: hidden;
      position: relative;
      margin: 4px 0 12px;
    }

    .deck-scroller {
      width: 100%;
      max-width: 100%;
      overflow-x: auto;
      overflow-y: hidden;
      padding: 16px 16px 24px;
      display: flex;
      flex-wrap: nowrap;
      gap: 12px;
      scroll-snap-type: x proximity;
      overscroll-behavior-x: contain;
      -webkit-overflow-scrolling: touch;
      scrollbar-width: thin;
      scrollbar-color: var(--sage-border) transparent;
    }

    .deck-scroller::-webkit-scrollbar {
      height: 5px;
    }

    .deck-scroller::-webkit-scrollbar-thumb {
      background: rgba(70, 102, 86, 0.25);
      border-radius: 3px;
    }

    .tarot-card-back {
      width: 114px;
      height: 184px;
      border-radius: 13px;
      background: linear-gradient(155deg, #354E41 0%, #24372D 100%);
      border: 2px solid #C5A87A;
      box-shadow: 0 6px 16px rgba(36, 55, 45, 0.16);
      flex: 0 0 auto;
      scroll-snap-align: center;
      cursor: pointer;
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      padding: 14px 8px;
      user-select: none;
      transition: transform 0.25s cubic-bezier(0.22, 1, 0.36, 1), box-shadow 0.25s ease;
    }

    .tarot-card-back::before {
      content: "";
      position: absolute;
      inset: 6px;
      border: 1px solid rgba(197, 168, 122, 0.42);
      border-radius: 8px;
      pointer-events: none;
    }

    .back-num {
      font-size: 0.7rem;
      color: #D7BE92;
      letter-spacing: 0.12em;
    }

    .back-eye-emblem {
      width: 46px;
      height: 46px;
      border-radius: 50%;
      border: 1px solid rgba(215, 190, 146, 0.55);
      display: flex;
      align-items: center;
      justify-content: center;
      color: #D7BE92;
    }

    .back-brand-text {
      font-size: 0.72rem;
      color: rgba(215, 190, 146, 0.85);
      letter-spacing: 0.18em;
    }

    .tarot-card-back.is-shuffling {
      animation: cardShufflePulse 0.45s ease-in-out;
    }

    @keyframes cardShufflePulse {
      0% { transform: translateY(0) scale(1); }
      50% { transform: translateY(-10px) scale(0.97); }
      100% { transform: translateY(0) scale(1); }
    }

    .deck-nav-controls {
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 14px;
      margin-top: 4px;
    }

    .nav-circle-btn {
      width: 38px;
      height: 38px;
      min-height: 38px;
      border-radius: 50%;
      background: #fff;
      border: 1px solid var(--sage-border);
      color: var(--sage-deep);
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      font-size: 1rem;
      flex-shrink: 0;
    }

    .nav-label {
      font-size: 0.82rem;
      color: var(--text-secondary);
      letter-spacing: 0.05em;
    }

    /* === 畫面 3：今日身心療癒與芳療處方籤 === */
    .rx-sheet {
      width: 100%;
      max-width: 900px;
      background: var(--bg-surface);
      border-radius: 20px;
      overflow: hidden;
      box-shadow: var(--shadow-elevated);
      border: 1px solid var(--sage-border);
    }

    .rx-banner {
      background: linear-gradient(135deg, #324B3E 0%, #446353 100%);
      color: #fff;
      padding: 16px 20px;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
    }

    .rx-banner-title {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 0.96rem;
      font-weight: 500;
      letter-spacing: 0.05em;
    }

    .rx-banner-dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: #D7BE92;
      flex-shrink: 0;
    }

    .rx-banner-pill {
      background: rgba(255, 255, 255, 0.14);
      border: 1px solid rgba(255, 255, 255, 0.24);
      padding: 5px 12px;
      border-radius: 18px;
      font-size: 0.76rem;
      color: #F3ECE0;
      letter-spacing: 0.05em;
    }

    .rx-grid {
      display: grid;
      grid-template-columns: 260px minmax(0, 1fr);
      gap: 24px;
      padding: 24px;
    }

    .card-stage {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .tarot-face-card {
      width: 224px;
      height: 344px;
      border-radius: 16px;
      background: linear-gradient(170deg, #FCFBF8 0%, #F1EDE4 100%);
      border: 1.5px solid #D4C2A3;
      box-shadow: var(--shadow-card);
      padding: 20px 14px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      text-align: center;
      position: relative;
      animation: revealFlip 0.6s cubic-bezier(0.22, 1, 0.36, 1) forwards;
    }

    @keyframes revealFlip {
      0% { opacity: 0; transform: rotateY(75deg) scale(0.94); }
      100% { opacity: 1; transform: rotateY(0deg) scale(1); }
    }

    .tarot-face-card::before {
      content: "";
      position: absolute;
      inset: 8px;
      border: 1px solid rgba(184, 152, 106, 0.42);
      border-radius: 11px;
      pointer-events: none;
    }

    .face-top-meta {
      margin-top: 2px;
    }

    .face-en {
      font-size: 0.7rem;
      letter-spacing: 0.14em;
      color: var(--gold-warm);
      text-transform: uppercase;
      font-weight: 600;
      margin-bottom: 4px;
    }

    .face-zh {
      font-size: 1.45rem;
      font-weight: 600;
      color: var(--sage-deep);
      letter-spacing: 0.06em;
    }

    .face-symbol-ring {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      background: rgba(229, 236, 231, 0.65);
      border: 1px solid rgba(184, 152, 106, 0.55);
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--sage-deep);
    }

    .face-bottom-tag {
      font-size: 0.78rem;
      color: var(--sage-mid);
      letter-spacing: 0.05em;
      margin-bottom: 2px;
    }

    .model-footnote {
      font-size: 0.74rem;
      color: var(--text-muted);
      text-align: center;
      line-height: 1.5;
      margin-top: 12px;
      max-width: 240px;
    }

    .rx-details-col {
      min-width: 0;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .rx-block-label {
      font-size: 0.86rem;
      font-weight: 600;
      color: var(--sage-deep);
      letter-spacing: 0.05em;
      margin-bottom: 8px;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .rx-state-box {
      background: #F9F8F4;
      border-left: 3px solid var(--sage-mid);
      border-radius: 12px;
      padding: 14px 16px;
      font-size: 0.95rem;
      line-height: 1.75;
      color: var(--text-primary);
      margin-bottom: 18px;
      overflow-wrap: anywhere;
    }

    .quadrant-pill {
      display: inline-block;
      background: var(--sage-deep);
      color: #fff;
      font-size: 0.76rem;
      padding: 5px 13px;
      border-radius: 18px;
      letter-spacing: 0.05em;
      margin-bottom: 10px;
    }

    .oil-prescription-box {
      border: 1px solid var(--sage-border);
      background: #FAF9F6;
      border-radius: 14px;
      padding: 16px 18px;
      margin-bottom: 12px;
      overflow-wrap: anywhere;
    }

    .oil-title-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 8px;
      margin-bottom: 8px;
    }

    .oil-title-row h4 {
      font-size: 1.25rem;
      font-weight: 600;
      color: var(--sage-deep);
    }

    .formula-chip {
      background: var(--gold-pale);
      color: #826438;
      font-size: 0.74rem;
      font-weight: 600;
      padding: 4px 10px;
      border-radius: 14px;
    }

    .oil-chem-desc {
      font-size: 0.9rem;
      color: var(--text-secondary);
      line-height: 1.65;
    }

    /* 基底油與滴數調配卡片 */
    .carrier-oil-box {
      border: 1px solid #DFD3BE;
      background: #FBF8F3;
      border-radius: 14px;
      padding: 14px 16px;
      margin-bottom: 14px;
      overflow-wrap: anywhere;
    }

    .carrier-header {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 6px;
      margin-bottom: 6px;
    }

    .carrier-title {
      font-size: 0.92rem;
      font-weight: 600;
      color: #6B5028;
    }

    .carrier-ratio-tag {
      background: #EFE4D2;
      color: #6B5028;
      font-size: 0.74rem;
      font-weight: 600;
      padding: 3px 10px;
      border-radius: 12px;
    }

    .carrier-desc {
      font-size: 0.85rem;
      color: var(--text-secondary);
      line-height: 1.6;
    }

    /* 現場試聞氣味微調手風琴 */
    .swap-accordion {
      border: 1px solid var(--sage-border);
      background: #F6F4EE;
      border-radius: 12px;
      margin-bottom: 20px;
      overflow: hidden;
    }

    .swap-accordion-btn {
      width: 100%;
      background: none;
      border: none;
      padding: 12px 14px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 8px;
      font-size: 0.84rem;
      font-weight: 600;
      color: var(--sage-deep);
      cursor: pointer;
      text-align: left;
    }

    .swap-accordion-panel {
      display: none;
      padding: 12px 14px 14px;
      background: #fff;
      border-top: 1px solid var(--sage-border);
    }

    .swap-accordion-panel.open {
      display: block;
    }

    .swap-intro {
      font-size: 0.82rem;
      color: var(--text-secondary);
      line-height: 1.6;
      margin-bottom: 10px;
    }

    .swap-chip-list {
      display: flex;
      flex-direction: column;
      gap: 7px;
    }

    .swap-oil-chip {
      background: #F4F6F4;
      border: 1px solid var(--sage-border);
      border-radius: 9px;
      padding: 8px 12px;
      font-size: 0.83rem;
      color: var(--text-primary);
      font-weight: 500;
    }

    .rx-footer-actions {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }

    .btn-outline-sage {
      background: #fff;
      border: 1px solid var(--sage-border);
      color: var(--sage-deep);
      padding: 12px 22px;
      border-radius: 28px;
      font-size: 0.92rem;
      font-weight: 500;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }

    footer {
      width: 100%;
      max-width: 1140px;
      margin: 0 auto;
      padding: 12px 16px 22px;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 6px 16px;
      font-size: 0.74rem;
      color: var(--text-muted);
      text-align: center;
    }

    /* 芳療師速查彈窗 */
    .modal-overlay {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(26, 36, 31, 0.55);
      backdrop-filter: blur(4px);
      z-index: 100;
      align-items: center;
      justify-content: center;
      padding: 12px;
    }

    .modal-overlay.open {
      display: flex;
    }

    .modal-card {
      background: #fff;
      width: min(100%, 880px);
      max-height: 88vh;
      border-radius: 18px;
      display: flex;
      flex-direction: column;
      overflow: hidden;
      box-shadow: 0 22px 50px rgba(0, 0, 0, 0.25);
    }

    .modal-top {
      background: var(--sage-deep);
      color: #fff;
      padding: 14px 18px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
    }

    .modal-top h3 {
      font-size: 0.95rem;
      font-weight: 500;
      letter-spacing: 0.04em;
    }

    .modal-x {
      background: none;
      border: none;
      color: #fff;
      font-size: 1.5rem;
      cursor: pointer;
      padding: 0 6px;
    }

    .modal-nav-tabs {
      display: flex;
      background: var(--bg-cream);
      border-bottom: 1px solid var(--sage-border);
    }

    .m-tab {
      flex: 1;
      padding: 11px 6px;
      background: none;
      border: none;
      font-size: 0.84rem;
      font-weight: 600;
      color: var(--text-secondary);
      cursor: pointer;
    }

    .m-tab.active {
      background: #fff;
      color: var(--sage-deep);
      border-bottom: 2px solid var(--sage-deep);
    }

    .modal-scroll-area {
      padding: 16px;
      overflow-y: auto;
      overflow-x: auto;
      -webkit-overflow-scrolling: touch;
      flex: 1;
    }

    .quad-cards-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 12px;
    }

    .quad-item {
      background: #FAF9F6;
      border: 1px solid var(--sage-border);
      border-radius: 12px;
      padding: 14px;
    }

    .quad-item h4 {
      color: var(--sage-deep);
      font-size: 0.94rem;
      margin-bottom: 5px;
    }

    .quad-item .chem-tag {
      font-size: 0.76rem;
      color: var(--gold-warm);
      font-weight: 600;
      margin-bottom: 6px;
    }

    .quad-item p {
      font-size: 0.83rem;
      color: var(--text-secondary);
      line-height: 1.55;
    }

    .filter-input {
      width: 100%;
      padding: 10px 12px;
      border: 1px solid var(--sage-border);
      border-radius: 10px;
      margin-bottom: 12px;
      font-size: 16px;
    }

    .ref-table {
      width: 100%;
      min-width: 520px;
      border-collapse: collapse;
      font-size: 0.83rem;
    }

    .ref-table th, .ref-table td {
      padding: 9px 7px;
      text-align: left;
      border-bottom: 1px solid var(--sage-border);
    }

    .ref-table th {
      background: var(--bg-cream);
      color: var(--sage-deep);
      position: sticky;
      top: 0;
    }

    .btn-preview-sm {
      background: var(--sage-soft);
      color: var(--sage-deep);
      border: none;
      padding: 6px 11px;
      border-radius: 12px;
      font-size: 0.76rem;
      font-weight: 500;
      cursor: pointer;
    }

    @media screen and (min-width: 768px) {
      .tarot-card-back {
        width: 132px;
        height: 214px;
      }
    }

    @media screen and (max-width: 767px) {
      .rx-grid {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 20px;
        padding: 18px 14px;
      }
      .tarot-face-card {
        width: 208px;
        height: 320px;
      }
      .rx-footer-actions {
        flex-direction: column;
      }
      .rx-footer-actions button {
        width: 100%;
      }
      .quad-cards-grid {
        grid-template-columns: 1fr;
      }
    }

    @media screen and (max-width: 420px) {
      .brand-titles .en-subtitle {
        display: none;
      }
      .btn-sage-solid {
        width: 100%;
      }
      .deck-toolbar {
        flex-direction: column;
      }
      .deck-toolbar button, .pill-hint {
        width: 100%;
      }
    }

    @media (hover: hover) and (pointer: fine) {
      .btn-ref:hover {
        background: #fff;
        border-color: var(--sage-mid);
      }
      .btn-sage-solid:hover {
        background: var(--sage-mid);
        transform: translateY(-2px);
      }
      .tarot-card-back:hover {
        transform: translateY(-12px) scale(1.03);
        box-shadow: 0 14px 28px rgba(36, 55, 45, 0.26);
      }
      .btn-outline-sage:hover {
        background: var(--sage-soft);
      }
    }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
        scroll-behavior: auto !important;
      }
    }
  </style>
</head>
<body>
  <div class="app-shell">
    <!-- 頂部品牌導覽（點擊品牌標誌亦可回到迎賓首頁） -->
    <header>
      <div class="brand-group" onclick="resetForNextGuest()" title="回到迎賓首頁">
        <div class="brand-emblem" aria-hidden="true">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
            <path d="M11 20A7 7 0 0 1 9.8 6.1C15.5 5 17 4.48 19 2c1 2 2 4.18 2 8 0 5.5-4.78 10-10 10Z"/>
            <path d="M2 21c0-3 1.85-5.36 5.08-6C9.5 14.52 12 13 13 12"/>
          </svg>
        </div>
        <div class="brand-titles">
          <span class="zh-title">森呼吸芳療塔羅</span>
          <span class="en-subtitle">BOTANICAL TAROT &amp; AROMATHERAPY</span>
        </div>
      </div>
      <button class="btn-ref" onclick="openRefModal()">
        <span>📋 芳療師速查表</span>
      </button>
    </header>

    <main>
      <!-- 畫面 1：靜心迎賓 -->
      <section id="view-welcome" class="view-section active">
        <div class="welcome-card">
          <div class="breath-orb-container">
            <div class="breath-aura"></div>
            <div class="breath-aura-inner"></div>
            <div class="breath-center">深呼吸</div>
          </div>
          <div class="eyebrow-tag">Aromatherapy × Tarot Ritual</div>
          <h1 class="welcome-heading">傾聽身體的聲音<br>尋找今日的命定香氣</h1>
          <p class="welcome-copy">
            請先喝一口溫熱的迎賓茶，輕輕閉上眼睛深呼吸三次。<br>
            在心中默想：<strong>「我現在的身心，最需要什麼樣的照顧？」</strong><br>
            準備好後，憑直覺為自己抽取一張專屬處方牌。
          </p>
          <button class="btn-sage-solid" onclick="showDrawView()">開始直覺選牌</button>
        </div>
      </section>

      <!-- 畫面 2：78 張橫向滑動牌陣 -->
      <section id="view-draw" class="view-section">
        <div class="deck-header">
          <div class="eyebrow-tag">78 TAROT CARDS</div>
          <h2>左右滑動牌陣，憑直覺點選一張吸引你的牌</h2>
          <p>共 78 張完整牌庫已為您展開，點擊任一張牌背即可翻開今日處方</p>
        </div>

        <div class="deck-toolbar">
          <button class="btn-ref" onclick="triggerShuffle()">🔀 重新洗牌</button>
          <div class="pill-hint">提示：可左右滑動瀏覽整副牌</div>
        </div>

        <div class="deck-carousel-wrap">
          <div class="deck-scroller" id="deck-scroller"></div>
        </div>

        <div class="deck-nav-controls">
          <button class="nav-circle-btn" onclick="scrollDeckBy(-250)" aria-label="向左滑動">‹</button>
          <span class="nav-label">滑動挑選您的命定牌卡</span>
          <button class="nav-circle-btn" onclick="scrollDeckBy(250)" aria-label="向右滑動">›</button>
        </div>
      </section>

      <!-- 畫面 3：今日身心療癒與芳療處方籤 -->
      <section id="view-result" class="view-section">
        <div class="rx-sheet">
          <div class="rx-banner">
            <div class="rx-banner-title">
              <span class="rx-banner-dot"></span>
              <span>今日身心療癒與芳療處方籤</span>
            </div>
            <div class="rx-banner-pill" id="rx-header-pill">小阿爾克那｜精準調理單方</div>
          </div>

          <div class="rx-grid">
            <!-- 左側抽出的塔羅牌視覺 -->
            <div class="card-stage">
              <div class="tarot-face-card" id="tarot-face-card">
                <div class="face-top-meta">
                  <div class="face-en" id="face-en">ACE OF CUPS</div>
                  <div class="face-zh" id="face-zh">聖杯 Ace</div>
                </div>
                <div class="face-symbol-ring" id="face-symbol"></div>
                <div class="face-bottom-tag" id="face-element-tag">水元素・心輪溫柔敞開</div>
              </div>
              <div class="model-footnote">
                此處方依據法系芳療《L'Aromathérapie Exactement》四象限與 Florihana 植物油模型匹配
              </div>
            </div>

            <!-- 右側芳療解讀與配方 -->
            <div class="rx-details-col">
              <div>
                <div class="rx-block-label">✦ 當下身心狀態解讀</div>
                <div class="rx-state-box" id="rx-reading-text"></div>

                <div class="rx-block-label">💧 今日命定精油與基底油配方</div>
                <div class="quadrant-pill" id="rx-quadrant-pill">淋巴型・水象限</div>

                <div class="oil-prescription-box">
                  <div class="oil-title-row">
                    <h4 id="rx-oil-name">無光敏佛手柑</h4>
                    <span class="formula-chip" id="rx-formula-chip">單方精油調理</span>
                  </div>
                  <div class="oil-chem-desc" id="rx-chem-desc"></div>
                </div>

                <!-- 基底油與滴數調配卡片 -->
                <div class="carrier-oil-box">
                  <div class="carrier-header">
                    <span class="carrier-title" id="rx-carrier-name">🧴 建議基底油：甜杏仁油 20ml（或荷荷芭油 1:1）</span>
                    <span class="carrier-ratio-tag" id="rx-carrier-drops">全身 2%｜共 8 滴</span>
                  </div>
                  <div class="carrier-desc" id="rx-carrier-guide"></div>
                </div>

                <!-- 現場試聞氣味微調手風琴 -->
                <div class="swap-accordion">
                  <button class="swap-accordion-btn" onclick="toggleSwapPanel()">
                    <span>＋ 現場試聞氣味微調（同象限替換建議）</span>
                    <span id="swap-chevron">⌄</span>
                  </button>
                  <div class="swap-accordion-panel" id="swap-panel">
                    <p class="swap-intro">
                      若現場試聞後想微調香氣，可隨時請芳療師為您更換以下<strong>同象限・同等療癒頻率</strong>的 Florihana 單方精油：
                    </p>
                    <div class="swap-chip-list" id="swap-chip-list"></div>
                  </div>
                </div>
              </div>

              <!-- 修正：下一位客人直接跳轉回靜心迎賓首頁 -->
              <div class="rx-footer-actions">
                <button class="btn-sage-solid" onclick="resetForNextGuest()">↻ 下一位客人（回到靜心迎賓）</button>
                <button class="btn-outline-sage" onclick="showDrawView()">返回牌陣重選</button>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer>
      <span>森呼吸芳療按摩工作室專屬系統</span>
      <span>78 張完整塔羅 × 芳療家 Florihana 植物油與精油對照</span>
    </footer>
  </div>

  <!-- 芳療師速查表彈窗 -->
  <div class="modal-overlay" id="ref-modal" onclick="handleModalBackdrop(event)">
    <div class="modal-card">
      <div class="modal-top">
        <h3>🌿 芳療師速查表（Florihana 四象限精油 × 基底油調配）</h3>
        <button class="modal-x" onclick="closeRefModal()">&times;</button>
      </div>
      <div class="modal-nav-tabs">
        <button class="m-tab active" id="m-tab-quad" onclick="switchModalView('quad')">四象限精油與基底油指南</button>
        <button class="m-tab" id="m-tab-db" onclick="switchModalView('db')">78 張完整牌庫一覽</button>
      </div>
      <div class="modal-scroll-area" id="m-view-quad">
        <div class="quad-cards-grid">
          <div class="quad-item">
            <h4>1. 神經型・土象限（陰／涼／負電｜親油性）</h4>
            <div class="chem-tag">官能基：酯類、倍半萜烯｜對應：錢幣牌組</div>
            <p><strong>Florihana 單方：</strong>高地真正薰衣草、快樂鼠尾草、羅馬洋甘菊、大西洋雪松、岩蘭草。<br>
               <strong>基底油搭檔：</strong>甜杏仁油 20ml（深層鬆肌推拿）；肩頸僵硬可加入 20% 聖約翰草浸泡油。</p>
          </div>
          <div class="quad-item">
            <h4>2. 淋巴型・水象限（陰／涼／負電｜親水性）</h4>
            <div class="chem-tag">官能基：醛類、酮類、內酯/香豆素｜對應：聖杯牌組</div>
            <p><strong>Florihana 單方：</strong>無光敏佛手柑 (FCF)、山雞椒、高地真正薰衣草、玫瑰天竺葵。<br>
               <strong>基底油搭檔：</strong>荷荷芭油 20ml（或與甜杏仁油 1:1 混合），清爽好吸收不黏膩。</p>
          </div>
          <div class="quad-item">
            <h4>3. 多血型・風象限（陽／熱／正電｜親水性）</h4>
            <div class="chem-tag">官能基：單萜醇、倍半萜醇｜對應：寶劍牌組</div>
            <p><strong>Florihana 單方：</strong>芳樟、玫瑰天竺葵、甜馬鬱蘭、澳洲檀香。<br>
               <strong>基底油搭檔：</strong>甜杏仁油 20ml（或搭配聖約翰草浸泡油安撫緊繃神經）。</p>
          </div>
          <div class="quad-item">
            <h4>4. 膽汁型・乾火象限（陽／熱／正電｜親油性）</h4>
            <div class="chem-tag">官能基：單萜烯、氧化物、醚類｜對應：權杖牌組</div>
            <p><strong>Florihana 單方：</strong>甜橙、黑雲杉、澳洲尤加利（搭配甜馬鬱蘭疏通肌肉）。<br>
               <strong>基底油搭檔：</strong>甜杏仁油 20ml（順滑推開氣血瘀滯，適合深層經絡油壓）。</p>
          </div>
        </div>
      </div>
      <div class="modal-scroll-area" id="m-view-db" style="display:none;">
        <input type="text" class="filter-input" id="ref-search" placeholder="搜尋牌名、精油或基底油（例如：佛手柑、聖約翰草、高塔）..." oninput="renderRefTable()" />
        <table class="ref-table">
          <thead>
            <tr>
              <th>牌名</th>
              <th>處方類型</th>
              <th>推薦精油</th>
              <th>建議基底油</th>
              <th>操作</th>
            </tr>
          </thead>
          <tbody id="ref-table-body"></tbody>
        </table>
      </div>
    </div>
  </div>

  <script>
    const SYMBOLS_SVG = {
      major: `<svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M6.34 17.66l-1.41 1.41M19.07 4.93l-1.41 1.41"/></svg>`,
      wands: `<svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2c.5 3.5-2 5.5-2 8.5a4 4 0 0 0 8 0c0-2.5-1.5-4.5-3-6.5-.5 2-1.5 3-3 3Z"/><path d="M12 14v8M9 18h6"/></svg>`,
      cups: `<svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><path d="M12 3c-1.5 2-3 3.5-3 5a3 3 0 0 0 6 0c0-1.5-1.5-3-3-5Z" stroke="#B8986A"/><path d="M7 11h10l-1 4a4 4 0 0 1-8 0l-1-4Z"/><path d="M12 19v3M8 22h8"/></svg>`,
      swords: `<svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><path d="M17.7 7.7a2.5 2.5 0 1 1 1.8 4.3H2"/><path d="M9.6 4.6A2 2 0 1 1 11 8H2"/><path d="M12.6 19.4A2 2 0 1 0 14 16H2"/></svg>`,
      pentacles: `<svg width="44" height="44" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"><path d="M11 20A7 7 0 0 1 9.8 6.1C15.5 5 17 4.48 19 2c1 2 2 4.18 2 8 0 5.5-4.78 10-10 10Z"/><path d="M2 21c0-3 1.85-5.36 5.08-6C9.5 14.52 12 13 13 12"/></svg>`
    };

    const CARRIER_PRESETS = {
      almond: {
        name: "甜杏仁油 20ml（主力滑順推拿）",
        dropsMajor: "全身 2%｜共 8 滴（主調 5 滴 ＋ 輔助 3 滴）",
        dropsMinor: "全身 2%｜共 8 滴（局部加強可至 3% / 12 滴）",
        guide: "延展性極佳、滑順好推且親膚溫和，最適合全身油壓舒展緊繃肌理；若客人背部易長痘或怕油感，可改用「荷荷芭油」或兩者 1:1 調和。"
      },
      jojoba: {
        name: "荷荷芭油 20ml（清爽親膚平衡）",
        dropsMajor: "全身 2%｜共 8 滴（主調 5 滴 ＋ 輔助 3 滴）",
        dropsMinor: "全身 2%｜共 8 滴（臉部/頭皮建議 1% / 4 滴）",
        guide: "分子與人體皮脂最接近，清爽不油膩、不致痘且極度穩定，特別適合情緒水腫調理、夏季或偏好輕盈膚觸的客人。"
      },
      stjohns: {
        name: "聖約翰草浸泡油 4ml ＋ 甜杏仁油 16ml",
        dropsMajor: "全身 2%｜共 8 滴（主調 5 滴 ＋ 輔助 3 滴）",
        dropsMinor: "全身 2%｜共 8 滴（肩頸/腰背深層痠痛 12 滴）",
        guide: "紅寶石色澤的聖約翰草浸泡油是芳療界著名的「肌肉與神經修復油」，以 20% 比例調入甜杏仁油，專攻肩頸僵硬與神經緊繃（註：具光敏性，適合避光部位按摩）。"
      }
    };

    const QUADRANT_SWAPS = {
      "神經型・土象限": [
        "大西洋雪松（倍半萜烯｜深層鬆肌與循環）",
        "岩蘭草（倍半萜烯｜極致接地與深層安神）",
        "高地真正薰衣草（酯類｜全方位神經撫慰）",
        "快樂鼠尾草（高比例酯類｜解除肌肉與情緒痙攣）",
        "羅馬洋甘菊（酯類｜溫柔安撫敏感受傷神經）"
      ],
      "淋巴型・水象限": [
        "無光敏佛手柑 FCF（酯類＋香豆素｜陽光安撫無反黑疑慮）",
        "山雞椒（醛類｜情緒降溫與疏通）",
        "高地真正薰衣草（酯類｜深度舒緩）",
        "玫瑰天竺葵（單萜醇｜平衡心輪）"
      ],
      "多血型・風象限": [
        "芳樟（單萜醇｜溫和定心與補氣）",
        "玫瑰天竺葵（單萜醇｜協調身心與荷爾蒙平衡）",
        "甜馬鬱蘭（單萜醇｜溫熱鬆弛緊繃肌理）",
        "澳洲檀香（倍半萜醇｜沉靜安神與滋養）"
      ],
      "膽汁型・乾火象限": [
        "甜橙（單萜烯｜陽光提振與活絡循環）",
        "黑雲杉（單萜烯｜森林正電與腎上腺支持）",
        "澳洲尤加利（氧化物｜打開胸廓深呼吸）",
        "甜馬鬱蘭（單萜醇｜疏通肩頸氣血瘀滯）"
      ],
      "全象限深度調和": [
        "保留主調精油，另一支可依現場嗅覺喜好微調為：高地真正薰衣草（安撫）",
        "保留主調精油，另一支可依現場嗅覺喜好微調為：無光敏佛手柑 FCF（開朗）",
        "保留主調精油，另一支可依現場嗅覺喜好微調為：甜橙（溫暖）",
        "保留主調精油，另一支可依現場嗅覺喜好微調為：大西洋雪松（沉穩）"
      ]
    };

    const TAROT_DECK = [
      // === 22 張大阿爾克那（複方） ===
      { id: 0, name: "0. 愚人", en: "THE FOOL", isMajor: true, symbol: "major", elementTag: "風元素・輕盈新生", quadrant: "膽汁型・乾火象限", carrier: "jojoba",
        reading: "你的靈魂正渴望一場輕盈的呼吸。近期可能背負了太多「應該」，身體需要卸下重擔，找回純粹的自由與彈性。",
        oil: "甜橙 ＋ 澳洲尤加利",
        chem: "單萜烯 ＋ 氧化物（膽汁型・乾火象限）：如清晨森林的微風，清空沉重思緒，打開胸腔呼吸空間，帶來輕盈愉悅感。" },
      { id: 1, name: "I. 魔術師", en: "THE MAGICIAN", isMajor: true, symbol: "major", elementTag: "風元素・思緒顯化", quadrant: "淋巴型・水象限", carrier: "jojoba",
        reading: "你的腦袋正高速運轉、充滿想法，但也容易因此感到肩頸與太陽穴緊繃。今天適合把飄在空中的能量，溫柔地帶回身體裡。",
        oil: "山雞椒 ＋ 芳樟",
        chem: "醛類 ＋ 單萜醇（淋巴型・水象限）：幫過熱的大腦降溫，同時溫和補氣，讓思緒清晰而不焦躁。" },
      { id: 2, name: "II. 女祭司", en: "THE HIGH PRIESTESS", isMajor: true, symbol: "major", elementTag: "水元素・內在靜謐", quadrant: "神經型・土象限", carrier: "jojoba",
        reading: "你最近接收了太多外界的聲音，內心需要一片安靜的湖水。這是一張邀請你向內傾聽、好好與自己獨處的牌。",
        oil: "澳洲檀香 ＋ 高地真正薰衣草",
        chem: "倍半萜醇 ＋ 酯類（神經型・土象限）：深層安撫神經系統，帶領意識回到平靜的內在中心。" },
      { id: 3, name: "III. 皇后", en: "THE EMPRESS", isMajor: true, symbol: "major", elementTag: "土元素・豐盛滋養", quadrant: "多血型・風象限", carrier: "almond",
        reading: "你一直在照顧身邊的人，現在輪到你被好好滋養了。身體渴望溫暖的包覆與寵愛，讓緊繃的肌膚與心靈都軟化下來。",
        oil: "玫瑰天竺葵 ＋ 甜橙",
        chem: "單萜醇 ＋ 單萜烯（多血型・風象限）：平衡情緒與能量流動，帶來如同被溫暖擁抱的豐盛療癒感。" },
      { id: 4, name: "IV. 皇帝", en: "THE EMPEROR", isMajor: true, symbol: "major", elementTag: "火元素・卸下盔甲", quadrant: "膽汁型・乾火象限", carrier: "stjohns",
        reading: "你扛起了許多責任，習慣凡事撐住，連肌肉都在不知不覺中武裝起來。今天請允許自己卸下盔甲，把重量交給按摩床。",
        oil: "黑雲杉 ＋ 大西洋雪松",
        chem: "單萜烯 ＋ 倍半萜烯（膽汁型・乾火象限）：給疲憊的腎上腺「類可體松」支持，同時深層鬆開僵硬背肌。" },
      { id: 5, name: "V. 教皇", en: "THE HIEROPHANT", isMajor: true, symbol: "major", elementTag: "土元素・安定呼吸", quadrant: "多血型・風象限", carrier: "almond",
        reading: "內心有些自我要求或規則讓你感到喘不過氣。身體需要一種穩定、被支持的安全感，幫助你釋放胸口的悶脹。",
        oil: "澳洲檀香 ＋ 無光敏佛手柑 (FCF)",
        chem: "倍半萜醇 ＋ 酯類與香豆素（多血型・風象限）：加深呼吸深度，化解內在的拘謹與無形壓力。" },
      { id: 6, name: "VI. 戀人", en: "THE LOVERS", isMajor: true, symbol: "major", elementTag: "風元素・心輪和諧", quadrant: "多血型・風象限", carrier: "almond",
        reading: "你正在尋找身與心的和諧共鳴。也許最近在關係或選擇上有些微的拉扯，需要讓心輪重新打開、恢復柔軟的流動。",
        oil: "玫瑰天竺葵 ＋ 快樂鼠尾草",
        chem: "單萜醇 ＋ 酯類（多血型・風象限）：協調自律神經與情感波動，讓身心回到溫柔的平衡點。" },
      { id: 7, name: "VII. 戰車", en: "THE CHARIOT", isMajor: true, symbol: "major", elementTag: "水元素・動能調節", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "你像一輛高速行駛的車，衝勁十足卻忘了進站保養。雙腿與下背可能累積了不少緊繃，需要幫身體踩個溫柔的煞車。",
        oil: "甜馬鬱蘭 ＋ 岩蘭草",
        chem: "單萜醇 ＋ 倍半萜烯（神經型・土象限）：極佳的肌肉鬆弛與接地組合，讓浮躁的動能平穩沉澱下來。" },
      { id: 8, name: "VIII. 力量", en: "STRENGTH", isMajor: true, symbol: "major", elementTag: "火元素・溫柔接納", quadrant: "淋巴型・水象限", carrier: "almond",
        reading: "外表看起來很堅強的你，內在其實有點累了。真正的力量來自於溫柔地接納自己的疲憊，今天讓雙手替你揉開深層的結。",
        oil: "無光敏佛手柑 (FCF) ＋ 高地真正薰衣草",
        chem: "酯類 ＋ 香豆素（淋巴型・水象限）：安撫緊繃的神經末梢，用陽光般的香氣融化內在的硬撐。" },
      { id: 9, name: "IX. 隱士", en: "THE HERMIT", isMajor: true, symbol: "major", elementTag: "土元素・深度靜心", quadrant: "神經型・土象限", carrier: "almond",
        reading: "你需要暫時關掉外界的喧囂，給自己一段不被打擾的修復時光。這是一張適合深度靜心、釋放深層疲勞的牌。",
        oil: "大西洋雪松 ＋ 澳洲檀香",
        chem: "倍半萜烯 ＋ 倍半萜醇（神經型・土象限）：深沉木質調，把向外耗散的能量全部收攝回體內修復。" },
      { id: 10, name: "X. 命運之輪", en: "WHEEL OF FORTUNE", isMajor: true, symbol: "major", elementTag: "火元素・節奏對齊", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "生活正處於一個節奏轉換的路口，身體可能因為適應變化而感到微微失衡。順應流動，讓今天的按摩幫你重新對齊節奏。",
        oil: "甜橙 ＋ 甜馬鬱蘭",
        chem: "單萜烯 ＋ 單萜醇（膽汁型・乾火象限）：暢通氣血循環，協助身體順暢地度過季節或生活轉折。" },
      { id: 11, name: "XI. 正義", en: "JUSTICE", isMajor: true, symbol: "major", elementTag: "風元素・思緒歸零", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "你花了很多心力在衡量、思考與維持平衡，大腦與肩頸處於過度緊繃的狀態。現在不需要再分析對錯，只需要單純地放鬆。",
        oil: "快樂鼠尾草 ＋ 無光敏佛手柑 (FCF)",
        chem: "高比例酯類 ＋ 香豆素（神經型・土象限）：強力抗痙攣與平衡神經，幫過度理性的大腦按下暫停鍵。" },
      { id: 12, name: "XII. 倒吊人", en: "THE HANGED MAN", isMajor: true, symbol: "major", elementTag: "水元素・蓄力流動", quadrant: "膽汁型・乾火象限", carrier: "jojoba",
        reading: "感覺有些事情卡住了，或是身體正處於「動彈不得」的沉重期。換個視角休息一下吧，這段停滯期其實是身體在為你蓄力。",
        oil: "澳洲尤加利 ＋ 大西洋雪松",
        chem: "氧化物 ＋ 倍半萜烯（膽汁型・乾火象限）：打開受限的呼吸空間，促進淋巴與末梢循環流動。" },
      { id: 13, name: "XIII. 死神", en: "DEATH", isMajor: true, symbol: "major", elementTag: "水元素・代謝重啟", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "舊的疲憊與情緒毒素正準備離開你的身體，這是一個「徹底代謝與重啟」的時刻。放心地把累積的痠痛都代謝掉吧。",
        oil: "黑雲杉 ＋ 大西洋雪松",
        chem: "單萜烯 ＋ 倍半萜烯（膽汁型・乾火象限）：清理停滯的能量與乳酸堆積，迎接身心煥然一新。" },
      { id: 14, name: "XIV. 節制", en: "TEMPERANCE", isMajor: true, symbol: "major", elementTag: "火元素・溫潤調和", quadrant: "多血型・風象限", carrier: "jojoba",
        reading: "你的身體正在努力尋找自我修復的平衡點。這是一張非常溫和的療癒牌，適合用如流水般順暢的手法，調和體內的水分與氣場。",
        oil: "芳樟 ＋ 高地真正薰衣草",
        chem: "單萜醇 ＋ 酯類（多血型・風象限）：最溫和親膚的黃金比例，如春雨般滋潤疲憊的身心。" },
      { id: 15, name: "XV. 惡魔", en: "THE DEVIL", isMajor: true, symbol: "major", elementTag: "土元素・深層鬆綁", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "身體被長期的壓力、熬夜或執念緊緊束縛住了，肩頸與腰背可能有明顯的氣結。今天讓我們一起把這些沉重的枷鎖鬆綁。",
        oil: "岩蘭草 ＋ 山雞椒",
        chem: "倍半萜烯 ＋ 醛類（神經型・土象限）：岩蘭草深層接地排濁，山雞椒打破沉悶鬱結，釋放深層壓力。" },
      { id: 16, name: "XVI. 高塔", en: "THE TOWER", isMajor: true, symbol: "major", elementTag: "火元素・張力釋放", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "累積已久的壓力似乎到了臨界點，身體正在發出「需要徹底釋放」的訊號。別擔心，打破緊繃之後，迎來的是前所未有的輕鬆。",
        oil: "羅馬洋甘菊 ＋ 甜橙",
        chem: "酯類 ＋ 單萜烯（神經型・土象限）：洋甘菊擁有極強的安撫與釋放張力效果，溫柔接住突如其來的疲憊。" },
      { id: 17, name: "XVII. 星星", en: "THE STAR", isMajor: true, symbol: "major", elementTag: "風元素・清澈微光", quadrant: "淋巴型・水象限", carrier: "jojoba",
        reading: "經過一段時間的忙碌，你終於迎來了療癒與希望的微光。今天的按摩將像星光灑落一樣，為你注入純淨、清澈的新能量。",
        oil: "無光敏佛手柑 (FCF) ＋ 芳樟",
        chem: "酯類 ＋ 單萜醇（淋巴型・水象限）：清澈透亮的香氣，撫平過去的勞累，帶來平靜與希望感。" },
      { id: 18, name: "XVIII. 月亮", en: "THE MOON", isMajor: true, symbol: "major", elementTag: "水元素・潛意識安撫", quadrant: "神經型・土象限", carrier: "almond",
        reading: "潛意識裡可能藏著一些說不出口的不安或敏感，連帶影響了睡眠品質與腸胃。在這個安全的空間裡，你可以完全放下戒備。",
        oil: "羅馬洋甘菊 ＋ 快樂鼠尾草",
        chem: "高比例酯類（神經型・土象限）：深度安撫敏感的神經系統與腹部緊繃，幫助夜晚深層好眠。" },
      { id: 19, name: "XIX. 太陽", en: "THE SUN", isMajor: true, symbol: "major", elementTag: "火元素・生命力回升", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "你的生命力正在回升，或正準備迎接充滿活力的新階段！今天的精油將為你點燃內在的小太陽，讓全身氣血暢通、充滿暖意。",
        oil: "甜橙 ＋ 黑雲杉",
        chem: "高比例單萜烯（膽汁型・乾火象限）：充滿陽光與森林正電能量的組合，提振精神、消除倦怠。" },
      { id: 20, name: "XX. 審判", en: "JUDGEMENT", isMajor: true, symbol: "major", elementTag: "火元素・自癒力喚醒", quadrant: "膽汁型・乾火象限", carrier: "jojoba",
        reading: "身體正在喚醒沉睡已久的自癒力。這是一個身心重新開機、找回輕盈感的重要時刻，深呼吸，迎接全新的自己。",
        oil: "澳洲尤加利 ＋ 玫瑰天竺葵",
        chem: "氧化物 ＋ 單萜醇（膽汁型・乾火象限）：清新的呼吸感搭配花香的滋養，喚醒身體每一個細胞的活力。" },
      { id: 21, name: "XXI. 世界", en: "THE WORLD", isMajor: true, symbol: "major", elementTag: "土元素・身心圓滿", quadrant: "全象限深度調和", carrier: "almond",
        reading: "恭喜你完成了一段不簡單的旅程，現在是犒賞自己、享受完整與圓滿的時刻。讓這場全身的香氣之旅，為你畫下最完美的句點。",
        oil: "澳洲檀香 ＋ 無光敏佛手柑 (FCF) ＋ 甜橙",
        chem: "倍半萜醇 ＋ 酯類 ＋ 單萜烯（全象限調和）：兼具穩定、安撫與愉悅的完美交響，帶來全方位的身心圓滿。" },

      // === 權杖牌組 14 張（單方） ===
      { id: 22, name: "權杖 Ace", en: "ACE OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・活力點燃", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "內心正燃起一股新的熱情與動力，身體也準備好迎接新開始。需要一點陽光的能量，幫你點燃活力。",
        oil: "甜橙", chem: "單萜烯（膽汁型・乾火象限）：帶來溫暖愉悅的陽光能量，活絡全身氣血循環。" },
      { id: 23, name: "權杖 2", en: "TWO OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・脊柱支撐", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "站在規劃與展望的十字路口，眼神看著遠方，肩膀卻不自覺微微聳起。先深呼吸，把力量收回到當下。",
        oil: "黑雲杉", chem: "單萜烯（膽汁型・乾火象限）：像高聳的針葉林般給予脊柱支撐力，穩定心神。" },
      { id: 24, name: "權杖 3", en: "THREE OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・溫熱舒展", quadrant: "多血型・風象限", carrier: "almond",
        reading: "事情正在推進中，你付出了許多心力等待成果。雙腿與下背有些微的奔波感，適合好好舒展筋骨。",
        oil: "甜馬鬱蘭", chem: "單萜醇（多血型・風象限）：溫熱舒緩奔波後的肌肉緊繃，讓身體重新暖起來。" },
      { id: 25, name: "權杖 4", en: "FOUR OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・喜悅安定", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "階段性的忙碌告一段落，現在是享受安定與喜悅的時刻。讓甜美的香氣陪你一起慶祝這份輕鬆。",
        oil: "甜橙", chem: "單萜烯（膽汁型・乾火象限）：放大身心的愉悅與放鬆感，享受無憂無慮的片刻。" },
      { id: 26, name: "權杖 5", en: "FIVE OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・疏通鬱熱", quadrant: "膽汁型・乾火象限", carrier: "jojoba",
        reading: "外界似乎有些雜音或小競爭讓你感到微躁，體內有一股悶熱的火氣。需要清涼的微風幫你理順氣場。",
        oil: "澳洲尤加利", chem: "氧化物（膽汁型・乾火象限）：疏通胸口鬱悶的熱氣，讓呼吸重新變得寬敞順暢。" },
      { id: 27, name: "權杖 6", en: "SIX OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・能量降落", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "你剛剛打了一場漂亮的勝仗，精神亢奮但肌肉其實已經很累了。現在可以安心把光環卸下，交給雙手照顧。",
        oil: "黑雲杉", chem: "單萜烯（膽汁型・乾火象限）：補充腎上腺能量，幫助亢奮的神經系統平穩降落。" },
      { id: 28, name: "權杖 7", en: "SEVEN OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・卸下防禦", quadrant: "多血型・風象限", carrier: "stjohns",
        reading: "感覺最近一直在防禦、應付各種突發狀況，上背部與肩胛骨特別僵硬。在這裡很安全，不用再武裝自己了。",
        oil: "甜馬鬱蘭", chem: "單萜醇（多血型・風象限）：軟化長期處於防禦狀態的僵硬背肌，帶來安全感。" },
      { id: 29, name: "權杖 8", en: "EIGHT OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・節奏降溫", quadrant: "淋巴型・水象限", carrier: "jojoba",
        reading: "生活節奏快得像一陣風，訊息與任務接踵而來，連呼吸都變得急促。讓香氣幫你把快轉鍵按回正常速度。",
        oil: "山雞椒", chem: "醛類（淋巴型・水象限）：快速幫高速運轉的躁動感降溫，理清混亂節奏。" },
      { id: 30, name: "權杖 9", en: "NINE OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・中場充電", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "雖然已經很疲憊了，但責任感讓你還在咬牙撐著最後一哩路。這是一張提醒你「該中場休息充電」的溫柔訊號。",
        oil: "黑雲杉", chem: "單萜烯（膽汁型・乾火象限）：深層滋養透支的體力，為疲憊的身體注入森林元氣。" },
      { id: 31, name: "權杖 10", en: "TEN OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・卸下重擔", quadrant: "多血型・風象限", carrier: "stjohns",
        reading: "身上背負了太多不屬於你的責任，肩膀沉重得快喘不過氣。今天把所有的重擔都放在門外，單純享受被照顧。",
        oil: "甜馬鬱蘭", chem: "單萜醇（多血型・風象限）：深度鬆開如石頭般堅硬的肩頸斜方肌，卸下重擔。" },
      { id: 32, name: "權杖侍者", en: "PAGE OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・純真好奇", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "對生活充滿好奇與躍躍欲試的能量，但偶爾會有點三分鐘熱度或小急躁。保持這份純真，同時讓身體穩下來。",
        oil: "甜橙", chem: "單萜烯（膽汁型・乾火象限）：滋養純粹的快樂與創造力，讓氣血順暢流動。" },
      { id: 33, name: "權杖騎士", en: "KNIGHT OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・平衡衝勁", quadrant: "膽汁型・乾火象限", carrier: "jojoba",
        reading: "一股腦往前衝的行動派，能量集中在頭部與上半身，容易感到燥熱或緊繃。讓清新的草本幫你平衡衝勁。",
        oil: "澳洲尤加利", chem: "氧化物（膽汁型・乾火象限）：引導過旺的火氣向下流動，帶來清爽的呼吸空間。" },
      { id: 34, name: "權杖皇后", en: "QUEEN OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・女王寵愛", quadrant: "多血型・風象限", carrier: "almond",
        reading: "充滿魅力與熱情的照顧者，總是用溫暖照亮別人，卻忘了留一點光給自己。今天換你享受女王般的寵愛。",
        oil: "玫瑰天竺葵", chem: "單萜醇（多血型・風象限）：平衡內在的付出與接收，溫柔滋養女性與心輪能量。" },
      { id: 35, name: "權杖國王", en: "KING OF WANDS", isMajor: false, symbol: "wands", elementTag: "火元素・王者減壓", quadrant: "膽汁型・乾火象限", carrier: "almond",
        reading: "擁有強大的領導力與決斷力，但長期處於高壓決策狀態，容易讓神經與血管緊繃。讓深沉的森林香氣為你減壓。",
        oil: "黑雲杉", chem: "單萜烯（膽汁型・乾火象限）：給予王者般的沉穩支持，深層釋放累積的操勞。" },

      // === 聖杯牌組 14 張（單方） ===
      { id: 36, name: "聖杯 Ace", en: "ACE OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・心輪溫柔敞開", quadrant: "淋巴型・水象限", carrier: "jojoba",
        reading: "心輪正在溫柔地敞開，適合接納愛、善意與純粹的放鬆。讓如清泉般的香氣流過全身，滋潤乾涸的身心。",
        oil: "無光敏佛手柑 (FCF)", chem: "酯類 ＋ 香豆素（淋巴型・水象限）：如陽光灑落湖面，帶來充滿希望的溫柔安撫。" },
      { id: 37, name: "聖杯 2", en: "TWO OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・身心共鳴", quadrant: "多血型・風象限", carrier: "almond",
        reading: "渴望身與心、自我與他人之間的和諧共鳴。今天的按摩將是一場你與自己身體最溫柔的深度對話。",
        oil: "玫瑰天竺葵", chem: "單萜醇（多血型・風象限）：協調身心的平衡頻率，帶來被理解與被呵護的感受。" },
      { id: 38, name: "聖杯 3", en: "THREE OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・輕盈愉悅", quadrant: "淋巴型・水象限", carrier: "jojoba",
        reading: "內心渴望輕鬆愉快的交流與陪伴，適合釋放平日的拘謹，讓心情像微醺般輕盈放鬆。",
        oil: "無光敏佛手柑 (FCF)", chem: "酯類 ＋ 香豆素（淋巴型・水象限）：掃去內心的陰霾與拘謹，喚起純粹的喜悅感。" },
      { id: 39, name: "聖杯 4", en: "FOUR OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・喚醒感官", quadrant: "淋巴型・水象限", carrier: "jojoba",
        reading: "對日常感到有些提不起勁、情緒微微悶著，身體也容易覺得懶洋洋或水腫。需要一點清新的香氣喚醒感官。",
        oil: "山雞椒", chem: "醛類（淋巴型・水象限）：像一顆檸檬糖般打破沉悶的情緒死水，提振低落氣場。" },
      { id: 40, name: "聖杯 5", en: "FIVE OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・情緒釋懷", quadrant: "神經型・土象限", carrier: "almond",
        reading: "心中還留著一點對過去的遺憾或失落，胸口感覺有些微酸澀緊縮。沒關係，允許情緒隨著呼吸慢慢流走。",
        oil: "高地真正薰衣草", chem: "酯類（神經型・土象限）：如母親般溫柔包容的香氣，撫平內心的委屈與皺褶。" },
      { id: 41, name: "聖杯 6", en: "SIX OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・內在小孩", quadrant: "神經型・土象限", carrier: "almond",
        reading: "內在小孩正在呼喚你，渴望回到單純、無憂無慮、被無條件呵護的狀態。安心閉上眼睛，享受這份純粹的照顧。",
        oil: "羅馬洋甘菊", chem: "酯類（神經型・土象限）：最溫柔的安撫力量，給內在小孩一個溫暖安全的擁抱。" },
      { id: 42, name: "聖杯 7", en: "SEVEN OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・收攏思緒", quadrant: "多血型・風象限", carrier: "jojoba",
        reading: "腦海中有太多想像、願望或未決定的事，讓能量有點飄浮不定。需要把分散的思緒收攏，重新回到身體裡。",
        oil: "芳樟", chem: "單萜醇（多血型・風象限）：溫和定心，幫飄在雲端的思緒找到安穩的落腳處。" },
      { id: 43, name: "聖杯 8", en: "EIGHT OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・情緒斷捨離", quadrant: "神經型・土象限", carrier: "almond",
        reading: "準備好揮別消耗你的人事物，踏上尋找內在平靜的旅程。這是一個斷捨離的時刻，讓身體把舊的情緒代謝掉。",
        oil: "高地真正薰衣草", chem: "酯類（神經型・土象限）：清理殘留的情緒疲勞，平靜地迎接下一個階段。" },
      { id: 44, name: "聖杯 9", en: "NINE OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・感官饗宴", quadrant: "多血型・風象限", carrier: "almond",
        reading: "內心感到滿足與富足，身體也處於相當不錯的狀態。今天是一場純粹的感官饗宴，盡情享受這份寵愛吧！",
        oil: "玫瑰天竺葵", chem: "單萜醇（多血型・風象限）：放大內在的豐盛感與幸福感，讓肌膚與心情都發光。" },
      { id: 45, name: "聖杯 10", en: "TEN OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・圓滿歸屬", quadrant: "淋巴型・水象限", carrier: "almond",
        reading: "渴望全方位的安穩、幸福與歸屬感。讓溫暖花香與柑橘調的氣息包圍你，感受身心靈合一的圓滿平靜。",
        oil: "無光敏佛手柑 (FCF)", chem: "酯類 ＋ 香豆素（淋巴型・水象限）：溫暖、陽光、包容，帶來如家一般的安心感。" },
      { id: 46, name: "聖杯侍者", en: "PAGE OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・溫柔防護", quadrant: "多血型・風象限", carrier: "jojoba",
        reading: "內心細膩敏感，容易察覺環境中細微的情緒變化。保護好這份珍貴的感受力，同時用香氣為自己建立溫柔防護罩。",
        oil: "芳樟", chem: "單萜醇（多血型・風象限）：增強身心防護力，溫柔守護敏感細膩的靈魂。" },
      { id: 47, name: "聖杯騎士", en: "KNIGHT OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・滋養自己", quadrant: "多血型・風象限", carrier: "almond",
        reading: "浪漫、重感情，總是把別人的感受放在前面，容易因此感到心累。今天不需要討好任何人，只需要討好你自己。",
        oil: "玫瑰天竺葵", chem: "單萜醇（多血型・風象限）：把向外流淌的愛收回來滋養自己，平衡情感耗損。" },
      { id: 48, name: "聖杯皇后", en: "QUEEN OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・排解濕氣", quadrant: "淋巴型・水象限", carrier: "jojoba",
        reading: "擁有極強的同理心與包容力，但可能默默吸收了太多周遭的負能量。讓流動的按摩手法幫你排出身體的情緒濕氣。",
        oil: "山雞椒", chem: "醛類（淋巴型・水象限）：疏通情緒與淋巴的滯留感，還原清澈輕盈的自己。" },
      { id: 49, name: "聖杯國王", en: "KING OF CUPS", isMajor: false, symbol: "cups", elementTag: "水元素・卸下防備", quadrant: "神經型・土象限", carrier: "almond",
        reading: "習慣在人前保持情緒穩定、成熟冷靜，把所有壓力都往心裡吞。在這個私密的空間裡，你可以安心卸下所有防備。",
        oil: "高地真正薰衣草", chem: "酯類（神經型・土象限）：深層鬆開壓抑已久的神經與胸口緊繃，釋放無聲的壓力。" },

      // === 寶劍牌組 14 張（單方） ===
      { id: 50, name: "寶劍 Ace", en: "ACE OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・清澈靈感", quadrant: "膽汁型・乾火象限", carrier: "jojoba",
        reading: "腦袋裡有許多新想法正在醞釀，思緒銳利但容易讓頭部與眉心緊繃。需要清涼的空氣感，讓靈感順暢流動。",
        oil: "澳洲尤加利", chem: "氧化物（膽汁型・乾火象限）：提升大腦含氧量，帶來清澈透亮的呼吸與思緒。" },
      { id: 51, name: "寶劍 2", en: "TWO OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・鬆開糾結", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "心裡似乎有兩個聲音在拉扯，讓你處於一種微微僵持、不敢放鬆的狀態。暫時把選擇題放一邊，先讓身體休息。",
        oil: "快樂鼠尾草", chem: "酯類（神經型・土象限）：解除內在的糾結與神經痙攣，讓緊繃的身體軟化下來。" },
      { id: 52, name: "寶劍 3", en: "THREE OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・心輪暖流", quadrant: "神經型・土象限", carrier: "almond",
        reading: "心中藏著一點隱隱的刺痛或委屈，可能連帶讓胸口與上背感到緊縮。讓溫柔的香氣像暖流一樣，慢慢融化這份不適。",
        oil: "羅馬洋甘菊", chem: "酯類（神經型・土象限）：極致的安撫與鎮靜，溫柔撫平心輪的酸澀與緊繃。" },
      { id: 53, name: "寶劍 4", en: "FOUR OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・深度休眠", quadrant: "神經型・土象限", carrier: "almond",
        reading: "這是一張最直接的「深度休眠牌」！你的大腦與神經已經過載，身體強烈渴望一場不受打擾的徹底關機與修復。",
        oil: "高地真正薰衣草", chem: "酯類（神經型・土象限）：引導腦波進入深層放鬆狀態，最適合在按摩中好好睡一覺。" },
      { id: 54, name: "寶劍 5", en: "FIVE OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・淨化雜音", quadrant: "多血型・風象限", carrier: "jojoba",
        reading: "最近可能經歷了一些溝通上的摩擦或無力感，讓你覺得心煩意亂。深吸一口氣，把外界的是非都留在門外。",
        oil: "芳樟", chem: "單萜醇（多血型・風象限）：溫和淨化煩躁氣場，讓心緒重新回到平靜與從容。" },
      { id: 55, name: "寶劍 6", en: "SIX OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・平靜過渡", quadrant: "多血型・風象限", carrier: "jojoba",
        reading: "正在離開一段混亂或高壓的時期，朝著平靜的水域前進。身體還在慢慢適應放鬆的節奏，需要溫和的陪伴與支持。",
        oil: "芳樟", chem: "單萜醇（多血型・風象限）：如平靜的微風推著小船前行，安撫過渡期的疲憊。" },
      { id: 56, name: "寶劍 7", en: "SEVEN OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・解除警覺", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "習慣用頭腦去應對各種複雜狀況，精神總是處於高度警覺。今天不需要再動腦想策略了，讓身體單純地感受觸碰。",
        oil: "快樂鼠尾草", chem: "酯類（神經型・土象限）：讓過度警覺的交感神經休息，啟動副交感神經的修復模式。" },
      { id: 57, name: "寶劍 8", en: "EIGHT OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・自由呼吸", quadrant: "膽汁型・乾火象限", carrier: "stjohns",
        reading: "感覺被自己的擔憂或完美主義困住了，肩頸像被無形的繩索綁緊。其實你隨時可以鬆開手，呼吸自由的空氣。",
        oil: "澳洲尤加利", chem: "氧化物（膽汁型・乾火象限）：打破窒息般的緊繃感，打開胸廓，找回自由呼吸的空間。" },
      { id: 58, name: "寶劍 9", en: "NINE OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・一夜好眠", quadrant: "神經型・土象限", carrier: "almond",
        reading: "深夜裡容易想太多、擔心還沒發生的事，導致睡眠品質受影響。今晚讓這支充滿安撫力的精油，陪你一夜好眠。",
        oil: "羅馬洋甘菊", chem: "酯類（神經型・土象限）：專攻焦慮型失眠與神經緊繃，帶來深沉安穩的睡眠品質。" },
      { id: 59, name: "寶劍 10", en: "TEN OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・觸底充電", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "體力與腦力都到達了一個徹底耗盡的谷底——好消息是，從這一刻起，一切都將觸底反彈、重新開始充電！",
        oil: "高地真正薰衣草", chem: "酯類（神經型・土象限）：在能量最低點給予最溫柔的修復，陪伴身心重新蓄力。" },
      { id: 60, name: "寶劍侍者", en: "PAGE OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・過濾雜訊", quadrant: "膽汁型・乾火象限", carrier: "jojoba",
        reading: "觀察力敏銳、資訊接收量大，但也容易因此感到精神緊繃、眼睛疲勞。讓清新的香氣幫你過濾掉多餘的雜訊。",
        oil: "澳洲尤加利", chem: "氧化物（膽汁型・乾火象限）：消除用眼與用腦過度的疲勞感，讓頭腦恢復清爽。" },
      { id: 61, name: "寶劍騎士", en: "KNIGHT OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・思緒煞車", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "說話與做事都講求效率，精神總是處於衝刺狀態，容易忽略身體發出的痠痛警訊。今天幫自己安排一場慢下來的儀式。",
        oil: "快樂鼠尾草", chem: "酯類（神經型・土象限）：幫高速運轉的思緒踩煞車，鬆開緊繃的頸部與頭皮。" },
      { id: 62, name: "寶劍皇后", en: "QUEEN OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・安心依靠", quadrant: "神經型・土象限", carrier: "almond",
        reading: "獨立、理性、習慣自己扛起一切，很少在別人面前示弱。今天請允許自己當一個單純被照顧的小孩，安心依靠。",
        oil: "羅馬洋甘菊", chem: "酯類（神經型・土象限）：融化理性堅強的外殼，溫柔安撫內在深處的疲憊。" },
      { id: 63, name: "寶劍國王", en: "KING OF SWORDS", isMajor: false, symbol: "swords", elementTag: "風元素・清空記憶體", quadrant: "多血型・風象限", carrier: "jojoba",
        reading: "每天需要做出許多專業判斷，大腦長期處於高壓運作。讓純淨的木質花香幫你清空記憶體，找回內在的寧靜。",
        oil: "芳樟", chem: "單萜醇（多血型・風象限）：兼顧清晰與放鬆，讓高壓的決策者獲得深層精神休息。" },

      // === 錢幣牌組 14 張（單方） ===
      { id: 64, name: "錢幣 Ace", en: "ACE OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・大地滋養", quadrant: "神經型・土象限", carrier: "almond",
        reading: "身體正準備好吸收滿滿的滋養與能量！這是一張非常適合做深層肌肉保養的牌，讓大地精華為你打好健康基礎。",
        oil: "大西洋雪松", chem: "倍半萜烯（神經型・土象限）：紮實穩定的大地能量，深層滋養疲憊的肌肉與筋膜。" },
      { id: 65, name: "錢幣 2", en: "TWO OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・找回重心", quadrant: "多血型・風象限", carrier: "almond",
        reading: "最近在工作與生活之間忙得團團轉，努力維持著平衡，雙腳與腰背也跟著忙碌不停。需要幫身體重新找回穩定的重心。",
        oil: "甜馬鬱蘭", chem: "單萜醇（多血型・風象限）：調和忙碌帶來的循環失衡，舒緩久站或久坐的腰腿痠痛。" },
      { id: 66, name: "錢幣 3", en: "THREE OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・精準鬆綁", quadrant: "神經型・土象限", carrier: "stjohns",
        reading: "專注在自己的專業與工作上，長時間維持同一個姿勢（如看電腦、低頭），容易造成局部肌肉僵硬。讓雙手幫你精準鬆綁。",
        oil: "大西洋雪松", chem: "倍半萜烯（神經型・土象限）：促進局部淋巴與循環流動，化解長時間固定姿勢的僵硬。" },
      { id: 67, name: "錢幣 4", en: "FOUR OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・深度接地", quadrant: "神經型・土象限", carrier: "almond",
        reading: "習慣把責任與壓力緊緊抓在手裡，身體也跟著變得緊繃、缺乏彈性。試著隨著吐氣慢慢鬆開拳頭，你會發現一切都很安全。",
        oil: "岩蘭草", chem: "倍半萜烯（神經型・土象限）：極致的「接地（Grounding）」力量，幫助緊繃的身心徹底放下戒備。" },
      { id: 68, name: "錢幣 5", en: "FIVE OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・厚實包覆", quadrant: "神經型・土象限", carrier: "almond",
        reading: "感覺身體有些虛寒、疲憊，或是最近耗費了太多體力卻沒時間好好吃飯休息。現在你需要最溫暖、厚實的能量包覆。",
        oil: "岩蘭草", chem: "倍半萜烯（神經型・土象限）：如厚實的大地毯子般溫暖身體，深層補充耗損的元氣。" },
      { id: 69, name: "錢幣 6", en: "SIX OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・愛的回饋", quadrant: "多血型・風象限", carrier: "almond",
        reading: "你在生活中付出了許多時間與精力，現在輪到宇宙透過這場按摩，把同等份量的滋養與愛回饋給你了。",
        oil: "澳洲檀香", chem: "倍半萜醇（多血型・風象限）：溫潤醇厚的木質香氣，帶來被珍視、被滋養的幸福感。" },
      { id: 70, name: "錢幣 7", en: "SEVEN OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・休養生息", quadrant: "神經型・土象限", carrier: "almond",
        reading: "辛苦耕耘了一段時間，身體正處於「需要耐心等待恢復」的緩衝期。別急著趕路，今天就在這裡好好休養生息。",
        oil: "大西洋雪松", chem: "倍半萜烯（神經型・土象限）：穩定耐心的木質能量，陪伴身體慢慢代謝累積的疲勞。" },
      { id: 71, name: "錢幣 8", en: "EIGHT OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・舒緩勞損", quadrant: "多血型・風象限", carrier: "stjohns",
        reading: "非常認真、一絲不苟地完成手邊每件事，但也因此讓手臂、肩膀與背部累積了不少職業疲勞。今天讓專業的雙手為你代勞。",
        oil: "甜馬鬱蘭", chem: "單萜醇（多血型・風象限）：專攻勞損型肌肉痠痛，溫熱活絡辛勤工作的四肢與背肌。" },
      { id: 72, name: "錢幣 9", en: "NINE OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・質感犒賞", quadrant: "多血型・風象限", carrier: "jojoba",
        reading: "獨立自主、懂得照顧自己，今天這場按摩正是你送給自己的質感犒賞！盡情享受這段純粹屬於你的優雅時光。",
        oil: "澳洲檀香", chem: "倍半萜醇（多血型・風象限）：高雅沉靜的香氣，襯托你懂得愛自己的質感與從容。" },
      { id: 73, name: "錢幣 10", en: "TEN OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・安穩根基", quadrant: "神經型・土象限", carrier: "almond",
        reading: "渴望長久、穩固的健康與安適感。讓深沉的大地根部與木質精油，為你的身體打下最安穩、放鬆的根基。",
        oil: "岩蘭草", chem: "倍半萜烯（神經型・土象限）：深層安定神經與肌肉張力，帶來由內而外的踏實感。" },
      { id: 74, name: "錢幣侍者", en: "PAGE OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・身體覺察", quadrant: "神經型・土象限", carrier: "almond",
        reading: "腳踏實地、認真感受身體的每一個微小變化。這是一張非常適合重新建立身體覺察、好好保養自己的牌。",
        oil: "大西洋雪松", chem: "倍半萜烯（神經型・土象限）：喚醒身體的感知力，讓每一次呼吸與按壓都更有感。" },
      { id: 75, name: "錢幣騎士", en: "KNIGHT OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・推開舊痠", quadrant: "多血型・風象限", carrier: "stjohns",
        reading: "雖然步調不快，但每天都在穩定地承受壓力，肌肉裡可能藏著不少「陳年舊痠」。需要深層而穩定的力道慢慢推開。",
        oil: "甜馬鬱蘭", chem: "單萜醇（多血型・風象限）：溫和滲透深層肌理，軟化累積已久的頑固緊繃。" },
      { id: 76, name: "錢幣皇后", en: "QUEEN OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・大地母親", quadrant: "多血型・風象限", carrier: "almond",
        reading: "務實、溫暖、總能把生活打理得井井有條，但往往把自己排在最後一位。今天請把所有照顧都留給自己，享受大地母親般的擁抱。",
        oil: "澳洲檀香", chem: "倍半萜醇（多血型・風象限）：極致溫潤與滋養，撫慰長期照顧他人的辛勞身心。" },
      { id: 77, name: "錢幣國王", en: "KING OF PENTACLES", isMajor: false, symbol: "pentacles", elementTag: "土元素・寧靜靠山", quadrant: "神經型・土象限", carrier: "almond",
        reading: "扛起了家庭或事業的穩重支柱，習慣把所有重量往自己肩上放。在這裡你不需要當任何人的靠山，讓按摩床成為你的靠山。",
        oil: "岩蘭草", chem: "倍半萜烯（神經型・土象限）：「寧靜之油」，深層卸除頂天立地的重壓，帶來深沉好眠。" }
    ];

    let activeDeck = [...TAROT_DECK];

    function switchView(viewId) {
      document.querySelectorAll(".view-section").forEach(v => v.classList.remove("active"));
      document.getElementById(viewId).classList.add("active");
      window.scrollTo({ top: 0, behavior: "smooth" });
    }

    // 下一位客人：重新洗牌並跳轉回最初始的「靜心迎賓首頁」
    function resetForNextGuest() {
      shuffleCards(activeDeck);
      document.getElementById("swap-panel").classList.remove("open");
      document.getElementById("swap-chevron").textContent = "⌄";
      switchView("view-welcome");
    }

    function shuffleCards(list) {
      for (let i = list.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [list[i], list[j]] = [list[j], list[i]];
      }
    }

    function showDrawView() {
      shuffleCards(activeDeck);
      renderDeckCarousel();
      switchView("view-draw");
      const scroller = document.getElementById("deck-scroller");
      setTimeout(() => {
        scroller.scrollTo({ left: (scroller.scrollWidth - scroller.clientWidth) / 2, behavior: "smooth" });
      }, 80);
    }

    function renderDeckCarousel() {
      const scroller = document.getElementById("deck-scroller");
      scroller.innerHTML = "";
      activeDeck.forEach((card, idx) => {
        const numStr = String(idx + 1).padStart(2, "0");
        const el = document.createElement("div");
        el.className = "tarot-card-back";
        el.innerHTML = `
          <div class="back-num">✦ ${numStr} ✦</div>
          <div class="back-eye-emblem">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.3">
              <path d="M2 12s3.5-6 10-6 10 6 10 6-3.5 6-10 6-10-6-10-6Z"/>
              <circle cx="12" cy="12" r="2.5"/>
            </svg>
          </div>
          <div class="back-brand-text">森呼吸</div>
        `;
        el.onclick = () => openPrescription(card);
        scroller.appendChild(el);
      });
    }

    function triggerShuffle() {
      shuffleCards(activeDeck);
      renderDeckCarousel();
      document.querySelectorAll(".tarot-card-back").forEach((el, i) => {
        setTimeout(() => el.classList.add("is-shuffling"), (i % 10) * 25);
      });
    }

    function scrollDeckBy(offset) {
      document.getElementById("deck-scroller").scrollBy({ left: offset, behavior: "smooth" });
    }

    function openPrescription(card) {
      document.getElementById("rx-header-pill").textContent = card.isMajor
        ? "大阿爾克那｜深層調理複方"
        : "小阿爾克那｜精準調理單方";

      document.getElementById("face-en").textContent = card.en;
      document.getElementById("face-zh").textContent = card.name;
      document.getElementById("face-symbol").innerHTML = SYMBOLS_SVG[card.symbol] || SYMBOLS_SVG.major;
      document.getElementById("face-element-tag").textContent = card.elementTag;

      document.getElementById("rx-reading-text").textContent = card.reading;
      document.getElementById("rx-quadrant-pill").textContent = card.quadrant;
      document.getElementById("rx-oil-name").textContent = card.oil;
      document.getElementById("rx-formula-chip").textContent = card.isMajor ? "深層複方調理" : "單方精油調理";
      document.getElementById("rx-chem-desc").textContent = card.chem;

      const carrierInfo = CARRIER_PRESETS[card.carrier] || CARRIER_PRESETS.almond;
      document.getElementById("rx-carrier-name").textContent = `🧴 建議基底油：${carrierInfo.name}`;
      document.getElementById("rx-carrier-drops").textContent = card.isMajor ? carrierInfo.dropsMajor : carrierInfo.dropsMinor;
      document.getElementById("rx-carrier-guide").textContent = carrierInfo.guide;

      const swapList = QUADRANT_SWAPS[card.quadrant] || QUADRANT_SWAPS["全象限深度調和"];
      const chipContainer = document.getElementById("swap-chip-list");
      chipContainer.innerHTML = swapList.map(item => `<div class="swap-oil-chip">${item}</div>`).join("");
      document.getElementById("swap-panel").classList.remove("open");
      document.getElementById("swap-chevron").textContent = "⌄";

      const faceCard = document.getElementById("tarot-face-card");
      faceCard.style.animation = "none";
      faceCard.offsetHeight;
      faceCard.style.animation = null;

      switchView("view-result");
    }

    function toggleSwapPanel() {
      const panel = document.getElementById("swap-panel");
      const isOpen = panel.classList.toggle("open");
      document.getElementById("swap-chevron").textContent = isOpen ? "⌃" : "⌄";
    }

    function openRefModal() {
      renderRefTable();
      document.getElementById("ref-modal").classList.add("open");
    }

    function closeRefModal() {
      document.getElementById("ref-modal").classList.remove("open");
    }

    function handleModalBackdrop(e) {
      if (e.target.id === "ref-modal") closeRefModal();
    }

    function switchModalView(mode) {
      document.getElementById("m-tab-quad").classList.toggle("active", mode === "quad");
      document.getElementById("m-tab-db").classList.toggle("active", mode === "db");
      document.getElementById("m-view-quad").style.display = mode === "quad" ? "block" : "none";
      document.getElementById("m-view-db").style.display = mode === "db" ? "block" : "none";
    }

    function renderRefTable() {
      const q = (document.getElementById("ref-search").value || "").trim().toLowerCase();
      const tbody = document.getElementById("ref-table-body");
      tbody.innerHTML = "";

      TAROT_DECK.filter(c => {
        const cInfo = CARRIER_PRESETS[c.carrier] || CARRIER_PRESETS.almond;
        return c.name.toLowerCase().includes(q) ||
          c.oil.toLowerCase().includes(q) ||
          c.reading.toLowerCase().includes(q) ||
          c.quadrant.toLowerCase().includes(q) ||
          cInfo.name.toLowerCase().includes(q);
      }).forEach(card => {
        const cInfo = CARRIER_PRESETS[card.carrier] || CARRIER_PRESETS.almond;
        const shortCarrier = cInfo.name.split("（")[0];
        const tr = document.createElement("tr");
        tr.innerHTML = `
          <td><strong>${card.name}</strong></td>
          <td>${card.isMajor ? "大牌複方" : "小牌單方"}</td>
          <td>${card.oil}</td>
          <td>${shortCarrier}</td>
          <td><button class="btn-preview-sm" onclick="previewFromRef(${card.id})">預覽處方</button></td>
        `;
        tbody.appendChild(tr);
      });
    }

    function previewFromRef(id) {
      const card = TAROT_DECK.find(c => c.id === id);
      if (card) {
        closeRefModal();
        openPrescription(card);
      }
    }
  </script>
</body>
</html>
