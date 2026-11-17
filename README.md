# Adventure Ledger 2.0 — Campaigns

GitHub Pages + Firebase Authentication + Firestore. No build step required.

## IMPORTANT: Upgrade order

1. **Keep a backup:** Download the current GitHub repository ZIP. In Firebase Console > Firestore > Data, do not delete any existing collections. Your existing `/members`, `/characters`, `/bootstrap`, and `/invites` data is preserved by this upgrade.
2. **Publish the new `firestore.rules` FIRST** in Firebase Console > Firestore Database > Rules. Replace the existing text, then Publish. These rules continue to permit existing authentication and onboarding, but the old version of the app will no longer be able to modify legacy `/characters` while the update is in progress. Schedule the change when nobody is playing.
3. Upload **all six files** from this ZIP to the root of the GitHub repository (`index.html`, `app.js`, `styles.css`, `firebase-config.js`, `firestore.rules`, `README.md`). Commit changes, wait for GitHub Pages to deploy, and hard refresh.
4. Sign in using your existing account. Create a campaign (e.g., Heroes of the Borderlands). You will initially be both owner and DM. The old global DM role remains only for initial account registration compatibility.
5. In Manage campaign, invite new players by email, have them register and verify their addresses, then **Add player** from the registered-user list. Existing accounts can be added directly.
6. Assign the DM from the campaign's member list. Only the owner can reassign the DM. Each campaign has one DM at a time.

## What is saved

`campaigns/{campaignId}` contains campaign name, owner ID, DM ID, roster, status, and session name. Each campaign has its own `characters/{userId}`, private `secrets/main` (DM notes), and owner-only `snapshots/{snapshotId}`. A snapshot can restore character sheets, but intentionally does **not** automatically restore roles, roster, or DM notes.

## Existing data / migration

Existing `/characters/{userId}` records are NOT deleted and are NOT automatically copied into campaigns. To migrate a player character, create a campaign, add the player, and enter their existing values into their new campaign character sheet. The previous global DM test character remains in the legacy collection but is not displayed in new campaigns. The new app does not modify it. This is intentionally conservative to prevent accidental data loss.

## Important limitations

- Only registered users can be added to a campaign. Email invitation enables account registration but does not automatically add a player to the campaign.
- Campaign owner cannot be transferred in this version; DM can be reassigned.
- One character per player per campaign.
- Snapshots are owner-only and restore character sheets, not campaign settings. For a full off-platform backup, export Firestore separately.
- The campaign document is readable by all members; private DM notes are stored separately in `secrets/main` and accessible only to DM/owner.
- Firestore rules need live Firebase testing before inviting family members. JavaScript syntax checks are not an end-to-end integration test.

## Security

Firebase web config contains public client identifiers, not a server secret. Firestore rules, not obscurity, enforce permissions. Keep authentication and email verification enabled. Do not use Firestore test mode.
