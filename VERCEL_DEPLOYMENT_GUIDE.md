# 🚀 Vercel Deployment Guide - Step by Step

## Quick Deploy (No Git Commands Needed!)

### Step 1: Prepare Your Files
✅ All files are ready in your project folder:
- `index.html` - Landing page (entry point)
- `home.html` - Main application page
- `api/movie-search.js` - API proxy function
- `vercel.json` - Vercel configuration
- All other HTML, JS, CSS files

### Step 2: Deploy to Vercel

#### Option A: Via Vercel Dashboard (Easiest - No Git Required)

1. **Go to Vercel**
   - Visit [https://vercel.com](https://vercel.com)
   - Sign up or log in (free account)

2. **Create New Project**
   - Click **"Add New..."** → **"Project"**
   - Click **"Browse"** or drag and drop your project folder
   - OR click **"Import Git Repository"** if you have it on GitHub

3. **Configure Project**
   - **Project Name**: `cinematch` (or your choice)
   - **Framework Preset**: Other (or leave as default)
   - **Root Directory**: `./` (root)
   - **Build Command**: Leave empty (no build needed)
   - **Output Directory**: Leave empty

4. **Set Environment Variable** (IMPORTANT!)
   - Before clicking "Deploy", click **"Environment Variables"**
   - Click **"Add"**
   - **Key**: `TMDB_API_KEY`
   - **Value**: `0b7ec94633601478da8ad67533d0275c`
   - **Environment**: Select all (Production, Preview, Development)
   - Click **"Save"**

5. **Deploy**
   - Click **"Deploy"** button
   - Wait for deployment to complete (1-2 minutes)

6. **Done!** ✅
   - Your site is live!
   - Visit the URL provided by Vercel
   - You should see the landing page first

#### Option B: Via Vercel CLI (If You Prefer Command Line)

```bash
# Install Vercel CLI (one time)
npm install -g vercel

# Login to Vercel
vercel login

# Deploy (from your project folder)
vercel

# Set environment variable
vercel env add TMDB_API_KEY
# When prompted, enter: 0b7ec94633601478da8ad67533d0275c
# Select all environments when asked

# Deploy to production
vercel --prod
```

### Step 3: Verify Deployment

1. **Visit your site** (URL provided by Vercel)
2. **Check the flow**:
   - ✅ Landing page (`index.html`) should load first
   - ✅ Click "Go to Home" → Should navigate to `home.html`
   - ✅ Search for movies → Should work
   - ✅ Genres should load below search bar
   - ✅ Content sections should load on scroll

## Application Flow

```
User visits site
    ↓
Landing Page (index.html)
    ↓
Click "Go to Home"
    ↓
Home Page (home.html)
    ↓
- Search movies
- Browse genres
- View popular/top rated content
- Scroll to see more sections
```

## Environment Variables

### Required on Vercel:
- **`TMDB_API_KEY`**: `0b7ec94633601478da8ad67533d0275c`

### How to Set:
1. Vercel Dashboard → Your Project → Settings → Environment Variables
2. Add new variable
3. Name: `TMDB_API_KEY`
4. Value: `0b7ec94633601478da8ad67533d0275c`
5. Select all environments
6. Save and redeploy

## File Structure

```
your-project/
├── index.html          ← Landing page (shown first)
├── home.html           ← Main application
├── login.html
├── register.html
├── database.html
├── api/
│   └── movie-search.js ← Vercel serverless function
├── vercel.json         ← Vercel configuration
├── package.json
├── auth.js
├── home.js
├── styles.css
└── ... (other files)
```

## Troubleshooting

### Issue: Only background image shows
**Solution**: 
- Make sure `index.html` exists in root directory
- Check `vercel.json` has rewrites configured
- Clear browser cache (Ctrl+Shift+R)

### Issue: API not working
**Solution**:
- Verify `TMDB_API_KEY` is set in Vercel Environment Variables
- Redeploy after setting environment variable
- Check browser console for errors

### Issue: 404 errors
**Solution**:
- Verify all HTML files are in root directory
- Check file names match exactly (case-sensitive)
- Verify `vercel.json` rewrites are correct

### Issue: Landing page not showing first
**Solution**:
- Verify `index.html` exists
- Check `vercel.json` has rewrite for `/` → `/index.html`
- Clear browser cache

## What Happens on Deployment

1. **Vercel detects** `vercel.json` configuration
2. **Routes configured**:
   - `/` → `index.html` (landing page)
   - `/home` → `home.html`
   - `/api/*` → Serverless functions
3. **Environment variables** loaded
4. **Site deployed** and live!

## No Git Required!

You can deploy directly from your local folder:
- Drag and drop folder to Vercel dashboard
- OR use Vercel CLI: `vercel`
- No need to push to GitHub first (though it's recommended for version control)

## After Deployment

✅ Your site is live on Vercel  
✅ Landing page loads first  
✅ All features work  
✅ API proxy handles CORS automatically  
✅ No VPN needed  

**That's it! You're done!** 🎉

