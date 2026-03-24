# Main Edition Documentation

**The full-featured Okay Arcade with all bells and whistles.**

---

## Overview

The Main Edition is the **flagship version** of Okay Arcade, featuring:

- Beautiful glassmorphism UI
- Dark/Light theme toggle
- Advanced search and filtering
- Favorites system with localStorage
- Game modal with fullscreen support
- Offline detection and handling
- Toast notifications
- Scroll-to-top button
- Responsive design
- SEO optimized
- Service Worker support

---

## Features Breakdown

### Navigation
- Sticky navbar with glass effect
- Logo with icon
- Navigation links (Home, Popular, Favorites)
- Random game button
- Theme toggle (dark/light)
- Mobile hamburger menu

### Hero Section
- Animated floating shapes background
- Hero badge with call-to-action
- Animated title
- Full-width search bar
- Category filter buttons
- Statistics cards (games, players, availability, cost)

### Game Grid
- Responsive grid layout
- Three view modes (grid, large, compact)
- Sort functionality
- Hover effects with overlay
- Play button
- Favorite star button
- Category badges
- Rating display

### Game Modal
- Fullscreen game embed
- Game title and category display
- Favorite toggle
- Fullscreen button
- Close button
- Click-outside to close

### Legal Pages (Modal)
- Privacy Policy
- Terms of Service
- Contact Us
- About Us
- FAQ

### Offline Features
- Offline detection
- Offline page with tips
- Auto-reconnect
- Status indicator
- Cookie-based offline tracking

### Additional Features
- Toast notifications (success, error, info)
- Scroll-to-top button
- Loading spinner
- Keyboard shortcuts (Escape to close)
- LocalStorage for favorites and theme

---

## File Structure

The Main Edition is a **single HTML file** containing:

```
index.html
├── <head>
│   ├── Meta tags (SEO, Open Graph, Twitter)
│   ├── Favicon (inline SVG)
│   ├── Font Awesome CDN
│   ├── Manifest link
│   └── <style> (all CSS inline)
├── <body>
│   ├── Navigation
│   ├── Hero Section
│   ├── Main Content (game grid)
│   ├── Game Modal
│   ├── Page Modal
│   ├── Toast Container
│   ├── Scroll to Top
│   ├── Footer
│   ├── Offline Page
│   └── <script> (all JavaScript inline)
└── Service Worker (sw.js - optional)
```

---

## JavaScript Architecture

### Game Data (Line 2450)
```javascript
const games = [
    {
        name: "Game Name",
        embedUrl: "https://...",
        imageUrl: "https://...",
        category: "Category"
    }
];
```

### State Management
```javascript
let favorites = JSON.parse(localStorage.getItem('favorites') || '[]');
let currentCategory = 'all';
let currentView = 'grid';
let currentSort = 'name';
let isDarkMode = true;
```

### Core Functions

| Function | Purpose |
|----------|---------|
| `init()` | Initialize the application |
| `renderGames()` | Render game cards to grid |
| `openGame()` | Open game in modal |
| `closeGame()` | Close game modal |
| `toggleFavorite()` | Add/remove favorite |
| `getFilteredGames()` | Filter by category/search |
| `showToast()` | Display notification |
| `openRandomGame()` | Play random game |
| `toggleTheme()` | Switch dark/light mode |
| `setView()` | Change grid layout |

---

## CSS Architecture

### CSS Variables (Lines 61-77)
All colors defined as CSS custom properties for easy theming.

### Component Styles
- Navigation
- Hero section
- Game cards
- Modals
- Toast notifications
- Footer
- Offline page

### Utility Classes
- `.glass-card` - Glassmorphism effect
- `.animate-in` - Entrance animation
- `.tooltip` - Tooltip on hover
- `.badge` - Status badges

---

## Customization Points

### Change Site Name
1. Title (line 8)
2. Logo text (line 2244)
3. Footer logo (line 2380)
4. Structured data (line 38)

### Add Games
Edit the `games` array (around line 2450).

### Add Categories
1. Add button to categories div (line 2283)
2. Use category in game objects

### Change Colors
Edit CSS variables (line 61-77).

### Update Legal Content
Edit `pageContent` object (line 2855).

### Update Footer
Edit footer section (line 2377).

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Escape` | Close modals |

---

## LocalStorage Keys

| Key | Purpose |
|-----|---------|
| `favorites` | Array of favorite game names |
| `darkMode` | Boolean for theme preference |
| `okay_arcade_offline` | Offline status cookie |

---

## Browser Support

| Browser | Support |
|---------|---------|
| Chrome | Full |
| Firefox | Full |
| Safari | Full |
| Edge | Full |
| Opera | Full |
| IE 11 | Partial (no glassmorphism) |

---

## Performance

### Optimization Techniques
1. **Lazy loading images**: `loading="lazy"`
2. **CSS animations**: Hardware-accelerated
3. **Event delegation**: Minimal event listeners
4. **LocalStorage**: Fast data access
5. **No external dependencies**: Only Font Awesome CDN

### File Size
- HTML: ~3400 lines
- CSS: ~1500 lines
- JavaScript: ~1000 lines
- Total: Single file, no external CSS/JS

---

## Common Modifications

### Remove Stats Section
Delete the `.stats-grid` div (lines 2293-2315).

### Remove Footer Sections
Delete unwanted `.footer-section` divs.

### Add Custom CSS
Add to the `<style>` section or create a new CSS file and link it.

### Add Custom JavaScript
Add to the `<script>` section or create a new JS file and link it before `</body>`.

---

## Troubleshooting

### Games Not Loading
- Check embed URLs are valid HTTPS
- Test URLs directly in browser
- Check console for errors

### Modal Not Opening
- Verify game data structure
- Check JavaScript console
- Ensure click events are attached

### Favorites Not Saving
- Check localStorage is enabled
- Verify no private browsing mode
- Check browser storage limits

### Offline Page Shows
- Normal on `file://` protocol
- Use local server for testing
- Check network connection

---

## Next Steps

- **[Simple UI Edition](simple.md)** - See alternative design
- **[Adding Games Guide](../customization/adding-games.md)** - Add your games
- **[Branding Guide](../customization/branding.md)** - Customize appearance
- **[Deployment Guide](../deployment.md)** - Deploy to production

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
