# CampusConnect 🔵🟠
**College of the Sequoias — CS Club MVP**

A mobile-first React web app centralizing COS events, club discovery, and campus life for Giants students. No login required.

---

## Features
- **Giant Feed** — scrollable event stream with campus filters and pin-to-calendar
- **Club Explorer** — swipe-style card discovery for COS clubs
- **Giant Calendar** — localStorage pinned schedule, no account needed

---

## Tech Stack
- React 19 + Vite 8 + React Router DOM
- localStorage for no-auth persistence
- COS Brand: Navy `#003865` · Orange `#FF671F`

---

## Local Development

```bash
npm install
npm run dev
```
Open http://localhost:5173

---

## Deploy to Railway (recommended)

1. Push this repo to GitHub
2. Go to railway.app → New Project → Deploy from GitHub repo
3. Select this repo — Railway auto-detects `railway.toml` and runs:
   - Build: `npm run build`
   - Start: `npm run start`
4. Click Deploy — Railway gives you a live public URL instantly.

### Railway CLI (alternative)
```bash
npm install -g @railway/cli
railway login
railway init
railway up
```

---

## Project Structure

```
src/
  App.jsx              # Root: tab state + localStorage
  data.js              # Seed data: events, clubs, calendar
  index.css            # Global styles + COS brand tokens
  main.jsx             # Entry point
  components/
    BottomNav.jsx
    StatusBar.jsx
  screens/
    FeedScreen.jsx
    DiscoverScreen.jsx
    CalendarScreen.jsx
```

---

## Month 4 — Supabase Integration

Replace src/data.js static arrays with live queries:

```js
import { createClient } from '@supabase/supabase-js'
const supabase = createClient(
  import.meta.env.VITE_SUPABASE_URL,
  import.meta.env.VITE_SUPABASE_ANON_KEY
)
const { data: events } = await supabase.from('events').select('*')
```

Add env vars in Railway dashboard: VITE_SUPABASE_URL and VITE_SUPABASE_ANON_KEY.

---

*Built by COS CS Club · May 2026*
