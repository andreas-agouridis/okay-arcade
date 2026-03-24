# Known Issues

**List of known issues and workarounds.**

---

## General Issues

### Issue: Games Not Loading in Modal

**Symptoms**: Clicking a game shows nothing or an error.

**Causes**:
- Invalid embed URL
- CORS restrictions
- Game provider blocks embedding
- HTTPS required but not available

**Workaround**:
1. Test the embed URL directly in browser
2. Use HTTPS URLs
3. Try a different game source
4. Contact the game provider

---

### Issue: Offline Page Shows Immediately

**Symptoms**: The offline page appears even with internet.

**Causes**:
- Opening file directly (`file://` protocol)
- Service worker issues
- Browser restrictions

**Workaround**:
1. Use a local server (`python -m http.server`)
2. Deploy to a proper hosting service
3. Clear browser cache

---

### Issue: Favorites Not Persisting

**Symptoms**: Favorite games reset after page refresh.

**Causes**:
- localStorage disabled
- Private/incognito browsing
- Browser storage full

**Workaround**:
1. Enable cookies/localStorage
2. Exit private browsing mode
3. Clear browser data
4. Try a different browser

---

### Issue: Theme Not Saving

**Symptoms**: Theme preference resets on reload.

**Cause**: Same as favorites - localStorage issue.

**Workaround**: See favorites workaround above.

---

## CSS/Styling Issues

### Issue: Glassmorphism Not Showing

**Symptoms**: Semi-transparent blur effect not visible.

**Cause**: Browser doesn't support `backdrop-filter`.

**Affected Browsers**: Safari < 15.4, older browsers

**Workaround**: Add fallback background:
```css
.game-card {
    background: rgba(30, 30, 46, 0.95);
    backdrop-filter: blur(20px);
}
```

---

### Issue: Icons Not Showing

**Symptoms**: Font Awesome icons appear as boxes or squares.

**Cause**: Font Awesome CDN not loading.

**Workaround**:
1. Check internet connection
2. Try a different CDN
3. Download Font Awesome locally

---

### Issue: Gradient Text Not Working

**Symptoms**: Logo/title shows as solid color.

**Cause**: Browser doesn't support `-webkit-background-clip: text`.

**Workaround**: Use solid color instead:
```css
.logo {
    color: var(--primary);
}
```

---

## JavaScript Issues

### Issue: "undefined" Error in Console

**Symptoms**: JavaScript errors about undefined variables.

**Cause**: Missing or incorrect script loading.

**Workaround**:
1. Check script is loaded
2. Verify function names match
3. Check for typos

---

### Issue: Search Not Working

**Symptoms**: Typing in search box shows no results.

**Cause**: Event listener not attached.

**Workaround**: Verify the event listener:
```javascript
searchInput.addEventListener('input', () => {
    renderGames(getFilteredGames());
});
```

---

### Issue: Category Filter Not Working

**Symptoms**: Clicking category does nothing.

**Cause**: `data-category` doesn't match game `category`.

**Workaround**: Ensure exact match:
```html
<button data-category="Action">...</button>
```
```javascript
{ category: "Action" }  // Must match exactly
```

---

## Deployment Issues

### Issue: 404 Error After Deployment

**Symptoms**: "Not Found" error on deployed site.

**Cause**: Files not in correct directory.

**Workaround**:
1. Ensure `index.html` is in root
2. Check GitHub Pages source settings
3. Wait a few minutes for propagation

---

### Issue: Custom Domain Not Working

**Symptoms**: Domain shows error or doesn't load.

**Cause**: DNS not configured correctly.

**Workaround**:
1. Wait up to 48 hours for DNS
2. Verify DNS records
3. Check hosting settings
4. Clear DNS cache

---

### Issue: HTTPS Not Working

**Symptoms**: Mixed content warnings or blocked resources.

**Cause**: Some resources using HTTP.

**Workaround**:
1. Update all URLs to HTTPS
2. Enable "Enforce HTTPS" in settings
3. Wait for certificate provisioning

---

## Mobile Issues

### Issue: Touch Targets Too Small

**Symptoms**: Hard to tap buttons on mobile.

**Workaround**: The template already has responsive styles. Ensure:
```css
.category-btn, .play-btn {
    min-height: 44px;  /* Apple recommended */
}
```

---

### Issue: Game Not Fullscreen on Mobile

**Symptoms**: Game modal doesn't fill screen properly.

**Workaround**: Add to CSS:
```css
.modal-container {
    height: 100vh;
    border-radius: 0;
}
```

---

## Browser-Specific Issues

### Safari Issues

**Issue**: Scroll bounce effect
**Fix**: Add to CSS:
```css
body {
    overscroll-behavior: none;
}
```

### Firefox Issues

**Issue**: Smooth scroll not working
**Fix**: Add:
```css
html {
    scroll-behavior: smooth;
}
```

### Edge Issues

**Issue**: Older Edge versions
**Fix**: Ensure Chromium-based Edge (version 79+)

---

## Performance Issues

### Issue: Slow Initial Load

**Cause**: Large number of games or large images.

**Workaround**:
1. Compress images
2. Use lazy loading (already implemented)
3. Reduce initial game count
4. Use image CDN

---

### Issue: Janky Animations

**Cause**: Browser can't keep up with animations.

**Workaround**:
```css
* {
    animation: none !important;
}
```

Or reduce animation complexity.

---

## Reporting New Issues

If you find a new issue:

1. Check this list first
2. Check browser console for errors
3. Test in different browser
4. Document steps to reproduce
5. Report on GitHub Issues

---

*Need more help? [Contact us](help.md)*
