# 🎮 SVG Animated Tetris

> A mesmerizing Tetris animation using pure SVG + CSS that works in GitHub READMEs!

<div align="center">

![Tetris Animation](https://svg-tetris.example.com/animation.svg)

<!-- Main Animated Tetris Board -->
<svg width="300" height="600" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      @keyframes fall {
        0% { transform: translateY(0px); }
        100% { transform: translateY(480px); }
      }
      
      @keyframes rotate {
        0%, 100% { transform: rotate(0deg) translateY(0px); }
        25% { transform: rotate(90deg) translateY(120px); }
        50% { transform: rotate(180deg) translateY(240px); }
        75% { transform: rotate(270deg) translateY(360px); }
      }
      
      @keyframes slide {
        0%, 20% { transform: translateX(0px); }
        30%, 50% { transform: translateX(40px); }
        60%, 80% { transform: translateX(-40px); }
        90%, 100% { transform: translateX(0px); }
      }
      
      @keyframes flash {
        0%, 90% { opacity: 1; }
        92%, 96% { opacity: 0; }
        98%, 100% { opacity: 1; }
      }
      
      @keyframes glow {
        0%, 100% { filter: brightness(1); }
        50% { filter: brightness(1.5) drop-shadow(0 0 10px rgba(255,255,255,0.8)); }
      }
      
      .falling-piece {
        animation: fall 4s ease-in infinite;
      }
      
      .rotating-piece {
        animation: fall 4s ease-in infinite, rotate 4s linear infinite;
        transform-origin: center;
      }
      
      .sliding-piece {
        animation: fall 4s ease-in infinite, slide 4s ease-in-out infinite;
      }
      
      .clearing-line {
        animation: flash 0.5s ease-in-out;
      }
      
      .score-glow {
        animation: glow 2s ease-in-out infinite;
      }
    </style>
    
    <!-- Grid pattern -->
    <pattern id="grid" width="30" height="30" patternUnits="userSpaceOnUse">
      <rect width="30" height="30" fill="none" stroke="#333" stroke-width="0.5"/>
    </pattern>
    
    <!-- Gradient for pieces -->
    <linearGradient id="pieceGradient" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#00ffff;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#0099ff;stop-opacity:1" />
    </linearGradient>
    
    <linearGradient id="pieceGradient2" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#ff00ff;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#ff0099;stop-opacity:1" />
    </linearGradient>
    
    <linearGradient id="pieceGradient3" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" style="stop-color:#ffff00;stop-opacity:1" />
      <stop offset="100%" style="stop-color:#ff9900;stop-opacity:1" />
    </linearGradient>
  </defs>
  
  <!-- Background -->
  <rect width="300" height="600" fill="#111" stroke="#444" stroke-width="2"/>
  <rect width="300" height="600" fill="url(#grid)" opacity="0.3"/>
  
  <!-- Game board frame -->
  <rect x="30" y="30" width="240" height="540" fill="none" stroke="#666" stroke-width="2"/>
  
  <!-- Static pieces at bottom -->
  <g id="static-pieces">
    <!-- Bottom row -->
    <rect x="30" y="540" width="30" height="30" fill="#666"/>
    <rect x="60" y="540" width="30" height="30" fill="#666"/>
    <rect x="90" y="540" width="30" height="30" fill="#666"/>
    <rect x="150" y="540" width="30" height="30" fill="#666"/>
    <rect x="180" y="540" width="30" height="30" fill="#666"/>
    <rect x="210" y="540" width="30" height="30" fill="#666"/>
    <rect x="240" y="540" width="30" height="30" fill="#666"/>
    
    <!-- Second row -->
    <rect x="30" y="510" width="30" height="30" fill="#666"/>
    <rect x="60" y="510" width="30" height="30" fill="#666"/>
    <rect x="90" y="510" width="30" height="30" fill="#666"/>
    <rect x="120" y="510" width="30" height="30" fill="#666"/>
    <rect x="180" y="510" width="30" height="30" fill="#666"/>
    <rect x="210" y="510" width="30" height="30" fill="#666"/>
    
    <!-- Third row -->
    <rect x="30" y="480" width="30" height="30" fill="#666"/>
    <rect x="90" y="480" width="30" height="30" fill="#666"/>
    <rect x="210" y="480" width="30" height="30" fill="#666"/>
  </g>
  
  <!-- Falling I-piece -->
  <g class="falling-piece">
    <rect x="120" y="30" width="30" height="30" fill="url(#pieceGradient)" stroke="#fff" stroke-width="1"/>
    <rect x="120" y="60" width="30" height="30" fill="url(#pieceGradient)" stroke="#fff" stroke-width="1"/>
    <rect x="120" y="90" width="30" height="30" fill="url(#pieceGradient)" stroke="#fff" stroke-width="1"/>
    <rect x="120" y="120" width="30" height="30" fill="url(#pieceGradient)" stroke="#fff" stroke-width="1"/>
  </g>
  
  <!-- Rotating T-piece (delayed) -->
  <g class="rotating-piece" style="animation-delay: 1s; opacity: 0; animation-fill-mode: forwards;">
    <rect x="180" y="30" width="30" height="30" fill="url(#pieceGradient2)" stroke="#fff" stroke-width="1"/>
    <rect x="150" y="60" width="30" height="30" fill="url(#pieceGradient2)" stroke="#fff" stroke-width="1"/>
    <rect x="180" y="60" width="30" height="30" fill="url(#pieceGradient2)" stroke="#fff" stroke-width="1"/>
    <rect x="210" y="60" width="30" height="30" fill="url(#pieceGradient2)" stroke="#fff" stroke-width="1"/>
  </g>
  
  <!-- Sliding L-piece (more delayed) -->
  <g class="sliding-piece" style="animation-delay: 2s; opacity: 0; animation-fill-mode: forwards;">
    <rect x="60" y="30" width="30" height="30" fill="url(#pieceGradient3)" stroke="#fff" stroke-width="1"/>
    <rect x="60" y="60" width="30" height="30" fill="url(#pieceGradient3)" stroke="#fff" stroke-width="1"/>
    <rect x="60" y="90" width="30" height="30" fill="url(#pieceGradient3)" stroke="#fff" stroke-width="1"/>
    <rect x="90" y="90" width="30" height="30" fill="url(#pieceGradient3)" stroke="#fff" stroke-width="1"/>
  </g>
  
  <!-- Score display -->
  <text x="150" y="20" text-anchor="middle" fill="#fff" font-family="monospace" font-size="16" class="score-glow">
    SCORE: 1337
  </text>
  
  <!-- Line clear effect -->
  <rect x="30" y="540" width="240" height="30" fill="#fff" opacity="0" class="clearing-line" style="animation-delay: 3.8s;"/>
</svg>

</div>

---

## 🎯 Interactive SVG Tetris States

Click the sections below to see different game states:

<details>
<summary><b>🎮 Game Start Animation</b></summary>

<div align="center">
<svg width="300" height="400" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      @keyframes intro {
        0% { transform: scale(0) rotate(180deg); opacity: 0; }
        50% { transform: scale(1.2) rotate(90deg); opacity: 0.8; }
        100% { transform: scale(1) rotate(0deg); opacity: 1; }
      }
      
      @keyframes pulse {
        0%, 100% { transform: scale(1); }
        50% { transform: scale(1.05); }
      }
      
      .intro-piece {
        animation: intro 2s ease-out;
        transform-origin: center;
      }
      
      .pulse-text {
        animation: pulse 2s ease-in-out infinite;
        transform-origin: center;
      }
    </style>
  </defs>
  
  <rect width="300" height="400" fill="#000"/>
  
  <!-- Animated Tetris logo -->
  <g transform="translate(150, 200)" class="intro-piece">
    <rect x="-60" y="-30" width="30" height="30" fill="#ff0000"/>
    <rect x="-30" y="-30" width="30" height="30" fill="#ff7700"/>
    <rect x="0" y="-30" width="30" height="30" fill="#ffff00"/>
    <rect x="30" y="-30" width="30" height="30" fill="#00ff00"/>
    <rect x="-30" y="0" width="30" height="30" fill="#0099ff"/>
    <rect x="0" y="0" width="30" height="30" fill="#0000ff"/>
    <rect x="30" y="0" width="30" height="30" fill="#ff00ff"/>
  </g>
  
  <text x="150" y="300" text-anchor="middle" fill="#fff" font-size="24" font-family="monospace" class="pulse-text">
    PRESS START
  </text>
</svg>
</div>

</details>

<details>
<summary><b>⚡ Speed Mode Animation</b></summary>

<div align="center">
<svg width="300" height="400" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      @keyframes superfast {
        0% { transform: translateY(0px); }
        100% { transform: translateY(350px); }
      }
      
      @keyframes shake {
        0%, 100% { transform: translateX(0); }
        25% { transform: translateX(-2px); }
        75% { transform: translateX(2px); }
      }
      
      .speed-piece-1 { animation: superfast 0.5s linear infinite; }
      .speed-piece-2 { animation: superfast 0.7s linear infinite; animation-delay: 0.2s; }
      .speed-piece-3 { animation: superfast 0.6s linear infinite; animation-delay: 0.4s; }
      .board-shake { animation: shake 0.1s linear infinite; }
    </style>
  </defs>
  
  <g class="board-shake">
    <rect width="300" height="400" fill="#111"/>
    <rect x="20" y="20" width="260" height="360" fill="none" stroke="#f00" stroke-width="2"/>
    
    <!-- Multiple falling pieces -->
    <rect x="50" y="20" width="30" height="30" fill="#0ff" class="speed-piece-1"/>
    <rect x="150" y="20" width="30" height="30" fill="#f0f" class="speed-piece-2"/>
    <rect x="220" y="20" width="30" height="30" fill="#ff0" class="speed-piece-3"/>
  </g>
  
  <text x="150" y="395" text-anchor="middle" fill="#f00" font-size="16" font-family="monospace">
    SPEED LEVEL 9!
  </text>
</svg>
</div>

</details>

<details>
<summary><b>🌟 T-Spin Animation</b></summary>

<div align="center">
<svg width="300" height="400" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      @keyframes tspin {
        0% { transform: rotate(0deg) translate(0, 0); }
        25% { transform: rotate(90deg) translate(30px, 0); }
        50% { transform: rotate(180deg) translate(30px, 30px); }
        75% { transform: rotate(270deg) translate(0, 30px); }
        100% { transform: rotate(360deg) translate(0, 0); }
      }
      
      @keyframes sparkle {
        0%, 100% { opacity: 0; transform: scale(0); }
        50% { opacity: 1; transform: scale(1); }
      }
      
      .t-spin-piece {
        animation: tspin 2s ease-in-out infinite;
        transform-origin: 45px 45px;
      }
      
      .sparkle {
        animation: sparkle 1s ease-out infinite;
      }
    </style>
  </defs>
  
  <rect width="300" height="400" fill="#000"/>
  
  <!-- T-piece performing spin -->
  <g transform="translate(100, 150)" class="t-spin-piece">
    <rect x="30" y="30" width="30" height="30" fill="#ff00ff" stroke="#fff" stroke-width="2"/>
    <rect x="0" y="60" width="30" height="30" fill="#ff00ff" stroke="#fff" stroke-width="2"/>
    <rect x="30" y="60" width="30" height="30" fill="#ff00ff" stroke="#fff" stroke-width="2"/>
    <rect x="60" y="60" width="30" height="30" fill="#ff00ff" stroke="#fff" stroke-width="2"/>
  </g>
  
  <!-- Sparkle effects -->
  <circle cx="100" cy="150" r="5" fill="#fff" class="sparkle"/>
  <circle cx="200" cy="150" r="5" fill="#fff" class="sparkle" style="animation-delay: 0.3s;"/>
  <circle cx="150" cy="100" r="5" fill="#fff" class="sparkle" style="animation-delay: 0.6s;"/>
  <circle cx="150" cy="200" r="5" fill="#fff" class="sparkle" style="animation-delay: 0.9s;"/>
  
  <text x="150" y="350" text-anchor="middle" fill="#fff" font-size="20" font-family="monospace">
    T-SPIN TRIPLE!
  </text>
</svg>
</div>

</details>

<details>
<summary><b>🎆 Line Clear Cascade</b></summary>

<div align="center">
<svg width="300" height="400" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      @keyframes disappear {
        0% { opacity: 1; transform: scale(1); }
        50% { opacity: 1; transform: scale(1.2); filter: brightness(2); }
        100% { opacity: 0; transform: scale(0); }
      }
      
      @keyframes drop {
        0% { transform: translateY(0); }
        100% { transform: translateY(30px); }
      }
      
      .clear-1 { animation: disappear 0.5s ease-out forwards; }
      .clear-2 { animation: disappear 0.5s ease-out 0.2s forwards; }
      .clear-3 { animation: disappear 0.5s ease-out 0.4s forwards; }
      .clear-4 { animation: disappear 0.5s ease-out 0.6s forwards; }
      
      .drop-pieces { animation: drop 0.5s ease-in 1s forwards; }
    </style>
  </defs>
  
  <rect width="300" height="400" fill="#000"/>
  
  <!-- Pieces above the cleared lines -->
  <g class="drop-pieces">
    <rect x="50" y="200" width="30" height="30" fill="#666"/>
    <rect x="110" y="200" width="30" height="30" fill="#666"/>
    <rect x="170" y="200" width="30" height="30" fill="#666"/>
  </g>
  
  <!-- Lines being cleared -->
  <rect x="20" y="230" width="260" height="30" fill="#fff" class="clear-1"/>
  <rect x="20" y="260" width="260" height="30" fill="#fff" class="clear-2"/>
  <rect x="20" y="290" width="260" height="30" fill="#fff" class="clear-3"/>
  <rect x="20" y="320" width="260" height="30" fill="#fff" class="clear-4"/>
  
  <text x="150" y="100" text-anchor="middle" fill="#ff0" font-size="24" font-family="monospace">
    TETRIS!
  </text>
</svg>
</div>

</details>

<details>
<summary><b>🏆 Victory Animation</b></summary>

<div align="center">
<svg width="300" height="400" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      @keyframes victory {
        0% { transform: translateY(400px) scale(0.5); opacity: 0; }
        50% { transform: translateY(0px) scale(1.2); opacity: 1; }
        100% { transform: translateY(0px) scale(1); opacity: 1; }
      }
      
      @keyframes rainbow {
        0% { fill: #ff0000; }
        16% { fill: #ff7700; }
        33% { fill: #ffff00; }
        50% { fill: #00ff00; }
        66% { fill: #0099ff; }
        83% { fill: #0000ff; }
        100% { fill: #ff00ff; }
      }
      
      @keyframes rotate-trophy {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
      }
      
      .victory-text {
        animation: victory 2s ease-out forwards, rainbow 2s linear infinite;
      }
      
      .trophy {
        animation: rotate-trophy 4s linear infinite;
        transform-origin: center;
      }
    </style>
  </defs>
  
  <rect width="300" height="400" fill="#000"/>
  
  <!-- Trophy -->
  <g transform="translate(150, 200)" class="trophy">
    <path d="M-30,-40 L-20,-20 L-10,-20 L-10,0 L10,0 L10,-20 L20,-20 L30,-40 Z" 
          fill="#ffd700" stroke="#fff" stroke-width="2"/>
    <ellipse cx="0" cy="-40" rx="35" ry="10" fill="#ffd700" stroke="#fff" stroke-width="2"/>
  </g>
  
  <text x="150" y="100" text-anchor="middle" font-size="32" font-family="monospace" class="victory-text">
    YOU WIN!
  </text>
  
  <text x="150" y="350" text-anchor="middle" fill="#fff" font-size="16" font-family="monospace">
    Score: 999,999
  </text>
</svg>
</div>

</details>

---

## 🎨 How It Works

This implementation uses:
- **Pure SVG** with embedded CSS animations
- **No JavaScript** - works perfectly in GitHub READMEs
- **CSS @keyframes** for smooth animations
- **Multiple animation types**: falling, rotating, sliding, pulsing
- **Gradient fills** for beautiful piece colors
- **Transform animations** for movement and rotation

## 🚀 Features

- ✨ **Auto-playing animations** - Pieces fall and rotate automatically
- 🎮 **Multiple game states** - Different animations for different scenarios
- 🌈 **Colorful gradients** - Modern, vibrant piece designs
- ⚡ **Performance optimized** - Smooth animations with CSS transforms
- 📱 **Responsive** - Scales well on different screen sizes

## 💻 Copy & Paste Code

To use this in your README, simply copy any of the SVG blocks above! Here's a minimal example:

```svg
<svg width="200" height="300" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      @keyframes fall {
        from { transform: translateY(0px); }
        to { transform: translateY(250px); }
      }
      .piece { animation: fall 3s linear infinite; }
    </style>
  </defs>
  <rect width="200" height="300" fill="#000"/>
  <rect x="85" y="10" width="30" height="30" fill="#0ff" class="piece"/>
</svg>
```

## 🎯 Customization Tips

1. **Change animation speed**: Modify the duration in `animation: fall 3s`
2. **Add more pieces**: Duplicate `<rect>` elements with different delays
3. **Custom colors**: Change the `fill` attribute or create new gradients
4. **Different movements**: Create new `@keyframes` for unique animations

---

<p align="center">
  <img src="https://img.shields.io/badge/Made_with-SVG_+_CSS-ff69b4?style=for-the-badge" />
  <img src="https://img.shields.io/badge/No_JavaScript-Required-00ff00?style=for-the-badge" />
  <img src="https://img.shields.io/badge/GitHub_README-Compatible-blue?style=for-the-badge" />
</p>
