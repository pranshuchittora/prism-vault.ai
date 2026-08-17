# Prism Vault AI

A curated, searchable directory of 500+ AI tools — spanning chat assistants, coding, image, video, voice, design, productivity, business, and more — presented as an airport-departures-style board.

**Live site:** [prismvaultai.netlify.app](https://prismvaultai.netlify.app)

## Features

- 🔍 **Instant search** across 500+ tools by name or purpose
- 🗂️ **9 terminals / 40+ categories** — Chat & Research, Coding & Dev, Creative Media, Design & Productivity, Business & Ops, Specialized, and more
- 🌗 **Light / dark theme** toggle
- 📥 **Downloadable** as a standalone HTML page
- 🔐 **Authentication-gated access** — sign in with a password or a 6-digit email passcode before browsing or downloading
- 📱 Fully responsive, single-file, no build step required

## Tech Stack

- Vanilla HTML, CSS, and JavaScript — no framework, no bundler
- [Supabase](https://supabase.com) for authentication:
  - Email/password sign-up & sign-in
  - 6-digit email OTP passcode sign-in
  - Google OAuth (optional, requires provider setup)
- Fonts: IBM Plex Mono + Inter (Google Fonts)

## Getting Started

1. Clone this repo
2. Open `index.html` directly, or serve it locally:
   ```bash
   python -m http.server 8000
   ```
   then visit `http://localhost:8000`

> **Note:** Authentication requires an `https://` or `http://localhost` origin — opening the file directly (`file://`) will block Supabase requests due to CORS.

## Authentication Setup

This project uses [Supabase Auth](https://supabase.com/docs/guides/auth). To run your own instance:

1. Create a free project at [supabase.com](https://supabase.com)
2. **Authentication → Providers → Email** — enable the Email provider
3. **Authentication → Emails → Templates** — edit the "Confirm signup" and "Magic Link" templates to show `{{ .Token }}` instead of the default confirmation link, so users receive a 6-digit code
   - Editing the raw template source requires **Custom SMTP** (Authentication → Emails → SMTP Settings) — a free Gmail App Password works fine for low volume
4. **Authentication → URL Configuration** — add your deployed URL (e.g. `https://prismvaultai.netlify.app`) as both the Site URL and a Redirect URL
5. Copy your **Project URL** and **anon public key** (Project Settings → API) into the `SUPABASE_URL` and `SUPABASE_ANON_KEY` constants near the bottom of `index.html`

Google sign-in additionally requires enabling the Google provider in Supabase and configuring OAuth credentials in Google Cloud Console.

## Deployment

The site is deployed on [Netlify](https://netlify.com). Any static host works — push `index.html` to your repo and connect it, or drag-and-drop into Netlify's dashboard.

## Adding or Editing Tools

All tool data lives in the `TERMINALS` array near the top of the `<script>` block in `index.html`. Each entry follows:

```js
["Tool Name", "https://tool-url.com", "Short description", hasDownloadApp /* optional bool */]
```

Tools are grouped into categories (`{ name, letter, tools: [...] }`), which are grouped into terminals (`{ label, categories: [...] }`).

## Credits

Created by **Absar Hussain Shaikh**.
Suggest a tool: [Hussain_Shaikh.8@outlook.com](mailto:Hussain_Shaikh.8@outlook.com)

## License

All destination links point to each tool's official site. This directory is for informational/navigational purposes only.
