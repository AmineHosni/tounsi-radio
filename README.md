# 📻 Tounsi Radio

Live Tunisian radio for the car — **22 stations, one tap, keeps playing with the phone locked**, and it
shows up on your car's screen with steering-wheel controls.

It's a web app that installs to your iPhone Home Screen like a real app. No Xcode, no App Store,
no developer account, no monthly fee.

---

## What you get

- **22 live stations** — Mosaïque (5 channels), Jawhara, Diwan, Express, KnOOz, Sabra, Misk, Al Hayet,
  plus the whole national network: Nationale, RTCI, Jeunes, Culturelle, Zitouna, Sfax, Monastir, Gafsa,
  Le Kef, Tataouine.
- **Built for driving**: huge buttons, high contrast, dark screen, controls at the bottom where your
  thumb is. Next/previous changes station without looking closely.
- **Plays with the screen off.** Lock the phone, put it in your pocket — audio keeps going, and the
  lock screen shows the station with play/pause.
- **Works with your car.** Bluetooth/CarPlay audio screen shows "Tounsi Radio"; steering-wheel
  next/previous switches stations.
- **No ads, no accounts, no tracking.** Favourites are stored on your phone only.
- **Works everywhere else too** — same address on an Android phone, a tablet or your laptop.
- Every stream in the list was **tested and confirmed working** (they're all HTTPS MP3, which is what
  iPhone Safari can actually play).

---

## The 10-minute setup (do this once)

The iPhone will only install a web app from a real `https://` address, so the app needs a home on the
internet first. Pick **one** of these. Both are free.

### Option A — GitHub Pages (recommended)

Free forever, no card, and it gives you a project you can build a native app from later.

1. Go to **github.com** and sign up (or log in).
2. Top-right **+** → **New repository**. Name it `tounsi-radio`, choose **Public**, click **Create repository**.
3. On the empty repo page, click the link **“uploading an existing file”**.
4. **Drag every file in this folder** onto the page — the 9 app files plus this README (select the
   files themselves, not the folder). Wait for them to finish uploading, then **Commit changes**.
5. Go to the **Settings** tab (top of the repo) → **Pages** in the left sidebar.
   Under *Build and deployment*: **Source** = `Deploy from a branch`, **Branch** = `main`, folder = `/ (root)`.
   Click **Save**.
6. Wait 1–2 minutes, refresh that page. Your address appears at the top:
   `https://YOUR-USERNAME.github.io/tounsi-radio/`

### Option B — Netlify Drop (fastest, ~60 seconds)

1. Open **app.netlify.com/drop**
2. Drag the **whole `tounsi-radio` folder** onto the page.
3. You instantly get an address like `https://something-random.netlify.app`.
   (It may ask you to create a free account to keep the site permanently.)

---

## Install it on the iPhone

1. Open your new address in **Safari** — it must be Safari, not Chrome.
2. Tap the **Share** button (square with an arrow pointing up).
3. Scroll down → **Add to Home Screen** → **Add**.
4. Launch it from the Home Screen icon. It opens full-screen, with no browser bars.

> If you don't see "Add to Home Screen", you're either not in Safari or you're on a page that isn't
> `https://`. Both matter.

---

## First listen

1. Tap a station. If iOS asks about audio, allow it.
2. Tap the star on the stations you want in **My stations** (a short list is much easier to cycle
   through in the car than 22).
3. Lock the phone. The music keeps playing; the lock screen shows the station.

**In the car:** connect by Bluetooth (or CarPlay), press play in the car's media screen if it doesn't
start by itself, and use the steering-wheel next/previous buttons to change stations.

**Keep the screen on while mounted:** Settings (gear icon) → *Keep screen on*.

---

## Try it on your Mac first (optional, 10 seconds)

Double-click `index.html`. It opens in Safari and plays through your Mac's speakers — a quick way to
check the streams work before you bother with hosting.

---

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The whole app — layout, styles, station list, audio engine. One file, no dependencies. |
| `manifest.json` | Tells the iPhone the app's name, icon and that it should run full-screen. |
| `sw.js` | Service worker: caches the app so it opens instantly even on a weak signal. Never touches audio. |
| `icon-180.png` … `icon-512.png` | App icons (the Tunisian crescent and star). |
| `favicon-32.png` | Tiny browser-tab icon. |
| `icon-1024.png` | Large icon, kept for a future App Store submission. |
| `README.md` | This guide. |

---

## Good to know

**Mobile data.** Live radio is a stream, so it needs data while playing. Roughly:

| Station bitrate | Per minute | Per hour |
|---|---|---|
| 64 kbps (Express FM, Radio Tataouine) | ~0.5 MB | ~29 MB |
| 128 kbps (most stations) | ~1 MB | ~57 MB |
| 192 kbps (Zitouna, Sabra, Misk, Al Hayet) | ~1.4 MB | ~86 MB |

On a Tunisian or EU plan that's usually fine; if you're roaming, the 64 kbps stations are the cheap ones.

**No geo-blocking.** All 22 streams were tested and play from Europe, not just from Tunisia.

**Calls and tunnels.** A phone call or a dead spot interrupts the stream. The app retries by itself;
if it's stubborn, tap play.

**If a station dies.** Broadcasters change URLs without warning. Open Settings → **Browse directory**
to pull the current Tunisian list from the community radio directory, or paste a stream link you found
on the station's own website under **Add a station**.

**Battery.** Streaming with the screen on is the expensive part. For long drives, play with the screen
locked.

---

## Later: making it a real App Store app

This is genuinely possible — you already own the hardest part (the app and its station list). What
changes:

| | This web app | A native iOS app |
|---|---|---|
| Install | Add to Home Screen, 10 seconds | App Store download, or Xcode for personal use |
| Cost | €0 | **$99/year** Apple Developer Program (or free, but the app expires every 7 days) |
| Tools | none | Xcode on your Mac (free) |
| CarPlay | audio + steering wheel only | full CarPlay screen — needs an entitlement Apple grants manually |
| Review | none | App Review can reject it |

Three things that would need attention in a store submission:

1. **Guideline 4.2 (minimum functionality)** — a thin wrapper around a website gets rejected. A native
   build needs real native value: a proper audio engine that survives bad networks, "now playing" song
   metadata, reliable CarPlay, offline favourites.
2. **Guideline 5.2.5 (implying affiliation)** — the app icon is the Tunisian flag, which can read as an
   official state app. For a public release, use a distinct logo instead.
3. **Content rights** — you'd be linking to streams broadcast by others. That's normal for radio apps,
   but it's the part that needs care if a broadcaster objects.

**My honest recommendation:** use this web version for a few weeks. If you find yourself reaching for
it daily, *then* the native app is worth the €99 and the weekend of work — and this folder is the right
starting point, because the station list, the design and the behaviour are already decided.

---

## Credits

Streams belong to their broadcasters — Mosaïque FM, Jawhara FM, Diwan FM, Express FM, KnOOz FM, Sabra FM,
Misk FM, Al Hayet FM and Radio Tunisienne (the national network). This app only tunes into them and
doesn't host or re-broadcast anything. Station data cross-checked against
[radio-browser.info](https://www.radio-browser.info), a free community radio directory.
