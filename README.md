# Adventure Ledger 2.3 — Character sheet enhancements

Based on Adventure Ledger 2.2. Keeps the same Firebase project and existing character documents.

## New
- Dropdowns for 2024 Player's Handbook species (10), classes (12), backgrounds (16), and alignments (9 plus Unaligned).
- **Custom / Other** for all four dropdowns, including preservation of older nonstandard character values.
- Proficiency bonus calculated from level (1–20).
- Six ability modifiers calculated from ability scores.
- Eighteen skill proficiency checkboxes, with live skill bonus previews.
- Saved `background`, `alignment`, and `skillProficiencies` fields in each character document.

## Deploy
1. Back up your GitHub repository.
2. Replace `index.html`, `app.js`, and `styles.css` in the repo root with these files.
3. Leave your existing `firebase-config.js` and Firestore rules unchanged.
4. Commit, wait for GitHub Pages, then hard-refresh.

## Test
- Open a character, choose species/class/background/alignment, and save.
- Try Custom / Other; save, reopen, verify custom text persists.
- Change STR from 10 to 16: modifier should change from +0 to +3.
- At level 5 proficiency bonus should show +3. Checking Athletics with STR 16 should show +6.
- Verify previous inventory and DM award actions still work.

## Scope
This is a calculated **reference sheet**, not a full rules engine. Saving a character does not automatically change AC, HP, spellcasting, class proficiencies, or saving throws. No dice roller, subclasses, multiclassing, expertise, or class-derived skill selections yet.

Static JS syntax validated. Live Firebase integration not tested.
