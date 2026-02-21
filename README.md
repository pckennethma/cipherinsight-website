# CipherInsight Website

A modern, responsive Vue.js 3 website for CipherInsight Limited - a privacy-preserving analytics company using Zero-Knowledge Proof technology.

## Tech Stack

- **Vue 3** - Progressive JavaScript framework
- **TypeScript** - Type-safe development
- **Vite** - Fast build tool
- **Tailwind CSS** - Utility-first CSS framework
- **Cloudflare Pages** - Static site hosting

## Features

- 🎨 Modern dark theme with gradient accents
- ✨ Smooth scroll animations and hover effects
- 📱 Fully responsive design
- ⚡ Fast performance with Vite
- 🔒 Privacy-focused (no tracking)

## Project Structure

```
cipherinsight-website/
├── src/
│   ├── components/       # Vue components
│   │   ├── NavigationBar.vue
│   │   ├── HeroSection.vue
│   │   ├── AboutSection.vue
│   │   ├── TeamSection.vue
│   │   ├── SolutionsSection.vue
│   │   ├── AwardsSection.vue
│   │   ├── PublicationsSection.vue
│   │   ├── ContactSection.vue
│   │   └── FooterSection.vue
│   ├── assets/          # Static assets
│   │   └── main.css     # Tailwind styles
│   ├── App.vue          # Root component
│   └── main.ts          # Entry point
├── index.html           # HTML template
├── package.json         # Dependencies
├── tailwind.config.js   # Tailwind configuration
├── vite.config.ts       # Vite configuration
└── wrangler.jsonc       # Cloudflare Pages config
```

## Development

### Install dependencies

```bash
npm install
```

### Start development server

```bash
npm run dev
```

### Build for production

```bash
npm run build
```

### Preview production build

```bash
npm run preview
```

## Deployment

### Option 1: Cloudflare Pages (Git Integration)

1. Push code to GitHub
2. Go to [Cloudflare Dashboard](https://dash.cloudflare.com)
3. Workers & Pages → Create → Pages → Connect to Git
4. Select your repository
5. Build settings:
   - Build command: `npm run build`
   - Build output directory: `dist`

### Option 2: Direct Upload

```bash
# Login to Cloudflare
npx wrangler login

# Deploy
npx wrangler pages deploy dist --project-name=cipherinsight-website
```

## Design Credits

Built following best practices from:
- Web Design Guidelines
- Tailwind CSS Design System
- Tailwind CSS Animations

## License

© 2025 CipherInsight Limited. All rights reserved.
