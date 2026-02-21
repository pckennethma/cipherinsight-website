# Troubleshooting Guide

## `npm run dev` Not Working?

### 1. Port Already in Use
**Symptom:** Error about port 5173 being in use

**Fix:** Vite will automatically try another port (like 5174, 5175, etc.)
- Just look for the URL in the output: `http://localhost:5174/`
- Or manually specify a port: `npm run dev -- --port 3000`

### 2. Kill Existing Process
```bash
# Kill any existing Vite processes
npx kill-port 5173

# Or find and kill manually
lsof -ti:5173 | xargs kill -9
```

### 3. Node Modules Issues
```bash
# Clean and reinstall
rm -rf node_modules package-lock.json
npm install
npm run dev
```

### 4. Clear Vite Cache
```bash
rm -rf node_modules/.vite
npm run dev
```

### 5. Check Node Version
```bash
node --version  # Should be 18.x or higher
```

If none of these work, check the error message carefully and share it for help.
