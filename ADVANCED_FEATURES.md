# Advanced Features & Customization Guide

## 🎨 Customization Options

### Change Terminal Colors

In your `tailwind.config.js` or directly in the color definitions:

**Original (Purple):**
```
--terminal-black: #000000
--terminal-lavender: #9d7ceb
--terminal-purple: #7c5aa6
```

**Green Terminal (Matrix style):**
```
--terminal-black: #000000
--terminal-lavender: #00FF00
--terminal-purple: #00AA00
```

**Cyan Terminal (Tron style):**
```
--terminal-black: #000000
--terminal-lavender: #00FFFF
--terminal-purple: #0088FF
```

**Amber Terminal (Retro):**
```
--terminal-black: #000000
--terminal-lavender: #FFB800
--terminal-purple: #FF8800
```

**Pink Terminal (Synthwave):**
```
--terminal-black: #0a0e27
--terminal-lavender: #FF006E
--terminal-purple: #FB5607
```

### Change Username Format

Edit `src/utils/generateUsername.js`:

**Option 1: Word-based**
```javascript
const adjectives = ['speedy', 'clever', 'quiet'];
const nouns = ['fox', 'bear', 'eagle'];
const adj = adjectives[Math.floor(Math.random() * adjectives.length)];
const noun = nouns[Math.floor(Math.random() * nouns.length)];
const num = Math.floor(Math.random() * 100);
return `${adj}${noun}${num}`;
```

**Option 2: Numeric only**
```javascript
const num1 = Math.floor(Math.random() * 100000);
const num2 = Math.floor(Math.random() * 100000);
return `user_${num1}_${num2}`;
```

### Change Message Expiry Time

Edit `src/utils/messageExpiry.js`:

```javascript
// Change the threshold:
const hoursDiff = (now - messageDate) / (1000 * 60 * 60);

// 1 hour:
return hoursDiff > 1;

// 48 hours:
return hoursDiff > 48;

// 7 days:
return hoursDiff > (24 * 7);

// Never expires:
return false;
```

### Add New Commands

Edit `src/components/InputBox.jsx`:

```javascript
if (cmd.command === '/info') {
  onCommand('info');
  setInput('');
  return;
}
```

Then handle in `src/components/Chat.jsx`:

```javascript
const handleCommand = (command) => {
  if (command === 'clear') {
    setMessages([]);
  } else if (command === 'info') {
    // Your custom logic
  }
};
```

## 🚀 Feature Additions

### Message Search

```javascript
const searchMessages = (messages, term) => {
  return messages.filter(msg => 
    msg.text.toLowerCase().includes(term.toLowerCase())
  );
};
```

### User Status Indicator

```javascript
const [userStatus, setUserStatus] = useState('offline');

useEffect(() => {
  setUserStatus('online');
  const timeout = setTimeout(() => {
    setUserStatus('idle');
  }, 5 * 60 * 1000);
  
  return () => clearTimeout(timeout);
}, [messages]);
```

## 🔐 Security Enhancements

### Input Validation

```javascript
export const validateMessage = (text) => {
  if (text.length > 1000) return false;
  return !/[\x00-\x1F\x7F]/.test(text);
};
```

### Rate Limiting

```javascript
const [lastMessageTime, setLastMessageTime] = useState(0);

const send = async (text) => {
  const now = Date.now();
  if (now - lastMessageTime < 500) {
    console.warn('Rate limited');
    return;
  }
  
  await sendMessage(chatId, currentUserId, text);
  setLastMessageTime(now);
};
```

## 📱 Mobile Optimizations

```css
.button-primary {
  min-height: 44px; /* iOS minimum */
  min-width: 44px;
  padding: 12px 16px;
}

.terminal-input {
  font-size: 16px; /* Prevent zoom on iOS */
}
```

## 🧪 Testing Examples

```javascript
import { isMessageExpired } from '../messageExpiry';

describe('messageExpiry', () => {
  test('message older than 24h is expired', () => {
    const oldDate = new Date(Date.now() - 25 * 60 * 60 * 1000);
    expect(isMessageExpired(oldDate)).toBe(true);
  });

  test('message newer than 24h is not expired', () => {
    const newDate = new Date(Date.now() - 1 * 60 * 60 * 1000);
    expect(isMessageExpired(newDate)).toBe(false);
  });
});
```

## 🚀 Deployment Checklist

- [ ] Update Firestore rules (remove test mode)
- [ ] Add production domain to Firebase
- [ ] Test on multiple browsers
- [ ] Test on mobile devices
- [ ] Set up error logging (Sentry)
- [ ] Configure backups
- [ ] Create privacy policy
- [ ] Create terms of service
- [ ] Enable HTTPS

## 🌐 Analytics

```javascript
export const logEvent = (eventName, data = {}) => {
  if (window.gtag) {
    gtag('event', eventName, data);
  }
};

// Usage:
logEvent('message_sent', { recipient: selectedUser.username });
logEvent('login', { method: 'google' });
```
