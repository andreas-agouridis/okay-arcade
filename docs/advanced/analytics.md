# Analytics Integration

**Track visitors and understand user behavior.**

---

## Why Analytics?

- Understand your audience
- Track popular games
- Monitor traffic sources
- Measure engagement
- Make data-driven decisions

---

## Google Analytics 4 (GA4)

### Step 1: Create GA4 Property
1. Go to [analytics.google.com](https://analytics.google.com)
2. Create an account (if needed)
3. Create a GA4 property
4. Get your Measurement ID (starts with `G-`)

### Step 2: Add Tracking Code
Add to `<head>` section in `index.html`:

```html
<!-- Google Analytics 4 -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-XXXXXXXXXX', {
        page_title: 'Okay Arcade',
        custom_map: {
            dimension1: 'game_category'
        }
    });
</script>
```

Replace `G-XXXXXXXXXX` with your Measurement ID.

---

## Custom Events

### Track Game Plays
Add this to the `openGame` function:

```javascript
function openGame(url, name, category) {
    // Existing code...
    
    // Track game play
    if (typeof gtag !== 'undefined') {
        gtag('event', 'game_play', {
            'game_name': name,
            'game_category': category
        });
    }
}
```

### Track Searches
Add to search input handler:

```javascript
searchInput.addEventListener('input', () => {
    const searchTerm = searchInput.value;
    
    // Track search
    if (searchTerm.length > 2 && typeof gtag !== 'undefined') {
        gtag('event', 'search', {
            'search_term': searchTerm
        });
    }
});
```

### Track Favorites
Add to `toggleFavorite` function:

```javascript
function toggleFavorite(gameName) {
    // Existing code...
    
    // Track favorite
    if (typeof gtag !== 'undefined') {
        gtag('event', 'add_to_favorites', {
            'game_name': gameName
        });
    }
}
```

### Track Category Filter
Add to category button click handler:

```javascript
categories.addEventListener('click', (e) => {
    const btn = e.target.closest('.category-btn');
    if (!btn) return;
    
    // Track category view
    if (typeof gtag !== 'undefined') {
        gtag('event', 'filter_category', {
            'category': btn.dataset.category
        });
    }
});
```

---

## Google Tag Manager (GTM)

### Step 1: Create GTM Account
1. Go to [tagmanager.google.com](https://tagmanager.google.com)
2. Create an account and container
3. Get your Container ID (starts with `GTM-`)

### Step 2: Add GTM Code
Add to `<head>`:

```html
<!-- Google Tag Manager -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-XXXXXXX');</script>
```

Add to `<body>` (immediately after opening tag):

```html
<!-- Google Tag Manager (noscript) -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-XXXXXXX"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
```

Replace `GTM-XXXXXXX` with your Container ID.

### Step 3: Configure in GTM
Create tags and triggers in the GTM interface:
- Page view trigger
- Custom event triggers for game plays, searches, etc.

---

## Plausible Analytics (Privacy-Friendly)

### Step 1: Create Account
1. Go to [plausible.io](https://plausible.io)
2. Add your site
3. Get the tracking script

### Step 2: Add Script
```html
<script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script>
```

---

## Cloudflare Web Analytics (Free)

### Step 1: Enable
1. Go to Cloudflare Dashboard
2. Enable Web Analytics
3. Get the beacon script

### Step 2: Add Script
```html
<script defer src='https://static.cloudflareinsights.com/beacon.min.js' 
    data-cf-beacon='{"token": "YOUR_TOKEN"}'></script>
```

---

## Simple Page Counter (No External Service)

If you want basic stats without external services:

```html
<script>
// Simple page view counter using localStorage
function trackPageView() {
    let views = parseInt(localStorage.getItem('pageViews') || '0');
    views++;
    localStorage.setItem('pageViews', views.toString());
    return views;
}

// Track and display
const totalViews = trackPageView();
console.log('Total page views:', totalViews);
</script>
```

---

## Track Game Popularity (Local)

Track which games are played most:

```javascript
// Initialize game stats
let gameStats = JSON.parse(localStorage.getItem('gameStats') || '{}');

function trackGamePlay(gameName) {
    if (!gameStats[gameName]) {
        gameStats[gameName] = { plays: 0 };
    }
    gameStats[gameName].plays++;
    localStorage.setItem('gameStats', JSON.stringify(gameStats));
}

function getMostPlayed() {
    return Object.entries(gameStats)
        .sort((a, b) => b[1].plays - a[1].plays)
        .slice(0, 10);
}

// Use in openGame function:
function openGame(url, name, category) {
    trackGamePlay(name);
    // ... rest of function
}
```

---

## Privacy Considerations

### Be Transparent
Add to your Privacy Policy:

```html
<h2>Analytics</h2>
<p>We use analytics to understand how our site is used. This includes:</p>
<ul>
    <li>Page views and session duration</li>
    <li>Games played (anonymized)</li>
    <li>Search queries</li>
    <li>Device and browser information</li>
</ul>
<p>We do not collect personal information through analytics.</p>
```

### Cookie Consent
Consider adding cookie consent for GDPR compliance:

```html
<div id="cookieConsent" style="position: fixed; bottom: 0; ...">
    <p>We use cookies for analytics. 
    <button onclick="acceptCookies()">Accept</button>
    <button onclick="declineCookies()">Decline</button>
    </p>
</div>
```

---

## Viewing Analytics

### Google Analytics
1. Go to analytics.google.com
2. Select your property
3. View real-time, audience, behavior reports

### Key Metrics to Track
- **Page Views**: Total visits
- **Unique Visitors**: Individual users
- **Bounce Rate**: Users leaving immediately
- **Session Duration**: Time on site
- **Top Games**: Most played
- **Traffic Sources**: Where visitors come from
- **Device Type**: Desktop vs mobile

---

## Next Steps

- **[SEO Guide](../customization/seo.md)** - Improve visibility
- **[Deployment Guide](../deployment.md)** - Deploy with HTTPS
- **[Custom Domain](custom-domain.md)** - Use your domain

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
