# CINE MATCH - Movie Database Application

A modern movie discovery and tracking application with user authentication and personal movie collections.

## Features

- 🎬 **Movie Search**: Search movies using TMDB API
- 🔐 **User Authentication**: Login and registration system
- 📋 **Movie Database**: Organize movies into Wishlist, Watching, and Already Watched categories
- 💾 **Offline Support**: All data stored in localStorage
- 🎨 **Modern UI**: Beautiful dark purple theme with glassmorphism effects
- 🌐 **Vercel Ready**: Fully configured for Vercel deployment

## Tech Stack

- HTML5, CSS3, JavaScript (Vanilla)
- TMDB API for movie data
- localStorage for data persistence
- Vercel for hosting

## Setup Instructions

### Local Development

1. **Clone or download the repository**

2. **Get TMDB API Key** (Free):
   - Go to https://www.themoviedb.org/
   - Create a free account
   - Navigate to Settings > API
   - Request an API key
   - Copy your API key

3. **Configure API Key for Local Development**:
   - Open `home.js`
   - Find line 26: `const TMDB_API_KEY = 'YOUR_TMDB_API_KEY_HERE';`
   - Replace `'YOUR_TMDB_API_KEY_HERE'` with your actual API key
   - Example: `const TMDB_API_KEY = 'abc123def456ghi789';`

4. **Run locally**:
   - **Option A**: Simple file opening
     - Just open `home.html` in your web browser
     - The app will automatically use direct API calls
   
   - **Option B**: Local server (recommended, avoids CORS issues)
     ```bash
     # Using Python
     python -m http.server 8000
     
     # Using Node.js (http-server)
     npx http-server -p 8000
     
     # Then open: http://localhost:8000/home.html
     ```

**Note:** The app automatically detects if it's running locally or on Vercel:
- **Locally**: Uses direct TMDB API calls (needs API key in `home.js`)
- **On Vercel**: Uses API proxy automatically (needs API key in Vercel env vars)

### Vercel Deployment (Simple - No Git Required!)

#### Quick Deploy Steps:

1. **Go to Vercel**:
   - Visit https://vercel.com
   - Sign up/Login (free account)

2. **Deploy Your Project**:
   - Click **"Add New..."** → **"Project"**
   - **Option A**: Drag and drop your project folder (no Git needed!)
   - **Option B**: Import from GitHub if you have it there
   - Project name: `cinematch` (or your choice)
   - Framework: Leave as default or select "Other"

3. **Set Environment Variable** (IMPORTANT - Do this before deploying!):
   - Click **"Environment Variables"** section
   - Click **"Add"**
   - **Key**: `TMDB_API_KEY`
   - **Value**: `0b7ec94633601478da8ad67533d0275c`
   - **Environment**: Select all (Production, Preview, Development)
   - Click **"Save"**

4. **Deploy**:
   - Click **"Deploy"** button
   - Wait 1-2 minutes for deployment

5. **Done!** ✅
   - Your site is live!
   - Landing page (`index.html`) will show first
   - Click "Go to Home" to access the main app
   - API proxy works automatically

**Note**: After deployment, if you need to add/change the environment variable:
- Go to Project → Settings → Environment Variables
- Add/Edit the variable
- Go to Deployments → Click ⋯ → Redeploy

#### Important Notes for Vercel:

- ✅ The API proxy (`/api/movie-search.js`) automatically handles:
  - CORS issues
  - VPN compatibility
  - API key security (server-side only)
  
- ✅ No code changes needed - the app automatically detects Vercel deployment

- ✅ Environment variable `TMDB_API_KEY` must be set for the API to work

- ✅ The app works without VPN because API calls go through Vercel's serverless function

## Project Structure

```
├── home.html          # Home page with movie search
├── login.html          # Login page
├── register.html       # Registration page
├── database.html       # Movie database management
├── styles.css          # Global styles
├── auth.js             # Authentication logic
├── home.js             # Home page functionality
├── login.js            # Login page functionality
├── register.js         # Registration functionality
├── database.js         # Movie database logic
├── api/
│   └── movie-search.js # Vercel serverless function (API proxy)
├── vercel.json         # Vercel configuration
└── README.md           # This file
```

## API Proxy

The application includes an API proxy function (`/api/movie-search.js`) that:
- ✅ Handles CORS issues
- ✅ Works with VPN
- ✅ Keeps API keys secure (server-side only)
- ✅ Automatically used on Vercel deployment

## Features Breakdown

### Home Page
- Movie search with TMDB API
- Account menu with database links
- Works without login (search only)
- Requires login to add movies

### Authentication
- User registration
- User login
- Session management
- Remember me functionality

### Movie Database
- Add movies to categories
- Move movies between categories
- Delete movies
- Three categories: Wishlist, Watching, Already Watched
- User-specific data storage

## Customization

### Background Image
- Edit `styles.css` and change `--background-image` variable
- Place your image file in the project root
- Supported formats: JPG, PNG, WebP

### Footer Credits
- Edit `home.html` footer section
- Find the comment with instructions
- Modify the text as needed

### Colors/Theme
- Edit CSS variables in `styles.css` (`:root` section)
- Home page theme in `home.html` (`<style>` section)

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## License

Free to use and modify.

## Support

For issues or questions:
- Check TMDB API documentation: https://developers.themoviedb.org/
- Vercel documentation: https://vercel.com/docs

