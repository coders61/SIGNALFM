# 📻 SIGNAL • FM

> Tune the World, Live.

**A free, open-source web radio app.** Stream 50,000+ live radio stations from 200+ countries, right in your browser. No account, no ads, no tracking, no install required (but you *can* install it as an app).

**▶ Live app: https://coders61.github.io/SIGNALFM/**

<p align="center">
  <img src="screenshot.png" width="80%" alt="SIGNAL•FM screenshot">
</p>

---

## ✨ Features

**Discover**
- 🌍 Browse 200+ countries, or jump straight to one from the dropdown
- 🔥 **Trending** and 👍 **Top voted** charts, updated live
- 📍 **Near you**: popular stations in your country
- 🎧 24 one-tap genres (Jazz, Lo-Fi, Hip-Hop, News, Classical, …)
- 🔍 Smart search across station names *and* genres
- ↕️ Sort by popularity, trending, votes, quality or name
- 🎲 **Surprise me**: finds a random station that is actually live

**Listen**
- ▶️ Reliable playback with automatic fallback between stream modes
- 📡 HLS (`.m3u8`) stream support
- 🔁 **Auto-reconnect** when a stream drops
- 🎚️ **5-band equalizer** with presets (Bass+, Vocal, Treble+, Loud, Night)
- 📊 **Real audio visualizer** (driven by the live audio when the station allows it)
- ⏾ **Sleep timer** with a gentle fade-out
- ⏮ ⏭ Next / previous station
- 🔒 Lock-screen & media-key controls (Media Session API)
- ⌨️ Keyboard shortcuts (press <kbd>?</kbd>)

**Your library**
- ★ **Favorites saved permanently** in your browser
- 🕘 **Recently played** history
- ⬇⬆ Export / import favorites as JSON (move them between devices)
- ↗ **Share links** to any station (`…/#station=<id>`)
- 👍 Vote for stations you love
- ▶ Remembers your last station, volume, EQ and theme

**App**
- 🌗 Dark, light & auto themes
- 📲 Installable **PWA** (works like a native app on phone & desktop)
- 📱 Fully responsive, accessible (keyboard & screen-reader friendly)
- ⚡ No frameworks, no build step, no backend

---

## ⌨️ Keyboard shortcuts

| Key | Action |
| --- | --- |
| <kbd>Space</kbd> / <kbd>K</kbd> | Play / pause |
| <kbd>N</kbd> / <kbd>P</kbd> | Next / previous station |
| <kbd>R</kbd> | Random station |
| <kbd>M</kbd> | Mute |
| <kbd>Shift</kbd> + <kbd>↑</kbd> / <kbd>↓</kbd> | Volume |
| <kbd>F</kbd> | Favorite current station |
| <kbd>I</kbd> | Station info |
| <kbd>E</kbd> | Equalizer |
| <kbd>S</kbd> | Cycle sleep timer |
| <kbd>/</kbd> | Search |

---

## 🚀 Run it yourself

It's a static site, so any web server works:

```bash
git clone https://github.com/coders61/SIGNALFM.git
cd SIGNALFM
python3 -m http.server 8000
```

Then open http://localhost:8000.

> Opening `index.html` directly (double-click) also works, but the installable-app and offline features need a web server.

### Deploy free on GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Source**, pick **Deploy from a branch**, then choose `main` and `/ (root)`.
4. Your radio is live at `https://<your-username>.github.io/SIGNALFM/` within a minute or two.

---

## 📂 Project structure

```
SIGNALFM/
├── index.html            # page layout
├── css/style.css         # all styles (dark + light themes)
├── js/app.js             # all app logic
├── sw.js                 # service worker (offline app shell)
├── manifest.webmanifest  # PWA manifest
├── icons/icon.svg        # app icon
└── .nojekyll             # serve files as-is on GitHub Pages
```

When you change files, bump `VERSION` in `sw.js` so installed copies pick up the update.

---

## 🧠 How it works

- **Station directory:** [Radio Browser](https://www.radio-browser.info/), a free, community-maintained API. The app discovers the live API servers and fails over automatically if one is down.
- **Playback:** each stream is first tried in CORS mode, routed through the Web Audio API, which enables the EQ and real visualizer. If the station doesn't allow that, it falls back to normal playback, so the station still plays.
- **HTTPS:** browsers block insecure (`http://`) audio on secure sites such as GitHub Pages. With *Secure streams only* on (the default on HTTPS), those stations are hidden so you don't hit dead ends.
- **Storage:** favorites, history and settings live in your browser's `localStorage`. Nothing is sent anywhere.

### Known limitations
- **Song titles** (now-playing metadata) can't be read directly from radio streams in a browser without a proxy server.
- **iPhone/iPad:** *Enhanced audio* is off by default, because Web Audio can stop playback when the screen locks.

---

## 🛣 Roadmap

- [x] Persistent favorites
- [x] Recently played
- [x] Trending & top-voted charts
- [x] Light theme
- [x] Installable app (PWA)
- [x] Sleep timer, 5-band EQ, keyboard shortcuts
- [ ] Now-playing song titles (optional proxy)
- [ ] World map browsing
- [ ] Multi-language UI
- [ ] Custom stations (add your own stream URL)
- [ ] Cloud sync

---

## 🤝 Contributing

Contributions are very welcome: bug reports, feature ideas, translations, and pull requests.

1. Fork the repo and create a branch: `git checkout -b my-feature`
2. Make your changes (plain HTML/CSS/JS, no build step)
3. Test locally with `python3 -m http.server`
4. Open a pull request describing what you changed

If you like the project, **give it a ⭐ on GitHub**. It really helps others find it!

---

## 📜 License

Released into the public domain under [CC0 1.0 Universal](LICENSE). Do whatever you like with it.

Radio streams and station logos belong to their respective broadcasters.

## ❤️ Acknowledgements

- [Radio Browser](https://www.radio-browser.info/) and its community
- [hls.js](https://github.com/video-dev/hls.js) for HLS playback
- Radio stations worldwide for broadcasting

---

<p align="center"><b>📻 SIGNAL • FM</b> — "Every station tells a story. Every frequency connects the world."</p>
