# Deployment Instructions

## GitHub Pages (Recommended - Free & Easy)

### Step 1: Create GitHub Account
1. Go to https://github.com
2. Sign up for free account

### Step 2: Create Repository
1. Click "New repository"
2. Name it: `health-wellness-app`
3. Make it **Public**
4. Don't initialize with README (we have one)
5. Click "Create repository"

### Step 3: Upload Files
Two options:

**Option A: Use GitHub Web Interface (Easiest)**
1. On your new repo page, click "uploading an existing file"
2. Drag all files from this folder:
   - `index.html`
   - `README.md`
   - `SETUP_GUIDE.md`
   - `.gitignore`
3. Click "Commit changes"

**Option B: Use Git Command Line**
```bash
# In this folder, run:
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOURUSERNAME/health-wellness-app.git
git push -u origin main
```

### Step 4: Enable GitHub Pages
1. Go to repo Settings
2. Click "Pages" in left sidebar
3. Under "Source", select:
   - Branch: `main`
   - Folder: `/ (root)`
4. Click Save
5. Wait 1-2 minutes

### Step 5: Visit Your Live App! 🎉
Your app will be at: `https://YOURUSERNAME.github.io/health-wellness-app/`

---

## Netlify (Alternative - Also Free)

### Option 1: Drag & Drop
1. Go to https://app.netlify.com/drop
2. Drag the entire folder
3. Get instant URL like `https://random-name.netlify.app`

### Option 2: Connect GitHub
1. Sign up at https://netlify.com
2. Click "New site from Git"
3. Connect your GitHub repo
4. Deploy automatically on every commit

---

## Vercel (Alternative - Also Free)

1. Sign up at https://vercel.com
2. Click "Import Project"
3. Connect GitHub repo
4. Deploy with one click
5. Get URL like `https://your-app.vercel.app`

---

## Custom Domain (Optional)

Once deployed, you can add a custom domain:

1. **Buy a domain** (~$12/year):
   - Namecheap.com
   - Google Domains
   - GoDaddy

2. **Connect to GitHub Pages**:
   - In repo Settings → Pages → Custom domain
   - Enter: `yourapp.com`
   - Follow DNS instructions

3. **Or connect to Netlify/Vercel**:
   - In dashboard, go to Domain settings
   - Add custom domain
   - Update your domain's DNS settings

---

## Adding API Keys (After Deployment)

⚠️ **IMPORTANT**: Don't commit API keys to GitHub!

1. After deploying, edit `index.html` directly on GitHub:
   - Click `index.html` in your repo
   - Click pencil icon (Edit)
   - Update the CONFIG section (lines 18-22)
   - Commit changes

2. Or use environment variables (advanced):
   - Create separate `config.js` file
   - Add to `.gitignore`
   - Deploy with build process

---

## Updating Your App

### Via GitHub Web:
1. Click on file to edit
2. Make changes
3. Commit
4. Auto-deploys in 1-2 minutes

### Via Git:
```bash
# Make changes locally
git add .
git commit -m "Updated feature X"
git push
# Auto-deploys
```

---

## Testing Locally

Just open `index.html` in your browser:
```bash
# macOS
open index.html

# Windows
start index.html

# Linux
xdg-open index.html
```

Or use a simple server:
```bash
# Python 3
python -m http.server 8000

# Node.js (if you have it)
npx serve .
```

Then visit: `http://localhost:8000`

---

## Troubleshooting

**App not loading?**
- Check browser console (F12) for errors
- Make sure all files uploaded correctly

**Calendar not connecting?**
- Add your Google API credentials
- Check authorized origins include your URL

**Voice not working?**
- Only works in Chrome/Safari
- Requires HTTPS (GitHub Pages has this)
- Must grant microphone permissions

---

## Need Help?

Open an issue on GitHub or email [your-email]
