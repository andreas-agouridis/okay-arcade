# Quick Start Guide

**Get your gaming arcade running in under 5 minutes!**

---

## Prerequisites

Before you begin, make sure you have:

- A GitHub account (for GitHub Pages deployment)
- Git installed on your computer (optional, for version control)
- A text editor (VS Code recommended)

---

## Step 1: Download the Template

### Option A: Download ZIP
1. Go to the [Okay Arcade GitHub repository](https://github.com/yourusername/okay-arcade)
2. Click the green **"Code"** button
3. Select **"Download ZIP"**
4. Extract the ZIP file to your desired location

### Option B: Clone with Git
```bash
git clone https://github.com/yourusername/okay-arcade.git
cd okay-arcade
```

---

## Step 2: Choose Your Edition

Okay Arcade comes with **4 editions** to choose from:

| Edition | File | Description |
|---------|------|-------------|
| **Main** | `index.html` | Full-featured arcade with all options |
| **Simple UI** | `(other)editions/simpleui(edition).html` | Clean, minimal design |
| **Terminal** | `(other)editions/terminal(no-ui)(edition).html` | CLI-style interface |
| **No Games** | `(other)editions/nogames(edition).html` | Empty template |

**For beginners**: Start with the **Main Edition** (`index.html`).

---

## Step 3: Customize Your Site

### Change the Site Name

Open `index.html` and find these lines:

```html
<title>Okay Arcade - Play Free Online Games | 3D Gaming Platform</title>
```

Replace "Okay Arcade" with your site name throughout the file.

### Update URLs

Find and replace:
- `okay.agouridis.site` → your domain
- `Andreas Agouridis` → your name

### Add Your Games

Locate the game data array (around line 2450):

```javascript
const games = [
    {
        name: "Your Game Name",
        embedUrl: "https://game-url.com/embed",
        imageUrl: "https://thumbnail-url.com/image.jpg",
        category: "Action"
    },
    // Add more games here...
];
```

See [Adding Games](customization/adding-games.md) for detailed instructions.

---

## Step 4: Test Locally

### Option A: Open Directly
Simply double-click `index.html` to open in your browser.

### Option B: Use a Local Server (Recommended)
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx http-server

# Using PHP
php -S localhost:8000
```

Then open `http://localhost:8000` in your browser.

---

## Step 5: Deploy

### GitHub Pages (Free)

1. Create a new GitHub repository
2. Upload your files
3. Go to **Settings** → **Pages**
4. Select **main** branch and **/ (root)** folder
5. Click **Save**

Your site will be live at `https://yourusername.github.io/repository-name/`

See [Deployment Guide](deployment.md) for more options.

---

## Quick Customization Checklist

- [ ] Change site title and description
- [ ] Update meta tags (SEO)
- [ ] Add your own games
- [ ] Customize colors (optional)
- [ ] Add legal pages content (Privacy, Terms)
- [ ] Update footer with your information
- [ ] Test on mobile devices
- [ ] Deploy to hosting

---

## What's Next?

- **[Installation Guide](installation.md)** - Detailed setup instructions
- **[Adding Games](customization/adding-games.md)** - Learn how to add games
- **[Branding Guide](customization/branding.md)** - Full customization options
- **[Deployment Guide](deployment.md)** - Deploy to various platforms

---

## Common First Steps

### I want to change the colors
→ See [Theme Customization](customization/themes.md)

### I want to add my own games
→ See [Adding Games](customization/adding-games.md)

### I want to use my own domain
→ See [Custom Domain](advanced/custom-domain.md)

### I want to understand how everything works
→ See [Main Edition Documentation](editions/main.md)

---

*Need help? Check our [FAQ](troubleshooting/faq.md) or [contact us](troubleshooting/help.md)*
