# Setup Guide

## Prerequisites

- Node.js >= 18.0.0
- npm >= 9.0.0
- Docker & Docker Compose (for local backend)
- PostgreSQL 15+ (or use Docker)
- Redis (or use Docker)

### For Mobile Development

- Expo CLI: `npm install -g expo-cli`
- iOS: Xcode 14+ (macOS only)
- Android: Android Studio & Android SDK
- EAS CLI: `npm install -g eas-cli` (for building/publishing)

## Web Development Setup

### 1. Clone the Repository

```bash
git clone https://github.com/zyxinfnite/first.git
cd first
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Environment Variables

Copy `.env.example` to `.env` and update with your values:

```bash
cp .env.example .env
```

### 4. Database Setup

Start PostgreSQL:

```bash
docker-compose up -d postgres redis
```

Run migrations:

```bash
cd backend
npm run migrate
```

### 5. Start Development Servers

```bash
npm run dev:web
```

This will start:
- Frontend: http://localhost:3000
- Backend: http://localhost:5000

## Mobile Development Setup

### 1. Install Expo CLI

```bash
npm install -g expo-cli eas-cli
```

### 2. Navigate to Mobile Directory

```bash
cd mobile
npm install
```

### 3. Start Development Server

```bash
npm run dev
```

Or start for specific platform:

```bash
npm run ios       # iOS simulator
npm run android   # Android emulator
```

### 4. Test on Physical Device

- Install Expo Go app from App Store or Google Play
- Scan the QR code from terminal

## Docker Setup (Full Stack)

Start all services with Docker Compose:

```bash
docker-compose up
```

Access:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000/api
- PostgreSQL: localhost:5432
- Redis: localhost:6379

## Building for Production

### Web

```bash
npm run build:web
npm start
```

### Mobile - Android

```bash
cd mobile
npm run build:android
```

### Mobile - iOS

```bash
cd mobile
npm run build:ios
```

### Mobile - Both Platforms

```bash
cd mobile
npm run build:all
```

## Publishing Mobile Apps

### Android Play Store

```bash
cd mobile
npm run submit:android
```

### iOS App Store

```bash
cd mobile
npm run submit:ios
```

## Troubleshooting

### Port Already in Use

If ports 3000 or 5000 are in use, modify the `.env` file or Docker configuration.

### Database Connection Error

Ensure PostgreSQL is running and the `DATABASE_URL` in `.env` is correct.

### Module Not Found

Run `npm install` in the root directory and each workspace:

```bash
npm install
cd frontend && npm install
cd ../backend && npm install
cd ../mobile && npm install
```

### Mobile App Won't Connect to Backend

1. Ensure backend is running: `npm run dev:web`
2. Check `NEXT_PUBLIC_API_URL` in frontend `.env`
3. For Android emulator, use `http://10.0.2.2:5000` instead of `localhost`
4. For iOS simulator, use `http://localhost:5000`

### Expo Build Errors

Clear cache and rebuild:

```bash
cd mobile
rm -rf node_modules .expo
npm install
npm run dev
```