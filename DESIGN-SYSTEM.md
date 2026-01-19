# Puzzle Hub - Game Design System
**Version 1.0 | Mobile-First Design Language**

---

## 🎨 Design Philosophy

All games in the Puzzle Hub should feel like part of a cohesive family while allowing individual personality. This design system ensures:

- **Consistency** - Users know what to expect
- **Mobile-first** - Touch-optimized for Android phones
- **Accessibility** - Clear, readable, inclusive
- **Performance** - Fast loading, smooth interactions

---

## 📐 Layout Structure

### Standard Game Layout

Every game should follow this basic structure:

```
┌─────────────────────────────────────┐
│  TOPBAR                             │
│  [Title]              [Stats] [Hub] │
├─────────────────────────────────────┤
│  CONTROLS                           │
│  [New Game] [Action Buttons] [🏆]  │
├─────────────────────────────────────┤
│  STATUS MESSAGE                     │
│  (Game feedback here)               │
├─────────────────────────────────────┤
│                                     │
│  GAME AREA                          │
│  (Main interactive content)         │
│                                     │
│                                     │
├─────────────────────────────────────┤
│  INSTRUCTIONS                       │
│  Rules and help text                │
└─────────────────────────────────────┘
```

### Responsive Breakpoints

```css
/* Mobile (default) */
@media (max-width: 500px) {
    /* Smaller cells, buttons, text */
}

/* Tablet */
@media (min-width: 501px) and (max-width: 900px) {
    /* Medium sizing */
}

/* Desktop */
@media (min-width: 901px) {
    /* Full sizing */
}
```

---

## 🎨 Color Palette

### Core Colors (Required for all games)

```css
:root {
    /* Backgrounds */
    --bg-color: #f8f9fa;           /* Main background */
    --card-bg: #ffffff;            /* Card/panel backgrounds */
    
    /* Text */
    --text-color: #333333;         /* Primary text */
    --text-muted: #6b7280;         /* Secondary text */
    --text-light: #9ca3af;         /* Tertiary text */
    
    /* Borders */
    --border-color: #dee2e6;       /* Standard borders */
    --border-dark: #adb5bd;        /* Emphasized borders */
    
    /* Status Colors */
    --success-color: #22c55e;      /* Correct/win states */
    --error-color: #ef4444;        /* Error/wrong states */
    --warning-color: #f59e0b;      /* Hints/warnings */
    --info-color: #3b82f6;         /* Information */
    
    /* Accent Colors */
    --accent-primary: #3b82f6;     /* Primary actions */
    --accent-secondary: #8b5cf6;   /* Secondary actions */
    --gold-color: #eab308;         /* Achievements */
    
    /* Interactive States */
    --hover-bg: #e9ecef;           /* Hover backgrounds */
    --active-bg: #dee2e6;          /* Active/pressed */
    --disabled-bg: #f1f3f5;        /* Disabled elements */
}
```

### Game-Specific Accent Colors (Optional)

Each game can have its own accent to add personality:

```css
/* Hitori - Logic puzzle (blues/grays) */
--game-accent: #3b82f6;

/* Memory Match - Fun game (purples/pinks) */
--game-accent: #8b5cf6;

/* Sudoku - Classic puzzle (indigo) */
--game-accent: #6366f1;

/* Word games (greens) */
--game-accent: #10b981;

/* Math puzzles (oranges) */
--game-accent: #f59e0b;
```

### Color Usage Guidelines

| Element | Color Variable | Usage |
|---------|---------------|--------|
| Primary buttons | `--accent-primary` | Main actions (New Game, Submit) |
| Success messages | `--success-color` | Win states, correct answers |
| Error highlights | `--error-color` | Wrong moves, rule violations |
| Hint indicators | `--warning-color` | Hints, suggestions |
| Achievement badges | `--gold-color` | Trophy icons, unlocks |
| Background gradients | Game-specific | Optional decorative backgrounds |

---

## 🔤 Typography

### Font Stack

```css
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, 
             -apple-system, BlinkMacSystemFont, sans-serif;
```

### Font Sizes (Mobile-First)

```css
/* Headings */
--text-3xl: 1.875rem;  /* 30px - Game titles */
--text-2xl: 1.5rem;    /* 24px - Section headers */
--text-xl: 1.25rem;    /* 20px - Card titles */
--text-lg: 1.125rem;   /* 18px - Large body */

/* Body */
--text-base: 1rem;     /* 16px - Standard text */
--text-sm: 0.875rem;   /* 14px - Secondary text */
--text-xs: 0.75rem;    /* 12px - Captions */

/* Game Content */
--game-number: 2.5rem; /* 40px - Grid numbers (desktop) */
--game-number-mobile: 2rem; /* 32px - Grid numbers (mobile) */
```

### Font Weights

```css
--font-normal: 400;
--font-medium: 500;
--font-semibold: 600;
--font-bold: 700;
```

### Typography Scale Example

```css
/* Game Title (Topbar) */
h1 {
    font-size: 1.6rem;
    font-weight: 700;
    line-height: 1.2;
}

/* Section Headers */
h2 {
    font-size: 1.25rem;
    font-weight: 600;
    line-height: 1.3;
}

/* Card Titles */
h3 {
    font-size: 1.125rem;
    font-weight: 600;
    line-height: 1.4;
}

/* Body Text */
p {
    font-size: 1rem;
    line-height: 1.5;
}

/* Small Text */
.small {
    font-size: 0.875rem;
    line-height: 1.4;
}
```

---

## 🔘 Buttons & Interactive Elements

### Button Styles

```css
/* Base Button */
button {
    padding: 10px 16px;
    min-height: 44px;           /* iOS touch target minimum */
    border-radius: 10px;
    font-size: 1rem;
    font-weight: 600;
    border: 1px solid var(--border-color);
    background: white;
    cursor: pointer;
    transition: all 0.2s ease;
    touch-action: manipulation;
    -webkit-tap-highlight-color: transparent;
}

/* Primary Action */
.button-primary {
    background-color: var(--accent-primary);
    color: white;
    border: none;
}

/* Secondary Action */
.button-secondary {
    background-color: white;
    color: var(--text-color);
    border: 1px solid var(--border-color);
}

/* Success Action */
.button-success {
    background-color: var(--success-color);
    color: white;
    border: none;
}

/* Warning/Hint Action */
.button-warning {
    background-color: var(--warning-color);
    color: white;
    border: none;
}

/* Achievement/Trophy */
.button-trophy {
    background-color: var(--gold-color);
    color: white;
    border: none;
}

/* Danger Action */
.button-danger {
    background-color: var(--error-color);
    color: white;
    border: none;
}

/* Interactive States */
button:active {
    transform: scale(0.97);
}

button:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}
```

### Button Sizing

```css
/* Small */
.button-sm {
    padding: 6px 12px;
    min-height: 36px;
    font-size: 0.875rem;
}

/* Default */
.button-md {
    padding: 10px 16px;
    min-height: 44px;
    font-size: 1rem;
}

/* Large */
.button-lg {
    padding: 12px 20px;
    min-height: 52px;
    font-size: 1.125rem;
}
```

### Touch Target Guidelines

**Critical Rule: All interactive elements must be at least 44×44px**

```css
/* Minimum touch target */
.touch-target {
    min-width: 44px;
    min-height: 44px;
}

/* Recommended spacing between targets */
.button-group button {
    margin: 4px;  /* 8px total spacing */
}
```

---

## 🎴 Cards & Containers

### Card Styles

```css
/* Standard Card */
.card {
    background: white;
    border: 1px solid var(--border-color);
    border-radius: 12px;
    padding: 16px;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

/* Elevated Card */
.card-elevated {
    background: white;
    border: 1px solid var(--border-color);
    border-radius: 12px;
    padding: 20px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Game Board Container */
.game-container {
    background: white;
    border: 2px solid var(--border-dark);
    border-radius: 12px;
    padding: 16px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
```

### Border Radius Scale

```css
--radius-sm: 6px;      /* Small elements */
--radius-md: 10px;     /* Buttons, inputs */
--radius-lg: 12px;     /* Cards, containers */
--radius-xl: 16px;     /* Modals, overlays */
--radius-full: 9999px; /* Pills, badges */
```

### Spacing Scale

```css
--space-1: 4px;
--space-2: 8px;
--space-3: 12px;
--space-4: 16px;
--space-5: 20px;
--space-6: 24px;
--space-8: 32px;
--space-10: 40px;
```

---

## 🎮 Game-Specific Elements

### Grid-Based Games (Hitori, Sudoku, etc.)

```css
.game-grid {
    display: grid;
    gap: 2px;
    background-color: var(--border-dark);
    border: 2px solid var(--border-dark);
    border-radius: 12px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    touch-action: manipulation;
    user-select: none;
}

.grid-cell {
    background-color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
    font-weight: bold;
    cursor: pointer;
    width: 44px;
    height: 44px;
    transition: background-color 0.15s ease;
    touch-action: manipulation;
}

/* Mobile Responsive */
@media (max-width: 500px) {
    .grid-cell {
        width: 36px;
        height: 36px;
        font-size: 1rem;
    }
}

@media (max-width: 400px) {
    .grid-cell {
        width: 32px;
        height: 32px;
        font-size: 0.95rem;
    }
}

/* Cell States */
.grid-cell:active {
    background-color: var(--hover-bg);
}

.grid-cell.selected {
    background-color: var(--accent-primary);
    color: white;
}

.grid-cell.error {
    color: var(--error-color);
    font-weight: bold;
}

.grid-cell.hint {
    animation: hint-pulse 1s ease-out;
}

@keyframes hint-pulse {
    0% { background-color: var(--warning-color); }
    100% { background-color: white; }
}
```

### Card-Based Games (Memory Match, Solitaire, etc.)

```css
.game-card {
    aspect-ratio: 3/4;
    background: white;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    cursor: pointer;
    transition: transform 0.3s ease;
    user-select: none;
    touch-action: manipulation;
}

.game-card:active {
    transform: scale(0.95);
}

.game-card.flipped {
    transform: rotateY(180deg);
}

.game-card.matched {
    opacity: 0.6;
    pointer-events: none;
}
```

### Word/Tile Games

```css
.tile {
    min-width: 44px;
    min-height: 44px;
    padding: 8px;
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    font-size: 1.25rem;
    font-weight: 700;
    text-align: center;
    cursor: pointer;
    transition: all 0.2s ease;
    touch-action: manipulation;
}

.tile:active {
    transform: translateY(2px);
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.tile.selected {
    border-color: var(--accent-primary);
    background: var(--accent-primary);
    color: white;
}
```

---

## 📊 Status & Feedback

### Status Bar

```css
.status-bar {
    width: 100%;
    max-width: 980px;
    padding: 12px 16px;
    border-radius: 10px;
    font-weight: 600;
    text-align: center;
    margin-bottom: 16px;
}

.status-bar.info {
    background-color: rgba(59, 130, 246, 0.1);
    color: var(--info-color);
}

.status-bar.success {
    background-color: rgba(34, 197, 94, 0.1);
    color: var(--success-color);
}

.status-bar.error {
    background-color: rgba(239, 68, 68, 0.1);
    color: var(--error-color);
}

.status-bar.warning {
    background-color: rgba(245, 158, 11, 0.1);
    color: var(--warning-color);
}
```

### Stats Display

```css
.stat-item {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 6px 12px;
    background: rgba(255, 255, 255, 0.9);
    border-radius: 999px;
    font-weight: 600;
    font-size: 0.9rem;
}

.stat-icon {
    font-size: 1.1rem;
}

/* Example: Timer, Moves, Score */
.timer { color: var(--info-color); }
.moves { color: var(--warning-color); }
.score { color: var(--success-color); }
```

### Progress Indicators

```css
.progress-bar {
    width: 100%;
    height: 8px;
    background: var(--hover-bg);
    border-radius: 999px;
    overflow: hidden;
}

.progress-fill {
    height: 100%;
    background: linear-gradient(90deg, 
        var(--accent-primary), 
        var(--accent-secondary));
    transition: width 0.3s ease;
}
```

---

## 🏆 Achievement System Design

### Achievement Toast

```css
.toast {
    background: #333;
    color: white;
    padding: 12px 16px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    display: flex;
    align-items: center;
    gap: 10px;
    animation: slideIn 0.3s ease-out;
    max-width: 360px;
}

@keyframes slideIn {
    from {
        transform: translateX(100%);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

.toast-icon {
    font-size: 1.8rem;
    flex-shrink: 0;
}

.toast-content {
    flex: 1;
}

.toast-title {
    font-weight: 700;
    margin-bottom: 2px;
}

.toast-description {
    font-size: 0.875rem;
    opacity: 0.9;
}
```

### Achievement Card

```css
.achievement-card {
    display: flex;
    align-items: center;
    padding: 12px;
    border: 1px solid var(--border-color);
    border-radius: 10px;
    background: white;
    transition: all 0.3s ease;
}

.achievement-card.locked {
    opacity: 0.6;
    filter: grayscale(1);
}

.achievement-card.unlocked {
    background: linear-gradient(135deg, 
        rgba(34, 197, 94, 0.05), 
        rgba(34, 197, 94, 0.1));
    border-color: var(--success-color);
}

.achievement-icon {
    font-size: 2rem;
    margin-right: 12px;
    flex-shrink: 0;
}

.achievement-badge {
    margin-left: auto;
    font-size: 1.2rem;
}
```

---

## 🎭 Modals & Overlays

### Modal Structure

```css
.modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(4px);
    display: none;
    align-items: center;
    justify-content: center;
    padding: 16px;
    z-index: 1000;
    animation: fadeIn 0.2s ease-out;
}

.modal-overlay.open {
    display: flex;
}

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.modal {
    background: white;
    border-radius: 16px;
    width: 100%;
    max-width: 560px;
    max-height: 85vh;
    overflow-y: auto;
    box-shadow: 0 20px 25px rgba(0, 0, 0, 0.15);
    animation: slideUp 0.3s ease-out;
}

@keyframes slideUp {
    from {
        transform: translateY(20px);
        opacity: 0;
    }
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

.modal-header {
    padding: 16px 20px;
    border-bottom: 1px solid var(--border-color);
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.modal-title {
    font-size: 1.25rem;
    font-weight: 600;
    margin: 0;
}

.modal-body {
    padding: 20px;
}

.modal-footer {
    padding: 16px 20px;
    border-top: 1px solid var(--border-color);
    display: flex;
    gap: 10px;
    justify-content: flex-end;
}
```

---

## ✨ Animations & Transitions

### Standard Transitions

```css
/* Button interactions */
button {
    transition: all 0.2s ease;
}

/* Background changes */
.cell, .card, .tile {
    transition: background-color 0.15s ease;
}

/* Transform animations */
.interactive {
    transition: transform 0.2s ease;
}

/* Opacity fades */
.fade {
    transition: opacity 0.3s ease;
}
```

### Animation Timing

| Action | Duration | Easing |
|--------|----------|--------|
| Button press | 0.2s | ease |
| Color change | 0.15s | ease |
| Modal open | 0.3s | ease-out |
| Toast slide | 0.3s | ease-out |
| Card flip | 0.4s | ease-in-out |
| Hint pulse | 1s | ease-out |

### Reusable Animations

```css
/* Pulse (for hints) */
@keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.5; }
}

.pulse {
    animation: pulse 2s ease-in-out infinite;
}

/* Shake (for errors) */
@keyframes shake {
    0%, 100% { transform: translateX(0); }
    25% { transform: translateX(-5px); }
    75% { transform: translateX(5px); }
}

.shake {
    animation: shake 0.4s ease-in-out;
}

/* Bounce (for celebrations) */
@keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
}

.bounce {
    animation: bounce 0.6s ease-in-out;
}

/* Spin (for loading) */
@keyframes spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
}

.spin {
    animation: spin 1s linear infinite;
}
```

---

## 📱 Mobile-Specific Considerations

### Touch Optimization

```css
* {
    /* Remove tap highlight */
    -webkit-tap-highlight-color: transparent;
    
    /* Prevent text selection on game elements */
    -webkit-user-select: none;
    user-select: none;
    
    /* Optimize touch scrolling */
    -webkit-overflow-scrolling: touch;
}

/* Allow text selection for instructions */
.instructions, .modal-body {
    -webkit-user-select: text;
    user-select: text;
}

/* Prevent zoom on double-tap */
body {
    touch-action: manipulation;
}
```

### Viewport Settings

```html
<!-- Required in all game HTML files -->
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="mobile-web-app-capable" content="yes">
```

### Safe Area (Notches/Camera Cutouts)

```css
/* Respect device safe areas */
.topbar {
    padding-top: max(18px, env(safe-area-inset-top));
}

body {
    padding-left: env(safe-area-inset-left);
    padding-right: env(safe-area-inset-right);
    padding-bottom: env(safe-area-inset-bottom);
}
```

---

## 🎯 Accessibility Guidelines

### Color Contrast

- **Text on white**: Minimum contrast ratio 4.5:1
- **Large text (18px+)**: Minimum contrast ratio 3:1
- **Interactive elements**: Must be distinguishable when color-blind

### Focus States

```css
/* Keyboard navigation support */
button:focus-visible,
.cell:focus-visible {
    outline: 3px solid var(--accent-primary);
    outline-offset: 2px;
}

/* Don't show focus on touch */
button:focus:not(:focus-visible) {
    outline: none;
}
```

### ARIA Labels

```html
<!-- Grid cells -->
<div class="cell" role="button" aria-label="Cell 1, value 5" tabindex="0">
    5
</div>

<!-- Game status -->
<div class="status" role="status" aria-live="polite">
    Puzzle solved!
</div>

<!-- Modals -->
<div class="modal" role="dialog" aria-modal="true" aria-labelledby="modal-title">
    <h2 id="modal-title">Achievements</h2>
</div>
```

### Screen Reader Support

```css
/* Visually hidden but accessible */
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border-width: 0;
}
```

---

## 🎨 Background Styles

### Game-Specific Backgrounds

```css
/* Clean (default) */
body {
    background-color: var(--bg-color);
}

/* Gradient (for colorful games) */
body.gradient {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* Subtle Pattern */
body.pattern {
    background-color: var(--bg-color);
    background-image: 
        repeating-linear-gradient(45deg, 
            transparent, 
            transparent 10px, 
            rgba(0,0,0,.02) 10px, 
            rgba(0,0,0,.02) 20px);
}

/* Radial Glow (like hub) */
body.glow {
    background:
        radial-gradient(circle at 20% 20%, rgba(59, 130, 246, 0.15), transparent 50%),
        radial-gradient(circle at 80% 80%, rgba(139, 92, 246, 0.15), transparent 50%),
        var(--bg-color);
}
```

---

## 📋 Component Checklist

Every game should include:

### Required Elements:
- ✅ Topbar with game title
- ✅ Back to Hub button
- ✅ Achievement system integration
- ✅ Achievement count display (🏆 X/Y)
- ✅ Modal for viewing achievements
- ✅ Toast notifications for unlocks
- ✅ Status/feedback area
- ✅ Instructions section
- ✅ Mobile-optimized controls

### Recommended Elements:
- ⭐ Timer display
- ⭐ Move/action counter
- ⭐ Difficulty selector
- ⭐ New Game button
- ⭐ Hint system
- ⭐ Check/Validate button
- ⭐ Settings panel

### Optional Elements:
- 💡 Undo/Redo
- 💡 Save game progress
- 💡 Statistics tracking
- 💡 Daily challenge
- 💡 Leaderboard
- 💡 Dark mode toggle

---

## 🔨 Implementation Template

### Minimal Game Starter

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>My Game</title>
    <style>
        /* Copy color palette from above */
        :root {
            --bg-color: #f8f9fa;
            --text-color: #333;
            --accent-primary: #3b82f6;
            /* ... rest of colors ... */
        }
        
        /* Copy base styles */
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body { font-family: 'Segoe UI', sans-serif; /* ... */ }
        button { /* Copy button styles */ }
        
        /* Your game-specific styles here */
    </style>
</head>
<body>
    <!-- Topbar -->
    <div class="topbar">
        <h1 id="gameTitle">My Game</h1>
        <div class="header-stats">
            <span id="ach-count">🏆 0/3</span>
            <button id="backBtn">← Hub</button>
        </div>
    </div>
    
    <!-- Controls -->
    <div class="controls">
        <button class="button-primary" onclick="game.newGame()">New Game</button>
        <button class="button-trophy" onclick="achievements.toggleModal()">🏆</button>
    </div>
    
    <!-- Status -->
    <div class="status" id="status">Ready to play!</div>
    
    <!-- Game Area -->
    <div id="gameArea" class="game-container">
        <!-- Your game interface here -->
    </div>
    
    <!-- Instructions -->
    <div class="instructions">
        <h3>How to Play</h3>
        <ul>
            <li>Rule 1</li>
            <li>Rule 2</li>
        </ul>
    </div>
    
    <!-- Achievement Modal -->
    <div class="modal-overlay" id="achModal">
        <div class="modal">
            <div class="modal-header">
                <h2>Achievements</h2>
                <button onclick="achievements.toggleModal()">Close</button>
            </div>
            <div class="modal-body" id="achList"></div>
        </div>
    </div>
    
    <!-- Toast Container -->
    <div class="toast-container" id="toastContainer"></div>
    
    <script>
        // Hub integration
        const params = new URLSearchParams(location.search);
        const GAME_ID = params.get('gameId') || 'my_game';
        const RETURN_TO = params.get('return') || '../index.html';
        
        document.getElementById('backBtn').onclick = () => {
            location.href = RETURN_TO;
        };
        
        // Achievement system (copy from template.html)
        class AchievementSystem { /* ... */ }
        
        // Your game logic here
        class MyGame { /* ... */ }
        
        const achievements = new AchievementSystem(GAME_ID);
        const game = new MyGame();
    </script>
</body>
</html>
```

---

## 🎨 Design Examples by Game Type

### Logic Puzzles (Hitori, Sudoku, Nonograms)
- **Colors**: Blues and grays (calm, focused)
- **Background**: Clean white or subtle pattern
- **Emphasis**: Grid clarity, number readability
- **Interactions**: Tap to cycle states

### Memory/Matching Games
- **Colors**: Bright, cheerful (purples, pinks, greens)
- **Background**: Gradient or colorful
- **Emphasis**: Card animations, smooth flips
- **Interactions**: Tap to reveal

### Word Games
- **Colors**: Warm tones (oranges, yellows, greens)
- **Background**: Textured or patterned
- **Emphasis**: Large, clear letters
- **Interactions**: Tap to select, drag optional

### Number/Math Games
- **Colors**: Oranges and blues (energetic but focused)
- **Background**: Clean with subtle accents
- **Emphasis**: Clear number display
- **Interactions**: Tap to input, calculator-style

### Strategy Games (Chess, Checkers)
- **Colors**: Classic (blacks, browns, golds)
- **Background**: Rich, elegant
- **Emphasis**: Board clarity, piece visibility
- **Interactions**: Drag-and-drop or tap-to-move

---

## 📚 Quick Reference

### Color Quick Copy
```css
--success: #22c55e;  --error: #ef4444;   --warning: #f59e0b;
--info: #3b82f6;     --gold: #eab308;    --purple: #8b5cf6;
```

### Spacing Quick Copy
```css
4px  8px  12px  16px  20px  24px  32px  40px
```

### Touch Target Sizes
```
Minimum: 44×44px | Recommended: 48×48px | Comfortable: 56×56px
```

### Font Sizes
```
xs:12px  sm:14px  base:16px  lg:18px  xl:20px  2xl:24px  3xl:30px
```

---

## 🚀 Getting Started

1. **Copy** `games/template.html` to start your game
2. **Apply** the color palette from this document
3. **Follow** the layout structure
4. **Use** the button and card styles
5. **Test** on mobile (44px touch targets!)
6. **Verify** accessibility (focus states, ARIA)

---

## 📝 Design Principles Summary

1. **Mobile-First**: Design for touch, scale up for desktop
2. **Consistent**: Use the shared color palette and components
3. **Accessible**: 4.5:1 contrast, 44px touch targets, ARIA labels
4. **Performant**: Smooth animations, no janky interactions
5. **Delightful**: Personality through game-specific accents
6. **Clear**: Obvious feedback, readable text, intuitive controls

---

**Questions or need help?** Check out the existing games (hitori.html, memory-match.html) for real-world examples of these patterns in action!
