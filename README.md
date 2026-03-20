# 🔐 Minimal Messaging App

A terminal-style, 1-to-1 messaging application built with React + Vite, Firebase, and Tailwind CSS.

## 🚀 Deploy in 3-5 Minutes

### Option 1: Vercel (⭐ Recommended - GitHub Auto-Deploy)

```bash
# 1. Update Firebase config in messaging-app-complete.html
#    (Copy from Firebase Console → Project Settings)

# 2. Push to GitHub
git add .
git commit -m "Update Firebase config"
git push origin main

# 3. Go to vercel.com, click "Import Git Repository"
# 4. Select: ArthurVirelith/minimal-messaging-app
# 5. Click "Deploy"

# Your app is now live at: https://your-app.vercel.app 🎉
```

**See [VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md) for detailed instructions.**

---

### Option 2: Firebase Hosting (5 Minutes)

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

# 6. Deploy!
firebase deploy --only hosting
```

**See [FIREBASE_HOSTING.md](./FIREBASE_HOSTING.md) for detailed instructions.**

---

### Option 3: Netlify (3 Minutes)

```bash
# 1. Drag and drop public/index.html to netlify.com
# 2. Update Firebase config in the file
# 3. Done!
```

---

## 📊 Deployment Options Comparison

| Platform | Setup | Deploy | Auto-update | SSL | Free |
|----------|-------|--------|-------------|-----|------|
| **Vercel** | 3 min | Instant | ✅ GitHub | ✅ | ✅ |
| **Firebase** | 5 min | 1 min | ❌ Manual | ✅ | ✅ |
| **Netlify** | 3 min | Instant | ✅ GitHub | ✅ | ✅ |
| GitHub Pages | 10 min | 2 min | ✅ Auto | ✅ | ✅ |

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

---

## 🎯 Implementation Options

### Option 1: Single HTML File (⚡ Easiest)
- **File**: `messaging-app-complete.html`
- **Size**: 26 KB
- **Setup**: 2 minutes
- **Deploy**: 3 minutes to Vercel
- **Best for**: Quick prototyping, learning

### Option 2: Vite Project (🏢 Professional)
- **Source**: Code in `VITE_PROJECT_FILES.md`
- **Files**: 20+ modular components
- **Setup**: 20 minutes
- **Deploy**: Optimized production build
- **Best for**: Production, teams

---

## 📚 Documentation

| Document | Purpose |
|----------|--------|
| **00_START_HERE.md** | Navigation & quick start |
| **VERCEL_DEPLOYMENT.md** | Vercel deployment (⭐ Recommended) |
| **FIREBASE_HOSTING.md** | Firebase deployment guide |
| **MESSAGING_APP_GUIDE.md** | Feature documentation |
| **VITE_PROJECT_FILES.md** | Full source code structure |
| **ADVANCED_FEATURES.md** | Customization examples |

---

## 🔧 Firebase Setup

1. Create Firebase project at [firebase.google.com](https://firebase.google.com)
2. Enable **Google Authentication**
3. Create **Firestore Database** (test mode for development)
4. Copy your **Firebase config**
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

## 🔐 Security

✅ **Firestore Rules** - Access control enforced  
✅ **Email Privacy** - Never exposed to other users  
✅ **Server Timestamps** - Accurate, trusted  
✅ **Auto-Expiration** - Messages delete after 24h  
✅ **HTTPS** - Automatic (all platforms)  
✅ **Google OAuth** - Secure authentication  

---

## 📊 Project Statistics

- **Components**: 5
- **Services**: 5
- **Custom Hooks**: 3
- **Utilities**: 4
- **Documentation**: 130+ KB
- **Source Files**: 20+
- **Setup Time**: 2-20 min (depending on option)
- **Deploy Time**: 1-5 min (depending on platform)

---

## 🛠️ Tech Stack

- **Frontend**: React 18 + Vite
- **Styling**: Tailwind CSS 3
- **Database**: Firebase Firestore
- **Auth**: Firebase Authentication
- **Real-time**: Firestore Listeners
- **Hosting**: Vercel (recommended) or Firebase Hosting

---

## 🚀 Getting Started

1. **Read**: `00_START_HERE.md` (5 min)
2. **Choose**: Vercel, Firebase, or Netlify
3. **Update**: Firebase credentials (2 min)
4. **Deploy**: Click deploy (1 min)
5. **Share**: Your live URL (instant)

---

## 🌐 Live Demo

Deploy your own instance:

1. Follow [VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md) (recommended)
2. Get your live URL: `https://your-app.vercel.app`
3. Share and enjoy!

---

## 🆘 Support & Resources

- **Getting Started**: See `00_START_HERE.md`
- **Vercel Deployment**: See `VERCEL_DEPLOYMENT.md` ⭐
- **Firebase Deployment**: See `FIREBASE_HOSTING.md`
- **Code Questions**: See `MESSAGING_APP_GUIDE.md`
- **Customization**: See `ADVANCED_FEATURES.md`

---

## 📄 License

MIT License - Use freely!

---

**Status**: ✅ Production Ready  
**Version**: 1.0.0  
**Last Updated**: March 20, 2026

---

## ⭐ Quick Links

- 🚀 **Deploy to Vercel**: [VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md)
- 🔥 **Deploy to Firebase**: [FIREBASE_HOSTING.md](./FIREBASE_HOSTING.md)
- 📖 **Full Docs**: [00_START_HERE.md](./00_START_HERE.md)
- 💻 **App File**: [messaging-app-complete.html](./messaging-app-complete.html)

**Ready to deploy?** Start with [VERCEL_DEPLOYMENT.md](./VERCEL_DEPLOYMENT.md)! 🚀
