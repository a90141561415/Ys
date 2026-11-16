<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="default">
  <meta name="apple-mobile-web-app-title" content="森呼吸芳療塔羅">
  <title>森呼吸・芳療塔羅處方</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+TC:wght@400;600;700&family=Noto+Sans+TC:wght@300;400;500&display=swap" rel="stylesheet">
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            forest: {
              50: '#F4F7F4',
              100: '#E5ECE5',
              200: '#C9D8C9',
              300: '#A3BDA4',
              500: '#5C7C5E',
              700: '#3D563F',
              800: '#2D412F',
              900: '#1F2D20'
            },
            cream: {
              50: '#FDFBF7',
              100: '#F7F3EB',
              200: '#EFE8D8'
            },
            gold: {
              400: '#C8A96E',
              500: '#B59253',
              600: '#9A783C'
            }
          },
          fontFamily: {
            serif: ['"Noto Serif TC"', 'serif'],
            sans: ['"Noto Sans TC"', 'sans-serif']
          }
        }
      }
    }
  </script>
  <style>
    body {
      background-color: #FDFBF7;
      color: #2D412F;
      -webkit-tap-highlight-color: transparent;
      user-select: none;
      overflow-x: hidden;
    }

    /* 3D 翻牌效果 */
    .perspective-1000 {
      perspective: 1000px;
    }
    .transform-style-3d {
      transform-style: preserve-3d;
    }
    .backface-hidden {
      backface-visibility: hidden;
    }
    .rotate-y-180 {
      transform: rotateY(180deg);
    }
    .card-inner {
      transition: transform 0.85s cubic-bezier(0.22, 1, 0.36, 1);
    }

    /* 呼吸光暈動畫 */
    @keyframes breathe {
      0%, 100% { transform: scale(1); opacity: 0.45; }
      50% { transform: scale(1.18); opacity: 0.85; }
    }
    .animate-breathe {
      animation: breathe 6s ease-in-out infinite;
    }

    /* 牌背精緻植物幾何紋理 */
    .tarot-back-pattern {
      background-color: #2D412F;
      background-image: 
        radial-gradient(circle at 50% 50%, rgba(200, 169, 110, 0.15) 0%, transparent 65%),
        repeating-linear-gradient(45deg, rgba(200, 169, 110, 0.05) 0px, rgba(200, 169, 110, 0.05) 1px, transparent 1px, transparent 10px),
        repeating-linear-gradient(-45deg, rgba(200, 169, 110, 0.05) 0px, rgba(200, 169, 110, 0.05) 1px, transparent 1px, transparent 10px);
    }

    /* 隱藏橫向捲軸但保留滑動功能 */
    .no-scrollbar::-webkit-scrollbar {
      display: none;
    }
    .no-scrollbar {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }

    /* 淡入動畫 */
    @
