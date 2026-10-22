# Pantry Rounds — Vercel deploy

Static site (no build step). Shared data lives in Firebase Firestore (free Spark plan is enough).

## 1. Firebase setup (one time)
1. Go to https://console.firebase.google.com → **Add project** (e.g. `pantry-rounds`). Google Analytics can be off.
2. **Build → Firestore Database → Create database** → choose a location (e.g. `asia-south1` Mumbai) → Production mode.
3. **Rules** tab → paste the contents of `firestore.rules` → **Publish**.
4. **Project settings (gear) → Your apps → Web (</>)** → register app → copy the `firebaseConfig` values into `firebase-config.js`.

## 2. Deploy to Vercel
**Option A – GitHub:** push this folder to a GitHub repo → https://vercel.com/new → Import the repo → Framework preset: **Other** → Deploy.

**Option B – CLI:**
```
npm i -g vercel
cd pantry-rounds
vercel          # first deploy (preview)
vercel --prod   # production
```

## 3. First use
Open the site → **Team** section → add names → each person taps their own name once (remembered on that phone).
Paste your WhatsApp group invite link in Team settings. **Send to Pantry Group** opens WhatsApp with the list already typed — pick the group and tap Send.

## Notes
- Old orders cleanup (30 days) needs a composite index. The first time it runs, the browser console shows a Firestore link to create it — click it once. The app works fine without it.
- Data from the claude.ai version is not copied over; re-add team names once.
- Rules are open to anyone who has the link (same as before). Don't share the URL publicly.
