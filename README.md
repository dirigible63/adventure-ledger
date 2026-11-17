# Adventure Ledger 2.5 — DM item preparation

## New
- DM can save a custom item to the campaign catalogue **without awarding it**.
- DM can alternatively create and award immediately, as before.
- Prepared catalogue items can later be awarded through the existing equipment catalogue.
- Optional DM-only secret notes are saved separately for prepared items.
- Campaign custom catalogue is DM-only to prevent players seeing unrevealed story items. Standard starter equipment remains available to players.
- Existing campaign inventory and encounters are unchanged.

## Install
Replace `app.js` and `index.html` in GitHub Pages with these files. Publish the included `firestore.rules` in Firebase Console (the itemCatalog read rule changes from campaign members to DM only). Keep `firebase-config.js` unchanged.

## Test
1. Sign in as DM and open a campaign, Inventory > Create custom item.
2. Choose Save to catalogue, enter a name, and save. It should appear in the equipment catalogue, but not anyone's inventory.
3. Later, select a recipient in Award equipment and click Add on the prepared item.
4. Confirm the item appears in the intended character's inventory.
5. Sign in as a player and confirm the unpublished item isn't visible in their catalogue.

JavaScript syntax checked; live Firebase integration not tested.
