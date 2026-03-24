# Branding & Customization Guide

**Make Okay Arcade truly yours with custom branding.**

---

## Site Identity

### Change Site Title

**In `<head>` section** (line 8):
```html
<title>Your Arcade Name - Play Free Online Games</title>
```

**In navigation** (line 2242-2245):
```html
<a href="#" class="nav-logo">
    <i class="fas fa-gamepad"></i>
    <span>Your Arcade Name</span>
</a>
```

**In footer** (line 2380):
```html
<div class="footer-logo">YOUR ARCADE</div>
```

### Update Meta Tags

**Description** (line 9):
```html
<meta name="description" content="Your custom description for search engines.">
```

**Keywords** (line 10):
```html
<meta name="keywords" content="your, keywords, here, games, arcade">
```

**Author** (line 11):
```html
<meta name="author" content="Your Name">
```

---

## URL Configuration

### Canonical URL
```html
<link rel="canonical" href="https://yourdomain.com">
```

### Open Graph URL
```html
<meta property="og:url" content="https://yourdomain.com">
<meta property="twitter:url" content="https://yourdomain.com">
```

### Structured Data URL
```json
{
    "@type": "WebSite",
    "url": "https://yourdomain.com",
    "potentialAction": {
        "target": "https://yourdomain.com/?search={search_term_string}"
    }
}
```

---

## Color Customization

### CSS Variables

Colors are defined in CSS variables (line 61-77):

```css
:root {
    --primary: #6c5ce7;           /* Main purple */
    --primary-dark: #5a4d1;       /* Darker purple */
    --secondary: #a29bfe;         /* Light purple */
    --dark: #2d3436;              /* Dark text */
    --dark-2: #1e1e2e;            /* Darker background */
    --light: #f9f9f9;             /* Light text */
    --accent: #00cec9;            /* Teal accent */
    --accent-dark: #00b5b0;       /* Darker teal */
    --gradient: linear-gradient(135deg, #6c5ce7, #00cec9);
}
```

### Color Schemes

#### Blue Theme
```css
:root {
    --primary: #3b82f6;
    --primary-dark: #2563eb;
    --secondary: #60a5fa;
    --accent: #06b6d4;
    --gradient: linear-gradient(135deg, #3b82f6, #06b6d4);
}
```

#### Red/Orange Theme
```css
:root {
    --primary: #ef4444;
    --primary-dark: #dc2626;
    --secondary: #f87171;
    --accent: #f97316;
    --gradient: linear-gradient(135deg, #ef4444, #f97316);
}
```

#### Green Theme
```css
:root {
    --primary: #22c55e;
    --primary-dark: #16a34a;
    --secondary: #4ade80;
    --accent: #14b8a6;
    --gradient: linear-gradient(135deg, #22c55e, #14b8a6);
}
```

#### Dark/Elegant Theme
```css
:root {
    --primary: #6366f1;
    --primary-dark: #4f46e5;
    --secondary: #818cf8;
    --accent: #f472b6;
    --gradient: linear-gradient(135deg, #6366f1, #f472b6);
}
```

---

## Background Customization

### Body Background
Find (line 320):
```css
body {
    background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
}
```

### Light Mode Background
Find (line 328):
```css
body.light-mode {
    background: linear-gradient(135deg, #667eea, #764ba2);
}
```

### Hero Section Background
Find (line 480):
```css
.hero::before {
    background: url('https://images.unsplash.com/photo-YOUR-IMAGE') center/cover;
}
```

Replace with your own background image URL.

---

## Typography

### Font Family
Find (line 54):
```css
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
```

### Popular Font Options

**Modern Sans-serif:**
```css
font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
```

**Tech/Gaming Style:**
```css
font-family: 'Orbitron', 'Segoe UI', sans-serif;
```

**Clean and Minimal:**
```css
font-family: 'Poppins', 'Helvetica Neue', sans-serif;
```

**Retro/Pixel:**
```css
font-family: 'Press Start 2P', 'Courier New', monospace;
```

To use Google Fonts, add to `<head>`:
```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---

## Favicon Customization

### Current Favicon
The favicon is an inline SVG (line 30):
```html
<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,...">
```

### Option 1: Create Custom SVG
Use a tool like [RealFaviconGenerator](https://realfavicongenerator.net/)

### Option 2: Use Image File
```html
<link rel="icon" type="image/png" href="favicon.png">
<link rel="icon" type="image/x-icon" href="favicon.ico">
```

### Recommended Favicon Sizes
- 16x16 (favicon.ico)
- 32x32 (favicon.ico)
- 192x192 (Android)
- 512x512 (PWA)

---

## Logo Customization

### Navigation Logo
Find (line 2242):
```html
<a href="#" class="nav-logo">
    <i class="fas fa-gamepad"></i>
    <span>Okay Arcade</span>
</a>
```

### Using Image Instead
```html
<a href="#" class="nav-logo">
    <img src="your-logo.png" alt="Your Logo" height="40">
</a>
```

### Icon Options
Font Awesome icons available:
- `fa-gamepad` - Game controller
- `fa-joystick` - Joystick
- `fa-dice` - Dice
- `fa-vr-cardboard` - VR headset
- `fa-controller` - Controller

---

## Footer Customization

### Update Footer Content (line 2381)
```html
<p class="footer-description">Your custom description here...</p>
```

### Social Links (line 2383-2386)
```html
<div class="footer-social">
    <a href="https://twitter.com/yourhandle" class="social-link">
        <i class="fab fa-twitter"></i>
    </a>
    <a href="https://discord.gg/yourserver" class="social-link">
        <i class="fab fa-discord"></i>
    </a>
    <!-- Add more social links -->
</div>
```

### Footer Copyright (line 2415)
```html
<p>&copy; 2026 Your Name. All rights reserved.</p>
```

---

## Hero Section Customization

### Hero Badge (line 2268-2271)
```html
<div class="hero-badge">
    <i class="fas fa-bolt"></i>
    <span>Your Custom Badge Text</span>
</div>
```

### Hero Title (line 2272)
```html
<h1 class="hero-title">Your Arcade Name</h1>
```

### Hero Subtitle (line 2273)
```html
<p class="hero-subtitle">Your custom tagline here...</p>
```

---

## Stats Section

### Update Stats (line 2294-2315)

**Total Games** - Automatically calculated
**Players** - Static number (change "10K+")
**Availability** - Change "24/7"
**Cost** - Keep "0" or customize

---

## Modal Content Customization

### Privacy Policy (line 2856-2904)
Update the content in `pageContent.privacy` object:
```javascript
privacy: {
    title: 'Privacy Policy',
    content: `
        <h2>Your Privacy Policy</h2>
        <p>Your policy content...</p>
    `
}
```

### Terms of Service (line 2905-2967)
Update `pageContent.terms` object.

### Contact Information (line 2969-3013)
Update email addresses:
```html
<p><a href="mailto:your@email.com">your@email.com</a></p>
```

### About Us (line 3015-3055)
Customize your story and mission.

---

## Search Placeholder

Find (line 2278):
```html
<input type="text" class="search-input" placeholder="Search for games...">
```

Change to your preference:
```html
<input type="text" class="search-input" placeholder="Find your favorite game...">
```

---

## Theme Colors for Mobile

### Theme Color Meta Tag (line 51)
```html
<meta name="theme-color" content="#6c5ce7">
```

Match this to your primary color for browser chrome.

---

## Complete Branding Example

```html
<head>
    <!-- Basic -->
    <title>GameZone - Free Online Games</title>
    <meta name="description" content="Play free online games at GameZone. Racing, action, puzzle games and more!">
    <meta name="author" content="John Doe">
    
    <!-- URLs -->
    <link rel="canonical" href="https://gamezone.com">
    
    <!-- Theme Color -->
    <meta name="theme-color" content="#3b82f6">
    
    <!-- Google Font -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
</head>
```

```css
:root {
    --primary: #3b82f6;
    --accent: #06b6d4;
    --gradient: linear-gradient(135deg, #3b82f6, #06b6d4);
}

body {
    font-family: 'Inter', sans-serif;
}
```

---

## Branding Checklist

- [ ] Site title updated
- [ ] Meta description updated
- [ ] URLs updated to your domain
- [ ] Colors customized
- [ ] Favicon changed
- [ ] Logo updated
- [ ] Footer content customized
- [ ] Social links updated
- [ ] Contact email updated
- [ ] Legal pages updated
- [ ] Theme color set
- [ ] Background customized (optional)

---

## Next Steps

- **[Themes Guide](themes.md)** - Advanced theme customization
- **[SEO Guide](seo.md)** - Optimize for search engines
- **[Adding Games](adding-games.md)** - Add your games

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
