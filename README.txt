BIRTHDAY OS + BIRTHDAY WEBSITE — combined single website

Contents
--------
- Root files (index.html, shell.js, terminal.js, …) = Birthday OS terminal
- birthday/ = original birthday surprise React app (App.tsx, content, UI, etc. unchanged)

What changed (only OS side)
---------------------------
- open birthday no longer opens an external Netlify link
- It navigates to ./birthday/ (same project)

Fix for Replit / npm errors
---------------------------
The original package.json used Replit-only "catalog:" and "workspace:*" dependencies.
Those only work inside the original Replit monorepo.

This package already has a STANDALONE package.json + vite.config.ts + tsconfig.json
so you can install and build normally:

  cd birthday
  npm install
  npm run build

After build you get birthday/dist/ — that is the static site.

How to deploy as ONE website
----------------------------
Option A – Netlify (recommended)
1. Unzip this archive.
2. Build the birthday app first (see above) so birthday/dist exists.
3. Copy the built files into a folder that the OS can serve, e.g.:
     mkdir -p birthday-site
     cp -r birthday/dist/* birthday-site/
   Or configure Netlify with two publish roots / redirects.
4. Simplest: after building, replace the birthday/ folder content with the
   contents of birthday/dist/ so that ./birthday/index.html is the built app.
5. Deploy the whole combined/ folder. The terminal is the homepage;
   open birthday goes to the local birthday page.

Option B – Replit
1. Upload the combined folder.
2. In the Shell:
     cd birthday
     npm install
     npm run build
3. Then serve the root (or configure the Replit run command to serve the
   static root + the built birthday/dist).

Local test (terminal only, no build needed)
-------------------------------------------
  npx serve .
  # or python -m http.server
Type: guide

Birthday: October 17, 2026 (Asia/Manila)
