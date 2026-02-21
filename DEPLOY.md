# Deployment Guide

## Git Repository Status

✅ Git repository initialized locally
✅ Initial commit made
✅ Founder photos included

## Step 1: Push to GitHub

### Option A: Using GitHub CLI (Recommended)

```bash
# Install GitHub CLI if not already installed
# brew install gh  (macOS)
# or download from https://cli.github.com/

# Login to GitHub
gh auth login

# Create a new repository and push
git remote add origin https://github.com/YOUR_USERNAME/cipherinsight-website.git
gh repo create cipherinsight-website --public --source=. --remote=origin --push
```

### Option B: Manual Git Commands

1. Create a new repository on GitHub:
   - Go to https://github.com/new
   - Name: `cipherinsight-website`
   - Make it Public or Private
   - Don't initialize with README (we already have one)

2. Push your code:

```bash
# Add remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/cipherinsight-website.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 2: Deploy to Cloudflare Pages

### Method 1: Git Integration (Recommended - Auto Deploy)

1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com)
2. Click **"Workers & Pages"** in the sidebar
3. Click **"Create"** → **"Pages"**
4. Click **"Connect to Git"**
5. Select your GitHub account and the `cipherinsight-website` repository
6. Click **"Begin setup"**

**Build Settings:**
- **Project name:** `cipherinsight-website`
- **Production branch:** `main`
- **Build command:** `npm run build`
- **Build output directory:** `dist`

7. Click **"Save and Deploy"**

Your site will be built and deployed automatically. Future pushes to `main` will trigger automatic redeployments.

### Method 2: Direct Upload (Manual)

```bash
# Build the project first
npm run build

# Install Wrangler if not already installed
npm install -g wrangler

# Login to Cloudflare
npx wrangler login

# Deploy to Pages
npx wrangler pages deploy dist --project-name=cipherinsight-website
```

## Step 3: Custom Domain (Optional)

After deployment, you can add a custom domain:

1. In Cloudflare Dashboard → Workers & Pages → Select your project
2. Go to **"Custom domains"** tab
3. Click **"Set up a custom domain"**
4. Enter your domain (e.g., `cipherinsight.io`)
5. Follow the DNS setup instructions

## Environment Variables (If Needed)

If you need environment variables for production:

1. Go to Cloudflare Dashboard → Workers & Pages → Your project
2. Go to **"Settings"** → **"Environment variables"**
3. Add your variables (e.g., API keys, analytics IDs)

## Troubleshooting

### Build Fails on Cloudflare

Make sure these files are committed:
- `package.json`
- `package-lock.json`
- `vite.config.ts`
- `tailwind.config.js`

### Photos Not Showing

Founder photos are in `public/founders/` and will be copied to `dist/` during build. Check:
1. Photos are committed: `git ls-files public/founders/`
2. Build output includes photos: `ls dist/founders/`

## Continuous Deployment

With Git integration enabled:
- Push to `main` → Auto deploy to production
- Create a Pull Request → Cloudflare generates a preview URL

## Your Site Will Be Available At:

- `https://cipherinsight-website.pages.dev` (default)
- Your custom domain (if configured)
