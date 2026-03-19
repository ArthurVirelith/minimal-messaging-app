# Quick Setup Reference

## Firebase Project Setup (10 minutes)

### 1. Create Firebase Project
1. Go to https://console.firebase.google.com
2. Click "Create Project"
3. Name it (e.g., "minimal-messaging")
4. Click "Create"

### 2. Enable Google Authentication
1. Go to **Authentication → Sign-in method**
2. Click **Google** provider
3. Enable it
4. Add your domain (localhost:5173 for dev, your domain for production)
5. Save

### 3. Create Firestore Database
1. Go to **Firestore Database**
2. Click "Create database"
3. Select **Test mode** (for development)
4. Choose your region
5. Create

### 4. Get Your Credentials
1. Go to **Project Settings** (gear icon)
2. Click **Your apps**
3. Create Web app (if not exists)
4. Copy the config object
5. Save for later

### 5. Apply Security Rules
1. Go to **Firestore → Rules**
2. Paste the security rules from README.md
3. Deploy

## Project Setup

### Option A: HTML File
```
1. Download messaging-app-complete.html
2. Open in text editor
3. Find firebaseConfig (line ~50)
4. Update with your Firebase credentials
5. Open in browser
```

### Option B: Vite Project
```
1. mkdir messaging-app && cd messaging-app
2. npm init -y
3. npm install react react-dom firebase
4. npm install -D vite @vitejs/plugin-react tailwindcss postcss autoprefixer
5. Create .env.local with Firebase config
6. Copy source files from VITE_PROJECT_FILES.md
7. npm run dev
```

## Environment Variables (.env.local)

```
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_messaging_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

## Firestore Security Rules

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

## Deployment

### Vercel
```bash
npm run build
vercel
```

### Netlify
```bash
npm run build
# Or drag & drop dist/ folder
```

### GitHub Pages
```bash
npm run build
# Upload dist/ as GitHub Pages
```

## Troubleshooting

**Firebase not working?**
- Check .env.local has correct values
- Verify API key has permissions
- Check internet connection

**Google login fails?**
- Add localhost:5173 to OAuth redirect URIs
- Clear browser cache
- Check Google auth is enabled

**Messages not updating?**
- Check Firestore rules
- Verify real-time listeners work
- Check browser console for errors

**24-hour expiry not working?**
- Verify createdAt timestamps are set
- Check message filtering in MessageList
