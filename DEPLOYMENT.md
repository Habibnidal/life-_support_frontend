# Frontend Deployment Guide (Vercel only)

## 1) Push to GitHub

```bash
git add -A
git commit -m "Frontend-only deploy setup"
git branch -M main
git remote add origin https://github.com/<YOUR_USERNAME>/<YOUR_REPO>.git
git push -u origin main
```

If `origin` already exists:

```bash
git remote set-url origin https://github.com/<YOUR_USERNAME>/<YOUR_REPO>.git
git push -u origin main
```

## 2) Configure API base for frontend

Set your backend API URL in `config.js`:

```js
window.VELORIA_CONFIG = {
  API_BASE: 'https://YOUR-BACKEND-API-DOMAIN'
};
```

Commit and push this change.

## 3) Deploy frontend on Vercel

1. Open Vercel -> Add New Project -> Import Git Repository.
2. Select this repository.
3. Framework preset: `Other`.
4. Root directory: repository root.
5. Build command: empty.
6. Output directory: empty.
7. Deploy.

`vercel.json` will serve this as a static frontend.

## 4) Verify

1. Open your Vercel URL.
2. Confirm browser network requests go to your configured `API_BASE`.
3. If API calls fail, update `config.js` with the correct backend URL and redeploy.
