# Currency Exchange Tracker

A full-stack web app for converting currencies, charting historical exchange rates, and saving favorite currency pairs.

Built with Node.js, Express, the [Frankfurter](https://frankfurter.dev/) exchange-rate API, Supabase, and Chart.js. Originally built as the final project for INST377 at the University of Maryland.

<!-- Add a screenshot: save it as docs/screenshot.png and uncomment the next line. -->
<!-- ![Currency Exchange Tracker](docs/screenshot.png) -->

## Features

- **Convert:** convert an amount between USD, EUR, GBP, and JPY at the latest rate.
- **Trends:** chart the rate between two currencies over a date range you choose.
- **Favorites:** save and delete currency pairs. Favorites are stored in a Supabase database.

## How it works

```
Browser (public/*.html, *.js, Chart.js)
        │  fetch /api/...
        ▼
Express server (server.js)
        ├── /api/convert, /api/history ──► Frankfurter API (live and historical rates)
        └── /api/favorites ─────────────► Supabase "favorites" table
```

The browser only talks to the Express server. The server calls the Frankfurter API and Supabase, so the database credentials stay on the server.

## Run it locally

Requires Node.js 18 or later and a Supabase project.

```bash
git clone https://github.com/SAADALKINANI/currency_exchange_tracker.git
cd currency_exchange_tracker
npm install
cp .env.example .env   # then fill in your Supabase URL and key
npm start
```

Open http://localhost:3000.

Database setup, the API reference, and the road map are in the [developer manual](docs/README.md).

## Deployment

`vercel.json` deploys `server.js` as a Vercel serverless function. Set `SUPABASE_URL` and `SUPABASE_KEY` as environment variables in the Vercel project settings.

## Known limitations

- Only four currencies are offered in the dropdowns.
- There are no automated tests yet.
- The layout targets desktop browsers.
