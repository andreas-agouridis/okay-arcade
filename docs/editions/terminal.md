# Terminal Edition Documentation

**A unique CLI-style gaming experience in the browser.**

---

## Overview

The Terminal Edition is a **unique, command-line interface style** arcade that provides:

- Terminal/console aesthetic
- Command-based navigation
- Text-based game listing
- Keyboard-first interaction
- Dark terminal theme
- Minimal visual design
- Fun, geeky experience

---

## When to Use Terminal Edition

Choose Terminal Edition when you want:
- **Unique aesthetic** - Stands out from typical gaming sites
- **Keyboard power users** - Fast command navigation
- **Minimal design** - No visual clutter
- **Developer audience** - Appeals to tech-savvy users
- **Educational** - Demonstrates CLI concepts
- **Fun factor** - Novel gaming experience

---

## Features

- Text-based game listing
- Command input system
- Search via command
- Filter by category
- Favorites management
- Statistics display
- Help system
- Quick action buttons

---

## Available Commands

| Command | Alias | Description |
|---------|-------|-------------|
| `list` | `ls` | Show all games |
| `play [id/name]` | - | Play a game |
| `random` | `r` | Play random game |
| `search [term]` | - | Search games |
| `fav` | `favorites` | Show favorites |
| `addfav [id/name]` | - | Add to favorites |
| `rmfav [id/name]` | - | Remove from favorites |
| `filter [category]` | - | Filter games |
| `stats` | `status` | Show statistics |
| `clear` | `cls` | Clear screen |
| `help` | `?` | Show help |
| `exit` | `quit` | Clear and reset |

---

## Game Data

Located around line 163:

```javascript
const GAMES = [
    { 
        id: 1,
        name: "Game Name", 
        embedUrl: "https://...", 
        category: "Category",
        plays: 1234  // Play count (unique to terminal)
    }
];
```

### Differences from Other Editions
- Has `id` field (number)
- Has `plays` field (play count tracking)

---

## Command Examples

### List All Games
```
> list
```

### Play a Game by ID
```
> play 3
> play 5
```

### Play a Game by Name
```
> play neon
> play basketball
```

### Search Games
```
> search racing
> search action
```

### Filter by Category
```
> filter action
> filter racing
> filter puzzle
> filter sports
> filter all
```

### Manage Favorites
```
> addfav 3
> addfav neon
> rmfav 3
> fav
```

### View Statistics
```
> stats
```

### Clear Screen
```
> clear
```

### Get Help
```
> help
```

---

## JavaScript Architecture

### State
```javascript
let favorites = JSON.parse(localStorage.getItem('okay_cli_favs') || '[]');
let currentFilter = 'all';
let searchQuery = '';
```

### Key Functions

| Function | Purpose |
|----------|---------|
| `processCommand()` | Parse and execute commands |
| `displayGames()` | Show game list |
| `playGameById()` | Play game by ID |
| `playGameByName()` | Play game by name |
| `launchGame()` | Open game in new tab |
| `randomGame()` | Random game selection |
| `addFavorite()` | Add to favorites |
| `removeFavorite()` | Remove from favorites |
| `showFavorites()` | Display favorites |
| `showStats()` | Show statistics |
| `setFilter()` | Filter by category |
| `searchGames()` | Search games |
| `write()` | Output to terminal |

---

## Output Styling

### Text Types
```javascript
write('message', 'normal');    // Gray
write('success', 'success');   // Green
write('info', 'info');         // Blue
write('warning', 'warning');   // Yellow
write('error', 'error');       // Red
```

---

## Customization

### Change Site Name
Find "OKAY ARCADE" in the terminal header (line 117-118).

### Change Colors
Edit CSS variables in `<style>`:
```css
body {
    color: #00ff9d;      /* Main text color */
}
.prompt::before {
    color: #569cd6;      /* Prompt color */
}
```

### Add Games
Edit the `GAMES` array (line 163).

### Add Categories
Update the `valid` array in `setFilter`:
```javascript
const valid = ['all', 'action', 'racing', 'puzzle', 'sports', 'newcategory'];
```

---

## Statistics Display

The stats command shows:
- Total games available
- Favorites count
- Games by category
- Most played game
- Play counts (local)

---

## Quick Action Buttons

| Button | Action |
|--------|--------|
| LIST | `list` command |
| RANDOM | `random` command |
| FAVS | `fav` command |
| STATS | `stats` command |
| CLEAR | `clear` command |

---

## Game Display Format

```
[01] ⭐ Game Name               [Category]  1234 plays
[02] ☆ Another Game             [Action]    567 plays
```

- `⭐` = Favorite
- `☆` = Not favorite
- ID padded to 2 digits

---

## LocalStorage

| Key | Purpose |
|-----|---------|
| `okay_cli_favs` | Array of favorite game IDs |

---

## Browser Behavior

Games open in **new tabs/windows** because:
- Terminal is text-based
- No modal overlay needed
- Returns to terminal when tab closed
- Better for CLI experience

---

## CSS Structure

```css
/* Container */
.console { ... }
.console-header { ... }
.console-content { ... }

/* Input */
.command-input { ... }

/* Output */
.game-item { ... }
.prompt { ... }
.help-text { ... }
.success { ... }
.info { ... }
.warning { ... }
.stats { ... }

/* Buttons */
button { ... }
```

---

## Customization Ideas

### Add ASCII Art
```javascript
write('''
   /\\___/\\
  ( o   o )
  (  =^=  )
   (      )
    (    )
     \\  /
      \\/
''', 'success');
```

### Add EASTER EGG Commands
```javascript
if (action === 'matrix') {
    write('Follow the white rabbit...', 'success');
    // Add fun response
}
```

### Add Command History
```javascript
let commandHistory = [];
let historyIndex = -1;

// Save command
commandHistory.push(cmd);

// Navigate with arrow keys
document.addEventListener('keydown', (e) => {
    if (e.key === 'ArrowUp') {
        // Show previous command
    }
});
```

---

## Responsive Design

The terminal adapts to mobile:
- Smaller font sizes
- Touch-friendly buttons
- Scrollable output area

---

## Next Steps

- **[Main Edition](main.md)** - See full GUI version
- **[Simple UI](simple.md)** - See minimal version
- **[Adding Games](../customization/adding-games.md)** - Add your games
- **[Branding Guide](../customization/branding.md)** - Customize

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
