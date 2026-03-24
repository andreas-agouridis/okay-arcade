# Installation Guide

**Complete installation instructions for Okay Arcade.**

---

## Overview

Okay Arcade is a **static HTML template** - no build tools, no npm packages, no complex setup required. You can have it running in minutes.

---

## Method 1: Download and Extract

### Step 1: Download
1. Navigate to the GitHub repository
2. Click **Code** → **Download ZIP**
3. Save to your desired location

### Step 2: Extract
Extract the ZIP file. You'll see this structure:

```
okay-arcade/
├── index.html              # Main arcade template
├── README.md               # Project documentation
├── LICENSE                 # MIT License
├── (other)editions/        # Alternative editions
│   ├── nogames(edition).html
│   ├── simpleui(edition).html
│   └── terminal(no-ui)(edition).html
└── docs/                   # Documentation (GitHub Pages)
    ├── index.md
    ├── getting-started.md
    └── ...
```

### Step 3: Test
Open `index.html` in your browser. That's it!

---

## Method 2: Git Clone

### Prerequisites
- Git installed ([Download Git](https://git-scm.com/))

### Clone the Repository
```bash
git clone https://github.com/yourusername/okay-arcade.git
cd okay-arcade
```

### Verify Installation
```bash
ls -la
# You should see: index.html, README.md, LICENSE, docs/, (other)editions/
```

---

## Method 3: Fork on GitHub

### Step 1: Fork
1. Go to the Okay Arcade repository
2. Click **Fork** in the top right
3. Select your GitHub account

### Step 2: Clone Your Fork
```bash
git clone https://github.com/YOUR-USERNAME/okay-arcade.git
cd okay-arcade
```

### Step 3: Make Changes
Edit files and commit:
```bash
git add .
git commit -m "Customized for my site"
git push origin main
```

---

## Setting Up a Local Development Server

While you can open `index.html` directly, using a local server is recommended for:

- Proper offline detection testing
- Service worker functionality
- CORS-free game loading

### Option 1: Python (Built-in)
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```
Visit: `http://localhost:8000`

### Option 2: Node.js (http-server)
```bash
# Install globally (one-time)
npm install -g http-server

# Run server
http-server -p 8000
```

### Option 3: VS Code Live Server
1. Install **Live Server** extension
2. Right-click `index.html`
3. Select **"Open with Live Server"**

### Option 4: PHP
```bash
php -S localhost:8000
```

### Option 5: Ruby
```bash
ruby -run -e httpd . -p 8000
```

---

## File Structure Explained

### Root Files
| File | Purpose |
|------|---------|
| `index.html` | Main arcade template - contains ALL code |
| `README.md` | Project documentation |
| `LICENSE` | MIT license file |

### (other)editions/ Folder
Contains alternative versions of the arcade:

| File | Description |
|------|-------------|
| `nogames(edition).html` | Empty template (no games pre-loaded) |
| `simpleui(edition).html` | Minimal, clean UI |
| `terminal(no-ui)(edition).html` | Command-line interface style |

### docs/ Folder
GitHub Pages documentation site:

| File | Purpose |
|------|---------|
| `index.md` | Documentation homepage |
| `getting-started.md` | Quick start guide |
| `customization/*.md` | Customization guides |
| `editions/*.md` | Edition documentation |

---

## Verifying Your Installation

### Checklist
- [ ] `index.html` opens in browser
- [ ] Games are displayed in the grid
- [ ] Search functionality works
- [ ] Category filters work
- [ ] Game modal opens when clicking a game
- [ ] Theme toggle works (dark/light)
- [ ] Favorites can be added/removed
- [ ] Footer links open modals (Privacy, Terms, etc.)

### Testing on Different Devices
1. **Desktop**: Test on Chrome, Firefox, Safari, Edge
2. **Mobile**: Use Chrome DevTools device emulator
3. **Tablet**: Test responsive layout

---

## Troubleshooting Installation

### Issue: Games Not Loading
**Solution**: Some games may require HTTPS. Use a local server:
```bash
python -m http.server 8000
```

### Issue: Service Worker Not Working
**Solution**: Service workers require HTTPS in production. They work on `localhost` for development.

### Issue: Offline Page Shows Immediately
**Solution**: This is normal on `file://` protocol. Use a local server.

### Issue: CORS Errors
**Solution**: Always use a local server or deploy to proper hosting.

---

## Next Steps

Now that you have Okay Arcade installed:

1. **[Getting Started](getting-started.md)** - Quick customization guide
2. **[Adding Games](customization/adding-games.md)** - Add your own games
3. **[Branding Guide](customization/branding.md)** - Customize appearance
4. **[Deployment Guide](deployment.md)** - Deploy to production

---

*Installation issues? Check the [FAQ](troubleshooting/faq.md)*
