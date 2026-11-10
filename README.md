# RE/WIND - A Journey Through Time (India edition)

A multi-page vintage-editorial nostalgia website about Indian culture, 1970s-2000s.
Built with **HTML5, CSS3 and Bootstrap 5 (CSS only)** - no JavaScript, no SVG, no APIs, no font CDN.

## How to run
Extract the ZIP, then open `index.html`. Bootstrap's stylesheet loads from the jsDelivr CDN (same setup as before),
so you need internet for the Bootstrap grid.

## Pages
index, explore, 70s, 80s, 90s, 2000s, moments, about (.html). Shared styles: `css/style.css`.

## Fonts
The Google Fonts link was removed (no external font APIs). `--serif` still lists 'Playfair Display' first and
`--sans` 'Source Sans 3' first, so machines with those fonts installed show them; others fall back to Georgia / Arial.
To bundle them yourself, put the .woff2 files in `fonts/` and add an `@font-face` block to `css/style.css`.

## Viva cheat-sheet
- **Mobile menu without JS:** hidden checkbox + `<label>`; CSS `:checked ~ .main-nav` shows the menu.
- **Colours/fonts:** CSS variables in `:root`; one change updates the whole site.
- **Images:** sepia look is a static `filter: sepia()`. There are no image hover effects anywhere.
- **Timeline vertical line:** see below.

### How the timeline line is made (moments.html)
- `<ol class="timeline">` has `position: relative`.
- `.timeline::before { content:""; position:absolute; left:10px; top:0; bottom:0; border-left:2px solid var(--brown); }`
  is an empty pseudo-element stretched from the top to the bottom of the list; its left border *is* the line.
- Each `<li class="t-item">` has `position: relative` and its own `::before` - a 16px circle
  (`border-radius:50%`, orange fill, ivory ring) placed on the line with `left:3px`.
- From 992px up, the line moves to the centre (`left:50%`), each item takes 50% width, and
  `.t-item:nth-child(even)` gets `margin-left:50%`, so entries alternate left/right of the line.
