# 🚀 AFEX Test Site - Setup & Installation Guide

Complete guide to set up AFEX Test Site on GitHub and run it locally.

## 📋 Prerequisites

- Git installed on your system
- A GitHub account
- A modern web browser (Chrome, Firefox, Safari, or Edge)
- (Optional) Node.js and npm for local server

## 🎯 GitHub Setup Instructions

### Step 1: Create Repository

```bash
# Login to GitHub and create a new repository
# Name: afex-test-site
# Description: Comprehensive automation testing platform
# Public: Yes
# Add README: No (we already have one)
# Add .gitignore: No (we already have one)
```

### Step 2: Clone Repository

```bash
# Create a local directory
mkdir afex-test-site
cd afex-test-site

# Initialize git
git init

# Add remote repository
git remote add origin https://github.com/YOUR_USERNAME/afex-test-site.git

# Create and switch to main branch
git branch -M main
```

### Step 3: Add Files

```bash
# Copy all files to the directory:
# - index.html
# - README.md
# - LICENSE
# - .gitignore
# - test-data-sample.json
# - SETUP_GUIDE.md

# Check git status
git status
```

### Step 4: Initial Commit

```bash
# Stage all files
git add .

# Commit changes
git commit -m "Initial commit: Add AFEX Test Site"

# Push to GitHub
git push -u origin main
```

### Step 5: GitHub Pages Setup (Optional)

```bash
# Go to GitHub repository settings
# Navigate to: Settings > Pages > Source
# Select: Deploy from a branch
# Branch: main
# Folder: root (/)
# Click Save

# Your site will be available at:
# https://YOUR_USERNAME.github.io/afex-test-site/
```

## 💻 Local Setup

### Option 1: Direct File Opening
```bash
# Simply open the HTML file in your browser
open index.html
# or
firefox index.html
```

### Option 2: Python Simple Server (Python 3)
```bash
# Navigate to project directory
cd afex-test-site

# Start server on port 8000
python3 -m http.server 8000

# Open browser to: http://localhost:8000
```

### Option 3: Python Simple Server (Python 2)
```bash
# Navigate to project directory
cd afex-test-site

# Start server on port 8000
python -m SimpleHTTPServer 8000

# Open browser to: http://localhost:8000
```

### Option 4: Node.js with http-server
```bash
# Install http-server globally
npm install -g http-server

# Navigate to project directory
cd afex-test-site

# Start server
http-server

# Open browser to: http://localhost:8080
```

### Option 5: Live Server (VS Code)
```bash
# Install Live Server extension in VS Code
# Right-click on index.html
# Select "Open with Live Server"

# Browser opens automatically with hot reload
```

### Option 6: Using PHP (if available)
```bash
# Navigate to project directory
cd afex-test-site

# Start server on port 8000
php -S localhost:8000

# Open browser to: http://localhost:8000
```

## 📁 Directory Structure After Setup

```
afex-test-site/
├── index.html                 # Main test site
├── README.md                  # Project documentation
├── SETUP_GUIDE.md            # This file
├── LICENSE                    # MIT License
├── .gitignore                # Git ignore rules
├── test-data-sample.json     # Sample test data
├── .git/                     # Git repository
└── .github/
    └── workflows/            # (Optional) GitHub Actions
```

## 🔧 Project Configuration

### Update Package Information

If you want to add a package.json for npm:

```json
{
  "name": "afex-test-site",
  "version": "1.0.0",
  "description": "Comprehensive automation testing platform",
  "license": "MIT",
  "author": "Your Name",
  "scripts": {
    "start": "python3 -m http.server 8000",
    "dev": "http-server -p 8000 -c-1"
  },
  "keywords": [
    "automation",
    "testing",
    "afex",
    "qa",
    "form-testing"
  ]
}
```

### Create GitHub Actions Workflow (Optional)

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      
      - name: Build
        run: echo "Building AFEX Test Site..."
      
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

## 🌐 Deployment Options

### Option 1: GitHub Pages (Free)
```
URL: https://your-username.github.io/afex-test-site/
Setup: Automatic via Settings
Cost: Free
```

### Option 2: Vercel (Free)
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# URL: https://afex-test-site.vercel.app/
```

### Option 3: Netlify (Free)
```bash
# Manual deployment via web interface
# Or using Netlify CLI:
npm i -g netlify-cli
netlify deploy
```

### Option 4: Personal Server/VPS
```bash
# SCP files to server
scp -r ./afex-test-site user@server:/var/www/html/

# Access via: http://your-domain.com/afex-test-site/
```

## 🧪 Testing the Site Locally

### Manual Testing Checklist
- [ ] Open index.html in browser
- [ ] Navigate to Signup tab
  - [ ] Fill text inputs
  - [ ] Select radio buttons
  - [ ] Check checkboxes
  - [ ] Select from dropdown
  - [ ] Submit form
- [ ] Navigate to Add Listing tab
  - [ ] Fill business information
  - [ ] Set business hours
  - [ ] Upload images
  - [ ] Select payment methods
  - [ ] Open preview modal
- [ ] Navigate to Test Components tab
  - [ ] Test toggle switch
  - [ ] Test dropdowns with search
  - [ ] Click various buttons
  - [ ] Open modal

### Browser Compatibility Testing
```
✓ Chrome (latest)
✓ Firefox (latest)
✓ Safari (latest)
✓ Edge (latest)
✓ Mobile Chrome
✓ Mobile Safari
```

## 🔐 Security Considerations

### Important Notes
- This is a **test/demo site** - not production-ready
- No real data is submitted anywhere
- All data stays in the browser (no backend)
- Images are converted to Base64 in memory
- No API calls to external services

### For Production Use
- Add server-side validation
- Implement HTTPS
- Add CSRF protection
- Sanitize all inputs
- Use secure file upload
- Add authentication
- Implement proper error handling
- Add rate limiting

## 📱 Mobile Testing

### iOS Safari
```
1. Open Safari
2. Enter URL: http://your-ip:8000
3. Test form elements
4. Test touch interactions
```

### Android Chrome
```
1. Open Chrome
2. Enter URL: http://your-ip:8000
3. Enable responsive mode
4. Test all features
```

## 🐛 Troubleshooting Setup

### Port Already in Use
```bash
# Find what's using the port (macOS/Linux)
lsof -i :8000

# Kill the process
kill -9 <PID>

# Or use different port
python3 -m http.server 9000
```

### Permission Denied
```bash
# Make directory writable
chmod 755 afex-test-site/

# Make files readable
chmod 644 afex-test-site/*.html
```

### Images Not Loading
- Ensure browser allows local file access
- Use a local server instead of opening file directly
- Check browser console for CORS errors

### JavaScript Not Working
- Check browser console for errors
- Ensure JavaScript is enabled
- Clear browser cache (Ctrl+Shift+Delete)
- Try in private/incognito mode

## 📚 Next Steps

### After Setup
1. [ ] Customize branding (colors, text)
2. [ ] Add your own test data
3. [ ] Create test automation scripts
4. [ ] Add CI/CD workflows
5. [ ] Document test cases
6. [ ] Share with team

### Customization Examples
```html
<!-- Change title -->
<title>Your Company Test Site</title>

<!-- Change header text -->
<h1>🔧 Your Company Test Platform</h1>

<!-- Customize colors in CSS -->
:root {
  --primary: #your-color;
}
```

## 🔗 Useful Resources

### Learning Resources
- [Git Handbook](https://guides.github.com/introduction/git-handbook/)
- [GitHub Pages Guide](https://pages.github.com/)
- [HTML/CSS/JavaScript Tutorials](https://www.w3schools.com/)
- [Automation Testing Best Practices](./docs/BEST_PRACTICES.md)

### Tools
- [GitHub Desktop](https://desktop.github.com/) - GUI for Git
- [VS Code](https://code.visualstudio.com/) - Code Editor
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/) - Browser debugging

### Similar Projects
- [AFEX Framework](https://github.com/search?q=afex)
- [Automation Testing Sites](https://github.com/topics/automation-testing)
- [Test Automation](https://github.com/topics/test-automation)

## 📞 Support

### Getting Help
1. Check [README.md](./README.md) for documentation
2. Review [TROUBLESHOOTING.md](./docs/TROUBLESHOOTING.md)
3. Check GitHub Issues
4. Create a new Issue with:
   - Steps to reproduce
   - Browser and OS
   - Error messages
   - Screenshots if applicable

## ✅ Verification Checklist

After setup, verify:
- [ ] Files are in correct location
- [ ] Git repository is initialized
- [ ] Files are committed to GitHub
- [ ] Site is accessible locally
- [ ] Site is accessible on GitHub Pages (if enabled)
- [ ] All forms work correctly
- [ ] Images can be uploaded
- [ ] Modals open and close
- [ ] Search functionality works
- [ ] Responsive design works on mobile

## 🎉 You're Ready!

Your AFEX Test Site is now set up and ready for testing!

### Quick Links
- **Local**: http://localhost:8000
- **GitHub**: https://github.com/YOUR_USERNAME/afex-test-site
- **Live**: https://YOUR_USERNAME.github.io/afex-test-site/

### Pro Tips
1. Use browser DevTools to inspect elements
2. Open browser console to see debug messages
3. Test with different browsers
4. Use form data sample from test-data-sample.json
5. Customize colors in CSS variables

---

**Last Updated**: 2024
**Version**: 1.0.0
**Status**: Ready for Use
