# My Shows

A simple personal tracker for the TV shows (and movies) I'm watching: which streaming service each is on, and which episodes I've seen.

- Single file: `index.html` — no build step, no server. Host it with GitHub Pages (Settings → Pages → Branch: `main`, folder `/ (root)`).
- Episode data: [TVMaze](https://www.tvmaze.com/api) (free, no key).
- Explore tab: [TMDB](https://www.themoviedb.org/) (free personal API key, entered in the app). This product uses the TMDB API but is not endorsed or certified by TMDB.
- Everything you track is saved in your browser; use ⋯ → Export backup to keep a copy or move to another device.

## Accounts (optional)

Accounts use Firebase (free plan) so your list is saved and syncs across devices. One-time setup:

1. Go to <https://console.firebase.google.com>, **Add project** (name it e.g. MyStream; Google Analytics can be off).
2. **Build → Authentication → Get started → Email/Password** → enable → Save.
3. **Authentication → Settings → Authorized domains → Add domain** → `bradleyh-sudo.github.io`.
4. **Build → Firestore Database → Create database** (production mode, any nearby location). On the **Rules** tab, paste the contents of [`firestore.rules`](firestore.rules) and **Publish**.
5. **Project settings (gear) → Your apps → Web (`</>`)** → register an app → copy the `firebaseConfig` values into `FIREBASE_CONFIG` in `index.html`.

The config values aren't secret (every Firebase web app ships them); the Firestore rules are what keep each person's list private.
