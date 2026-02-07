# Health & Wellness AI Coach 🏃‍♂️💪

An AI-powered fitness app that creates personalized workout plans, integrates with your Google Calendar, and remembers your preferences through intelligent conversation.

## 🚀 Live Demo

**[Try it now →](https://yourusername.github.io/health-wellness-app/)**

## ✨ Features

- 🎙️ **Voice-Powered Onboarding** - Tell us your goals naturally
- 🤖 **AI Coach with Memory** - Remembers your preferences, barriers, and progress
- 📅 **Calendar Integration** - Syncs with Google Calendar to find optimal workout times
- 📊 **Progress Tracking** - Visual dashboards showing completion rates and streaks
- 💬 **Smart Chat** - Adjust your plan by talking to your AI coach
- 📱 **Mobile-First Design** - Works perfectly on iPhone and Android

## 🎯 How It Works

1. **Complete Voice Onboarding** - Answer 5 questions about your fitness goals
2. **Get Personalized Plan** - AI generates a custom workout schedule
3. **Connect Calendar** (optional) - Auto-schedule around your existing commitments
4. **Track Progress** - Check off completed workouts and see your stats
5. **Chat with AI** - Adjust your plan anytime by chatting with your coach

## 🛠️ Quick Start

### Option 1: Use It Right Now (No Setup)

Just open `index.html` in your browser. Works immediately with mock data.

### Option 2: Enable Full Features (5 minutes)

1. **Get Google Calendar API credentials:**
   - Go to [Google Cloud Console](https://console.cloud.google.com/)
   - Create a project and enable Google Calendar API
   - Create OAuth credentials
   - Copy your Client ID and API Key

2. **Add your credentials:**
   - Open `index.html`
   - Edit lines 18-22:
   ```javascript
   const CONFIG = {
     GOOGLE_CLIENT_ID: 'your-client-id',
     GOOGLE_API_KEY: 'your-api-key',
     ANTHROPIC_API_KEY: 'your-anthropic-key', // Optional for real AI
   };
   ```

3. **Deploy to GitHub Pages:**
   ```bash
   # Fork this repo, then:
   git clone https://github.com/yourusername/health-wellness-app
   cd health-wellness-app
   # Edit index.html with your keys
   git add .
   git commit -m "Add API credentials"
   git push
   ```

4. **Enable GitHub Pages:**
   - Go to repo Settings → Pages
   - Source: Deploy from `main` branch
   - Your app will be live at `https://yourusername.github.io/health-wellness-app/`

## 📖 Full Documentation

See [SETUP_GUIDE.md](./SETUP_GUIDE.md) for detailed setup instructions.

## 🎨 Tech Stack

- React 18 (via CDN)
- Tailwind CSS
- Google Calendar API
- Web Speech API
- Anthropic Claude API (optional)

## 🔒 Privacy

- All data stored locally in your browser
- Calendar permissions read-only by default
- No data sent to third-party servers (except Google/Anthropic APIs if configured)

## 💰 Monetization (Future)

This is designed to support:
- **Free Tier**: Basic plan, limited AI chats
- **Premium ($9.99/mo)**: Unlimited AI coaching, calendar sync, advanced analytics

## 🤝 Contributing

Pull requests welcome! Feel free to:
- Add new workout types
- Improve the AI coaching logic
- Add more calendar integrations (Apple Calendar, Outlook)
- Enhance the UI/UX

## 📝 License

MIT License - use it however you want!

## 🙏 Credits

Built with ❤️ by [Your Name]

Powered by:
- [Anthropic Claude](https://www.anthropic.com/)
- [Google Calendar API](https://developers.google.com/calendar)

---

**Questions?** Open an issue or reach out at your@email.com

**Star ⭐ this repo if you found it helpful!**
