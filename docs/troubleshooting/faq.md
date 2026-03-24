# Frequently Asked Questions

**Common questions and solutions for Okay Arcade.**

---

## General Questions

### What is Okay Arcade?
Okay Arcade is a free, open-source HTML5 gaming arcade template. It's a single HTML file that contains everything needed to run a gaming website.

### Do I need to know how to code?
Basic HTML knowledge is helpful, but you can use the template as-is and just change the games. See our [Getting Started Guide](../getting-started.md).

### Is it really free?
Yes! Okay Arcade is released under the MIT License, which means it's free to use, modify, and distribute.

### What games can I add?
Any game that can be embedded via iframe. This includes HTML5 games from various providers.

### Do I need a server?
No backend server is required. It's a static HTML file that can be hosted anywhere.

---

## Installation Questions

### How do I install Okay Arcade?
Simply download the files and open `index.html` in a browser, or deploy to any web host.

### Can I use it with WordPress?
Yes, you can embed it in an iframe or use it as a standalone page.

### Does it work on mobile?
Yes, the template is fully responsive and works on all devices.

---

## Customization Questions

### How do I change the site name?
Find and replace "Okay Arcade" with your site name throughout the HTML file.

### How do I add games?
Add game objects to the `games` array in the JavaScript section. See [Adding Games](../customization/adding-games.md).

### How do I change colors?
Edit the CSS variables in the `:root` selector. See [Themes Guide](../customization/themes.md).

### Can I remove the legal pages?
Yes, you can remove or modify the page content in the `pageContent` object.

### How do I add my own logo?
Replace the logo text or add an `<img>` tag in the navigation section.

---

## Game-Related Questions

### Why won't a game load?
Possible causes:
1. The embed URL is invalid or expired
2. The game provider blocks embedding
3. CORS restrictions
4. The game requires HTTPS

### How do I find game embed URLs?
1. Visit the game page
2. Right-click the game → Inspect Element
3. Find the `<iframe>` src attribute
4. Copy the URL

### Can I use games from Poki or CrazyGames?
Many games from these platforms can be embedded, but some may have restrictions. Always check the terms of service.

### How many games can I add?
There's no technical limit. However, more games may affect initial load time.

---

## Technical Questions

### What browsers are supported?
- Chrome (full support)
- Firefox (full support)
- Safari (full support)
- Edge (full support)
- Opera (full support)

### Does it work offline?
Yes, with the service worker enabled, users can access previously loaded content offline.

### What is localStorage used for?
- Storing favorite games
- Remembering theme preference
- Offline status tracking

### How do I enable HTTPS?
Depends on your hosting provider. Most free hosts (GitHub Pages, Netlify) provide free HTTPS.

---

## Deployment Questions

### Where can I host it?
- GitHub Pages (free)
- Netlify (free)
- Vercel (free)
- Any traditional web host
- Cloudflare Pages (free)

### How do I use a custom domain?
1. Buy a domain
2. Configure DNS to point to your host
3. Enable custom domain in hosting settings
4. Wait for DNS propagation

### Is GitHub Pages free?
Yes, completely free for public repositories.

### How long does deployment take?
Usually 1-5 minutes after pushing changes.

---

## Troubleshooting Questions

### The site shows a blank page
1. Check browser console for errors
2. Verify `index.html` is in the root
3. Try a different browser

### Games show but don't open in modal
1. Check JavaScript console for errors
2. Verify game data structure is correct
3. Test embed URL directly

### Favorites aren't saving
1. Ensure localStorage is enabled
2. Check if in private browsing mode
3. Clear browser cache and try again

### Theme toggle doesn't work
1. Check JavaScript console for errors
2. Verify themeToggle element exists
3. Try hard refresh (Ctrl+Shift+R)

### Search not finding games
1. Check for typos in search term
2. Verify game names are correct
3. Check category filter is set to "All"

---

## Still Need Help?

### Check Documentation
Browse the [full documentation](../index.md) for detailed guides.

### Report an Issue
Submit bugs or feature requests on GitHub Issues.

### Contact Support
Email: mydreamz.agency@agouridis.tech

---

*Can't find your answer? [Contact us](help.md)*
