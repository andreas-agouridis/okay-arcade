# Deployment Guide

**Deploy your Okay Arcade to production - free hosting options included.**

---

## Deployment Options Overview

| Platform | Cost | Custom Domain | Ease | Best For |
|----------|------|---------------|------|----------|
| **GitHub Pages** | Free | Yes | Easy | Open source projects |
| **Netlify** | Free tier | Yes | Very Easy | Quick deployments |
| **Vercel** | Free tier | Yes | Very Easy | Frontend projects |
| **Cloudflare Pages** | Free | Yes | Easy | Performance |
| **Traditional Hosting** | Varies | Yes | Medium | Full control |

---

## GitHub Pages (Recommended)

GitHub Pages is **free** and perfect for Okay Arcade.

### Step 1: Create Repository
```bash
# Create new repository on GitHub
# Name it: yourusername.github.io (for user site)
# Or: any-name (for project site)
```

### Step 2: Upload Files
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/your-repo.git
git push -u origin main
```

### Step 3: Enable GitHub Pages
1. Go to your repository on GitHub
2. Click **Settings**
3. Scroll to **Pages** section
4. Under **Source**, select **Deploy from a branch**
5. Choose **main** branch and **/ (root)** folder
6. Click **Save**

### Step 4: Access Your Site
Your site will be live at:
- User site: `https://yourusername.github.io`
- Project site: `https://yourusername.github.io/repository-name`

**Note**: It may take a few minutes for the first deployment.

### Custom 404 Page (Optional)
Create a `404.html` file with the same content as `index.html`.

---

## Netlify

### Option A: Drag and Drop
1. Go to [netlify.com](https://netlify.com)
2. Sign up/Login
3. Drag your entire Okay Arcade folder to the deploy area
4. Done! You get a random URL like `random-name.netlify.app`

### Option B: Git Integration
1. Connect your GitHub account
2. Select your Okay Arcade repository
3. Set build command: (leave empty)
4. Set publish directory: `/` (root)
5. Click **Deploy**

### Custom Domain on Netlify
1. Go to **Domain settings**
2. Click **Add custom domain**
3. Enter your domain
4. Update your DNS records as instructed

---

## Vercel

### Deploy with Vercel CLI
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Follow prompts
```

### Deploy via GitHub
1. Go to [vercel.com](https://vercel.com)
2. Import your GitHub repository
3. Click **Deploy**
4. Done!

---

## Cloudflare Pages

1. Go to [pages.cloudflare.com](https://pages.cloudflare.com)
2. Connect your GitHub/GitLab account
3. Select your repository
4. Build settings:
   - Build command: (leave empty)
   - Build output directory: `/`
5. Click **Save and Deploy**

---

## Traditional Web Hosting

### Using FTP/SFTP

1. **Get hosting** (e.g., Bluehost, HostGator, Namecheap)
2. **Upload files** via FTP client (FileZilla, Cyberduck)

```
Upload to: /public_html/ or /www/
Files needed:
- index.html
- manifest.json (optional)
- sw.js (optional)
```

3. **Set index.html** as the default document (usually automatic)

### Using cPanel
1. Log into cPanel
2. Go to **File Manager**
3. Navigate to `public_html`
4. Upload `index.html`
5. Done!

---

## Custom Domain Setup

### Step 1: Buy a Domain
Purchase from: Namecheap, Google Domains, Cloudflare Registrar, etc.

### Step 2: Configure DNS

#### For GitHub Pages
Add these DNS records at your domain registrar:

**ALIAS/ANAME Record:**
```
Name: @
Value: yourusername.github.io
```

**Or A Records:**
```
Name: @
Value: 185.199.108.153

Name: @
Value: 185.199.109.153

Name: @
Value: 185.199.110.153

Name: @
Value: 185.199.111.153
```

#### For Netlify
Add DNS record:
```
Type: CNAME
Name: www
Value: random-name.netlify.app
```

### Step 3: Enable HTTPS
- **GitHub Pages**: Automatic with custom domain
- **Netlify**: Automatic Let's Encrypt
- **Cloudflare**: Free SSL automatically

---

## Performance Optimization

### Enable Compression
Most platforms enable this automatically.

### Cache Headers
Add a `_headers` file (Netlify) or configure in your hosting:
```
/*
  Cache-Control: public, max-age=31536000
```

### Image Optimization
- Use WebP format for thumbnails
- Implement lazy loading (already done in template)
- Use responsive images

---

## Updating Your Deployment

### GitHub Pages
```bash
git add .
git commit -m "Update: description of changes"
git push
```
Changes go live automatically (1-2 minutes).

### Netlify/Vercel
Same git push process - auto-deploys on push.

---

## SSL/HTTPS

### Why HTTPS is Important
- Required for Service Workers
- Required for geolocation
- Better SEO ranking
- User trust

### Getting Free SSL
| Platform | SSL |
|----------|-----|
| GitHub Pages | Automatic |
| Netlify | Automatic (Let's Encrypt) |
| Cloudflare | Free SSL |
| Vercel | Automatic |

---

## Environment Variables (Advanced)

If you need to add analytics or API keys:

### Netlify
Create `netlify.toml`:
```toml
[build]
  publish = "."

[context.production.environment]
  ANALYTICS_ID = "your-analytics-id"
```

### Vercel
```bash
vercel env add ANALYTICS_ID
```

---

## Troubleshooting Deployment

### Site Shows 404
- Ensure `index.html` is in the root directory
- Check branch settings in GitHub Pages
- Wait a few minutes for propagation

### Changes Not Showing
- Clear browser cache (Ctrl+Shift+R)
- Check if deployment completed
- Verify git push was successful

### Custom Domain Not Working
- Wait up to 48 hours for DNS propagation
- Verify DNS records are correct
- Check domain registrar settings

### HTTPS Not Working
- Enable "Enforce HTTPS" in settings
- Wait for certificate provisioning (up to 24 hours)

---

## Deployment Checklist

- [ ] Files uploaded to repository
- [ ] GitHub Pages enabled (or other platform)
- [ ] Custom domain configured (optional)
- [ ] HTTPS enabled
- [ ] Test site on multiple devices
- [ ] Test offline functionality
- [ ] Update all URLs to production domain
- [ ] Submit sitemap to Google Search Console

---

## Next Steps

- **[Custom Domain Guide](advanced/custom-domain.md)** - Detailed domain setup
- **[Analytics Integration](advanced/analytics.md)** - Track visitors
- **[SEO Optimization](customization/seo.md)** - Improve search ranking

---

*Need help? Check [FAQ](troubleshooting/faq.md) or [contact us](troubleshooting/help.md)*
