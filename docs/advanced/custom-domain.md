# Custom Domain Setup

**Use your own domain name with Okay Arcade.**

---

## Overview

This guide covers setting up a custom domain with:
- GitHub Pages
- Netlify
- Other hosting providers

---

## Prerequisites

Before starting:
- A registered domain name
- Access to your domain's DNS settings
- A hosting account (GitHub, Netlify, etc.)

---

## Step 1: Update Site URLs

Before configuring DNS, update URLs in your `index.html`:

### Replace All Occurrences
Find and replace:
- `okay.agouridis.site` → `yourdomain.com`
- `https://okay.agouridis.site` → `https://yourdomain.com`

### Locations to Update
1. `<title>` tag
2. `<link rel="canonical">`
3. Meta tags (og:url, twitter:url)
4. Structured data
5. Footer links

---

## Step 2: GitHub Pages Setup

### For User Site (username.github.io)
1. Go to repository **Settings** → **Pages**
2. Under **Custom domain**, enter your domain
3. Click **Save**
4. Check **Enforce HTTPS** (wait a few minutes)

### For Project Site
1. Same as above
2. GitHub will create a CNAME file automatically

### DNS Configuration for GitHub Pages

Add these DNS records at your domain registrar:

**Option A: A Records (Recommended)**
```
Type: A
Name: @
Value: 185.199.108.153

Type: A
Name: @
Value: 185.199.109.153

Type: A
Name: @
Value: 185.199.110.153

Type: A
Name: @
Value: 185.199.111.153
```

**Option B: CNAME Record**
```
Type: CNAME
Name: www
Value: yourusername.github.io
```

### CNAME File (Optional)
Create a `CNAME` file in your repository:
```
yourdomain.com
```

---

## Step 3: Netlify Setup

### Custom Domain in Netlify
1. Go to your site's **Domain settings**
2. Click **Add custom domain**
3. Enter your domain (e.g., `yourdomain.com`)
4. Click **Verify** → **Yes, add domain**

### DNS Configuration for Netlify

**Option A: Netlify DNS (Recommended)**
1. In Netlify, go to **Domain settings** → **DNS management**
2. Click **Set up Netlify DNS**
3. Update nameservers at your registrar to:
   ```
   dns1.p05.nsone.net
   dns2.p05.nsone.net
   dns3.p05.nsone.net
   dns4.p05.nsone.net
   ```

**Option B: External DNS**
Add at your registrar:
```
Type: CNAME
Name: www
Value: your-site-name.netlify.app

Type: A
Name: @
Value: 75.2.60.5
```

### Enable HTTPS
1. Netlify provides free Let's Encrypt SSL
2. Go to **Domain settings** → **HTTPS**
3. Click **Provision certificate**

---

## Step 4: Vercel Setup

### Add Domain in Vercel
1. Go to your project **Settings** → **Domains**
2. Add your domain
3. Configure DNS as instructed

### DNS Configuration for Vercel
```
Type: CNAME
Name: www
Value: cname.vercel-dns.com

Type: A
Name: @
Value: 76.76.21.21
```

---

## Step 5: Cloudflare Setup (Optional CDN)

Cloudflare provides free CDN, DNS, and SSL:

### Add Your Domain
1. Create Cloudflare account
2. Add your site
3. Cloudflare provides nameservers

### Update Nameservers
At your registrar, update to Cloudflare's nameservers:
```
name1.cloudflare.com
name2.cloudflare.com
```

### Configure DNS in Cloudflare
Add records pointing to your host:
```
Type: CNAME
Name: www
Value: yourusername.github.io
Proxy: Enabled (orange cloud)

Type: A
Name: @
Value: 185.199.108.153
Proxy: Enabled
```

### SSL Settings
1. Go to **SSL/TLS** → **Overview**
2. Set to **Full (strict)**
3. Enable **Always Use HTTPS**

---

## DNS Providers

### Popular Domain Registrars with DNS
| Provider | DNS Management |
|----------|----------------|
| Namecheap | Advanced DNS tab |
| Google Domains | DNS management |
| GoDaddy | DNS Management |
| Cloudflare Registrar | Automatic |
| Porkbun | DNS Records |

---

## Common DNS Records

### A Record (Points to IP)
```
Type: A
Name: @
TTL: Auto
Value: 185.199.108.153
```

### CNAME Record (Points to hostname)
```
Type: CNAME
Name: www
TTL: Auto
Value: yourhost.github.io
```

### AAAA Record (IPv6)
```
Type: AAAA
Name: @
TTL: Auto
Value: (provided by host)
```

---

## Testing DNS

### Wait for Propagation
DNS changes can take 24-48 hours (usually faster).

### Check DNS Propagation
- [whatsmydns.net](https://www.whatsmydns.net)
- [dnschecker.org](https://dnschecker.org)

### Command Line
```bash
# Check A record
nslookup yourdomain.com

# Check CNAME
nslookup www.yourdomain.com

# Or use dig
dig yourdomain.com
```

---

## HTTPS/SSL Certificate

### Free SSL Options
| Provider | SSL Type |
|----------|----------|
| GitHub Pages | Automatic |
| Netlify | Let's Encrypt (Free) |
| Vercel | Automatic |
| Cloudflare | Free Universal SSL |

### Enable HTTPS
1. Wait for DNS to propagate
2. Enable "Enforce HTTPS" in hosting settings
3. Wait for certificate provisioning (up to 24 hours)

---

## Subdomain Setup

### Using www subdomain
```
Type: CNAME
Name: www
Value: yourhost.github.io
```

### Using app subdomain
```
Type: CNAME
Name: app
Value: yourhost.github.io
```

Result: `app.yourdomain.com`

---

## Apex Domain vs www

### Apex Domain (yourdomain.com)
Use A records pointing to IP addresses.

### www Subdomain (www.yourdomain.com)
Use CNAME pointing to host.

### Best Practice: Use Both
Set up both and redirect one to the other:
- Redirect `www` → apex, OR
- Redirect apex → `www`

---

## Troubleshooting

### DNS Not Resolving
1. Wait longer (up to 48 hours)
2. Check DNS records are correct
3. Flush local DNS cache:
   - Windows: `ipconfig /flushdns`
   - Mac: `sudo dscacheutil -flushcache`

### Certificate Errors
1. Ensure DNS is properly configured
2. Wait for certificate provisioning
3. Check hosting provider status

### Mixed Content Warnings
1. Update all HTTP URLs to HTTPS
2. Use protocol-relative URLs: `//example.com`

### Site Not Loading
1. Verify DNS records
2. Check hosting status
3. Verify index.html exists
4. Check for firewall/network issues

---

## Quick Reference

### GitHub Pages DNS
```
A Records:
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153

CNAME (www):
yourusername.github.io
```

### Netlify DNS
```
A Record (apex):
75.2.60.5

CNAME (www):
yoursite.netlify.app
```

### Vercel DNS
```
A Record (apex):
76.76.21.21

CNAME (www):
cname.vercel-dns.com
```

---

## Next Steps

- **[SEO Guide](../customization/seo.md)** - Optimize for search
- **[Analytics Guide](analytics.md)** - Track visitors
- **[Deployment Guide](../deployment.md)** - Full deployment guide

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
