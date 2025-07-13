# 🎮 Simple SVG Animated Tetris

> Testing the simplest possible SVG animation for GitHub README

## Test 1: Basic Falling Block

<svg width="200" height="300" xmlns="http://www.w3.org/2000/svg">
  <rect width="200" height="300" fill="#000000"/>
  <rect x="85" y="10" width="30" height="30" fill="#00ffff">
    <animate attributeName="y" from="10" to="260" dur="3s" repeatCount="indefinite"/>
  </rect>
</svg>

## Test 2: Falling + Rotating Block

<svg width="200" height="300" xmlns="http://www.w3.org/2000/svg">
  <rect width="200" height="300" fill="#000000"/>
  <g>
    <rect x="85" y="10" width="30" height="30" fill="#ff00ff">
      <animate attributeName="y" from="10" to="260" dur="3s" repeatCount="indefinite"/>
      <animateTransform attributeName="transform" type="rotate" from="0 100 25" to="360 100 25" dur="3s" repeatCount="indefinite"/>
    </rect>
  </g>
</svg>

## Test 3: Multiple Blocks Falling

<svg width="200" height="300" xmlns="http://www.w3.org/2000/svg">
  <rect width="200" height="300" fill="#111111"/>
  
  <!-- First block -->
  <rect x="50" y="10" width="30" height="30" fill="#00ffff">
    <animate attributeName="y" from="10" to="260" dur="2s" repeatCount="indefinite"/>
  </rect>
  
  <!-- Second block (delayed) -->
  <rect x="85" y="10" width="30" height="30" fill="#ffff00">
    <animate attributeName="y" from="10" to="260" dur="2s" begin="0.5s" repeatCount="indefinite"/>
  </rect>
  
  <!-- Third block (more delayed) -->
  <rect x="120" y="10" width="30" height="30" fill="#ff00ff">
    <animate attributeName="y" from="10" to="260" dur="2s" begin="1s" repeatCount="indefinite"/>
  </rect>
</svg>

## Test 4: Simple Tetris I-Piece

<svg width="200" height="400" xmlns="http://www.w3.org/2000/svg">
  <rect width="200" height="400" fill="#000000"/>
  
  <!-- I-piece (4 blocks) -->
  <g>
    <rect x="85" y="10" width="30" height="30" fill="#00ffff" stroke="#ffffff" stroke-width="2">
      <animate attributeName="y" from="10" to="340" dur="4s" repeatCount="indefinite"/>
    </rect>
    <rect x="85" y="40" width="30" height="30" fill="#00ffff" stroke="#ffffff" stroke-width="2">
      <animate attributeName="y" from="40" to="370" dur="4s" repeatCount="indefinite"/>
    </rect>
    <rect x="85" y="70" width="30" height="30" fill="#00ffff" stroke="#ffffff" stroke-width="2">
      <animate attributeName="y" from="70" to="400" dur="4s" repeatCount="indefinite"/>
    </rect>
    <rect x="85" y="100" width="30" height="30" fill="#00ffff" stroke="#ffffff" stroke-width="2">
      <animate attributeName="y" from="100" to="430" dur="4s" repeatCount="indefinite"/>
    </rect>
  </g>
</svg>

## Test 5: Grid Background + Falling Piece

<svg width="240" height="400" xmlns="http://www.w3.org/2000/svg">
  <!-- Background -->
  <rect width="240" height="400" fill="#000000"/>
  
  <!-- Grid lines -->
  <g stroke="#333333" stroke-width="1" fill="none">
    <!-- Vertical lines -->
    <line x1="30" y1="0" x2="30" y2="400"/>
    <line x1="60" y1="0" x2="60" y2="400"/>
    <line x1="90" y1="0" x2="90" y2="400"/>
    <line x1="120" y1="0" x2="120" y2="400"/>
    <line x1="150" y1="0" x2="150" y2="400"/>
    <line x1="180" y1="0" x2="180" y2="400"/>
    <line x1="210" y1="0" x2="210" y2="400"/>
    
    <!-- Horizontal lines every 30px -->
    <line x1="0" y1="30" x2="240" y2="30"/>
    <line x1="0" y1="60" x2="240" y2="60"/>
    <line x1="0" y1="90" x2="240" y2="90"/>
    <line x1="0" y1="120" x2="240" y2="120"/>
    <line x1="0" y1="150" x2="240" y2="150"/>
    <line x1="0" y1="180" x2="240" y2="180"/>
    <line x1="0" y1="210" x2="240" y2="210"/>
    <line x1="0" y1="240" x2="240" y2="240"/>
    <line x1="0" y1="270" x2="240" y2="270"/>
    <line x1="0" y1="300" x2="240" y2="300"/>
    <line x1="0" y1="330" x2="240" y2="330"/>
    <line x1="0" y1="360" x2="240" y2="360"/>
  </g>
  
  <!-- Static pieces at bottom -->
  <rect x="30" y="360" width="30" height="30" fill="#666666"/>
  <rect x="60" y="360" width="30" height="30" fill="#666666"/>
  <rect x="90" y="360" width="30" height="30" fill="#666666"/>
  <rect x="150" y="360" width="30" height="30" fill="#666666"/>
  <rect x="180" y="360" width="30" height="30" fill="#666666"/>
  
  <!-- Falling T-piece -->
  <g>
    <rect x="90" y="0" width="30" height="30" fill="#ff00ff">
      <animate attributeName="y" from="0" to="330" dur="3s" repeatCount="indefinite"/>
    </rect>
    <rect x="60" y="30" width="30" height="30" fill="#ff00ff">
      <animate attributeName="y" from="30" to="360" dur="3s" repeatCount="indefinite"/>
    </rect>
    <rect x="90" y="30" width="30" height="30" fill="#ff00ff">
      <animate attributeName="y" from="30" to="360" dur="3s" repeatCount="indefinite"/>
    </rect>
    <rect x="120" y="30" width="30" height="30" fill="#ff00ff">
      <animate attributeName="y" from="30" to="360" dur="3s" repeatCount="indefinite"/>
    </rect>
  </g>
</svg>

## Test 6: Line Clear Effect

<svg width="240" height="200" xmlns="http://www.w3.org/2000/svg">
  <rect width="240" height="200" fill="#000000"/>
  
  <!-- Bottom row that will "clear" -->
  <g>
    <rect x="0" y="170" width="30" height="30" fill="#ffffff">
      <animate attributeName="opacity" values="1;1;0" dur="2s" repeatCount="indefinite"/>
    </rect>
    <rect x="30" y="170" width="30" height="30" fill="#ffffff">
      <animate attributeName="opacity" values="1;1;0" dur="2s" repeatCount="indefinite"/>
    </rect>
    <rect x="60" y="170" width="30" height="30" fill="#ffffff">
      <animate attributeName="opacity" values="1;1;0" dur="2s" repeatCount="indefinite"/>
    </rect>
    <rect x="90" y="170" width="30" height="30" fill="#ffffff">
      <animate attributeName="opacity" values="1;1;0" dur="2s" repeatCount="indefinite"/>
    </rect>
    <rect x="120" y="170" width="30" height="30" fill="#ffffff">
      <animate attributeName="opacity" values="1;1;0" dur="2s" repeatCount="indefinite"/>
    </rect>
    <rect x="150" y="170" width="30" height="30" fill="#ffffff">
      <animate attributeName="opacity" values="1;1;0" dur="2s" repeatCount="indefinite"/>
    </rect>
    <rect x="180" y="170" width="30" height="30" fill="#ffffff">
      <animate attributeName="opacity" values="1;1;0" dur="2s" repeatCount="indefinite"/>
    </rect>
    <rect x="210" y="170" width="30" height="30" fill="#ffffff">
      <animate attributeName="opacity" values="1;1;0" dur="2s" repeatCount="indefinite"/>
    </rect>
  </g>
  
  <!-- Pieces above that will drop -->
  <rect x="60" y="140" width="30" height="30" fill="#00ffff">
    <animate attributeName="y" values="140;140;170" dur="2s" repeatCount="indefinite"/>
  </rect>
  <rect x="150" y="140" width="30" height="30" fill="#ffff00">
    <animate attributeName="y" values="140;140;170" dur="2s" repeatCount="indefinite"/>
  </rect>
</svg>

---

## 🧪 Which animations work for you?

These are the simplest possible SVG animations. They use only:
- `<animate>` for basic property animation
- `attributeName` to specify what to animate
- `from`/`to` or `values` for the animation values
- `dur` for duration
- `repeatCount="indefinite"` for looping

No CSS, no complex transforms, just pure SVG animation elements.

Let me know which ones display correctly and we can build from there!
