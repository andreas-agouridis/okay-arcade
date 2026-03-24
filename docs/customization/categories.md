# Categories Guide

**Learn how to customize game categories in Okay Arcade.**

---

## Understanding Categories

Categories help users filter and find games. Each game belongs to one category, and each category has a corresponding filter button.

---

## Default Categories

The main edition comes with these categories:

| Category | Icon | Description |
|----------|------|-------------|
| All Games | `fa-th-large` | Shows all games |
| Action | `fa-fist-raised` | Fighting, combat, adventure |
| Racing | `fa-car` | Car, bike, racing games |
| Sports | `fa-futbol` | Sports simulation games |
| Platformer | `fa-running` | Jump and run games |
| Runner | `fa-forward` | Endless runner games |
| IO Games | `fa-globe` | Multiplayer .io games |

---

## Adding a New Category

### Step 1: Add Category Button

Find the categories section (around line 2283) and add your button:

```html
<div class="categories" id="categories">
    <button class="category-btn active" data-category="all">
        <i class="fas fa-th-large"></i> All Games
    </button>
    <!-- Existing buttons... -->
    
    <!-- ADD YOUR NEW CATEGORY -->
    <button class="category-btn" data-category="Puzzle">
        <i class="fas fa-puzzle-piece"></i> Puzzle
    </button>
</div>
```

### Step 2: Add Games with That Category

```javascript
const games = [
    {
        name: "Puzzle Game 1",
        embedUrl: "https://...",
        imageUrl: "https://...",
        category: "Puzzle"  // Must match the data-category exactly!
    },
    {
        name: "Puzzle Game 2",
        embedUrl: "https://...",
        imageUrl: "https://...",
        category: "Puzzle"
    }
];
```

### Step 3: Test

1. Save the file
2. Refresh your browser
3. Click the new category button
4. Verify games filter correctly

---

## Category Button Anatomy

```html
<button class="category-btn" data-category="CategoryName">
    <i class="fas fa-icon-name"></i> Category Label
</button>
```

| Attribute | Purpose |
|-----------|---------|
| `class="category-btn"` | Styling class |
| `data-category="Name"` | Category identifier (must match game category) |
| `<i class="fas fa-icon">` | Font Awesome icon |
| Text after icon | Display label |

---

## Available Font Awesome Icons

### Gaming Icons
```html
<i class="fas fa-gamepad"></i>        <!-- Gamepad -->
<i class="fas fa-dice"></i>           <!-- Dice -->
<i class="fas fa-chess"></i>          <!-- Chess -->
<i class="fas fa-puzzle-piece"></i>   <!-- Puzzle -->
<i class="fas fa-car"></i>            <!-- Car (Racing) -->
```

### Action Icons
```html
<i class="fas fa-fist-raised"></i>    <!-- Fist (Action) -->
<i class="fas fa-crosshairs"></i>     <!-- Target -->
<i class="fas fa-bolt"></i>           <!-- Lightning -->
<i class="fas fa-fire"></i>           <!-- Fire -->
<i class="fas fa-shield-alt"></i>     <!-- Shield -->
```

### Sports Icons
```html
<i class="fas fa-futbol"></i>         <!-- Soccer ball -->
<i class="fas fa-basketball-ball"></i><!-- Basketball -->
<i class="fas fa-table-tennis"></i>   <!-- Ping pong -->
<i class="fas fa-running"></i>        <!-- Running -->
<i class="fas fa-swimmer"></i>        <!-- Swimming -->
```

### Other Icons
```html
<i class="fas fa-globe"></i>          <!-- Globe (IO) -->
<i class="fas fa-music"></i>          <!-- Music -->
<i class="fas fa-brain"></i>          <!-- Brain (Puzzle) -->
<i class="fas fa-magic"></i>          <!-- Magic -->
<i class="fas fa-rocket"></i>         <!-- Rocket -->
```

Find more at [Font Awesome Icons](https://fontawesome.com/icons)

---

## Removing Categories

To remove a category:

1. **Delete the button** from HTML:
```html
<!-- DELETE this entire line -->
<button class="category-btn" data-category="Runner">...</button>
```

2. **Update games** using that category:
```javascript
// Change category for affected games
{
    name: "My Game",
    category: "Action"  // Changed from "Runner"
}
```

---

## Renaming Categories

### Step 1: Update Button
```html
<!-- Before -->
<button class="category-btn" data-category="Platformer">
    <i class="fas fa-running"></i> Platformer
</button>

<!-- After -->
<button class="category-btn" data-category="Platformer">
    <i class="fas fa-mountain"></i> Jump & Run
</button>
```

Note: Keep `data-category` the same, only change the display text.

### Step 2: Or Change Category Completely

If you want to change the category name entirely:

1. Change `data-category` value
2. Update all games with that category
3. Update button label

```html
<button class="category-btn" data-category="Adventure">
    <i class="fas fa-hiking"></i> Adventure
</button>
```

```javascript
{
    name: "My Game",
    category: "Adventure"  // Updated from "Platformer"
}
```

---

## Category-Specific Styling

### Add Category Colors (Optional CSS)

Add this to your `<style>` section:

```css
/* Category-specific badge colors in game cards */
.game-card[data-category="Action"] .game-category {
    color: #ef4444;
}

.game-card[data-category="Racing"] .game-category {
    color: #f97316;
}

.game-card[data-category="Sports"] .game-category {
    color: #22c55e;
}

.game-card[data-category="Puzzle"] .game-category {
    color: #8b5cf6;
}
```

---

## Using Categories in Simple UI Edition

The Simple UI edition uses a simpler category system:

```html
<div class="filters" id="filterGroup">
    <button data-cat="all" class="filter-chip active">All</button>
    <button data-cat="Action" class="filter-chip">Action</button>
    <button data-cat="Racing" class="filter-chip">Racing</button>
    <button data-cat="Puzzle" class="filter-chip">Puzzle</button>
    <button data-cat="Sports" class="filter-chip">Sports</button>
</div>
```

Note: Uses `data-cat` instead of `data-category`.

---

## Using Categories in Terminal Edition

Terminal edition filters via commands:

```
> filter action     # Filter by action games
> filter racing     # Filter by racing games
> filter all        # Show all games
```

Valid filters: `all`, `action`, `racing`, `puzzle`, `sports`

---

## Category Best Practices

### 1. Keep Categories Balanced
- Aim for 5-10 categories maximum
- Ensure games are distributed across categories
- Avoid categories with only 1-2 games

### 2. Use Clear Names
- Keep category names short (1-2 words)
- Use commonly understood terms
- Avoid abbreviations

### 3. Consistent Naming
```javascript
// Good - consistent case
category: "Action"
category: "Racing"

// Bad - inconsistent
category: "action"
category: "ACTION"
category: "Action Game"
```

### 4. Match Data Exactly
The `data-category` attribute must match the game's `category` exactly:

```html
<!-- Button -->
<button data-category="Puzzle">Puzzle</button>

<!-- Game -->
{ category: "Puzzle" }  // ✓ Match!
{ category: "puzzle" }  // ✗ No match!
```

---

## Complete Example: Adding Adventure Category

### HTML (in categories div):
```html
<button class="category-btn" data-category="Adventure">
    <i class="fas fa-mountain"></i> Adventure
</button>
```

### Games:
```javascript
const games = [
    {
        name: "Temple Quest",
        embedUrl: "https://...",
        imageUrl: "https://...",
        category: "Adventure"
    },
    {
        name: "Jungle Explorer",
        embedUrl: "https://...",
        imageUrl: "https://...",
        category: "Adventure"
    }
];
```

---

## Troubleshooting

### Category Not Filtering
**Problem**: Clicking category shows no games

**Solutions**:
1. Check `data-category` matches game `category` exactly
2. Ensure games exist with that category
3. Check browser console for JavaScript errors

### Category Button Not Highlighting
**Problem**: Active state not working

**Solution**: Ensure the button has the correct class structure:
```html
<button class="category-btn" data-category="Name">
```

### Missing Icon
**Problem**: Icon not showing

**Solution**: 
1. Ensure Font Awesome is loaded
2. Check icon name is correct
3. Verify `fas` class is present

---

## Next Steps

- **[Adding Games](adding-games.md)** - Add games to your categories
- **[Branding Guide](branding.md)** - Customize appearance
- **[Editions Guide](../editions/main.md)** - Learn about different editions

---

*Need help? Check [FAQ](../troubleshooting/faq.md)*
