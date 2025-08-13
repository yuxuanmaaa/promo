# Project Structure & Organization

## Recommended Folder Structure

```
src/
├── components/           # Reusable UI components
│   ├── common/          # Generic components (Button, Input, etc.)
│   ├── timer/           # Timer-specific components
│   ├── story/           # Story-related components
│   ├── shop/            # Shop and inventory components
│   └── stats/           # Statistics and achievement components
├── screens/             # Screen-level components
│   ├── HomeScreen/
│   ├── TimerScreen/
│   ├── StoryScreen/
│   ├── ShopScreen/
│   ├── StatsScreen/
│   └── SettingsScreen/
├── services/            # Business logic and API services
│   ├── TimerService.ts
│   ├── StoryEngine.ts
│   ├── FocusCoinSystem.ts
│   ├── ShopSystem.ts
│   └── SyncService.ts
├── models/              # TypeScript interfaces and types
│   ├── User.ts
│   ├── Story.ts
│   ├── Session.ts
│   └── Shop.ts
├── storage/             # Data persistence layer
│   ├── repositories/    # Repository pattern implementations
│   ├── migrations/      # Database migrations
│   └── cache/           # Caching strategies
├── utils/               # Helper functions and utilities
│   ├── validation.ts
│   ├── formatting.ts
│   └── constants.ts
├── hooks/               # Custom React hooks
├── navigation/          # Navigation configuration
├── assets/              # Images, fonts, sounds
│   ├── images/
│   ├── fonts/
│   └── sounds/
└── __tests__/           # Test files mirroring src structure
```

## Key Architectural Patterns

### Component Organization
- **Atomic Design**: Build components from atoms → molecules → organisms
- **Feature-Based**: Group related components by feature domain
- **Separation of Concerns**: Keep UI, business logic, and data separate

### Service Layer Pattern
- **TimerService**: Manages focus/break sessions and timing logic
- **StoryEngine**: Handles story progression and branching logic
- **FocusCoinSystem**: Manages virtual economy and transactions
- **ShopSystem**: Handles item catalog and purchase logic
- **SyncService**: Manages cloud synchronization and offline support

### Data Flow Architecture
```
UI Components → Services → Repositories → Storage
     ↑              ↓
State Management ← Events/Callbacks
```

### File Naming Conventions
- **Components**: PascalCase (e.g., `TimerComponent.tsx`)
- **Services**: PascalCase with Service suffix (e.g., `TimerService.ts`)
- **Models**: PascalCase (e.g., `User.ts`, `Story.ts`)
- **Utilities**: camelCase (e.g., `validation.ts`, `formatTime.ts`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `API_ENDPOINTS.ts`)

## Core System Boundaries

### Timer System
- Handles focus/break session management
- Maintains timing accuracy and background operation
- Integrates with notification system

### Story System
- Manages narrative content and progression
- Handles branching logic and choice validation
- Supports multiple story themes

### Economy System
- Tracks Focus Coin earning and spending
- Manages shop inventory and purchases
- Handles item effects on story progression

### User System
- Manages user preferences and settings
- Tracks statistics and achievements
- Handles cloud sync and multi-device support

## Integration Points

- **Timer → Coin System**: Session completion triggers coin rewards
- **Coin System → Story**: Coins unlock story choices and chapters
- **Story → Shop**: Story progress affects item availability
- **All Systems → Analytics**: Track user behavior and app performance

## Development Workflow

1. **Feature Development**: Start with models/interfaces, then services, then UI
2. **Testing Strategy**: Unit tests for services, integration tests for workflows
3. **Code Reviews**: Focus on type safety, performance, and user experience
4. **Documentation**: Maintain clear README files for each major system