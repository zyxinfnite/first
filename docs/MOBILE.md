# Mobile App Development Guide

## Architecture

The mobile app uses React Native with Expo for iOS and Android development.

```
mobile/
├── src/
│   ├── screens/          # App screens (Home, Editor, Projects, etc.)
│   ├── navigation/       # Navigation configuration
│   ├── components/       # Reusable components
│   ├── hooks/            # Custom hooks
│   ├── services/         # API & local services
│   ├── store/            # Zustand state management
│   ├── types/            # TypeScript types
│   ├── utils/            # Utility functions
│   └── assets/           # Images, fonts, etc.
├── app.json              # Expo configuration
└── package.json
```

## Features

### Platform-Specific Implementations

- **iOS**: Native UI with iOS HIG
- **Android**: Material Design 3
- **Web**: Responsive design (via Expo Web)

### Core Features

1. **Code Editor**
   - Syntax highlighting
   - Code completion
   - Multiple language support
   - Offline editing capability

2. **OS Emulation**
   - Virtual terminal
   - File browser
   - Process viewer

3. **AI Assistance**
   - Code suggestions
   - Error debugging
   - Learning mode
   - Offline hints

4. **Project Management**
   - Local storage
   - Cloud sync
   - Sharing & collaboration

5. **Notifications**
   - Execution status
   - AI suggestions
   - Collaboration updates

## Development Commands

```bash
# Start Expo development server
npm run dev

# Run on iOS simulator
npm run ios

# Run on Android emulator
npm run android

# Type checking
npm run type-check

# Run tests
npm test

# Lint code
npm run lint
```

## Building & Publishing

### Development Build

```bash
# Create development build for testing
eas build --platform ios --profile preview
eas build --platform android --profile preview
```

### Production Build

```bash
# Create production builds
eas build --platform ios
eas build --platform android
```

### Submit to App Stores

```bash
# Submit to App Store (iOS)
eas submit --platform ios

# Submit to Play Store (Android)
eas submit --platform android
```

## Key Technologies

- **Framework**: React Native with Expo
- **Navigation**: React Navigation (Stack, Tab, Drawer)
- **State**: Zustand
- **HTTP**: Axios
- **UI Components**: React Native built-ins + custom
- **Storage**: Expo FileSystem + AsyncStorage
- **Notifications**: Expo Notifications + Firebase Cloud Messaging
- **Code Editor**: Custom implementation using React Native

## Responsive Design

```typescript
import { useWindowDimensions } from 'react-native';

const screenSize = useWindowDimensions();
const isMobile = screenSize.width < 600;
const isTablet = screenSize.width >= 600 && screenSize.width < 900;
const isLargeScreen = screenSize.width >= 900;
```

## Performance Optimization

- FlatList for large lists
- Code splitting via dynamic imports
- Image optimization
- Lazy loading screens
- Memoization for expensive components

## Testing

```bash
# Unit tests
npm test -- --testPathPattern="src/"

# With coverage
npm test -- --coverage
```

## Deployment

### Staging Environment

```bash
eas build --platform ios --profile staging
eas build --platform android --profile staging
```

### Production Environment

```bash
eas build --platform ios --profile production
eas build --platform android --profile production

# Then submit
eas submit --platform ios --profile production
eas submit --platform android --profile production
```

## Troubleshooting

### App Crashes on Startup

1. Check console logs: `npx expo start --verbose`
2. Clear cache: `expo prebuild --clean`
3. Rebuild: `eas build --platform ios --profile preview --clear-cache`

### Cannot Connect to Backend

- Use `http://10.0.2.2:5000` on Android emulator
- Use `http://localhost:5000` on iOS simulator
- Use actual IP on physical device

### Build Fails

```bash
cd mobile
rm -rf node_modules .expo
npm install
npm run dev
```

## Resources

- [Expo Documentation](https://docs.expo.dev)
- [React Native Docs](https://reactnative.dev)
- [EAS Documentation](https://docs.expo.dev/eas/)
- [React Navigation](https://reactnavigation.org)