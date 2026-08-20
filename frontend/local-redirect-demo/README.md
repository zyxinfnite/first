Local redirect demo for OS Emulator

This folder contains a simple HTML file that redirects your browser to http://localhost:3000/

Files:
- index.html : auto-redirects to http://localhost:3000 and includes a clickable link if redirect is blocked.

How to use:
1. Ensure your frontend dev server is running (example):
   cd frontend
   npm install
   npm run dev

2. Open the redirect HTML in your browser:
   - From the GitHub repo: download the branch or file and open frontend/local-redirect-demo/index.html in Chrome.
   - Or open the branch zip: https://github.com/zyxinfnite/first/archive/refs/heads/feat/pwa.zip and extract the frontend/local-redirect-demo/index.html file.

3. The page will attempt to redirect to http://localhost:3000/ immediately.

Notes:
- If you need the redirect to point to a different URL, edit index.html and change the meta refresh and link.
- This demo is intended for legitimate local development and admin review. Do not use it to bypass network restrictions.
