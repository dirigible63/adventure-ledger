# Adventure Ledger 2.4

Based on the **fixed** 2.3 release.

## Features
- DM-only encounter tracker: create named encounters, mix monster types, add multiple combatants with separate HP/AC, apply damage or healing, reset HP, remove combatants, delete encounters.
- Encounter state is stored in Firestore under `campaigns/{campaignId}/encounters` and updates live across DM sessions.
- Transfer or drop inventory items. Players may transfer their own **whole** item stacks to another character, party supplies, or dropped items. The DM may also split stacks. Dropped items remain in a recoverable shared list. Unidentified stacks cannot be split.
- Preserves the v2.3 character dropdowns and calculations.

## Installation — important
1. Back up your GitHub repository and save a copy of your **existing Firestore rules**.
2. Upload **app.js**, **index.html**, **styles.css** to the GitHub Pages repository root. Keep your existing firebase-config.js.
3. **Update Firestore rules** in Firebase Console with the supplied `firestore.rules`. This release **requires** the new encounter permission and inventory transfer rule. The rules also include the v2.3 character-field permissions.
4. Wait for GitHub Pages to deploy and hard refresh (Ctrl+Shift+R).

## Test
1. Sign in as DM, open a campaign, select **Encounters**. Create Forest Ambush; add 3 goblins (15 HP) and 2 wolves (11 HP). Damage Goblin 1, refresh, confirm HP persists.
2. Award an item to a player; sign in as player, transfer the whole stack to Party supplies, verify it appears there.
3. As DM, split a stack and drop part of it; inspect Dropped items and transfer it back.
4. Verify the character sheet still saves species, class, background, alignment, and skill proficiencies.

## Limitations
- Monster names, AC and HP are manually entered; there is no licensed monster catalogue or initiative tracker yet.
- Only the DM can manage encounters. Monster HP is private to the DM.
- Players can transfer whole stacks; DM can split stacks. There is no separate player-to-player acceptance workflow.
- Encounter data is separate from map locations; Adventure Atlas integration is later.
- Item transfers do not transfer DM-only secret documents when splitting; splitting unidentified items is disabled.
- Rules and syntax were checked locally, but Firebase live integration has not been tested.
