# Simple UI Edition Documentation

**A clean, minimal gaming arcade with focus on simplicity.**

---

## Overview

The Simple UI Edition is a **lightweight alternative** to the Main Edition, featuring:

- Clean, minimal design
- Light theme (white/gray)
- Simplified game cards
- Compact search and filters
- Basic modal system
- Essential features only
- Smaller file size (~840 lines vs ~3400)

---

## When to Use Simple UI

Choose Simple UI when you want:
- **Fast loading** - Minimal code, quick render
- **Clean aesthetic** - No visual clutter
- **Mobile-first** - Optimized for small screens
- **Easy customization** - Simple HTML structure
- **Focus on games** - UI doesn't distract

---

## Features Comparison

| Feature | Main Edition | Simple UI |
|---------|--------------|-----------|
| Dark/Light theme | Both | Light only |
| Animations | Heavy | Minimal |
| Glassmorphism | Yes | No |
| Game modal | Advanced | Basic |
| Favorites | Yes | Yes |
| Search | Yes | Yes |
| Categories | Yes | Yes |
| Legal pages | Modal | Modal |
| Offline page | Yes | No |
| Toast | Advanced | Simple |
| File size | ~50KB | ~20KB |

---

## File Structure

```
simpleui(edition).html
├── <head>
│   ├── Meta tags
│   └── <style> (minimal CSS)
└── <body>
    ├── Header (logo + nav buttons)
    ├── Hero (minimal)
    ├── Search + Filters
    ├── Game Grid
    ├── Game Modal
    ├── Page Modal
    ├── Toast
    └── Footer
```

---

## Game Data

Located around line 546:

```javascript
const GAMES = [
    { 
        name: "Game Name", 
        embedUrl: "https://...", 
        imageUrl: "https://...", 
        category: "Category" 
    }
];
```

---

## Key Differences from Main Edition

### CSS
- No CSS variables
- No glassmorphism
- Simple white/gray theme
- Minimal animations
- Responsive grid only

### JavaScript
- Simpler state management
- No offline detection
- Basic toast (text only)
- Favorites via localStorage
- Categories as filter chips

### HTML
- Shorter, cleaner structure
- No complex hero section
- No stats cards
- Minimal footer

---

## Customization

### Change Site Name
Find and replace "Okay Arcade" in:
- Title tag
- Logo text
- Footer

### Change Colors
Edit CSS directly (around line 8):
```css
.logo {
    background: linear-gradient(135deg, #2563eb, #0891b2);
}
.btn-primary {
    background: #2563eb;
}
.filter-chip.active {
    background: #2563eb;
}
```

### Add Games
Edit the `GAMES` array (around line 546).

### Add Categories
Add filter buttons (around line 496):
```html
<button data-cat="NewCategory" class="filter-chip">New Category</button>
```

---

## JavaScript Functions

| Function | Purpose |
|----------|---------|
| `renderGames()` | Render game cards |
| `openGameModal()` | Open game |
| `closeGameModal()` | Close game |
| `toggleFavorite()` | Manage favorites |
| `getFilteredGames()` | Filter games |
| `showToast()` | Show notification |
| `randomGame()` | Play random game |
| `showInfoModal()` | Show legal pages |

---

## LocalStorage

| Key | Purpose |
|-----|---------|
| `okay_favs` | Favorite game names array |

---

## CSS Structure

```css
/* Layout */
.container { ... }
.header { ... }
.hero-mini { ... }

/* Components */
.search-wrapper { ... }
.filter-chip { ... }
.game-card { ... }
.play-btn { ... }
.modal { ... }
.page-modal { ... }
.toast-simple { ... }

/* Responsive */
@media (max-width: 600px) { ... }
```

---

## Mobile Responsiveness

The Simple UI is optimized for mobile:
- 2-column grid on mobile (line 454)
- Stacked filters
- Touch-friendly buttons
- Simplified header

---

## Adding Features

### Add Dark Mode
1. Add toggle button to header
2. Add CSS for dark mode
3. Add toggle JavaScript

### Add Statistics
Add stat badge (already exists):
```html
<div class="stat-badge">
    <i class="fas fa-gamepad"></i> 
    <span id="gameCount">0</span> games
</div>
```

### Add More Legal Pages
Edit the `showInfoModal` function and add content variables.

---

## Minimal CSS Variables (Optional)

If you want to add variables:
```css
:root {
    --primary: #2563eb;
    --accent: #0891b2;
}

.logo {
    background: linear-gradient(135deg, var(--primary), var(--accent));
}
```

---

## File Size Optimization

The Simple UI is already optimized:
- No external CSS (except Font Awesome)
- No external JavaScript
- Minimal HTML structure
- Efficient CSS selectors

---

## Common Customizations

### Remove Filter Section
Delete the `.filters` div (around line 495).

### Remove Legal Pages
Delete the page modal HTML and related JavaScript.

### Add Custom Font
Add to `<head>`:
```html
<link href="https://fonts.googleapis.com/css2?family=Inter&display=swap" rel="stylesheet">
```
Add to CSS:
```css
body {
    font-family: 'Inter', sans-serif;
}
```

---

## Next Steps

- **[Main Edition](main.md)** - See full-featured version
- **[Terminal Edition](terminal.md)** - See CLI version
- **[Branding Guide](../customization/branding.md)** - Customize
- **[Adding Games](../customization/adding-games.md)** - Add games

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
