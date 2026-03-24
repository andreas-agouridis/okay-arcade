# Service Worker & PWA Guide

**Enable offline support and Progressive Web App features.**

---

## Overview

Okay Arcade includes PWA (Progressive Web App) support:

- Offline detection and page
- Service worker for caching
- Manifest file for installation
- Offline game favorites

---

## What is a PWA?

Progressive Web Apps are web applications that:
- Work offline
- Can be installed on devices
- Send push notifications
- Load instantly
- Feel like native apps

---

## Service Worker

### Location
The service worker file is `sw.js` (in root directory).

### Registration
In `index.html` (line 3406-3410):
```javascript
if ("serviceWorker" in navigator) {
    navigator.serviceWorker.register("/sw.js");
}
```

### What It Does
- Caches HTML, CSS, JavaScript
- Serves cached content when offline
- Updates cache when online

---

## Manifest File

### Location
`manifest.json` (in root directory).

### Content
```json
{
    "name": "Okay Arcade",
    "short_name": "OkayArcade",
    "description": "Free online gaming arcade",
    "start_url": "/",
    "display": "standalone",
    "background_color": "#0f0c29",
    "theme_color": "#6c5ce7",
    "icons": [
        {
            "src": "icon-192.png",
            "sizes": "192x192",
            "type": "image/png"
        },
        {
            "src": "icon-512.png",
            "sizes": "512x512",
            "type": "image/png"
        }
    ]
}
```

### Customize Manifest

```json
{
    "name": "Your Arcade Name",
    "short_name": "YourArcade",
    "description": "Your description here",
    "start_url": "/",
    "display": "standalone",
    "background_color": "#your-bg-color",
    "theme_color": "#your-theme-color",
    "icons": [
        {
            "src": "icon-192.png",
            "sizes": "192x192",
            "type": "image/png",
            "purpose": "any maskable"
        },
        {
            "src": "icon-512.png",
            "sizes": "512x512",
            "type": "image/png",
            "purpose": "any maskable"
        }
    }
}
```

---

## Creating Icons

### Required Sizes
- 192x192 pixels
- 512x512 pixels
- Optional: 48x48, 72x72, 96x96, 128x128, 144x144, 384x384

### Generate Icons
1. Create one large icon (512x512)
2. Use an icon generator:
   - [Maskable.app](https://maskable.app)
   - [Favicon Generator](https://realfavicongenerator.net)
   - [PWA Builder](https://www.pwabuilder.com)

### Icon Best Practices
- Use PNG format
- Include padding for maskable icons
- Match your site's branding
- Keep design simple (recognizable at small sizes)

---

## Offline Detection

### Built-in Features

Okay Arcade includes offline detection (lines 3236-3404):

1. **Offline Page**: Shows when user is offline
2. **Status Indicator**: Shows connection status
3. **Retry Button**: Attempts reconnection
4. **Auto-reconnect**: Checks periodically when offline
5. **Cookie Tracking**: Remembers offline state

### Offline Page Elements
```html
<div id="offlinePage" class="offline-page">
    <div class="offline-content">
        <div class="offline-icon">
            <i class="fas fa-wifi-slash"></i>
        </div>
        <h1 class="offline-title">You're Offline</h1>
        <p class="offline-subtitle">No internet connection detected.</p>
        <!-- Tips, retry button, status -->
    </div>
</div>
```

---

## Customizing Offline Page

### Change Message
```html
<h1 class="offline-title">You're Offline</h1>
<p class="offline-subtitle">Your custom message here.</p>
```

### Change Tips
```html
<div class="offline-tips">
    <h3><i class="fas fa-lightbulb"></i> Tips:</h3>
    <ul>
        <li><i class="fas fa-check"></i> Your tip here</li>
    </ul>
</div>
```

### Change Colors
```css
.offline-page {
    background: linear-gradient(135deg, #your-colors);
}
```

---

## Testing Offline Mode

### Browser DevTools
1. Open DevTools (F12)
2. Go to **Network** tab
3. Check **Offline** checkbox
4. Refresh page

### Physical Testing
1. Disconnect from WiFi
2. Try to access the site
3. Verify offline page shows
4. Reconnect and verify recovery

---

## Cache Strategies

### Current Strategy: Cache First
The service worker caches files and serves them when offline.

### Other Strategies

**Network First:**
```javascript
// Try network, fall back to cache
```

**Stale While Revalidate:**
```javascript
// Serve cache, update in background
```

---

## Updating Service Worker

### Update Process
1. Modify `sw.js`
2. Change the cache name
3. Deploy new version
4. Users get updated on next visit

### Cache Versioning
```javascript
const CACHE_NAME = 'okay-arcade-v2'; // Increment version
```

---

## PWA Installation

### Install Prompt
Browsers may show "Install" or "Add to Home Screen" prompt.

### Requirements
- HTTPS enabled
- Valid manifest.json
- Service worker registered
- Icon 192x192 and 512x512

### Trigger Install Programmatically
```javascript
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
    e.preventDefault();
    deferredPrompt = e;
    // Show your own install button
});

// Later, when user clicks install button
deferredPrompt.prompt();
```

---

## PWA Display Modes

### standalone
Looks like a native app (no browser UI).

### fullscreen
No browser UI, fills entire screen.

### minimal-ui
Minimal browser UI (back, forward buttons).

### browser
Normal browser experience.

```json
{
    "display": "standalone"  // Recommended
}
```

---

## Troubleshooting

### Service Worker Not Registering
1. Ensure using HTTPS (or localhost)
2. Check `sw.js` exists
3. Check console for errors

### Offline Page Shows Immediately
1. Using `file://` protocol - use localhost
2. Service worker caching issues
3. Clear browser cache

### PWA Not Installing
1. Check manifest.json is valid
2. Ensure HTTPS is enabled
3. Verify icons exist
4. Check browser support

### Cache Not Updating
1. Increment cache version in `sw.js`
2. Hard refresh (Ctrl+Shift+R)
3. Clear browser cache

---

## Disabling PWA Features

### Remove Service Worker
Delete or comment out:
```javascript
// if ("serviceWorker" in navigator) {
//     navigator.serviceWorker.register("/sw.js");
// }
```

### Remove Offline Detection
Delete the offline detection code (lines 3236-3404).

### Remove Manifest Link
Delete from `<head>`:
```html
<link rel="manifest" href="manifest.json">
```

---

## Next Steps

- **[SEO Guide](../customization/seo.md)** - Improve visibility
- **[Deployment Guide](../deployment.md)** - Deploy with HTTPS
- **[Custom Domain](custom-domain.md)** - Use your domain

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
