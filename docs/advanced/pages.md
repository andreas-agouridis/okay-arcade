# Adding New Pages

**Create additional pages and modals for your Okay Arcade.**

---

## Overview

Okay Arcade uses **modal dialogs** for additional pages (Privacy, Terms, Contact, About, FAQ). This guide shows how to add or modify these pages.

---

## Page Structure

Pages are defined in the `pageContent` object (around line 2855):

```javascript
const pageContent = {
    privacy: {
        title: 'Privacy Policy',
        content: `<h2>Section Title</h2><p>Content here...</p>`
    },
    terms: {
        title: 'Terms of Service',
        content: `...`
    },
    // Add more pages here
};
```

---

## Adding a New Page

### Step 1: Add Page Content

Add to the `pageContent` object:

```javascript
const pageContent = {
    // ... existing pages ...
    
    mypage: {
        title: 'My Custom Page',
        content: `
            <h2>Welcome to My Page</h2>
            <p>This is my custom page content.</p>
            
            <h2>Section Two</h2>
            <p>More content here.</p>
            
            <ul>
                <li>Item one</li>
                <li>Item two</li>
                <li>Item three</li>
            </ul>
            
            <p>Contact: <a href="mailto:email@example.com">email@example.com</a></p>
        `
    }
};
```

### Step 2: Add Trigger Link

Add a link that opens your page. In the footer or navigation:

```html
<!-- In footer -->
<a href="#" class="footer-link" data-page="mypage">
    <i class="fas fa-icon"></i> My Page
</a>

<!-- Or in navigation -->
<a href="#" class="nav-link" data-page="mypage">
    <i class="fas fa-icon"></i> My Page
</a>
```

### Step 3: Test

Click your link and verify the modal opens with correct content.

---

## HTML Content in Pages

### Headings
```html
<h2>Main Section</h2>
```

### Paragraphs
```html
<p>Regular paragraph text.</p>
```

### Lists
```html
<ul>
    <li>Unordered item</li>
</ul>

<ol>
    <li>Ordered item</li>
</ol>
```

### Links
```html
<a href="https://example.com">External link</a>
<a href="mailto:email@example.com">Email link</a>
<a href="#" data-page="privacy">Internal page link</a>
```

### Emphasis
```html
<strong>Bold text</strong>
<em>Italic text</em>
```

### Highlight Box
```html
<div class="highlight-box">
    <p>Important information highlighted.</p>
</div>
```

### Contact Information
```html
<div class="contact-info">
    <div class="contact-item">
        <i class="fas fa-envelope"></i>
        <div class="contact-item-content">
            <h4>Email</h4>
            <p><a href="mailto:email@example.com">email@example.com</a></p>
        </div>
    </div>
</div>
```

---

## Page Examples

### Privacy Policy
```javascript
privacy: {
    title: 'Privacy Policy',
    content: `
        <h2>1. Information We Collect</h2>
        <p>We collect minimal information to provide our service...</p>
        
        <h2>2. How We Use Information</h2>
        <p>We use collected information to...</p>
        
        <h2>3. Contact</h2>
        <p>Email: <a href="mailto:privacy@example.com">privacy@example.com</a></p>
    `
}
```

### Contact Page
```javascript
contact: {
    title: 'Contact Us',
    content: `
        <h2>Get In Touch</h2>
        <p>We'd love to hear from you!</p>
        
        <div class="contact-info">
            <div class="contact-item">
                <i class="fas fa-envelope"></i>
                <div class="contact-item-content">
                    <h4>Email</h4>
                    <p><a href="mailto:contact@example.com">contact@example.com</a></p>
                </div>
            </div>
            <div class="contact-item">
                <i class="fas fa-twitter"></i>
                <div class="contact-item-content">
                    <h4>Twitter</h4>
                    <p><a href="https://twitter.com/yourhandle">@yourhandle</a></p>
                </div>
            </div>
        </div>
    `
}
```

### Terms of Service
```javascript
terms: {
    title: 'Terms of Service',
    content: `
        <h2>1. Acceptance</h2>
        <p>By using this site, you agree to these terms...</p>
        
        <h2>2. Use of Service</h2>
        <p>You agree to use this service responsibly...</p>
        
        <h2>3. Disclaimer</h2>
        <p>Games are provided "as is"...</p>
    `
}
```

---

## Cross-Linking Pages

Link between pages within modals:

```javascript
about: {
    title: 'About Us',
    content: `
        <h2>About</h2>
        <p>Read our <a href="#" data-page="privacy">Privacy Policy</a> and 
        <a href="#" data-page="terms">Terms of Service</a>.</p>
    `
}
```

---

## Removing Pages

### Remove Footer Link
Delete the `<a>` element with `data-page="pagename"`.

### Remove Page Content
Delete the page object from `pageContent`:

```javascript
// Delete this
privacy: { ... }
```

### Disable Page Completely
Comment out or remove the page modal HTML (lines 2356-2366).

---

## Custom Page Styles

Add custom CSS for your page content:

```css
.page-modal-body .custom-class {
    /* Your styles */
}

.page-modal-body h2 {
    color: var(--accent);
}

.page-modal-body a {
    color: var(--primary);
}
```

---

## Opening Pages Programmatically

Open a page via JavaScript:

```javascript
openPageModal('mypage');
```

Close the page modal:

```javascript
closePageModalHandler();
```

---

## Accessibility Tips

1. Use semantic HTML (`<h2>`, `<p>`, `<ul>`)
2. Add descriptive link text
3. Ensure sufficient color contrast
4. Test with screen readers

---

## Next Steps

- **[Branding Guide](../customization/branding.md)** - Customize appearance
- **[SEO Guide](../customization/seo.md)** - Optimize content
- **[FAQ](../troubleshooting/faq.md)** - Common questions

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
