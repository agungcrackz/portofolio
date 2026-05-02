# Portfolio SPA

A modern, responsive portfolio website built with Vue 3, TypeScript, and Vite. Features a dark theme design with smooth animations and interactive components.

## Features

- ⚡ **Fast & Modern** - Built with Vue 3 and Vite for optimal performance
- 🎨 **Dark Theme** - Beautiful dark design with gradient accents
- 📱 **Fully Responsive** - Works seamlessly on desktop, tablet, and mobile
- ✨ **Smooth Animations** - Animated skill progress bars and transitions
- 📧 **Contact Form** - Integrated with Formspree for email delivery
- 🔗 **Social Links** - Direct links to GitHub, LinkedIn, Instagram, and Twitter
- 🎯 **Smooth Scrolling** - Smooth navigation between sections

## Tech Stack

- **Frontend Framework**: Vue 3
- **Language**: TypeScript
- **Build Tool**: Vite
- **Styling**: CSS3 with Glassmorphism effects
- **Form Service**: Formspree
- **Deployment**: Ready for Vercel, Netlify, or any static host

## Project Structure

```
src/
├── components/
│   ├── Header.vue       # Navigation header with smooth scrolling
│   ├── Hero.vue         # Hero section with CTA
│   ├── About.vue        # About section
│   ├── Skills.vue       # Skills with animated progress bars
│   ├── Projects.vue     # Projects showcase
│   └── Contact.vue      # Contact form with social links
├── assets/
│   └── style.css        # Global styles
├── App.vue              # Root component
└── main.ts              # Entry point
```

## Getting Started

### Prerequisites
- Node.js 16+ 
- npm or yarn

### Installation

1. Clone the repository
```bash
git clone https://github.com/agungcrackz/portofolio.git
cd portofolio
```

2. Install dependencies
```bash
npm install
```

3. Start development server
```bash
npm run dev
```

The app will be available at `http://localhost:5173`

### Build for Production

```bash
npm run build
```

The built files will be in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## Configuration

### Contact Form Setup

The contact form uses Formspree for email delivery. To set it up:

1. Go to https://formspree.io/
2. Sign up with your email
3. Create a new form
4. Copy your Form ID (format: `f/xxxxxxxx`)
5. Update `FORMSPREE_ID` in `src/components/Contact.vue`

### Customize Content

Edit the following files to customize your portfolio:

- **Header/Navigation**: `src/components/Header.vue`
- **Hero Section**: `src/components/Hero.vue`
- **About Section**: `src/components/About.vue`
- **Skills**: `src/components/Skills.vue` (update skills array)
- **Projects**: `src/components/Projects.vue` (update projects array)
- **Contact Info**: `src/components/Contact.vue` (update email, phone, location, social links)

## Deployment

### Deploy to Vercel (Recommended)

1. Push code to GitHub
2. Go to https://vercel.com/
3. Import your GitHub repository
4. Vercel will auto-detect Vue 3 + Vite settings
5. Deploy with one click

### Deploy to Netlify

1. Build the project: `npm run build`
2. Go to https://app.netlify.com/drop
3. Drag and drop the `dist/` folder
4. Your site is live!

### Deploy to Other Hosts

The `dist/` folder contains all static files needed. Upload it to any static hosting service.

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## License

This project is open source and available under the MIT License.

## Author

**Agung Crackz**
- Email: agungcrackz@gmail.com
- GitHub: [@agungcrackz](https://github.com/agungcrackz)
- Location: Langkat, Indonesia

---

Made with ❤️ using Vue 3 & Vite
