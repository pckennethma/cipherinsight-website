# Cloudflare Pages Deployment Fix

## The Issue

Cloudflare is trying to run `wrangler deploy` (Workers command) instead of building a Pages site.

## Solution

### Step 1: Check Cloudflare Dashboard Settings

1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com)
2. Navigate to **Workers & Pages**
3. Find your `cipherinsight-website` project
4. Click on **Settings** → **Builds & deployments**

### Step 2: Correct Build Configuration

Make sure these settings are exactly as shown:

| Setting | Value |
|---------|-------|
| **Build command** | `npm run build` |
| **Build output directory** | `dist` |
| **Root directory** | (leave empty) |

**IMPORTANT:** Do NOT use `npx wrangler deploy` as the build command!

### Step 3: Environment Variables (if needed)

Add these in Settings → Environment variables:

| Variable | Value |
|----------|-------|
| `NODE_VERSION` | `20` |

### Step 4: Redeploy

1. Go to the **Deployments** tab
2. Click **Retry deployment** on the latest failed build
3. Or push a new commit to trigger a fresh build

## Alternative: Delete and Recreate Project

If the above doesn't work, the project might be configured as Workers instead of Pages:

1. In Cloudflare Dashboard → Workers & Pages
2. Find `cipherinsight-website` → Click **Settings** → **Delete project**
3. Create new:
   - Click **Create** → **Pages**
   - **Connect to Git**
   - Select `cipherinsight-website` repository
   - Build command: `npm run build`
   - Build output directory: `dist`
   - Click **Save and Deploy**

## Manual Deploy (Bypass Git Integration)

If Git integration continues to fail:

```bash
# Build locally
npm run build

# Deploy directly
npx wrangler pages deploy dist --project-name=cipherinsight-website
```

## Build Log Should Show

```
✨ Success! Uploaded x files
✨ Upload complete!
```

Not:
```
✘ [ERROR] It looks like you've run a Workers-specific command...
```
