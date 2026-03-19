# 🔐 Minimal Messaging App

A terminal-style, 1-to-1 messaging application built with React + Vite, Firebase, and Tailwind CSS.

## 🚀 Quick Start

### Option 1: Single HTML File (5 minutes ⚡)
```bash
1. Open messaging-app-complete.html
2. Get Firebase credentials from Firebase Console
3. Update firebaseConfig in the file
4. Open in browser
```

### Option 2: Vite Project (20 minutes 💻)
```bash
mkdir messaging-app && cd messaging-app
npm init -y
npm install react react-dom firebase
npm install -D vite @vitejs/plugin-react tailwindcss postcss autoprefixer
```

Then copy all files from the `src/` structure provided in documentation.

## ✨ Features

✅ Google OAuth authentication  
✅ 1-to-1 direct messaging  
✅ Real-time updates (Firestore)  
✅ Message status tracking  
✅ Auto-delete after 24 hours  
✅ Terminal-style UI (black + lavender/purple)  
✅ Commands (/clear, /help)  
✅ Browser notifications  
✅ Invite codes to connect users  
✅ Auto-generated usernames  
✅ Security best practices  

## 📚 Documentation

- **00_START_HERE.md** - Read this first!
- **README_MESSAGING_APP.md** - Complete implementation guide
- **VITE_PROJECT_FILES.md** - All source code files
- **MESSAGING_APP_GUIDE.md** - Feature documentation
- **ADVANCED_FEATURES.md** - Customization examples
- **SETUP_GUIDE.md** - Quick reference

## 🔧 Firebase Setup

1. Create Firebase project at [firebase.google.com](https://firebase.google.com)
2. Enable Google Authentication
3. Create Firestore Database (test mode for development)
4. Copy credentials to `.env.local` (Vite) or `firebaseConfig` in HTML
5. Apply provided security rules to Firestore

## 🎨 Design

- **Colors**: Black background, Lavender (#9d7ceb) primary, Purple (#7c5aa6) accent
- **Font**: Courier New, monospace (terminal-style)
- **UX**: Keyboard-first, no animations, minimal layout
- **Responsive**: Works on desktop and mobile

## 📱 Deployment

Deploy to:
- Vercel
- Netlify
- GitHub Pages
- Firebase Hosting
- Any static web host

## 🔐 Security

✅ Google OAuth for authentication  
✅ Firestore security rules included  
✅ User emails never exposed  
✅ Server-side timestamps  
✅ 24-hour auto-expiration  
✅ HTTPS recommended  

## 📖 Learn More

See the included documentation files for:
- Step-by-step setup
- Complete architecture explanation
- All source code (20+ files)
- Customization examples (15+ options)
- Troubleshooting guide
- Best practices

## 🚀 Get Started

**Next step**: Read `00_START_HERE.md` for complete guidance!

## 📄 License

MIT License - Use freely!

---

**Status**: ✅ Production Ready  
**Version**: 1.0.0  
**Last Updated**: March 19, 2026
