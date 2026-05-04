# Trap Race Deluxe 🏁

A multiplayer browser game — place traps, then race through them.  
**6 characters · 4 maps · 6 trap types · powerups · 60-second races**

---

## Deploy in 5 minutes (GitHub + Vercel + Firebase)

### Step 1 — Get a free Firebase database

1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Click **Add project** → give it any name → click through
3. In the left sidebar: **Build → Realtime Database**
4. Click **Create Database** → choose any region → start in **test mode**
5. In the left sidebar: **Project Overview → click the `</>` Web icon**
6. Register a web app (any nickname) → copy the `firebaseConfig` object shown

### Step 2 — Paste your Firebase config into the game

Open `index.html` and find this block near the top of the `<script>`:

```js
const FIREBASE_CONFIG = {
  apiKey:            "REPLACE_WITH_YOUR_API_KEY",
  authDomain:        "REPLACE_WITH_YOUR_AUTH_DOMAIN",
  databaseURL:       "REPLACE_WITH_YOUR_DATABASE_URL",
  ...
};
```

Replace each `"REPLACE_WITH_..."` value with the real values from your Firebase project.

> **Important:** Make sure `databaseURL` is included. If it's missing from the Firebase console,  
> it's usually `https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com`

### Step 3 — Push to GitHub

```bash
git init
git add .
git commit -m "Trap Race Deluxe"
git remote add origin https://github.com/YOUR_USERNAME/trap-race-deluxe.git
git push -u origin main
```

Or just upload the folder via github.com → New repository → upload files.

### Step 4 — Deploy on Vercel

1. Go to [vercel.com](https://vercel.com) → sign in with GitHub
2. Click **Add New → Project**
3. Import your `trap-race-deluxe` repository
4. Leave all settings as default → click **Deploy**
5. Done! Vercel gives you a live URL like `https://trap-race-deluxe.vercel.app`

Share the link — friends open it on their phones, enter the same room code, and play!

---

## How to play

| Phase | What happens |
|-------|-------------|
| **Character select** | Each player picks their fighter (different abilities) |
| **Map select** | Host picks the arena |
| **Build phase (25s)** | Everyone places traps secretly on the track |
| **Race phase (60s)** | Run, jump, dodge — collect powerups |
| **Results** | Scores shown, host starts next round |

### Controls
- **Run button** — hold to move right
- **Jump button** — tap to jump (Witch gets double jump)
- **Star button** — activate collected powerup

### Characters
| Character | Special ability |
|-----------|----------------|
| 🥷 Ninja   | Fastest speed |
| 🤖 Robot   | 30% less trap damage |
| 🧙 Witch   | Double jump |
| 👻 Ghost   | Spikes do no damage |
| ⚔️ Knight  | Immune to ice traps |
| 🧚 Fairy   | Slow floaty fall |

### Scoring
- **+100 pts** for finishing
- **+remaining HP** as bonus points
- Scores accumulate across rounds

---

## Firebase security (optional, for production)

After testing, update your Firebase Realtime Database rules:

```json
{
  "rules": {
    "rooms": {
      "$roomId": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

For a public game this is fine. Old rooms auto-expire if you enable Firebase's TTL rules.
