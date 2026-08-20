# PWA support added

This small patch adds basic PWA support so the frontend can be installed on Chrome/Chromebook as a standalone app.

What I added:
- next-pwa integration (frontend/next.config.js)
- Web App Manifest (frontend/public/manifest.json)
- Simple SVG icons (frontend/public/icons/)
- Head/meta injection via pages/_document.tsx
- package.json dependency: next-pwa

How to test locally:
1. cd frontend
2. npm install
3. npm run build
4. npm run start
5. Open the site in Chrome, open DevTools > Application > Manifest to verify manifest and icons, and use "Install" from the address bar or chrome://apps

Notes and follow-ups:
- If this project uses the App Router (app/) instead of pages/, move the manifest/meta injection into app/layout.tsx instead.
- For offline caching customization and runtimeCaching strategies, we can tune next-pwa options.
