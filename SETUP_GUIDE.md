# Setup Guide: Calendar Integration & AI Memory

## Prerequisites
1. Google Cloud Console account
2. Anthropic API key

## Step 1: Google Calendar API Setup

### 1.1 Create Google Cloud Project
1. Go to https://console.cloud.google.com/
2. Create new project: "Health Coach App"
3. Enable Google Calendar API:
   - Go to "APIs & Services" > "Library"
   - Search "Google Calendar API"
   - Click "Enable"

### 1.2 Create OAuth Credentials
1. Go to "APIs & Services" > "Credentials"
2. Click "Create Credentials" > "OAuth client ID"
3. Configure OAuth consent screen:
   - User Type: External
   - App name: "Health Coach"
   - Scopes: Add `../auth/calendar.readonly` and `../auth/calendar.events`
4. Create OAuth Client ID:
   - Application type: Web application
   - Authorized JavaScript origins: 
     - `http://localhost:5173` (for dev)
     - Your production URL (e.g., `https://yourapp.netlify.app`)
   - Authorized redirect URIs: Same as above
5. Copy your Client ID and API Key

### 1.3 Add Credentials to Your App
Create `.env.local`:
```
VITE_GOOGLE_CLIENT_ID=your_client_id_here
VITE_GOOGLE_API_KEY=your_api_key_here
VITE_ANTHROPIC_API_KEY=your_anthropic_key_here
```

## Step 2: Install Dependencies

```bash
npm install gapi-script
# or
yarn add gapi-script
```

## Step 3: Update Your Code

### 3.1 Replace calendar-integration.ts
Copy the `calendar-integration.ts` file I created and update:
```typescript
const CLIENT_ID = import.meta.env.VITE_GOOGLE_CLIENT_ID;
const API_KEY = import.meta.env.VITE_GOOGLE_API_KEY;
```

### 3.2 Replace useAppState hook
Use the updated `useAppState-updated.tsx` I provided

### 3.3 Update AuthPage component
Use the updated `AuthPage-updated.tsx` I provided

### 3.4 Update Index.tsx to pass new props
```typescript
case "auth":
  return (
    <AuthPage
      onComplete={() => generateRecommendations()}
      onSkip={() => generateRecommendations()}
      connectCalendar={connectCalendar}  // Add this
      isCalendarConnected={isCalendarConnected}  // Add this
    />
  );
```

## Step 4: Anthropic API Setup

### 4.1 Get API Key
1. Go to https://console.anthropic.com/
2. Create API key
3. Add to `.env.local` (already done in Step 1.3)

### 4.2 Important: API Key Security
⚠️ **NEVER expose your Anthropic API key in frontend code!**

For production, you need a backend proxy:

**Option A: Create simple backend proxy**
```javascript
// backend/api/chat.js (Next.js API route example)
export default async function handler(req, res) {
  const response = await fetch('https://api.anthropic.com/v1/messages', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'x-api-key': process.env.ANTHROPIC_API_KEY, // Server-side only
      'anthropic-version': '2023-06-01'
    },
    body: JSON.stringify(req.body)
  });
  
  const data = await response.json();
  res.json(data);
}
```

Then update `ai-coach-memory.ts` to call `/api/chat` instead of Anthropic directly.

**Option B: Use Anthropic's client SDK (if available for your platform)**

## Step 5: Test It

### 5.1 Test Calendar Integration
1. Run your app: `npm run dev`
2. Complete onboarding
3. Click "Connect Google Calendar" on auth page
4. Grant permissions
5. Check console for free time blocks

### 5.2 Test AI Memory
1. Open FloatingChat
2. Say: "I don't like morning workouts"
3. Say: "Can you move them to evening?"
4. AI should reference your previous message

## Features You Now Have

✅ **Calendar Integration:**
- Analyzes user's Google Calendar for free time
- Schedules workouts in available slots
- Can add workouts to calendar with reminders
- Avoids conflicts with existing events

✅ **AI Memory:**
- Remembers entire conversation history
- References user's onboarding answers
- Tracks completed/skipped workouts
- Gives context-aware responses
- Updates recommendations based on chat feedback

## Monetization Ready

With these features, you can now charge for:
- **Free tier:** Basic plan, limited AI chats
- **Premium ($9.99/mo):** 
  - Unlimited AI coaching
  - Calendar sync
  - Advanced insights
  - Priority support

## Next Steps

1. Add user authentication (Supabase/Firebase)
2. Store conversation history in database
3. Add proper error handling
4. Create backend API proxy for Anthropic
5. Add analytics (PostHog/Mixpanel)
6. Implement subscription payments (Stripe)

## Troubleshooting

**Calendar not connecting:**
- Check OAuth credentials are correct
- Verify authorized origins match your URL
- Check browser console for errors

**AI not responding:**
- Verify Anthropic API key is valid
- Check you're not hitting rate limits
- Look for CORS errors (means you need backend proxy)

**Memory not working:**
- Ensure AICoach is initialized with user context
- Check conversation history is being passed to API
- Verify system prompt includes user data

Need help? Check the issues or contact support.
