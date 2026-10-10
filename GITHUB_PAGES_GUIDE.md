# Publish VisionMesh on GitHub Pages (about 5 minutes)

GitHub Pages hosts static files only. This site is fully static, so it works. The Docker backend (FastAPI, Postgres, Neo4j) cannot run on Pages; run it locally or on a server.

## Option A: phone or browser only
1. github.com > **New repository** > name it `visionmesh-ai` > Public > Create.
2. Unzip `visionmesh-pages.zip` on your phone.
3. In the repo tap **Add file > Upload files**, select `index.html`, `README.md` and `.nojekyll` (hidden files may not show; `.nojekyll` is optional), then **Commit changes**.
4. **Settings > Pages**. Under *Build and deployment* choose **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
5. Wait 1 to 2 minutes. Your site: **https://nikhil-creat.github.io/visionmesh-ai/**

## Option B: Termux (phone)
```
pkg install git unzip -y && termux-setup-storage
cd ~/storage/downloads
unzip visionmesh-pages.zip -d visionmesh-ai && cd visionmesh-ai
git init -b main && git add . && git commit -m "VisionMesh AI v3 showcase"
git remote add origin https://github.com/Nikhil-creat/visionmesh-ai.git
git push -u origin main
```
When asked for a password, paste a **personal access token** (GitHub > Settings > Developer settings > Tokens, scope `repo`). Then do step 4 above.

## Publishing the full monorepo instead
Push the whole monorepo zip. Its `docs/` folder holds the same site. In **Settings > Pages** choose branch **main**, folder **/docs**. (Or choose *GitHub Actions* as the source: `.github/workflows/pages.yml` deploys `docs/`.)

## Troubleshooting
- **404:** repo must be Public (or a paid plan), file must be named exactly `index.html` in the chosen folder, and wait a couple of minutes.
- **Old version showing:** hard refresh, or open in a private tab.
- **3D background missing:** WebGL is blocked or the CDN is offline; the page still works with a plain background.
- **Custom domain:** Settings > Pages > Custom domain, then add a CNAME record at your DNS provider.
