# Budgetly — mobile + cloud-ready package

This package preserves the existing Budgetly features and preferred pastel-pink interface, adds PWA install support, and includes Firebase email/password authentication plus per-user cloud sync.

## Included
- `index.html` — Budgetly app
- `manifest.webmanifest` — install metadata
- `sw.js` — app-shell caching for PWA
- `icons/budgetly-icon.svg` — home-screen icon
- `firestore.rules` — starter rules for private per-user cloud data

## Important status
Firebase syncing is **not active until you configure your own Firebase project**. The account dialog lets you enter the Firebase web config. The config is saved in this browser only. This version syncs one user's Budgetly state to that user's private cloud document. It does not yet implement joint-workspace invitations or shared-budget membership; those require a separate shared-workspace schema and security rules, which should be added before using joint accounts.

## Setup
1. Create a Firebase project at https://console.firebase.google.com/
2. In Project settings → General → Your apps, add a Web app and copy its `apiKey`, `authDomain`, `projectId`, and `appId`.
3. In Authentication → Sign-in method, enable **Email/Password**.
4. In Firestore Database, create a database.
5. Publish `firestore.rules` in Firestore → Rules. Review them before production use.
6. Upload `index.html`, `manifest.webmanifest`, `sw.js`, and the `icons` folder to the same GitHub Pages directory.
7. Open Budgetly over its HTTPS GitHub Pages URL, select **Sign in / Profile**, enter the four config values, and choose **Create account** or **Sign in**.
8. On another device, open the same hosted URL, configure the same Firebase web app, and sign in with the same account.

## Data safety
- Make a JSON backup from the app before migrating important data.
- The first sign-in uploads the current browser's local Budgetly data if that cloud account has no saved state yet.
- Do not share your password. Firebase web configuration is intended for client-side use, but access control depends on the deployed Firestore rules.
- Joint budgets should not be used until shared workspace invitations and membership permissions are implemented and tested.
- PWA caching makes the app shell more accessible offline; it does not guarantee offline editing or conflict-free syncing.
