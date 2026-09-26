# D&O Quote Comparator — Vercel deployment

Static site. One page, no server, no build step, no dependencies to install.

## Files
- `index.html` — the whole tool (PDF reader, Excel writer, fonts and logo are all inside this one file)
- `vercel.json` — security headers + "always serve the newest version" for index.html

## Option A — drag and drop (easiest, no tools needed)
1. Zip this folder (or use the `DO_Comparator_Vercel.zip` provided).
2. Go to https://vercel.com/new
3. Scroll to the bottom and drop the zip onto the upload box.
4. Click **Deploy**. You get a URL like `do-quote-comparator.vercel.app`.

## Option B — Vercel CLI
```
npm i -g vercel
cd <this folder>
vercel          # preview URL
vercel --prod   # live URL
```

## Option C — GitHub (best if you want to keep updating it)
1. Create a new empty repo on GitHub.
2. Upload `index.html` and `vercel.json` to it.
3. On https://vercel.com/new choose **Import Git Repository**, pick the repo.
4. Framework preset: **Other**. Build command: leave empty. Output directory: leave empty.
5. Deploy. Every future push to the repo redeploys automatically.

## Updating the tool later
Replace `index.html` and redeploy (re-drop the zip, run `vercel --prod`, or push to GitHub).

## Notes
- Quote PDFs are read **inside the browser**. Nothing is uploaded to Vercel or anywhere else — the server only sends the page, it never sees a quote.
- Taught insurer layouts are stored per browser on each person's own machine. To give the whole team the same taught layouts, use **Download tool with layouts built in** in the tool, rename that file to `index.html`, and redeploy.
- Free Vercel plan is enough. To restrict access to your team, add Vercel Authentication (Project → Settings → Deployment Protection), which needs a Pro plan.
- Custom domain: Project → Settings → Domains, e.g. `cq.idealinsurance.in`.
