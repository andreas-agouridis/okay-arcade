# SEO Optimization Guide

**Optimize Okay Arcade for search engines and social media.**

---

## Why SEO Matters

- Higher search engine rankings
- More organic traffic
- Better social media sharing
- Improved user experience

---

## Meta Tags Overview

### Location in index.html
All meta tags are in the `<head>` section (lines 7-47).

---

## Essential Meta Tags

### Title Tag (Line 8)
```html
<title>Your Arcade - Play Free Online Games | Gaming Platform</title>
```

**Best Practices:**
- 50-60 characters
- Include primary keyword
- Include brand name
- Unique per page

### Meta Description (Line 9)
```html
<meta name="description" content="Play the best free online games at Your Arcade. Action, racing, sports games. No downloads required. 100% free!">
```

**Best Practices:**
- 150-160 characters
- Include keywords naturally
- Compelling call-to-action
- Unique per page

### Meta Keywords (Line 10)
```html
<meta name="keywords" content="free online games, browser games, arcade, action games, racing games, sports games, free games">
```

### Meta Author (Line 11)
```html
<meta name="author" content="Your Name">
```

### Robots Meta (Line 12)
```html
<meta name="robots" content="index, follow">
```

Options:
- `index, follow` - Allow indexing and link following
- `noindex, follow` - Don't index, but follow links
- `index, nofollow` - Index but don't follow links
- `noindex, nofollow` - Do neither

### Canonical URL (Line 13)
```html
<link rel="canonical" href="https://yourdomain.com">
```

Prevents duplicate content issues.

---

## Open Graph Tags (Facebook, LinkedIn)

```html
<meta property="og:type" content="website">
<meta property="og:url" content="https://yourdomain.com">
<meta property="og:title" content="Your Arcade - Free Online Games">
<meta property="og:description" content="Play thousands of free games instantly. No downloads needed!">
<meta property="og:image" content="https://yourdomain.com/og-image.png">
<meta property="og:site_name" content="Your Arcade">
```

### Image Requirements
- **Size**: 1200x630 pixels (recommended)
- **Format**: PNG or JPG
- **File size**: Under 1MB
- Must be publicly accessible

---

## Twitter Card Tags

```html
<meta property="twitter:card" content="summary_large_image">
<meta property="twitter:url" content="https://yourdomain.com">
<meta property="twitter:title" content="Your Arcade - Free Online Games">
<meta property="twitter:description" content="Play thousands of free games instantly!">
<meta property="twitter:image" content="https://yourdomain.com/twitter-card.png">
<meta property="twitter:site" content="@yourtwitterhandle">
```

### Card Types
- `summary_large_image` - Large image card
- `summary` - Small image card
- `player` - Video/audio player

---

## Structured Data (Schema.org)

### Current Implementation (Lines 34-47)
```json
{
    "@context": "https://schema.org",
    "@type": "WebSite",
    "name": "Your Arcade",
    "url": "https://yourdomain.com",
    "description": "Free online gaming platform",
    "potentialAction": {
        "@type": "SearchAction",
        "target": "https://yourdomain.com/?search={search_term_string}",
        "query-input": "required name=search_term_string"
    }
}
```

### Additional Schema Types

#### Organization
```json
{
    "@context": "https://schema.org",
    "@type": "Organization",
    "name": "Your Company",
    "url": "https://yourdomain.com",
    "logo": "https://yourdomain.com/logo.png",
    "sameAs": [
        "https://twitter.com/yourhandle",
        "https://facebook.com/yourpage"
    ]
}
```

#### VideoGame (for each game)
```json
{
    "@context": "https://schema.org",
    "@type": "VideoGame",
    "name": "Game Name",
    "description": "Game description",
    "image": "https://yourdomain.com/game-image.jpg",
    "genre": "Action",
    "gamePlatform": "Web Browser",
    "applicationCategory": "Game"
}
```

---

## Sitemap

### Create sitemap.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
        <loc>https://yourdomain.com/</loc>
        <lastmod>2026-03-24</lastmod>
        <changefreq>weekly</changefreq>
        <priority>1.0</priority>
    </url>
</urlset>
```

### Submit to Search Engines
1. **Google**: [Google Search Console](https://search.google.com/search-console)
2. **Bing**: [Bing Webmaster Tools](https://www.bing.com/webmasters)
3. Add to robots.txt:
```
Sitemap: https://yourdomain.com/sitemap.xml
```

---

## robots.txt

### Create robots.txt
```
User-agent: *
Allow: /

Sitemap: https://yourdomain.com/sitemap.xml
Disallow: /sw.js
```

---

## Image Optimization

### Alt Tags
Add alt attributes to all images:

```html
<img src="game-thumb.jpg" alt="Game Name - Action Game" loading="lazy">
```

### Image Best Practices
- Use descriptive file names: `basketball-stars-game.webp`
- Compress images (use WebP format)
- Add alt text for accessibility
- Use responsive images when possible

---

## Performance SEO

### Core Web Vitals
- **LCP** (Largest Contentful Paint): < 2.5s
- **FID** (First Input Delay): < 100ms
- **CLS** (Cumulative Layout Shift): < 0.1

### Performance Tips
1. **Lazy load images**: Already implemented (`loading="lazy"`)
2. **Minimize CSS/JS**: Not needed (inline)
3. **Use CDN for fonts**: Already using CDN
4. **Optimize images**: Use WebP format
5. **Enable compression**: Configure on hosting

---

## Content SEO

### Page Title Optimization
Include target keywords:
- "Free Online Games"
- "Browser Games"
- "Play Games Online"
- "No Download Games"

### Content Recommendations
- Add game descriptions
- Use heading hierarchy (H1, H2, H3)
- Include internal links
- Add alt text to images

---

## Mobile SEO

### Already Implemented
- Responsive design
- Viewport meta tag
- Touch-friendly buttons
- Fast loading

### Test Mobile-Friendly
- [Google Mobile-Friendly Test](https://search.google.com/test/mobile-friendly)

---

## Local SEO (Optional)

If targeting a specific region:

```html
<html lang="en">
<meta name="geo.region" content="US-CA">
<meta name="geo.placename" content="Los Angeles">
```

---

## Analytics Integration

### Google Analytics 4
Add to `<head>`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Google Tag Manager
```html
<!-- Google Tag Manager -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-XXXXXXX');</script>
```

---

## SEO Checklist

### Basic SEO
- [ ] Unique, descriptive title tag
- [ ] Compelling meta description
- [ ] Canonical URL set
- [ ] robots.txt created
- [ ] sitemap.xml created
- [ ] Submit to Google Search Console

### Open Graph
- [ ] og:title set
- [ ] og:description set
- [ ] og:image set (1200x630)
- [ ] og:url set
- [ ] og:type set

### Twitter Cards
- [ ] twitter:card set
- [ ] twitter:title set
- [ ] twitter:description set
- [ ] twitter:image set

### Technical SEO
- [ ] HTTPS enabled
- [ ] Mobile-friendly
- [ ] Fast loading (< 3s)
- [ ] No broken links
- [ ] Proper heading hierarchy

### Content SEO
- [ ] Descriptive image alt tags
- [ ] Unique content
- [ ] Target keywords included
- [ ] Internal linking

---

## Testing Your SEO

### Tools
1. [Google Search Console](https://search.google.com/search-console)
2. [Google PageSpeed Insights](https://pagespeed.web.dev/)
3. [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)
4. [Twitter Card Validator](https://cards-dev.twitter.com/validator)
5. [Schema Markup Validator](https://validator.schema.org/)

### Test Steps
1. Enter your URL in each tool
2. Fix any errors or warnings
3. Re-test after fixes
4. Monitor regularly

---

## Next Steps

- **[Branding Guide](branding.md)** - Customize appearance
- **[Deployment Guide](../deployment.md)** - Deploy with HTTPS
- **[Analytics Guide](../advanced/analytics.md)** - Track visitors

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
