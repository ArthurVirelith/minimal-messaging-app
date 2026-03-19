# 🔐 Minimal Messaging App

A terminal-style, 1-to-1 messaging application built with React + Vite, Firebase, and Tailwind CSS.

## 🚀 Deploy in 5 Minutes

### Quick Firebase Hosting Deployment

```bash
# 1. Install Firebase CLI
npm install -g firebase-tools

# 2. Login
firebase login

# 3. Create & Initialize
mkdir messaging-app-hosting && cd messaging-app-hosting
firebase init hosting

# 4. Copy app
mkdir -p public
cp messaging-app-complete.html public/index.html

# 5. UPDATE FIREBASE CONFIG IN public/index.html ⚠️
# Go to Firebase Console → Project Settings → Your apps
# Copy firebaseConfig and replace placeholder in HTML

# 6. Deploy!
firebase deploy --only hosting

# Your app is now live at: https://your-project-id.web.app
```

**See [FIREBASE_HOSTING.md](./FIREBASE_HOSTING.md) for detailed instructions.**

---

## 📋 Other Deployment Options

- **Vercel**: `vercel deploy` (1 min setup)
- **Netlify**: Drag & drop dist/ folder (instant)
- **GitHub Pages**: Push to GitHub (2-5 min)
- **Any static host**: Upload files

---

## ✨ Features

✅ **Google Authentication** - Firebase Auth  
✅ **Real-time Messaging** - 1-to-1 direct chat  
✅ **Message Status** - Sent → Delivered tracking  
✅ **Auto-Delete** - Messages expire after 24 hours  
✅ **Terminal UI** - Black background, lavender accents  
✅ **Invite Codes** - 6-character codes to connect  
✅ **Username Search** - Find users by username  
✅ **Commands** - /clear, /help  
✅ **Notifications** - Browser alerts  
✅ **Secure** - Firestore rules, email privacy  

## 📄 Implementation Options

### Option 1: Single HTML File (⚡ Easiest)
- **File**: `messaging-app-complete.html`
- **Size**: 26 KB
- **Setup**: 5 minutes
- **Deploy**: Instant to any host
- **Best for**: Quick prototyping, learning

### Option 2: Vite Project (💻 Professional)
- **Source**: Code in `VITE_PROJECT_FILES.md`
- **Files**: 20+ modular components
- **Setup**: 20 minutes
- **Deploy**: Optimized build
- **Best for**: Production, teams

---

## 📚 Documentation

| Document | Purpose |
|----------|--------|
| **00_START_HERE.md** | Navigation & quick start |
| **FIREBASE_HOSTING.md** | Firebase deployment guide |
| **DEPLOY_GUIDE.md** | Quick command reference |
| **MESSAGING_APP_GUIDE.md** | Feature documentation |
| **VITE_PROJECT_FILES.md** | Full source code structure |
| **ADVANCED_FEATURES.md** | Customization examples |

---

## 🔧 Firebase Setup

1. Create Firebase project at [firebase.google.com](https://firebase.google.com)
2. Enable Google Authentication
3. Create Firestore Database (test mode for development)
4. Copy your Firebase config
5. Update `firebaseConfig` in HTML or `.env.local` (Vite)
6. Apply Firestore security rules (provided in docs)

### Firestore Security Rules

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth.uid == userId;
    }
    match /chats/{chatId}/messages/{messageId} {
      allow read, write: if request.auth != null;
    }
  }
}
```

---

## 🎨 Design

- **Colors**: Black background, Lavender (#9d7ceb) primary, Purple (#7c5aa6) accent
- **Font**: Courier New (monospace, terminal-style)
- **UX**: Keyboard-first, no animations, minimal layout
- **Responsive**: Works on desktop and mobile

---

## ⌨️ Keyboard Shortcuts

| Key | Action |
|-----|--------|
| **Enter** | Send message |
| **/** | Command mode |
| **Tab** | Navigate fields |

---

## 💬 Commands

| Command | Effect |
|---------|-----------|
| **/clear** | Clear chat view |
| **/help** | Show commands |

---

## 🚀 Deployment Platforms

| Platform | Cost | Setup | Deploy | Recommendation |
|----------|------|-------|--------|----------------|
| **Firebase** | Free | 5 min | 1 min | ⭐ Recommended |
| Vercel | Free | 5 min | 1 min | ⭐ Great |
| Netlify | Free | 5 min | Auto | ⭐ Great |
| GitHub Pages | Free | 10 min | 2 min | Good |

---

## 🔐 Security

✅ **Firestore Rules** - Access control enforced  
✅ **Email Privacy** - Never exposed to other users  
✅ **Server Timestamps** - Accurate, trusted  
✅ **Auto-Expiration** - Messages delete after 24h  
✅ **HTTPS** - Automatic (Firebase)  
✅ **Google OAuth** - Secure authentication  

---

## 📊 Project Statistics

- **Components**: 5
- **Services**: 5
- **Custom Hooks**: 3
- **Utilities**: 4
- **Documentation**: 130+ KB
- **Source Files**: 20+
- **Setup Time**: 5-20 min
- **Deploy Time**: 1-2 min

---

## 🎓 Tech Stack

- **Frontend**: React 18 + Vite
- **Styling**: Tailwind CSS 3
- **Database**: Firebase Firestore
- **Auth**: Firebase Authentication
- **Real-time**: Firestore Listeners
- **Hosting**: Firebase Hosting (recommended)

---

## 📝 Getting Started

1. **Read**: `00_START_HERE.md` (5 min)
2. **Choose**: HTML file or Vite project
3. **Setup**: Firebase credentials (10 min)
4. **Deploy**: Firebase Hosting (5 min)
5. **Share**: Your live URL

---

## 🌐 Live Demo

Deploy your own instance:

1. Follow [FIREBASE_HOSTING.md](./FIREBASE_HOSTING.md)
2. Get your live URL: `https://your-project-id.web.app`
3. Share and enjoy!

---

## 📞 Support & Resources

- **Setup Help**: See `00_START_HERE.md`
- **Deployment Help**: See `FIREBASE_HOSTING.md`
- **Code Questions**: See `MESSAGING_APP_GUIDE.md`
- **Customization**: See `ADVANCED_FEATURES.md`

---

## 📄 License

MIT License - Use freely!

---

**Status**: ✅ Production Ready  
**Version**: 1.0.0  
**Last Updated**: March 19, 2026

🚀 **Ready to deploy?** See [FIREBASE_HOSTING.md](./FIREBASE_HOSTING.md)!
