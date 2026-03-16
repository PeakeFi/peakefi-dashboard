# PeakeFi Dashboard — Deployment Guide

Charlie, here's the step-by-step to get this live tonight. You'll need about 15 minutes.

---

## Step 1: Create a GitHub Account (skip if you have one)

1. Go to **github.com** and click **Sign up**
2. Use your PeakeFi email or a personal email — totally up to you
3. Pick a username (e.g. `peakefi-ops` or `charliereynolds`)
4. Verify your email

---

## Step 2: Create a New Repository

1. Once logged in, click the **+** icon (top-right) → **New repository**
2. Name it: `peakefi-dashboard`
3. Set it to **Private** (your team's data will eventually flow through here)
4. **Do NOT** check "Add a README" or ".gitignore" — we already have those
5. Click **Create repository**
6. You'll see a page with setup instructions — keep this tab open, you'll need the URL

---

## Step 3: Upload the Project Files

**Easiest way (no command line needed):**

1. On your new repo page, click **"uploading an existing file"** link
2. Drag the entire contents of the `peakefi-dashboard` folder into the upload area:
   - `public/` folder (contains `index.html`)
   - `server.js`
   - `package.json`
   - `.gitignore`
3. Type a commit message like: "Initial dashboard MVP"
4. Click **Commit changes**

**Note:** Make sure the files are at the ROOT of the repo, not nested inside another folder. The repo structure should look like:
```
peakefi-dashboard/
├── public/
│   └── index.html
├── server.js
├── package.json
└── .gitignore
```

---

## Step 4: Deploy on Railway

1. Go to **railway.com** and click **Login** → **Login with GitHub**
   - Authorize Railway to access your GitHub account
2. From the Railway dashboard, click **New Project**
3. Choose **Deploy from GitHub Repo**
4. Select your `peakefi-dashboard` repository
5. Railway will automatically detect it's a Node.js project and start building
6. Wait about 60 seconds for it to deploy (you'll see a green checkmark)
7. Click **Settings** → scroll to **Networking** → click **Generate Domain**
8. Railway will give you a URL like `peakefi-dashboard-production-xxxx.up.railway.app`
9. That's your live dashboard! Share the URL with your team.

---

## Step 5: Share with the Team

Send the Railway URL to your team. They can:
- Bookmark it
- Filter by their name to see their own clients
- Check it daily to stay on top of classifications

---

## When Cameron Takes Over

Hand Cameron this repo. To wire it to Double's API, he'll:
1. Replace the `MOCK_DATA` array in `public/index.html` with a fetch call to Double's API
2. Add the Double API credentials as **environment variables** in Railway (Settings → Variables)
3. Add a simple API route in `server.js` that proxies requests to Double (keeps the API key secure)

The integration notes are at the bottom of the dashboard itself.

---

## Troubleshooting

**Railway says "build failed":**
- Make sure `package.json` and `server.js` are at the root of the repo (not inside a subfolder)

**Page is blank:**
- Make sure `public/index.html` exists in the repo

**Need to update the dashboard:**
- Edit files on GitHub (click the file → pencil icon → edit → commit)
- Railway auto-deploys every time you push changes

---

## Cost

Railway's free Starter plan gives you $5/month in credits, which is more than enough for this dashboard. If you use it more heavily later, the Hobby plan is $5/month.
