# Adventure Ledger 2.2 — Usability update

Responsive interface update based on the existing v2.1 app and Firestore data model.

## What's changed
- DM dashboard shows one card per player, with HP, AC, item count, and direct **Inventory**, **Award**, and **Character** actions.
- Inventory tab has visible player/party selectors for DMs; awards launched from a player card preselect that recipient.
- Players see **My inventory** first, with shared party supplies collapsible underneath.
- Character view starts with HP, AC, gold, and an inventory shortcut; full editing form is expandable.
- Common touch targets enlarged; phone navigation scrolls horizontally and stays visible.
- Custom item creation is collapsible to reduce screen clutter.
- Asset cache-busting query strings (`?v=2.2`) help avoid stale JavaScript after deployment.

## Installation
1. Back up your current repository (Code > Download ZIP).
2. Upload **index.html**, **app.js**, and **styles.css** to the root of your GitHub repository, replacing the existing versions. Keep **firebase-config.js** unchanged if you've customized it.
3. Commit to `main`, wait for GitHub Pages deployment, and refresh the site.

**No Firestore rules or database migration required.** The included `firestore.rules` is a copy of the existing v2.1 rules for reference, not an instruction to republish them.

## Test
1. Sign in as DM and open a campaign; choose Inventory on a character card, then Award on that same card.
2. Award a starter item; check the recipient's inventory and verify the item appears for that player.
3. Test on a phone-sized screen and on a tablet/laptop.

## Known limitations
- This is a responsive UI redesign, not a new equipment or rules engine.
- Character form is still reconstructed on Firestore snapshot updates, so save detailed edits before switching tabs.
- The app still requires internet access; offline/PWA support is not included.
- This package has been statically checked, but has not been tested against your live Firebase project.
