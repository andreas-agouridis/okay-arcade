# Theme Customization Guide

**Customize the look and feel of Okay Arcade.**

---

## Theme Overview

Okay Arcade supports:
- **Dark Mode** (default)
- **Light Mode** (toggle available)
- **Custom color schemes**
- **Custom backgrounds**

---

## Dark/Light Mode Toggle

### How It Works
Users can toggle between dark and light modes using the theme button in the navigation bar. The preference is saved to localStorage.

### Toggle Button Location
```html
<button class="theme-toggle" id="themeToggle" title="Toggle Theme">
    <i class="fas fa-moon"></i>
</button>
```

### JavaScript Logic (line 2834-2839)
```javascript
function toggleTheme() {
    isDarkMode = !isDarkMode;
    document.body.classList.toggle('light-mode', !isDarkMode);
    themeToggle.innerHTML = `<i class="fas fa-${isDarkMode ? 'moon' : 'sun'}"></i>`;
    localStorage.setItem('darkMode', isDarkMode);
}
```

---

## Color Variables

### Location
Find CSS variables in the `:root` selector (lines 61-77):

```css
:root {
    --primary: #6c5ce7;           /* Main brand color */
    --primary-dark: #5a4d1;       /* Darker shade */
    --secondary: #a29bfe;         /* Secondary/accent text */
    --dark: #2d3436;              /* Dark mode text */
    --dark-2: #1e1e2e;            /* Dark backgrounds */
    --light: #f9f9f9;             /* Light mode text */
    --accent: #00cec9;            /* Accent/highlight color */
    --accent-dark: #00b5b0;       /* Darker accent */
    --gradient: linear-gradient(135deg, #6c5ce7, #00cec9);
}
```

### Creating Your Own Color Scheme

#### Step 1: Choose Colors
Pick 2-3 colors that work well together:

- **Primary**: Your main brand color
- **Accent**: A complementary color for highlights
- **Gradient**: Combination of both

#### Step 2: Update Variables
```css
:root {
    --primary: #your-color;
    --primary-dark: #darker-shade;
    --secondary: #lighter-shade;
    --accent: #accent-color;
    --gradient: linear-gradient(135deg, #primary, #accent);
}
```

---

## Color Scheme Examples

### Cyberpunk Theme
```css
:root {
    --primary: #ff00ff;
    --primary-dark: #cc00cc;
    --secondary: #ff66ff;
    --accent: #00ffff;
    --gradient: linear-gradient(135deg, #ff00ff, #00ffff);
}

body {
    background: linear-gradient(135deg, #0a0a0a, #1a0a1a, #0a1a1a);
}
```

### Sunset Theme
```css
:root {
    --primary: #ff6b6b;
    --primary-dark: #ee5a5a;
    --secondary: #ffa502;
    --accent: #ffdd59;
    --gradient: linear-gradient(135deg, #ff6b6b, #ffa502);
}

body {
    background: linear-gradient(135deg, #2d1f3d, #1a1a2e, #16213e);
}
```

### Ocean Theme
```css
:root {
    --primary: #0984e3;
    --primary-dark: #0770c2;
    --secondary: #74b9ff;
    --accent: #00cec9;
    --gradient: linear-gradient(135deg, #0984e3, #00cec9);
}

body {
    background: linear-gradient(135deg, #0c1929, #0a2647, #144272);
}
```

### Forest Theme
```css
:root {
    --primary: #00b894;
    --primary-dark: #00a381;
    --secondary: #55efc4;
    --accent: #ffeaa7;
    --gradient: linear-gradient(135deg, #00b894, #55efc4);
}

body {
    background: linear-gradient(135deg, #0d1f0d, #1a2f1a, #0f2f1f);
}
```

### Monochrome Theme
```css
:root {
    --primary: #636e72;
    --primary-dark: #4a5568;
    --secondary: #b2bec3;
    --accent: #dfe6e9;
    --gradient: linear-gradient(135deg, #636e72, #b2bec3);
}

body {
    background: linear-gradient(135deg, #1a1a1a, #2d2d2d, #1a1a1a);
}
```

---

## Customizing Dark Mode

### Dark Mode Background (line 320)
```css
body {
    background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
}
```

### Custom Dark Mode Example
```css
body {
    background: linear-gradient(135deg, #0a0a0a, #1a1a2e, #16213e);
}
```

### Dark Mode Navbar (line 333)
```css
.navbar {
    background: rgba(15, 12, 41, 0.95);
}
```

### Dark Mode Cards (line 781)
```css
.game-card {
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
}
```

---

## Customizing Light Mode

### Light Mode Background (line 328)
```css
body.light-mode {
    background: linear-gradient(135deg, #667eea, #764ba2);
}
```

### Custom Light Mode
```css
body.light-mode {
    background: linear-gradient(135deg, #f5f7fa, #c3cfe2);
}

body.light-mode .navbar {
    background: rgba(255, 255, 255, 0.95);
}

body.light-mode .game-card {
    background: rgba(255, 255, 255, 0.95);
    border: 1px solid rgba(0, 0, 0, 0.1);
}
```

---

## Gradient Customization

### Main Gradient
Used for buttons, badges, and highlights:

```css
--gradient: linear-gradient(135deg, #6c5ce7, #00cec9);
```

### Gradient Variations

**Horizontal:**
```css
linear-gradient(90deg, #color1, #color2)
```

**Vertical:**
```css
linear-gradient(180deg, #color1, #color2)
```

**Radial:**
```css
radial-gradient(circle, #color1, #color2)
```

**Multi-color:**
```css
linear-gradient(135deg, #color1, #color2, #color3)
```

---

## Card Styling

### Game Card Styles (line 780)
```css
.game-card {
    background: rgba(255, 255, 255, 0.05);
    border-radius: 20px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    transition: all 0.4s;
}
```

### Glassmorphism Effect
```css
.game-card {
    background: rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 20px;
}
```

### Flat Design
```css
.game-card {
    background: #2d3436;
    border: none;
    border-radius: 12px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
```

### Neumorphism
```css
.game-card {
    background: #2d3436;
    border-radius: 20px;
    box-shadow: 8px 8px 16px #1a1a1a, -8px -8px 16px #3d3d3d;
}
```

---

## Button Styling

### Primary Button
```css
.btn-primary, .game-play-btn {
    background: var(--gradient);
    border-radius: 30px;
    padding: 12px 24px;
}
```

### Pill Button
```css
.game-play-btn {
    border-radius: 50px;
}
```

### Rounded Button
```css
.game-play-btn {
    border-radius: 8px;
}
```

### Square Button
```css
.game-play-btn {
    border-radius: 4px;
}
```

---

## Typography Styles

### Modern (Default)
```css
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
```

### Google Fonts - Inter
```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```
```css
font-family: 'Inter', sans-serif;
```

### Google Fonts - Poppins
```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
```
```css
font-family: 'Poppins', sans-serif;
```

### Google Fonts - Roboto
```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
```
```css
font-family: 'Roboto', sans-serif;
```

---

## Animation Customization

### Faster Animations
```css
.game-card {
    transition: all 0.2s ease;
}

.game-play-btn:hover {
    transition: all 0.15s ease;
}
```

### Slower/Smother Animations
```css
.game-card {
    transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}
```

### Disable Animations
```css
*, *::before, *::after {
    animation: none !important;
    transition: none !important;
}
```

---

## Scrollbar Customization

### Custom Scrollbar (line 80-95)
```css
::-webkit-scrollbar {
    width: 10px;
}

::-webkit-scrollbar-track {
    background: var(--dark-2);
}

::-webkit-scrollbar-thumb {
    background: var(--gradient);
    border-radius: 5px;
}
```

### Thin Scrollbar
```css
::-webkit-scrollbar {
    width: 6px;
}
```

### Hidden Scrollbar
```css
::-webkit-scrollbar {
    width: 0;
    background: transparent;
}
```

---

## Theme Export/Import

### Save Your Theme
Create a CSS snippet with your custom variables:

```css
/* My Custom Theme */
:root {
    --primary: #your-color;
    --accent: #your-accent;
    --gradient: linear-gradient(135deg, #color1, #color2);
}

body {
    background: linear-gradient(135deg, #bg1, #bg2, #bg3);
}

body.light-mode {
    background: linear-gradient(135deg, #lightbg1, #lightbg2);
}
```

### Apply a Theme
Replace the existing `:root` variables and body backgrounds with your saved theme.

---

## Quick Theme Template

```css
/* === YOUR THEME NAME === */
:root {
    --primary: #HEX;
    --primary-dark: #HEX;
    --secondary: #HEX;
    --dark: #HEX;
    --dark-2: #HEX;
    --light: #HEX;
    --accent: #HEX;
    --accent-dark: #HEX;
    --gradient: linear-gradient(135deg, #HEX, #HEX);
}

body {
    background: linear-gradient(135deg, #HEX, #HEX, #HEX);
}

body.light-mode {
    background: linear-gradient(135deg, #HEX, #HEX);
}
```

---

## Testing Your Theme

1. **Check both modes**: Toggle dark/light mode
2. **Test all components**: Cards, buttons, modals, toasts
3. **Test on mobile**: Ensure readability
4. **Check contrast**: Text must be readable
5. **Test all states**: Hover, active, focus

---

## Next Steps

- **[Branding Guide](branding.md)** - Full branding customization
- **[SEO Guide](seo.md)** - Optimize for search
- **[Editions](../editions/main.md)** - Different UI styles

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
