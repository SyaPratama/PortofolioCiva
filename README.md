# Civa Camelia — Portfolio Website

A modern, responsive single-page portfolio built with **Vue 3** + **Vite**.

## 🎨 Color Theme
- `#FFF9D2` Cream (background)
- `#FFEBCC` Peach (sections/cards)
- `#BFDDF0` Sky Blue (accents)
- `#8CC0EB` Blue (primary/buttons)

## 📁 Project Structure
```
src/
├── assets/
│   └── css/
│       └── main.css         # Global styles & CSS variables
├── components/
│   ├── NavBar.vue           # Fixed navigation
│   ├── HeroSection.vue      # Landing hero
│   ├── AboutSection.vue     # About me
│   ├── SkillsSection.vue    # Skills & expertise
│   ├── ProjectsSection.vue  # Featured projects
│   ├── ContactSection.vue   # Contact form
│   └── FooterSection.vue    # Footer
├── App.vue                  # Root component
└── main.js                  # Entry point
```

## 🚀 Getting Started
```bash
npm install
npm run dev
```

## 🏗️ Build for Production
```bash
npm run build
```

## 🌐 Deploy to GitHub Pages
1. Push the repo to GitHub
2. Run `npm run build`
3. Deploy the `dist/` folder using GitHub Actions or manually

### GitHub Actions (auto-deploy)
Create `.github/workflows/deploy.yml` and configure for GitHub Pages.

## ✏️ Customization
- **Personal info**: Edit each section component directly
- **Colors**: Change CSS variables in `src/assets/css/main.css`
- **Projects**: Update the `projects` array in `ProjectsSection.vue`
- **Skills**: Update the `skills` array in `SkillsSection.vue`

## 📄 Copyright
© Rasya 2026
