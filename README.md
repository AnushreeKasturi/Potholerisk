# PotholeRisk — Bengaluru Dynamic Risk Engine

Your OpenWeather API key now lives **only on the server** in a `.env` file.
It is never sent to the browser or visible in DevTools.

---

## Setup (one time)

**1. Install Node.js** if you don't have it: https://nodejs.org (LTS version)

**2. Install dependencies**
```bash
npm install
```

**3. Add your API key**
```bash
cp .env.example .env
```
Open `.env` and replace `your_key_here` with your real OpenWeather API key:
```
OPENWEATHER_API_KEY=abc123yourkeyhere
```

---

## Run

```bash
npm start
```

Then open **http://localhost:3000** in your browser.

---

## How it works

```
Browser  ──GET /api/weather──▶  server.js  ──(key added here)──▶  OpenWeather
         ◀── weather JSON ───             ◀── weather JSON ──────
```

- The browser only ever talks to **your own server** at `/api/weather`
- `server.js` reads the key from `.env` and adds it before forwarding to OpenWeather
- The key is **never** in the HTML, JS, or any network request the browser makes

---

## Files

```
potholerisk/
├── server.js          ← Node/Express backend (proxy lives here)
├── package.json
├── .env               ← YOUR SECRET KEY (gitignored, never committed)
├── .env.example       ← Template to share safely
├── .gitignore
└── public/
    └── index.html     ← Frontend (no API key anywhere in here)
```
