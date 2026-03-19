# Minimal Messaging App - Feature & Architecture Guide

## Complete Feature Overview

### Authentication System
- Google OAuth via Firebase Auth
- Secure login flow
- Auto-generated unique usernames on first login
- User profile stored in Firestore
- No email exposure to other users

### Messaging System
- 1-to-1 direct messaging only
- Real-time message delivery using Firestore listeners
- Message status tracking: "sent" → "delivered"
- Plain text messages only (no images, emojis, media)
- Automatic deletion after 24 hours
- Server-side timestamps for accuracy

### User System
- Auto-generated usernames (format: animal_#### e.g., "ghost_1234")
- Search users by username
- 6-character invite codes (format: ABC123)
- Join chat via invite code
- User profiles contain: uid, username, createdAt, inviteCode

### UI/UX
- Terminal-style design (black background)
- Lavender (#9d7ceb) and purple (#7c5aa6) accent colors
- Monospace font (Courier New)
- Keyboard-first navigation (Enter to send)
- No animations or transitions (minimal, fast)
- Responsive layout

### Commands
- `/clear` - Clears the current chat view
- `/help` - Shows available commands

### Additional Features
- Browser notifications for new messages
- Message search (client-side)
- Responsive design for mobile and desktop

## Architecture

### Component Structure
```
App (Main container)
├── Login (Google auth)
├── Chat (Main interface)
│   ├── UserSearch (Find users)
│   ├── MessageList (Display messages)
│   ├── InputBox (Send messages)
│   └── Help modal
```

### Data Flow
```
React Components
    ↓
Custom Hooks (useAuth, useChat, useMessages)
    ↓
Firebase Services (authService, chatService, messageService)
    ↓
Firestore Database
    ↓
Real-time Listeners
    ↓
Update Component State
    ↓
Render UI
```

## Firestore Data Structure

### Users Collection
```
/users/{uid}
  ├── uid: string (Firebase auth UID)
  ├── username: string (auto-generated)
  ├── createdAt: timestamp
  └── inviteCode: string (6 chars, uppercase)
```

### Chats Collection
```
/chats/{chatId}
  ├── participants: array [uid1, uid2]
  ├── createdAt: timestamp
  └── /messages/{messageId}
      ├── senderId: string
      ├── text: string (plain text)
      ├── status: string ("sent" | "delivered")
      └── createdAt: timestamp
```

## Security Model

### Firestore Rules
- Users can only read/write their own profile
- Any authenticated user can read/write messages
- Server-side validation of timestamps

### Privacy
- User emails never exposed
- Only usernames visible to other users
- No profile pictures or personal info

## Message Flow

1. User logs in with Google
2. Auto-generated username created
3. User searches for another user by username or invite code
4. Select user to open 1-to-1 chat
5. Type and send message
6. Message appears with status "sent"
7. Status changes to "delivered" after confirmation
8. Other user receives real-time update
9. After 24 hours, message auto-deletes

## Performance Optimizations

- Real-time listeners only for active chat
- Message cleanup (auto-delete)
- Minimal DOM updates with React
- CSS Grid layout
- No heavy asset loading

## Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Android)

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Enter | Send message |
| / | Enter command mode |
| Tab | Navigate between fields |

## File Structure

```
src/
├── components/
│   ├── Login.jsx
│   ├── Chat.jsx
│   ├── MessageList.jsx
│   ├── InputBox.jsx
│   └── UserSearch.jsx
├── hooks/
│   ├── useAuth.js
│   ├── useChat.js
│   └── useMessages.js
├── services/
│   ├── firebase.js
│   ├── authService.js
│   ├── userService.js
│   ├── chatService.js
│   └── messageService.js
├── utils/
│   ├── generateUsername.js
│   ├── generateInviteCode.js
│   ├── messageExpiry.js
│   └── messageCommands.js
├── App.jsx
├── App.css
└── main.jsx
```
