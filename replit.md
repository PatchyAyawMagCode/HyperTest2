# HyperDiaSense - AI Nutritional Label Analysis

## Overview
HyperDiaSense is an AI-driven nutritional label analysis system designed specifically for people managing hypertension and diabetes. The app helps users make informed food choices by analyzing scanned nutrition labels or manually entered nutrition data.

## Current State
✅ Successfully imported and configured to run on Replit
✅ Firebase authentication working
✅ Gradio AI integration configured
✅ Development server running on port 5000
✅ Deployment configuration set up

## Project Architecture

### Tech Stack
- **Frontend**: React 18 + Vite + TypeScript
- **Backend**: Express.js (serves Vite app in dev mode)
- **Database**: Firebase Firestore (user profiles, scan history)
- **Authentication**: Firebase Auth
- **AI Service**: Gradio Space (Hugging Face)
- **UI Components**: Radix UI + Tailwind CSS
- **Forms**: React Hook Form + Zod validation

### Project Structure
```
├── client/               # React frontend application
│   ├── src/
│   │   ├── components/  # UI components (auth, health, scanner, layout)
│   │   ├── contexts/    # React contexts (AuthContext)
│   │   ├── hooks/       # Custom hooks
│   │   ├── lib/         # Utility functions and integrations
│   │   │   ├── firebase.ts        # Firebase config
│   │   │   ├── firestore.ts       # Firestore database operations
│   │   │   ├── analyzeFood.ts     # Manual nutrition analysis
│   │   │   ├── analyzeImage.ts    # Image scanning & OCR
│   │   │   └── fallbackAnalysis.ts # Heuristic analysis fallback
│   │   ├── pages/       # Page components (Home, Scanner, Profile, History)
│   │   └── App.tsx      # Main app component
│   └── index.html
├── server/              # Express backend
│   ├── index.ts         # Main server file
│   └── vite.ts          # Vite middleware configuration
├── shared/              # Shared schemas and types
│   └── schema.ts        # Zod schemas for validation
└── package.json
```

### Key Features
1. **Image Scanning**: Upload nutrition label photos for AI analysis
2. **Manual Entry**: Enter nutrition facts manually via form
3. **Health Assessment**: AI evaluates if food is safe or risky based on user's health profile
4. **User Profiles**: Store health conditions, medications, demographics
5. **Scan History**: Track past nutrition analyses
6. **Personalized Tips**: Get health recommendations based on profile

## Configuration

### Environment Variables (Already Set)
- `VITE_FIREBASE_API_KEY` - Firebase API key
- `VITE_FIREBASE_AUTH_DOMAIN` - Firebase auth domain
- `VITE_FIREBASE_PROJECT_ID` - Firebase project ID
- `VITE_FIREBASE_STORAGE_BUCKET` - Firebase storage bucket
- `VITE_FIREBASE_MESSAGING_SENDER_ID` - Firebase messaging sender ID
- `VITE_FIREBASE_APP_ID` - Firebase app ID
- `VITE_GRADIO_SPACE_NAME` - Hugging Face Gradio Space name
- `VITE_HF_TOKEN` - Hugging Face API token (for private spaces)
- `DATABASE_URL` - PostgreSQL connection (not used, app uses Firestore)

### Development
- **Start Dev Server**: `npm run dev`
- **Port**: 5000 (both frontend and backend)
- **Host**: 0.0.0.0 (configured for Replit proxy)
- **Allowed Hosts**: Enabled in vite.config.ts for Replit iframe

### Build & Deploy
- **Build Command**: `npm run build`
  - Builds frontend with Vite
  - Bundles backend with esbuild
  - Output: `dist/public` (frontend), `dist/index.js` (backend)
- **Start Production**: `npm start`
- **Deployment**: Configured for Autoscale deployment

## Recent Changes (Nov 20, 2025)
- ✅ Imported from GitHub to Replit
- ✅ Installed all dependencies (npm install)
- ✅ Configured workflow for development server
- ✅ Set up all required environment variables
- ✅ Configured deployment settings (autoscale)
- ✅ Verified app is running successfully

## Firebase Setup Notes
The app uses Firebase for:
- User authentication (email/password)
- Firestore database for storing:
  - User profiles (health conditions, medications, demographics)
  - Scan records (nutrition analysis history)

Make sure Firebase Authentication is enabled in the Firebase Console:
1. Enable Email/Password authentication
2. Set up Firestore database with appropriate security rules

## AI Analysis Flow
1. **Image Mode**: User uploads nutrition label photo → Gradio AI extracts nutrition facts → Analyze with user profile
2. **Manual Mode**: User enters nutrition data in form → Analyze with user profile
3. **Fallback**: If Gradio API fails, uses heuristic analysis based on FDA guidelines
