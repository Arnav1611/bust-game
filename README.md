# Burst Card Game – Friends Edition

A real-time multiplayer card prediction game built with React, Firebase, and Tailwind CSS.

## Features

- Real-time multiplayer gameplay (5-20 players)
- Admin-controlled game flow
- Live score tracking and leaderboard
- Analytics dashboard with charts
- Session persistence (auto-rejoin on refresh)
- Dark mode UI with glass morphism
- Smooth animations with Framer Motion
- Confetti celebration for winners

## Tech Stack

- React 18 (Functional Components + Hooks)
- Tailwind CSS
- Firebase (Firestore Realtime DB)
- Framer Motion
- Recharts
- React Hot Toast
- Canvas Confetti
- Vite

## Setup

1. Install dependencies:
```bash
npm install
```

2. Create Firebase project:
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project
   - Enable Firestore Database
   - Get your config credentials

3. Create `.env` file:
```bash
cp .env.example .env
```

4. Add your Firebase credentials to `.env`:
```
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

5. Run development server:
```bash
npm run dev
```

6. Build for production:
```bash
npm run build
```

## Game Rules

- Admin sets starting number of cards (e.g., 10)
- Total rounds = starting cards
- Cards decrease each round (10 → 9 → 8 ... → 1)
- Each round:
  - Player enters predicted sets
  - Player enters actual sets after playing
  - If predicted == actual: score = (11 × sets) + 10
  - Else: score = 0
- Score is cumulative across all rounds

## Deployment

This app is ready to deploy on Vercel:

1. Push code to GitHub
2. Import project in Vercel
3. Add environment variables
4. Deploy

## Firestore Structure

```
games/{gameCode}
  - startingCards
  - totalRounds
  - currentRound
  - status (lobby/active/finished)
  - adminId
  
  players/{playerId}
    - name
    - totalScore
    - correctPredictions
    - roundHistory[]
```

## License

MIT
