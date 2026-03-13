# LCS Local Development Setup

## Migration from Firebase to VS Code

This guide helps you set up LCS for local development in VS Code.

## Prerequisites

- VS Code installed
- Git installed
- Python 3 (for local server) OR Live Server extension

## Setup Steps

### 1. Open in VS Code

**Option A: Open workspace file**
```bash
code lcs.code-workspace
```

**Option B: Open folder**
```bash
code .
```

### 2. Install Recommended Extensions

VS Code will prompt to install recommended extensions:
- **Live Server** - Local development server with live reload
- **Prettier** - Code formatting
- **ESLint** - JavaScript linting
- **Auto Rename Tag** - HTML tag pair renaming
- **CSS Peek** - Jump to CSS definitions

### 3. Start Development Server

**Option A: Using Live Server (Recommended)**
1. Install "Live Server" extension
2. Right-click on `main.html`
3. Select "Open with Live Server"
4. Browser opens at `http://localhost:5500/main.html`

**Option B: Using Python**
```bash
./dev-server.sh
```
Opens at `http://localhost:8000/main.html`

**Option C: Using Node.js**
```bash
npx http-server -p 8000
```

## Development Workflow

### File Structure
```
LCS/
├── .vscode/              # VS Code settings
├── .credentials/         # Git tokens (ignored)
├── gas-backend/          # Backend deployment
├── hf-deployment/        # HF Spaces deployment
├── assets/               # Static assets
├── main.html             # Entry point
└── *.html, *.js, *.css   # Application files
```

### Hot Reload
Live Server automatically reloads when you save files:
- HTML changes → instant reload
- CSS changes → instant reload
- JS changes → instant reload

### Debugging
1. Press `F5` or go to Run & Debug
2. Select "Launch LCS in Chrome"
3. Set breakpoints in JS files
4. Debug in VS Code

## Backend Development

The Google Apps Script backend is separate:
```bash
cd gas-backend
./deploy.sh
```

## Deployment

### Deploy to Hugging Face
```bash
cd hf-deployment
./deploy-hf.sh
```

### Deploy Backend
```bash
cd gas-backend
./deploy.sh
```

## Tips

- Use `Ctrl+P` to quickly open files
- Use `Ctrl+Shift+F` to search across all files
- Use `Ctrl+B` to toggle sidebar
- Use `Ctrl+`` to open terminal
- Use `F12` on functions/variables to go to definition

## Troubleshooting

**CORS Issues**: Use Live Server or Python server, not `file://` protocol

**Port Already in Use**: Change port in `.vscode/settings.json`

**Backend Not Working**: Check Google Apps Script URLs in `layout.js`

## Git Workflow

```bash
# Check status
git status

# Stage changes
git add .

# Commit
git commit -m "Your message"

# Push to GitHub
git push origin main

# Push to HF Spaces
git push huggingface main
```
