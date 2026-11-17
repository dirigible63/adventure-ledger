# Adventure Ledger 2.1 — Inventory & Treasure

An update to Adventure Ledger 2.0. No build tools required.

## Install

1. Back up the current GitHub repository (Code → Download ZIP) and preserve your existing Firestore data.
2. Firebase Console → Firestore Database → Rules: paste the full contents of `firestore.rules` and click **Publish**. This adds the inventory permissions while retaining the campaign permissions.
3. Upload the six files in this ZIP to the **root** of your existing `adventure-ledger` GitHub repository, replacing matching filenames. Commit directly to `main`.
4. GitHub Actions → wait for a successful Pages deployment. Open the site and hard-refresh with Ctrl+Shift+R.
5. Sign in as DM, open a campaign, and choose the new **Inventory** tab. Add an item to the party or a player. Sign in as a player to verify visibility and restrictions.

## Features

- Searchable built-in **starter** equipment list (13 familiar entries), plus a per-campaign catalogue of DM-created items. The built-in list is intentionally a curated starter, **not** the complete SRD 5.2 catalogue.
- DM creates items on the fly, awards to a player or party, optionally saves to campaign catalogue.
- Players can add mundane gear to their own inventory; only DM can award magic/quest items.
- Item quantities, removal, party inventory and live synchronization.
- Unidentified items can have a public-facing name and description. Secret true names and notes live in a separate DM-only Firestore collection. Unidentified items are not automatically saved into the shared catalogue, preventing a secret-name leak.
- The previous free-text character inventory remains as **Legacy inventory notes** so nothing is lost.

## Current limitations / next steps

- This is a starter catalogue, not a licensed reproduction of the full Player's Handbook or Dungeon Master's Guide. For a complete SRD-based catalogue, import an appropriately attributed/licensed dataset in a later version.
- No player-to-player transfer control, automatic potion dice/healing, equipment stat modifiers, or automatic inventory snapshots yet.
- The DM can reveal an unidentified item's true name when a secret record exists. Public inventory fields should never contain secrets.
- Security rules and cross-account flows require live testing in your Firebase project. `node --check` validates JavaScript syntax, not integration.
- Existing campaign and character records are preserved. This update creates new `inventory`, `itemCatalog`, and `itemSecrets` subcollections under each campaign.
