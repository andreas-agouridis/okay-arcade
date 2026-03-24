# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 2.x     | ✅ Yes             |
| 1.x     | ❌ No (EOL)       |
| < 1.0   | ❌ No             |

---

## Reporting a Vulnerability

We take security seriously at Okay Arcade. If you discover a security vulnerability, please report it responsibly.

### How to Report

**Email:** mydreamz.agency@agouridis.tech

**Subject:** `[SECURITY] Vulnerability Report - Okay Arcade`

Please include the following information in your report:

1. **Description** - What is the vulnerability?
2. **Impact** - What could an attacker achieve?
3. **Steps to Reproduce** - How can we reproduce the issue?
4. **Affected Version** - Which version(s) are affected?
5. **Suggested Fix** - If you have a solution (optional)

### What to Expect

| Timeframe | Action |
|-----------|--------|
| Within 48 hours | Acknowledgment of your report |
| Within 7 days | Initial assessment and severity rating |
| Within 14 days | Status update on the fix |
| After fix | Public disclosure (with credit to reporter) |

### Response Commitments

- We will acknowledge receipt within **48 hours**
- We will provide a detailed response within **7 days**
- We will work on a fix for confirmed vulnerabilities
- We will credit you in the release notes (unless you prefer anonymity)

---

## Security Best Practices for Users

### For Self-Hosters

1. **Keep Updated** - Always use the latest version
2. **HTTPS Only** - Never deploy over HTTP in production
3. **Validate Game URLs** - Only add games from trusted sources
4. **Content Security Policy** - Implement CSP headers
5. **Regular Audits** - Review your customizations periodically

### Game Embed Security

When adding games to your arcade:

- ✅ Use HTTPS URLs only
- ✅ Verify the game provider is reputable
- ✅ Test embeds in isolation before adding
- ❌ Never embed games from unknown sources
- ❌ Don't allow user-submitted game URLs without validation

### Recommended Security Headers

```http
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline' https://cdnjs.cloudflare.com; style-src 'self' 'unsafe-inline' https://cdnjs.cloudflare.com; img-src 'self' data: https:; frame-src https:;
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=()
```

---

## Known Security Considerations

### External Game Embeds

Okay Arcade loads games via iframes from third-party sources. This means:

- Third-party games may have their own privacy policies
- Game providers may set their own cookies
- We cannot control third-party game content

**Recommendation:** Review game providers before adding them to your arcade.

### LocalStorage Usage

The application uses localStorage for:
- Favorites list
- Theme preferences
- Offline status tracking

**Note:** LocalStorage is accessible to any JavaScript running on the page. Do not store sensitive information.

### Service Worker

The service worker caches assets for offline functionality. It:
- Only caches assets from your domain
- Does not collect user data
- Can be disabled by users

---

## Scope

### In Scope

- XSS vulnerabilities in the main template
- CSRF vulnerabilities
- Clickjacking vulnerabilities
- Insecure content loading
- Dependency vulnerabilities

### Out of Scope

- Issues in third-party game embeds
- Server-side vulnerabilities (not applicable - static site)
- Social engineering attacks
- Physical access attacks

---

## Vulnerability Disclosure Timeline

| Event | Timeframe |
|-------|-----------|
| Report received | Day 0 |
| Acknowledgment | Day 2 |
| Initial assessment | Day 7 |
| Fix development | Day 7-21 |
| Fix released | Day 21-30 |
| Public disclosure | Day 30+ |

---

## Security Updates

Security updates will be:
- Released as patch versions (e.g., 2.0.1)
- Documented in CHANGELOG.md
- Announced in GitHub Security Advisories
- Tagged with `[SECURITY]` prefix

---

## Contact

For security-related inquiries:

- **Email:** mydreamz.agency@agouridis.tech
- **GitHub Security Advisories:** [Report privately](https://github.com/andreas-agouridis/okay-arcade/security/advisories/new)

---

## Credits

We appreciate security researchers who help keep Okay Arcade safe. Contributors will be credited in:

- Release notes
- SECURITY.md (with permission)
- Hall of Fame (if we create one)

---

## Disclaimer

Okay Arcade is provided "as is" without warranty. While we strive to maintain security, users are responsible for:

- Their own deployment security
- Third-party game content
- Compliance with local laws and regulations
- Proper server configuration

---

*Last Updated: March 2026*
