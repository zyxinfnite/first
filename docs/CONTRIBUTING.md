# Contributing Guide

## Getting Started

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Commit with clear messages: `git commit -am 'Add feature description'`
5. Push to the branch: `git push origin feature/your-feature`
6. Open a Pull Request

## Code Standards

### TypeScript

- Use strict mode: `"strict": true` in `tsconfig.json`
- No `any` types without justification
- Use interfaces for object shapes
- Export types explicitly

### Naming Conventions

- `camelCase` for variables and functions
- `PascalCase` for classes and types
- `UPPER_SNAKE_CASE` for constants
- Use descriptive names

### File Structure

**Backend** (`backend/src/`):
```
src/
├── types/          # TypeScript interfaces/types
├── models/         # Database models
├── services/       # Business logic
├── controllers/    # Route handlers
├── middleware/     # Express middleware
├── routes/         # Route definitions
└── utils/          # Helper functions
```

**Frontend** (`frontend/src/`):
```
src/
├── components/     # React components
├── pages/          # Next.js pages
├── hooks/          # Custom hooks
├── styles/         # CSS/Tailwind
├── types/          # TypeScript types
├── utils/          # Utilities
└── services/       # API calls
```

**Mobile** (`mobile/src/`):
```
src/
├── screens/        # React Native screens
├── navigation/     # Navigation setup
├── components/     # Reusable components
├── hooks/          # Custom hooks
├── services/       # API & local services
├── store/          # State management
├── types/          # TypeScript types
└── utils/          # Utilities
```

## Testing

- Write unit tests for new features
- Maintain at least 80% code coverage
- Run tests before committing: `npm test`

```bash
# Run specific test
npm test -- filename.test.ts

# Run with coverage
npm test -- --coverage
```

## Commit Messages

Follow Conventional Commits:

```
<type>(<scope>): <subject>

<body>

<footer>
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`
Scopes: `web`, `mobile`, `backend`, `emulator`, `ai`

Example:
```
feat(mobile): add offline code editor

Implement offline editing capability with local storage.
Data syncs when connection is restored.

Closes #123
```

## Pull Request Process

1. Update documentation if needed
2. Add/update tests
3. Run linter: `npm run lint`
4. Ensure all tests pass: `npm test`
5. Fill out the PR template completely
6. Request review from maintainers

### PR Title Format

```
[Platform] Component: Brief description
```

Examples:
- `[Web] Editor: Add syntax highlighting`
- `[Mobile] Navigation: Fix tab bar layout`
- `[Backend] API: Implement project sharing`
- `[All] CI/CD: Update workflow`

## Code Review Guidelines

- Be respectful and constructive
- Ask questions rather than making demands
- Provide context and examples
- Approve when all concerns are addressed

## Platform-Specific Guidelines

### Web
- Use Next.js best practices
- Ensure responsive design (mobile, tablet, desktop)
- Follow TailwindCSS conventions
- Test in Chrome, Firefox, Safari

### Mobile
- Test on both iOS and Android
- Follow platform UI guidelines
- Use safe area insets
- Optimize for different screen sizes
- Handle permissions properly

### Backend
- Document all endpoints
- Add validation for inputs
- Use proper error handling
- Write efficient database queries
- Consider rate limiting

## Reporting Bugs

1. Check if the bug is already reported
2. Include:
   - Steps to reproduce
   - Expected behavior
   - Actual behavior
   - Platform (Web/iOS/Android)
   - Environment details
   - Screenshots if applicable

## Feature Requests

1. Describe the use case
2. Explain the expected behavior
3. Provide examples if possible
4. Discuss implementation approach
5. Consider impact on different platforms