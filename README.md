# Adventure Ledger — family D&D character tracker

A mobile-friendly, static website using Firebase Authentication and Cloud Firestore. Suitable for GitHub Pages. No paid hosting required for modest family use, subject to Firebase's current free-tier quotas.

## Setup (about 15–25 minutes)

1. Create a Firebase project at https://console.firebase.google.com/ .
2. In **Build > Authentication > Sign-in method**, enable **Email/Password**.
3. In **Build > Firestore Database**, create a database in production mode, selecting a nearby region. Do **not** use open test rules.
4. Open **Firestore Database > Rules**. Replace the rules with the contents of `firestore.rules` and publish them.
5. In **Project settings > General > Your apps**, register a **Web** app. Copy its `firebaseConfig` object into `firebase-config.js`, replacing `null`, for example:

```js
window.ADVENTURE_FIREBASE_CONFIG = {
  apiKey: "...",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project",
  storageBucket: "your-project.firebasestorage.app",
  messagingSenderId: "...",
  appId: "..."
};
```

Firebase web configuration values are intended to be public. Do not paste private service-account keys.

6. In **Authentication > Settings > Authorized domains**, add your GitHub Pages hostname (e.g. `username.github.io`) if not already present.
7. Create a new GitHub repository (e.g. `adventure-ledger`). Upload all files in this folder to the repository root. In **Settings > Pages**, deploy from the `main` branch and `/ (root)` folder.
8. Visit `https://YOUR_USERNAME.github.io/adventure-ledger/`. Create **your DM account first** and verify the email. Sign out and sign in again. The first verified account to claim the database's bootstrap document becomes DM.
9. On the DM dashboard, invite each family member by their exact email address. They register with that email, verify it, and sign in. Each can then create their character.

## Security and privacy

- This is for a private family game, not sensitive personal records. Use unique passwords and do not store real-world sensitive information in character notes.
- Email verification is required before account membership. Firestore rules restrict player writes to their own character and allow the DM to edit everyone.
- **All registered campaign members can see other players' character sheets, including notes and inventory.** Don't enter secret DM-only information there.
- Firebase Authentication accounts and Firestore data persist separately from GitHub Pages. Back up important character data occasionally in Firebase Console.
- The first account is automatically DM. Do not publish the site until you're ready to register your own account. If someone else claims DM first, reset the Firebase project/database before use or use Firebase Console to repair the roles safely.
- Invitations grant access to anyone who can verify the invited email address. Use addresses controlled by your family.
- Account removal and campaign export are not implemented in v1; use Firebase Console for administration.

## Features

- Individual email/password accounts and email verification
- DM invitation allowlist and party-wide editing
- Current/max/temporary HP, quick damage and healing
- Gold/silver/copper, quick gold adjustments
- Level, XP, AC, speed, six ability scores
- Inventory, resources/spells, character notes
- Party overview and recent quick-adjustment activity
- Live synchronization across devices

## Limitations

- No automated D&D character creation, rules enforcement, spell tracking, or dice roller yet.
- Coin and health quick buttons save immediately. Other fields require **Save character**.
- One character per account in v1. DM can edit all existing characters.
- Firebase's free tier has quotas; check Firebase's current pricing and usage dashboard.
- The site requires an internet connection.
