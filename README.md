# Drone Studio — Deployment Guide

A browser-based violin drone music player with an Art Deco zodiac wheel UI.
Works as a full-screen iPhone app via PWA (no App Store needed).

---

## Files in this package

```
drone-studio/
├── index.html          ← The entire app
├── manifest.json       ← PWA metadata (name, icon, display mode)
├── service-worker.js   ← Offline caching
├── icons/
│   ├── icon-192.png    ← App icon (home screen, small)
│   └── icon-512.png    ← App icon (splash screen, large)
└── README.md
```

---

## Step 1 — Deploy to the web (pick one)

### Option A: Vercel (recommended, ~60 seconds)
1. Go to vercel.com → sign up free with GitHub or email
2. Click **Add New → Project**
3. Drag your `drone-studio` folder onto the page
4. Click **Deploy**
5. You get a URL like `https://drone-studio-abc.vercel.app`

### Option B: Netlify (also free, drag-and-drop)
1. Go to app.netlify.com/drop
2. Drag your `drone-studio` folder onto the page
3. You get a URL instantly

### Option C: GitHub Pages
1. Create a repo on github.com, upload these files
2. Go to Settings → Pages → Source: main branch / root
3. Your URL: `https://yourusername.github.io/drone-studio`

---

## Step 2 — Install as iPhone app

1. Open Safari on your iPhone (must be Safari, not Chrome)
2. Go to your deployed URL
3. Tap the **Share** button (the box with an arrow at the bottom)
4. Scroll down and tap **"Add to Home Screen"**
5. Name it "Drone Studio" → tap **Add**

The app icon now appears on your home screen.
Tap it to open full-screen with no browser chrome — just like a native app.

---

## Step 3 — Add your audio files

In the app:
1. Tap **Upload audio files**
2. Select your 14 violin drone recordings
3. Files are matched by name — use this naming convention for auto-match:
   - `a-major.mp3` / `a-minor.wav`
   - `b-major.flac` / `b-minor.mp3`
   - etc.
4. If a file name is ambiguous, the app will ask which scale it belongs to

Supported formats: MP3, WAV, FLAC, OGG, AAC, M4A

---

## Replacing the icon

The included icons are auto-generated placeholders.
To use a custom icon:
1. Create a 512×512 PNG with your design
2. Export also at 192×192
3. Replace `icons/icon-192.png` and `icons/icon-512.png`
4. Re-deploy

For best results on iPhone, use a square design with no transparency
(iOS clips it to a rounded square automatically).

---

## Notes

- Audio files are NOT cached by the service worker (they're large).
  You'll need to re-upload them each session unless you host the audio
  files on the same server and load them via URL.
- The app works offline once deployed — the UI loads from cache.
- Tested on Safari iOS 16+, Chrome, Firefox, Edge.
