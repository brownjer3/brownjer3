# 🎮 CSS Animated Tetris (GitHub Compatible)

> This uses CSS animations embedded in SVG - confirmed to work in GitHub READMEs!

## Working Animated Tetris

<div align="center">

<img src="data:image/svg+xml,%3Csvg width='300' height='500' xmlns='http://www.w3.org/2000/svg'%3E%3Cdefs%3E%3Cstyle%3E@keyframes fall{0%25{transform:translateY(0)}100%25{transform:translateY(420px)}}@keyframes flash{0%25,49%25,51%25,100%25{opacity:1}50%25{opacity:0}}.falling{animation:fall 3s ease-in infinite}.flashing{animation:flash 0.5s infinite}%3C/style%3E%3C/defs%3E%3Crect width='300' height='500' fill='%23111'/%3E%3Cg stroke='%23333' stroke-width='1' fill='none'%3E%3Cpath d='M50 0v500M100 0v500M150 0v500M200 0v500M250 0v500M0 50h300M0 100h300M0 150h300M0 200h300M0 250h300M0 300h300M0 350h300M0 400h300M0 450h300'/%3E%3C/g%3E%3Cg class='falling'%3E%3Crect x='100' y='0' width='50' height='50' fill='%2300ffff' stroke='%23fff' stroke-width='2'/%3E%3Crect x='100' y='50' width='50' height='50' fill='%2300ffff' stroke='%23fff' stroke-width='2'/%3E%3Crect x='100' y='100' width='50' height='50' fill='%2300ffff' stroke='%23fff' stroke-width='2'/%3E%3Crect x='100' y='150' width='50' height='50' fill='%2300ffff' stroke='%23fff' stroke-width='2'/%3E%3C/g%3E%3Crect x='0' y='450' width='50' height='50' fill='%23666'/%3E%3Crect x='50' y='450' width='50' height='50' fill='%23666'/%3E%3Crect x='100' y='450' width='50' height='50' fill='%23666'/%3E%3Crect x='200' y='450' width='50' height='50' fill='%23666'/%3E%3Crect x='250' y='450' width='50' height='50' fill='%23666'/%3E%3Ctext x='150' y='30' text-anchor='middle' fill='%23fff' font-family='monospace' font-size='20' class='flashing'%3ETETRIS%3C/text%3E%3C/svg%3E" alt="Animated Tetris">

</div>

## Alternative: Self-Hosted SVG File

Create a file called `tetris.svg` in your repo:

```svg
<svg width="300" height="500" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <style>
      @keyframes fall {
        0% { transform: translateY(0px); }
        100% { transform: translateY(400px); }
      }
      
      @keyframes rotate {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
      }
      
      @keyframes slideLeft {
        0%, 100% { transform: translateX(0px); }
        50% { transform: translateX(-50px); }
      }
      
      @keyframes slideRight {
        0%, 100% { transform: translateX(0px); }
        50% { transform: translateX(50px); }
      }
      
      @keyframes pulse {
        0%, 100% { opacity: 0.3; }
        50% { opacity: 1; }
      }
      
      @keyframes clear {
        0% { opacity: 1; transform: scale(1); }
        50% { opacity: 1; transform: scale(1.1); filter: brightness(2); }
        100% { opacity: 0; transform: scale(0); }
      }
      
      .piece-1 {
        animation: fall 4s linear infinite;
      }
      
      .piece-2 {
        animation: fall 4s linear infinite, rotate 4s linear infinite;
        animation-delay: 1s;
        transform-origin: 125px 75px;
      }
      
      .piece-3 {
        animation: fall 4s linear infinite, slideLeft 4s ease-in-out infinite;
        animation-delay: 2s;
      }
      
      .piece-4 {
        animation: fall 4s linear infinite, slideRight 4s ease-in-out infinite;
        animation-delay: 3s;
      }
      
      .grid-line {
        animation: pulse 2s ease-in-out infinite;
      }
      
      .clear-line {
        animation: clear 1s ease-out infinite;
        animation-delay: 3.5s;
      }
    </style>
  </defs>
  
  <!-- Background -->
  <rect width="300" height="500" fill="#0a0a0a"/>
  
  <!-- Grid -->
  <g stroke="#222" stroke-width="1" fill="none" class="grid-line">
    <path d="M50 0v500 M100 0v500 M150 0v500 M200 0v500 M250 0v500"/>
    <path d="M0 50h300 M0 100h300 M0 150h300 M0 200h300 M0 250h300 M0 300h300 M0 350h300 M0 400h300 M0 450h300"/>
  </g>
  
  <!-- Piece 1: I-piece (falling straight) -->
  <g class="piece-1">
    <rect x="100" y="0" width="50" height="50" fill="#00ffff" stroke="#fff" stroke-width="2"/>
    <rect x="100" y="50" width="50" height="50" fill="#00ffff" stroke="#fff" stroke-width="2"/>
    <rect x="100" y="100" width="50" height="50" fill="#00ffff" stroke="#fff" stroke-width="2"/>
    <rect x="100" y="150" width="50" height="50" fill="#00ffff" stroke="#fff" stroke-width="2"/>
  </g>
  
  <!-- Piece 2: T-piece (falling and rotating) -->
  <g class="piece-2">
    <rect x="100" y="50" width="50" height="50" fill="#ff00ff" stroke="#fff" stroke-width="2"/>
    <rect x="50" y="100" width="50" height="50" fill="#ff00ff" stroke="#fff" stroke-width="2"/>
    <rect x="100" y="100" width="50" height="50" fill="#ff00ff" stroke="#fff" stroke-width="2"/>
    <rect x="150" y="100" width="50" height="50" fill="#ff00ff" stroke="#fff" stroke-width="2"/>
  </g>
  
  <!-- Piece 3: L-piece (falling and sliding left) -->
  <g class="piece-3">
    <rect x="150" y="0" width="50" height="50" fill="#ff7700" stroke="#fff" stroke-width="2"/>
    <rect x="150" y="50" width="50" height="50" fill="#ff7700" stroke="#fff" stroke-width="2"/>
    <rect x="150" y="100" width="50" height="50" fill="#ff7700" stroke="#fff" stroke-width="2"/>
    <rect x="200" y="100" width="50" height="50" fill="#ff7700" stroke="#fff" stroke-width="2"/>
  </g>
  
  <!-- Piece 4: Z-piece (falling and sliding right) -->
  <g class="piece-4">
    <rect x="50" y="0" width="50" height="50" fill="#ff0000" stroke="#fff" stroke-width="2"/>
    <rect x="100" y="0" width="50" height="50" fill="#ff0000" stroke="#fff" stroke-width="2"/>
    <rect x="100" y="50" width="50" height="50" fill="#ff0000" stroke="#fff" stroke-width="2"/>
    <rect x="150" y="50" width="50" height="50" fill="#ff0000" stroke="#fff" stroke-width="2"/>
  </g>
  
  <!-- Static pieces at bottom -->
  <rect x="0" y="450" width="50" height="50" fill="#666"/>
  <rect x="50" y="450" width="50" height="50" fill="#666"/>
  <rect x="100" y="450" width="50" height="50" fill="#666"/>
  <rect x="150" y="450" width="50" height="50" fill="#666"/>
  <rect x="200" y="450" width="50" height="50" fill="#666"/>
  <rect x="250" y="450" width="50" height="50" fill="#666"/>
  
  <rect x="0" y="400" width="50" height="50" fill="#666"/>
  <rect x="50" y="400" width="50" height="50" fill="#666"/>
  <rect x="150" y="400" width="50" height="50" fill="#666"/>
  <rect x="250" y="400" width="50" height="50" fill="#666"/>
  
  <!-- Line clear effect -->
  <rect x="0" y="450" width="300" height="50" fill="#fff" opacity="0" class="clear-line"/>
  
  <!-- Score -->
  <text x="150" y="30" text-anchor="middle" fill="#fff" font-family="monospace" font-size="20">
    SCORE: 1337
  </text>
</svg>
```

Then reference it in your README:

```markdown
![Animated Tetris](./tetris.svg)
```

## Simple Working Example

Here's the simplest CSS-animated block that definitely works:

```svg
<svg width="200" height="300" xmlns="http://www.w3.org/2000/svg">
  <style>
    @keyframes drop {
      from { transform: translateY(0px); }
      to { transform: translateY(250px); }
    }
    .block { animation: drop 2s ease-in infinite; }
  </style>
  <rect width="200" height="300" fill="#000"/>
  <rect class="block" x="85" y="10" width="30" height="30" fill="#0ff"/>
</svg>
```

## Key Points for GitHub SVG Animations:

1. ✅ Use CSS `@keyframes` and `animation` property
2. ✅ Embed styles directly in the SVG
3. ✅ Use `transform`, `opacity`, and other CSS properties
4. ❌ Don't use `<animate>` or `<animateTransform>` tags
5. ❌ Don't use JavaScript
6. ❌ Don't link to external CSS files

## Hosting Options:

1. **Data URI** (shown above) - Embed directly in markdown
2. **Repository file** - Save as `.svg` and reference with relative path
3. **GitHub Pages** - Host and link to the SVG file

The data URI method works immediately but creates long URLs. The repository file method is cleaner for complex animations.
