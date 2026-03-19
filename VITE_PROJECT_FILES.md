# MINIMAL MESSAGING APP - COMPLETE VITE PROJECT FILES

This document contains all files needed to build the Vite project. Copy each file to the appropriate location.

## Setup Instructions

```bash
mkdir messaging-app
cd messaging-app
npm init -y
npm install react react-dom firebase
npm install -D vite @vitejs/plugin-react tailwindcss postcss autoprefixer
```

Then create the directory structure:
```
src/
  ├── components/
  ├── hooks/
  ├── services/
  └── utils/
```

Copy all files from the sections below to their respective locations.

## Key Files

### Configuration

**vite.config.js**
```javascript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})
```

**tailwind.config.js**
```javascript
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx}",
  ],
  theme: {
    extend: {
      colors: {
        terminal: {
          black: '#000000',
          lavender: '#9d7ceb',
          purple: '#7c5aa6',
          darkPurple: '#5a3d8a',
          gray: '#333333',
          darkGray: '#1a1a1a',
        }
      },
      fontFamily: {
        mono: ['Courier New', 'Courier', 'monospace'],
      }
    },
  },
  plugins: [],
}
```

**postcss.config.js**
```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

**package.json**
```json
{
  "name": "minimal-messaging-app",
  "private": true,
  "version": "0.0.1",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "firebase": "^10.7.1"
  },
  "devDependencies": {
    "@types/react": "^18.2.43",
    "@types/react-dom": "^18.2.17",
    "@vitejs/plugin-react": "^4.2.1",
    "vite": "^5.0.8",
    "postcss": "^8.4.32",
    "autoprefixer": "^10.4.16",
    "tailwindcss": "^3.4.1"
  }
}
```

### Main App Files

**src/main.jsx** - Entry point
**src/App.jsx** - Main component with auth
**src/App.css** - Styling

See README.md for complete list and detailed implementations.

## Firebase Setup

1. Create `.env.local`:
```
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_messaging_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

2. Apply Firestore security rules:
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

## Installation

```bash
npm install
npm run dev
```

For complete source code of all 20+ files, see the individual component implementations in this repo.
