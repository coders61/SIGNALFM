<h1 align="center">📻 SIGNAL • FM</h1>

<p align="center"><b>Tune the World, Live.</b></p>

<p align="center">
  A free, open-source web radio app. Stream <b>50,000+ live radio stations</b> from <b>200+ countries</b> right in your browser.<br>
  No account, no ads, no tracking. Install it as an app if you like.
</p>

<p align="center">
  <a href="https://coders61.github.io/SIGNALFM/"><img src="https://img.shields.io/badge/▶_Listen_now-coders61.github.io%2FSIGNALFM-2be8ff?style=for-the-badge" alt="Listen now"></a>
</p>

<p align="center">
  <a href="https://github.com/coders61/SIGNALFM/stargazers"><img src="https://img.shields.io/github/stars/coders61/SIGNALFM?style=flat-square&color=ffc233" alt="GitHub stars"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-CC0_1.0-9b6bff?style=flat-square" alt="License: CC0"></a>
  <img src="https://img.shields.io/badge/dependencies-none-c6ff3d?style=flat-square" alt="No dependencies">
  <img src="https://img.shields.io/badge/PWA-installable-ff3fc0?style=flat-square" alt="Installable PWA">
</p>

<p align="center">
  <img src="photo.png" width="85%" alt="SIGNAL•FM screenshot">
</p>

---

## 📑 Contents

- [Features](#-features)
- [Install it as an app](#-install-it-as-an-app)
- [Keyboard shortcuts](#️-keyboard-shortcuts)
- [Run it yourself](#-run-it-yourself)
- [Project structure](#-project-structure)
- [How it works](#-how-it-works)
- [Troubleshooting](#-troubleshooting)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [License](#-license)

---

## ✨ Features

### 🌍 Discover
- Browse **200+ countries**, or jump straight to one from the dropdown
- 🔥 **Trending** and 👍 **Top voted** charts, updated live
- 📍 **Near you**: popular stations in your country
- 🎧 **24 one-tap genres** (Jazz, Lo-Fi, Hip-Hop, News, Classical, …)
- 🔍 **Smart search** across station names *and* genres
- ↕️ Sort by popularity, trending, votes, quality or name
- 🎲 **Surprise me**: finds a random station that is actually live

### 🎧 Listen
- Reliable playback with automatic fallback between stream modes
- 📡 **HLS** (`.m3u8`) stream support
- 🔁 **Auto-reconnect** when a stream drops
- 🎚️ **5-band equalizer** with presets: Bass+, Vocal, Treble+, Loud, Night
- 📊 **Real audio visualizer**, driven by the live audio when the station allows it
- ⏾ **Sleep timer** with a gentle fade-out
- ⏮ ⏭ Next / previous station
- 🔒 **Lock-screen & media-key controls**
- ⌨️ **Keyboard shortcuts** (press <kbd>?</kbd> in the app)

### ⭐ Your library
- **Favorites saved permanently** in your browser
- 🕘 **Recently played** history
- ⬇⬆ **Export / import favorites** as a JSON file to move them between devices
- ↗ **Share links** to any station (`…/#station=<id>`)
- 👍 **Vote** for stations you love
- Remembers your last station, volume, EQ and theme

### 📱 App
- 🌗 **Dark, light & auto** themes
- 📲 **Installable** on phone and desktop (PWA)
- Fully responsive and accessible (keyboard & screen-reader friendly)
- ⚡ No frameworks, no build step, no backend: just HTML, CSS and JavaScript

---

## 📲 Install it as an app

SIGNAL•FM can be installed like a normal app, with its own icon and window.

| Device | How |
| --- | --- |
| **Chrome / Edge (desktop)** | Click **Install** in the top bar of the app, or the install icon in the address bar |
| **Android (Chrome)** | Menu **⋮** → **Add to Home screen** / **Install app** |
| **iPhone / iPad (Safari)** | **Share** button → **Add to Home Screen** |

---

## ⌨️ Keyboard shortcuts

| Key | Action |
| --- | --- |
| <kbd>Space</kbd> / <kbd>K</kbd> | Play / pause |
| <kbd>N</kbd> / <kbd>P</kbd> | Next / previous station |
| <kbd>R</kbd> | Random station |
| <kbd>M</kbd> | Mute / unmute |
| <kbd>Shift</kbd> + <kbd>↑</kbd> / <kbd>↓</kbd> | Volume up / down |
| <kbd>F</kbd> | Favorite the current station |
| <kbd>I</kbd> | Station info |
| <kbd>E</kbd> | Equalizer |
| <kbd>S</kbd> | Cycle the sleep timer |
| <kbd>/</kbd> | Search |
| <kbd>Esc</kbd> | Close panels |

---

## 🚀 Run it yourself

It's a static site, so any web server works:

```bash
git clone https://github.com/coders61/SIGNALFM.git
cd SIGNALFM
python3 -m http.server 8000
```

Then open **http://localhost:8000**.

> Double-clicking `index.html` also works, but the install-as-app and offline features need a web server.

### Host your own copy on GitHub Pages (free)

1. **Fork** this repository.
2. In your fork, go to **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, then `main` and `/ (root)`, and click **Save**.
4. After a minute or two your radio is live at `https://<your-username>.github.io/SIGNALFM/`.

---

## 📂 Project structure

```
SIGNALFM/
├── index.html            # page layout
├── css/style.css         # all styles (dark + light themes)
├── js/app.js             # all app logic
├── sw.js                 # service worker (offline app shell)
├── manifest.webmanifest  # app name, icon and colors for installing
├── icons/icon.svg        # app icon
├── photo.png             # screenshot used in this README
├── .nojekyll             # tells GitHub Pages to serve files as-is
└── LICENSE               # CC0 1.0
```

> 💡 After changing any file, bump `VERSION` in `sw.js` (e.g. `signalfm-v2.0.1`) so people who installed the app get the update.

---

## 🧠 How it works

- **Station directory:** [Radio Browser](https://www.radio-browser.info/), a free, community-maintained database of radio stations. The app finds the live API servers and switches automatically if one is down.
- **Playback:** each stream is first tried through the Web Audio API, which powers the EQ and real visualizer. If the station doesn't allow that (a browser security rule called CORS), it falls back to normal playback, so the station still plays.
- **HTTPS:** browsers block insecure `http://` audio on secure sites like GitHub Pages. With **Secure streams only** on (the default), those stations are hidden so you don't hit dead ends.
- **Privacy:** favorites, history and settings are stored only in your browser (`localStorage`). There are no accounts, analytics or cookies.

---

## 🛠 Troubleshooting

| Problem | Try this |
| --- | --- |
| A station won't play | Some streams go offline; pick another one, or press **N** for the next station. |
| I can't find a station I know | Open **⚙ Settings** and turn off **Secure streams only**. It may only offer an `http://` stream. |
| The EQ doesn't change the sound | That station doesn't allow audio processing. The EQ panel tells you when this happens. |
| Audio stops when my iPhone locks | Make sure **Enhanced audio** is off in Settings (it's off by default on iPhone/iPad). |
| I don't see new changes after an update | Refresh the page twice, or close and reopen the installed app. |
| My favorites are gone on another device | Favorites are saved per browser. Use **Export** in Settings, then **Import** on the other device. |

### Known limitations
- **Song titles** (what's playing right now) can't be read from radio streams in a browser without a separate proxy server.
- Station logos, names and stream quality come from the Radio Browser community and are sometimes missing or out of date.

---

## 🛣 Roadmap

- [x] Saved favorites & recently played
- [x] Trending & top-voted charts
- [x] Light theme
- [x] Installable app (PWA)
- [x] Sleep timer, 5-band EQ, keyboard shortcuts
- [x] Share links & favorites export/import
- [ ] Now-playing song titles (optional proxy)
- [ ] World map browsing
- [ ] Multi-language interface
- [ ] Add your own custom stream URLs
- [ ] Cloud sync

Have an idea? [Open an issue](https://github.com/coders61/SIGNALFM/issues)!

---

## 🤝 Contributing

Contributions are very welcome: bug reports, feature ideas, translations and pull requests.

1. Fork the repo and create a branch: `git checkout -b my-feature`
2. Make your changes. It's plain HTML/CSS/JS, with no build step or installs.
3. Test locally with `python3 -m http.server`
4. Open a pull request describing what you changed and why

Found a bug? Please [open an issue](https://github.com/coders61/SIGNALFM/issues) and include your browser, device, and the station name.

### ⭐ Like it?
**Give SIGNAL•FM a star on GitHub.** It helps more people find it!

---

## 📜 License

Released into the public domain under [CC0 1.0 Universal](LICENSE). Use it, change it and share it however you like.

Radio streams and station logos belong to their respective broadcasters.

## ❤️ Acknowledgements

- [Radio Browser](https://www.radio-browser.info/) and its community, for the free station directory
- [hls.js](https://github.com/video-dev/hls.js), for HLS playback
- [Shields.io](https://shields.io/), for the badges
- Radio stations around the world, for broadcasting

---

<p align="center">
  <b>📻 SIGNAL • FM</b><br>
  <i>"Every station tells a story. Every frequency connects the world."</i>
</p>
