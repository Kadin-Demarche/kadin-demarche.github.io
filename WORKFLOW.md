# Your Blog Workflow

## 📁 Location
Your blog is at: `/Users/kadin/Cursor/kadin-demarche.github.io`

## 🛠️ Working Locally

### 1. Preview Your Blog
```bash
cd /Users/kadin/Cursor/kadin-demarche.github.io
npm run serve
```
Visit: http://localhost:3000

The server will auto-rebuild when you change files!

### 2. Create a New Post
```bash
npm run new "Your Post Title"
```
This creates a new post file in `content/posts/` with today's date.

### 3. Edit Content
- **Posts**: `content/posts/*.md`
- **Homepage**: `content/index.md`
- **About page**: `content/about.md`

### 4. Edit Settings
- **Site config**: `config.yaml` (title, description, social links)
- **Navigation**: Edit `navigation:` section in `config.yaml`

## 🚀 Deploy to GitHub Pages

### Option 1: Quick Deploy
```bash
npm run build          # Build the site
git add .              # Stage all changes
git commit -m "Update blog content"
git push origin main   # Deploy!
```

GitHub Actions will automatically deploy your site in ~1 minute.

### Option 2: Deploy with Realistic Timestamps
```bash
npm run build
git add .

# Set a past timestamp (yesterday evening)
export GIT_AUTHOR_DATE="Tue Nov 19 20:30:00 2025 -0800"
export GIT_COMMITTER_DATE="Tue Nov 19 20:30:00 2025 -0800"

git commit -m "Add new post about X"
git push origin main
```

## 📝 Writing Tips

### Post Format
```markdown
---
title: "Your Post Title"
date: 2025-11-20
tags: [tech, projects]
excerpt: "A short description"
---

Your content here...
```

### What to Write
- Projects you're working on
- Things you learned
- Failed experiments (people love these)
- College/school experiences
- Tech opinions

### Keep it Real
- Write like you talk
- Short paragraphs
- Be honest about failures
- Don't overthink it

## 🔧 Customization

### Change Colors
Edit `assets/css/style.css` - look for `:root` variables at the top

### Add Pages
1. Create `content/your-page.md`
2. Add to navigation in `config.yaml`

### Modify Templates
Templates are in `templates/` folder:
- `base.html` - Header/footer
- `post.html` - Blog post layout
- `blog.html` - Blog listing page

## 🐛 Troubleshooting

### Server won't start (port in use)
```bash
npm run serve -- --port 3001
```

### Build errors
```bash
rm -rf _site node_modules
npm install
npm run build
```

### See what changed
```bash
git status          # See modified files
git diff            # See exact changes
```

## 📊 Check Your Live Site
- **Blog**: https://kadin-demarche.github.io
- **GitHub Actions**: https://github.com/Kadin-Demarche/kadin-demarche.github.io/actions

---

**Quick Commands:**
```bash
npm run build    # Build site
npm run serve    # Preview locally
npm run new      # Create new post
git push         # Deploy to GitHub
```
