# Adding Games Guide

**Learn how to add your own games to Okay Arcade.**

---

## Understanding the Game Data Structure

Games are stored as JavaScript objects in an array. Each game has these properties:

```javascript
{
    name: "Game Name",           // Display name
    embedUrl: "https://...",     // URL to embed the game
    imageUrl: "https://...",     // Thumbnail image URL
    category: "Category"         // Game category
}
```

---

## Step-by-Step: Adding a Game

### Step 1: Open index.html

Find the game data array (around line 2450):

```javascript
const games = [
    {
        name: "Level Devil",
        embedUrl: "https://leveldevilnotatrollgame.io/level-devil-unblocked.embed",
        imageUrl: "https://leveldevilnotatrollgame.io/cache/data/image/game/level-devil-not-a-troll-game-f255x255.webp",
        category: "Platformer"
    },
    // ... more games
];
```

### Step 2: Add Your Game Object

Add a new game object to the array:

```javascript
const games = [
    // ... existing games ...
    {
        name: "My Awesome Game",
        embedUrl: "https://gamesite.com/embed/my-game",
        imageUrl: "https://gamesite.com/images/my-game-thumb.jpg",
        category: "Action"
    }
];
```

### Step 3: Add a Comma

Make sure to add a comma after the previous game object:

```javascript
    {
        name: "Previous Game",
        // ...
    },  // <-- COMMA HERE
    {
        name: "My New Game",
        // ...
    }
];
```

### Step 4: Save and Test

Save the file and refresh your browser to see the new game.

---

## Finding Game URLs

### Method 1: Direct Embed URL
Many game providers offer embed URLs:
- Look for "embed" in the URL
- Example: `https://site.com/embed/game-name`

### Method 2: Inspect Element
1. Go to a gaming website
2. Right-click the game → **Inspect**
3. Find the `<iframe>` element
4. Copy the `src` attribute

### Method 3: Game Portals with Embeds
| Portal | Embed Pattern |
|--------|---------------|
| CrazyGames | `https://www.crazygames.com/embed/GAME-SLUG` |
| Poki | Requires API (see below) |
| GameDistribution | `https://html5.gamedistribution.com/ID/` |
| 1Games | `https://GAMENAME.1games.io/UUID` |

---

## Finding Thumbnail Images

### Option 1: From the Embed Site
- Check the game page for thumbnail
- Right-click → Copy image address
- Look for URLs ending in `.jpg`, `.png`, `.webp`

### Option 2: Create Your Own
- Recommended size: 400x240 pixels or 255x255 pixels
- Use free tools: Canva, Figma, Photopea

### Option 3: Use Placeholder
```javascript
imageUrl: "https://via.placeholder.com/400x240/1e293b/ffffff?text=Game+Name"
```

---

## Game Categories

### Available Categories in Main Edition
The main edition has these categories:

| Category | Icon Class | Description |
|----------|------------|-------------|
| Action | `fa-fist-raised` | Fighting, combat games |
| Racing | `fa-car` | Car, bike racing games |
| Sports | `fa-futbol` | Sports simulation |
| Platformer | `fa-running` | Jump and run games |
| Runner | `fa-forward` | Endless runner games |
| IO Games | `fa-globe` | Multiplayer .io games |

### Adding a New Category

**Step 1: Add the category button** (around line 2284):

```html
<button class="category-btn" data-category="Puzzle"><i class="fas fa-puzzle-piece"></i> Puzzle</button>
```

**Step 2: Use the category in your game:**

```javascript
{
    name: "Puzzle Game",
    // ...
    category: "Puzzle"
}
```

**Step 3: Add the CSS for the icon** (if needed):

```javascript
// In the category button, use any Font Awesome icon:
<i class="fas fa-puzzle-piece"></i>
```

---

## Complete Example: Adding Multiple Games

```javascript
const games = [
    // ... existing games ...

    // NEW: Racing game
    {
        name: "Turbo Racing 3D",
        embedUrl: "https://gamesite.com/embed/turbo-racing",
        imageUrl: "https://gamesite.com/thumbs/turbo-racing.jpg",
        category: "Racing"
    },

    // NEW: Action game
    {
        name: "Ninja Warrior",
        embedUrl: "https://gamesite.com/embed/ninja-warrior",
        imageUrl: "https://gamesite.com/thumbs/ninja-warrior.jpg",
        category: "Action"
    },

    // NEW: Puzzle game (add category button first!)
    {
        name: "Brain Teaser",
        embedUrl: "https://gamesite.com/embed/brain-teaser",
        imageUrl: "https://gamesite.com/thumbs/brain-teaser.jpg",
        category: "Puzzle"
    }
];
```

---

## Adding Games via External JSON (Advanced)

For easier management, you can load games from an external JSON file:

### Step 1: Create games.json
```json
[
    {
        "name": "Game 1",
        "embedUrl": "https://...",
        "imageUrl": "https://...",
        "category": "Action"
    },
    {
        "name": "Game 2",
        "embedUrl": "https://...",
        "imageUrl": "https://...",
        "category": "Racing"
    }
]
```

### Step 2: Modify index.html

Replace the hardcoded array with:

```javascript
// Replace this:
const games = [ ... ];

// With this:
let games = [];

// Add this function:
async function loadGames() {
    try {
        const response = await fetch('games.json');
        games = await response.json();
        renderGames(games);
        animateCounter();
    } catch (error) {
        console.error('Failed to load games:', error);
    }
}

// Call loadGames() instead of the original init
loadGames();
```

---

## Game Embed Best Practices

### 1. Test Before Adding
Always test embed URLs before adding to your site:
- Open the URL directly in a browser
- Ensure it loads properly
- Check for any restrictions

### 2. HTTPS Only
Always use HTTPS URLs:
```javascript
// Good
embedUrl: "https://game.com/embed/game"

// Bad (will cause issues)
embedUrl: "http://game.com/embed/game"
```

### 3. Valid Image URLs
Ensure images are publicly accessible:
- Test by opening image URL in browser
- Use direct image links, not HTML pages
- Consider using CDN for reliability

### 4. Consistent Categories
Use consistent category names throughout:
```javascript
// Good - consistent
category: "Action"
category: "Action"

// Bad - inconsistent
category: "action"
category: "Action"
category: "ACTION"
```

---

## Removing Games

To remove a game, simply delete its object from the array:

```javascript
const games = [
    {
        name: "Game to Keep",
        // ...
    },
    // DELETE this entire object:
    // {
    //     name: "Game to Remove",
    //     // ...
    // },
    {
        name: "Another Game to Keep",
        // ...
    }
];
```

---

## Editing Existing Games

Modify the properties directly:

```javascript
// Original
{
    name: "Old Name",
    embedUrl: "https://old-url.com/embed",
    imageUrl: "https://old-url.com/thumb.jpg",
    category: "Action"
}

// Updated
{
    name: "New Name",                    // Changed
    embedUrl: "https://new-url.com/embed",  // Changed
    imageUrl: "https://new-url.com/thumb.jpg",  // Changed
    category: "Racing"                   // Changed
}
```

---

## Game Data Template

Copy this template for each new game:

```javascript
{
    name: "",
    embedUrl: "",
    imageUrl: "",
    category: ""
}
```

---

## Troubleshooting

### Game Not Showing
- Check for syntax errors (missing commas, brackets)
- Verify embed URL is valid
- Check browser console for errors

### Game Not Loading in Modal
- Ensure embed URL uses HTTPS
- Check if the game provider allows embedding
- Try opening embed URL directly

### Thumbnail Not Loading
- Verify image URL is correct
- Check if image is publicly accessible
- Use a different image hosting service

### Category Not Filtering
- Ensure category name matches exactly
- Add the category button to HTML
- Check for typos in category names

---

## Next Steps

- **[Categories Guide](categories.md)** - Create custom categories
- **[Branding Guide](branding.md)** - Customize appearance
- **[Deployment Guide](deployment.md)** - Deploy your site

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
