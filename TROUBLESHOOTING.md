# 🔧 Troubleshooting: "Failed to Load Movies" Error

## Common Causes & Solutions

### Issue 1: TMDB_API_KEY Not Set in Vercel ⚠️ MOST COMMON

**Symptom**: "Failed to load movies" or "TMDB API key not configured"

**Solution**:
1. Go to Vercel Dashboard → Your Project
2. Click **Settings** → **Environment Variables**
3. Check if `TMDB_API_KEY` exists
4. If not, add it:
   - **Key**: `TMDB_API_KEY`
   - **Value**: `0b7ec94633601478da8ad67533d0275c`
   - **Environment**: Select all (Production, Preview, Development)
5. **IMPORTANT**: Go to **Deployments** → Click ⋯ → **Redeploy**
6. Wait for redeployment to complete

**Why**: Environment variables only take effect after redeployment!

---

### Issue 2: API Proxy Not Working

**Symptom**: Network errors in browser console

**Check**:
1. Open browser DevTools (F12)
2. Go to **Network** tab
3. Try searching for a movie
4. Look for `/api/movie-search` request
5. Check the response:
   - **Status 200**: Working ✅
   - **Status 500**: API key issue (see Issue 1)
   - **Status 404**: API function not found
   - **CORS error**: Check vercel.json headers

**Solution**:
- If 404: Verify `api/movie-search.js` exists in your project
- If 500: Set environment variable (see Issue 1)
- If CORS: Check `vercel.json` has CORS headers

---

### Issue 3: Browser Console Errors

**Check Browser Console**:
1. Open DevTools (F12)
2. Go to **Console** tab
3. Look for red error messages
4. Common errors:
   - `Failed to fetch` → Network/API issue
   - `TMDB API key not configured` → Set environment variable
   - `CORS error` → Check vercel.json
   - `404 Not Found` → Check API function path

---

### Issue 4: API Function Not Deployed

**Symptom**: 404 errors for `/api/movie-search`

**Check**:
1. Verify `api/movie-search.js` exists in your project
2. Verify it's in the root `api/` folder (not nested)
3. Check Vercel deployment logs:
   - Go to Deployments → Click on latest deployment
   - Check **Functions** tab
   - Should see `api/movie-search.js` listed

**Solution**:
- Make sure file is at: `api/movie-search.js` (not `api/api/movie-search.js`)
- Redeploy if file was added after initial deployment

---

### Issue 5: Environment Variable Not Applied

**Symptom**: API key error even though it's set

**Solution**:
1. **Redeploy** after setting environment variable
2. Environment variables only apply to NEW deployments
3. Go to Deployments → Click ⋯ → Redeploy
4. Wait for deployment to complete

---

## Quick Diagnostic Steps

### Step 1: Check Environment Variable
```bash
# In Vercel Dashboard:
Settings → Environment Variables → Check TMDB_API_KEY exists
```

### Step 2: Check Browser Console
```javascript
// Open DevTools (F12) → Console tab
// Look for errors when page loads
```

### Step 3: Check Network Requests
```javascript
// Open DevTools (F12) → Network tab
// Try searching for a movie
// Check /api/movie-search request:
//   - Status code
//   - Response body
//   - Error messages
```

### Step 4: Test API Directly
Visit in browser (replace YOUR_DOMAIN):
```
https://YOUR_DOMAIN.vercel.app/api/movie-search?type=popular&media_type=movie&page=1
```

**Expected Response**:
```json
{
  "success": true,
  "results": [...],
  "total_pages": 500,
  "total_results": 10000
}
```

**If Error**:
```json
{
  "error": "TMDB API key not configured",
  "message": "Please set TMDB_API_KEY in your Vercel environment variables"
}
```

---

## Debugging Code Added

The code now includes better error messages:
- Shows specific error messages
- Indicates if API key is missing
- Logs detailed error information to console

**Check Browser Console** for detailed error logs:
```javascript
// Look for:
Error fetching popular: Failed to fetch popular: TMDB API key not configured
Error details: { type: 'popular', mediaType: 'movie', ... }
```

---

## Step-by-Step Fix

1. ✅ **Set Environment Variable**
   - Vercel Dashboard → Settings → Environment Variables
   - Add: `TMDB_API_KEY` = `0b7ec94633601478da8ad67533d0275c`

2. ✅ **Redeploy**
   - Deployments → Click ⋯ → Redeploy
   - Wait for completion

3. ✅ **Test**
   - Visit your site
   - Open browser console (F12)
   - Try searching for a movie
   - Check for errors

4. ✅ **Verify API**
   - Check Network tab for `/api/movie-search` request
   - Should return status 200 with movie data

---

## Still Not Working?

1. **Check Vercel Logs**:
   - Deployments → Latest deployment → Functions tab
   - Look for error logs

2. **Verify File Structure**:
   ```
   your-project/
   ├── api/
   │   └── movie-search.js  ← Must exist here
   ├── vercel.json
   └── ...
   ```

3. **Test Locally First**:
   - Open `home.html` in browser
   - Should work with direct API calls
   - If local works but Vercel doesn't → Environment variable issue

4. **Contact Support**:
   - Check Vercel documentation
   - Check TMDB API status
   - Verify API key is valid

---

## Success Indicators

✅ **Working Correctly When**:
- Movies load on page load
- Search returns results
- Genres display below search bar
- Content sections load on scroll
- No errors in browser console
- Network requests return status 200

