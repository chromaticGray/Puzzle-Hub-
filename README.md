# Puzzle Hub - Mobile-Friendly Game Collection

A beautiful, mobile-optimized hub for managing and playing logic puzzle games on Android.

## 📱 Features

- **Mobile-First Design**: Optimized for touch controls on Android phones
- **Game Management**: Browse, search, filter, and favorite your puzzle games
- **Achievement System**: Track progress with per-game achievements stored in localStorage
- **Offline Ready**: Works without internet once loaded
- **Easy to Extend**: Just add HTML files and update games.json

## 📂 Folder Structure

```
puzzle-hub/
├── index.html          # Main hub interface
├── games.json          # Game configuration file
└── games/              # Individual game HTML files
    └── hitori.html     # Example: Hitori puzzle game
```

## 🚀 Setup Instructions

### Option 1: Using a Simple Web Server (Recommended)

1. **Install Python** (if not already installed)
   - Most Android devices: Install Termux from F-Droid or Google Play
   - In Termux: `pkg install python`

2. **Navigate to the puzzle-hub folder**
   ```bash
   cd /path/to/puzzle-hub
   ```

3. **Start the server**
   ```bash
   python -m http.server 8000
   ```

4. **Open in your browser**
   - Navigate to: `http://localhost:8000`
   - Or use your device's IP address from other devices: `http://192.168.1.X:8000`

### Option 2: Using File Manager Apps (Simpler, Limited)

1. **Install a File Manager** (e.g., Solid Explorer, Total Commander)
2. **Copy puzzle-hub folder** to your device's storage
3. **Open index.html** with Chrome or Firefox
   - Note: Some features may not work when opening files directly (CORS restrictions)

### Option 3: Using Hosting Services (Best for Long-Term)

Upload the entire `puzzle-hub` folder to:
- **GitHub Pages** (free, easy)
- **Netlify** (free, drag-and-drop)
- **Vercel** (free, automatic deployment)

## 🎮 Adding New Games

### Step 1: Create Your Game HTML File

Create a new HTML file in the `games/` folder (e.g., `sudoku.html`):

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Your Game</title>
</head>
<body>
    <h1 id="gameTitle">Your Game Name</h1>
    <button id="backBtn">← Back to Hub</button>
    
    <!-- Your game content here -->
    
    <script>
        // Hub integration
        const params = new URLSearchParams(location.search);
        const GAME_ID = params.get('gameId') || 'your_game';
        const RETURN_TO = params.get('return') || '../index.html';
        
        document.getElementById('gameTitle').textContent = 'Your Game';
        document.getElementById('backBtn').addEventListener('click', () => {
            location.href = RETURN_TO;
        });
        
        // Your game logic here
    </script>
</body>
</html>
```

### Step 2: Update games.json

Add your game entry to the JSON file:

```json
{
  "id": "sudoku",
  "name": "Sudoku",
  "file": "sudoku.html",
  "image": "",
  "description": "Fill the grid so each row, column, and 3×3 box contains 1-9.",
  "difficultyRating": 4,
  "isFavorite": false,
  "rules": [
    "Each row must contain numbers 1-9 without repetition.",
    "Each column must contain numbers 1-9 without repetition.",
    "Each 3×3 box must contain numbers 1-9 without repetition."
  ],
  "achievements": [
    { "id": "first_solve", "title": "First Solve", "description": "Complete your first puzzle", "unlocked": false },
    { "id": "speed_solver", "title": "Speed Solver", "description": "Solve in under 5 minutes", "unlocked": false }
  ]
}
```

### Step 3: Test Your Game

1. Refresh the hub (`index.html`)
2. Your new game should appear in the grid
3. Click "Open Game" to test it

## 🏆 Achievement System

Games can track and unlock achievements using localStorage:

```javascript
// In your game file
class AchievementSystem {
    constructor(gameId) {
        this.gameId = gameId;
        this.storageKey = `ach_${this.gameId}`;
        this.unlocked = this.loadUnlocked();
    }
    
    loadUnlocked() {
        try {
            const raw = localStorage.getItem(this.storageKey);
            return raw ? JSON.parse(raw) : [];
        } catch {
            return [];
        }
    }
    
    saveUnlocked() {
        localStorage.setItem(this.storageKey, JSON.stringify(this.unlocked));
    }
    
    unlock(achievementId) {
        if (!this.unlocked.includes(achievementId)) {
            this.unlocked.push(achievementId);
            this.saveUnlocked();
            // Show notification
            this.showToast(achievementId);
        }
    }
}

const achievements = new AchievementSystem(GAME_ID);
```

## 🎨 games.json Schema

```json
{
  "id": "string (unique identifier, lowercase, no spaces)",
  "name": "string (display name)",
  "file": "string (HTML filename in games/ folder)",
  "image": "string (optional: path to cover image)",
  "description": "string (brief description)",
  "difficultyRating": number (1-5, where 5 is hardest),
  "isFavorite": boolean (default favorite status),
  "rules": ["string", "string", "..."],
  "achievements": [
    {
      "id": "string (unique per game)",
      "title": "string",
      "description": "string",
      "unlocked": boolean (starting state, overridden by localStorage)
    }
  ]
}
```

## 📱 Mobile Tips

1. **Add to Home Screen**: 
   - Chrome: Menu → "Add to Home Screen"
   - Firefox: Menu → "Install"

2. **Full Screen Mode**: Most games hide the address bar when scrolling

3. **Touch Controls**: All buttons are sized for easy tapping (44px minimum)

4. **Performance**: Games run entirely client-side (no server needed after loading)

## 🔧 Troubleshooting

### Games.json won't load
- **File protocol**: Use a web server instead of opening files directly
- **CORS error**: Start a local server with Python or use a hosting service

### Achievements not saving
- **localStorage disabled**: Check browser privacy settings
- **Incognito mode**: Achievements won't persist in private browsing

### Back button doesn't work
- **URL parameters**: Ensure the hub passes `?gameId=X&return=../index.html`

### Mobile controls feel unresponsive
- **Touch delay**: Make sure `-webkit-tap-highlight-color: transparent` is set
- **Viewport**: Include `<meta name="viewport" content="width=device-width, initial-scale=1.0">`

## 🎯 Example: Complete Game Template

See `games/hitori.html` for a fully-featured example including:
- Hub integration (back button, gameId)
- Achievement system with notifications
- Mobile-optimized touch controls
- Timer and statistics tracking
- Modal dialogs
- Responsive grid layout

## 📝 License

This puzzle hub is free to use and modify for personal projects.

## 🙏 Contributing

To add your own puzzle games:
1. Create HTML file in `games/`
2. Add entry to `games.json`
3. Test on mobile
4. Enjoy!

---

**Enjoy your puzzle collection!** 🧩
