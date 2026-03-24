<div align="center">

# 🎮 Okay Arcade

### A Beautiful Free Online Gaming Arcade Template

**Create your own gaming website in minutes - no coding required!**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Docs](https://img.shields.io/github/stars/anomalyco/okay-arcade.svg)](https://andreas-agouridis.github.io/okay-arcade/)

[Live Demo](https://okay.agouridis.site) • [Documentation](https://okay.agouridis.site/docs) • [Report Bug](https://github.com/anomalyco/okay-arcade/issues) • [Request Feature](https://github.com/anomalyco/okay-arcade/issues)

</div>

---

## 📋 Table of Contents

- [Features](#-features)
- [Editions](#-editions)
- [Quick Start](#-quick-start)
- [Customization](#-customization)
- [Documentation](#-documentation)
- [Contributing](#-contributing)
- [License](#-license)
- [Support](#-support)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🎨 **Beautiful UI** | Modern glassmorphism design with smooth animations |
| 🌓 **Dark/Light Mode** | Toggle between dark and light themes |
| 🔍 **Smart Search** | Instant search across all games |
| 📂 **Categories** | Filter games by category |
| ⭐ **Favorites** | Save your favorite games (localStorage) |
| 📱 **Fully Responsive** | Works on desktop, tablet, and mobile |
| 🔌 **Offline Support** | Works offline with service worker |
| 🚀 **Fast & Lightweight** | Single HTML file, no dependencies |
| 🔒 **SEO Optimized** | Meta tags, Open Graph, structured data |
| 📦 **Multiple Editions** | Main, Simple UI, Terminal, No Games |
| 🎮 **Game Modal** | Fullscreen gaming experience |
| 🔔 **Toast Notifications** | Beautiful notification system |
| 📄 **Legal Pages** | Privacy, Terms, Contact, About, FAQ |
| 💾 **LocalStorage** | Persistent favorites and preferences |
| ⌨️ **Keyboard Shortcuts** | ESC to close modals |

---

## 🎭 Editions

Okay Arcade comes with **4 unique editions** to suit your needs:

| Edition | Style | Best For |
|---------|-------|----------|
| **Main** | Full-featured, glassmorphism UI | Complete gaming sites |
| **Simple UI** | Clean, minimal design | Lightweight deployments |
| **Terminal** | CLI/command-line interface | Developer-focused sites |
| **No Games** | Empty template | Starting from scratch |

### Main Edition
The flagship version with all features - search, filters, favorites, theme toggle, offline support, and more.

### Simple UI Edition
A clean, minimal alternative with light theme - perfect for fast loading and mobile-first experiences.

### Terminal Edition
A unique CLI-style interface where users type commands to browse and play games - great for tech-savvy audiences.

### No Games Edition
Same as Main Edition but with an empty games array - perfect for building your own custom arcade from scratch.

---

## 🚀 Quick Start

### Option 1: Download & Run
```bash
# Clone the repository
git clone https://github.com/anomalyco/okay-arcade.git

# Open in browser
open index.html  # macOS
start index.html # Windows
xdg-open index.html # Linux
```

### Option 2: Local Server (Recommended)
```bash
# Python
python -m http.server 8000

# Node.js
npx http-server

# PHP
php -S localhost:8000
```

Then visit `http://localhost:8000`

### Option 3: Deploy to GitHub Pages
1. Fork this repository
2. Go to Settings → Pages
3. Select `main` branch and `/ (root)` folder
4. Your site will be at `https://yourusername.github.io/okay-arcade/`

---

## 🎮 Adding Games

Games are stored in a JavaScript array. Add your games like this:

```javascript
const games = [
    {
        name: "Game Name",
        embedUrl: "https://game-url.com/embed",
        imageUrl: "https://thumbnail-url.com/image.jpg",
        category: "Action"
    },
    // Add more games...
];
```

### Supported Categories
- Action
- Racing
- Sports
- Platformer
- Runner
- IO Games
- *Add your own categories!*

See the [Adding Games Guide](docs/customization/adding-games.md) for detailed instructions.

---

## 🎨 Customization

### Change Site Name
Find and replace "Okay Arcade" throughout `index.html` with your site name.

### Change Colors
Edit CSS variables in the `:root` selector:

```css
:root {
    --primary: #6c5ce7;      /* Main color */
    --accent: #00cec9;       /* Accent color */
    --gradient: linear-gradient(135deg, #6c5ce7, #00cec9);
}
```

### Update URLs
Replace all occurrences of:
- `okay.agouridis.site` → your domain
- `Andreas Agouridis` → your name

See the [Customization Guide](docs/customization/branding.md) for more options.

---

## 📚 Documentation

Complete documentation is available in the [`/docs`](docs/) folder:

### Getting Started
- [Quick Start Guide](docs/getting-started.md)
- [Installation](docs/installation.md)
- [Deployment](docs/deployment.md)

### Customization
- [Branding & Customization](docs/customization/branding.md)
- [Adding Games](docs/customization/adding-games.md)
- [Categories](docs/customization/categories.md)
- [Themes](docs/customization/themes.md)
- [SEO Optimization](docs/customization/seo.md)

### Editions
- [Main Edition](docs/editions/main.md)
- [Simple UI Edition](docs/editions/simple.md)
- [Terminal Edition](docs/editions/terminal.md)
- [No Games Edition](docs/editions/nogames.md)

### Advanced
- [Adding Pages](docs/advanced/pages.md)
- [PWA & Offline Support](docs/advanced/pwa.md)
- [Analytics Integration](docs/advanced/analytics.md)
- [Custom Domain](docs/advanced/custom-domain.md)

### Troubleshooting
- [FAQ](docs/troubleshooting/faq.md)
- [Known Issues](docs/troubleshooting/issues.md)
- [Getting Help](docs/troubleshooting/help.md)

---

## 📁 Project Structure

```
okay-arcade/
├── index.html                    # Main arcade template
├── sw.js                         # Service worker (optional)
├── manifest.json                 # PWA manifest (optional)
├── README.md                     # This file
├── LICENSE                       # MIT License
├── (other)editions/              # Alternative editions
│   ├── nogames(edition).html     # Empty template
│   ├── simpleui(edition).html    # Simple UI version
│   └── terminal(no-ui)(edition).html  # CLI-style version
└── docs/                         # Documentation (GitHub Pages)
    ├── index.md                  # Documentation home
    ├── getting-started.md        # Quick start guide
    ├── installation.md           # Installation instructions
    ├── deployment.md             # Deployment guide
    ├── customization/            # Customization guides
    ├── editions/                 # Edition documentation
    ├── advanced/                 # Advanced guides
    └── troubleshooting/          # Troubleshooting guides
```

---

## 🛠️ Technologies

- **HTML5** - Semantic markup
- **CSS3** - Modern styling with CSS variables, glassmorphism
- **JavaScript (ES6+)** - Vanilla JS, no frameworks
- **Font Awesome 6** - Icons (CDN)
- **LocalStorage** - Persistent data
- **Service Worker** - Offline support

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### What We Accept
- Bug fixes
- New features
- Documentation improvements
- New game additions
- Translations

---

## 📝 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

You are free to:
- ✅ Use commercially
- ✅ Modify
- ✅ Distribute
- ✅ Use privately

---

## 💬 Support

- 📧 **Email**: mydreamz.agency@agouridis.tech
- 🐛 **Issues**: [GitHub Issues](https://github.com/anomalyco/okay-arcade/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/anomalyco/okay-arcade/discussions)
- 🌐 **Website**: [okay.agouridis.site](https://okay.agouridis.site)

---

## ⭐ Star History

If you find this project useful, please give it a star! It helps others discover the project.

[![Star History Chart](https://api.star-history.com/svg?repos=anomalyco/okay-arcade&type=Date)](https://star-history.com/#anomalyco/okay-arcade&Date)

---

## 🙏 Acknowledgments

- [Font Awesome](https://fontawesome.com/) for icons
- [Unsplash](https://unsplash.com/) for background images
- All game providers for embeddable games
- The open-source community for inspiration

---

<div align="center">

**Made with ❤️ by [Andreas Agouridis](https://agouridis.tech)**

[⬆ Back to Top](#-okay-arcade)

</div>
