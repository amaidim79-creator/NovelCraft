# NovelCraft - Novel Writing App

## Overview
NovelCraft is a powerful mobile application designed to help writers craft their novels. Built with Expo/React Native, it provides comprehensive tools for plot design, character management, note-taking, and distraction-free writing with smart grammar and consistency checking.

## Current State
The app is fully functional with all core features implemented:
- User authentication (sign in/sign up/guest mode)
- Project management for multiple novels
- Plot designer with templates (Three-Act Structure, Hero's Journey)
- Character profiles with detailed tracking
- Notes workspace with categories
- Rich text editor with auto-save and word count
- Character name consistency checking
- Export to HTML and TXT formats

## Project Architecture

### Directory Structure
```
├── App.tsx                 # Main app entry with providers
├── context/
│   ├── AppContext.tsx      # Global app state management
│   └── AuthContext.tsx     # Authentication state
├── screens/
│   ├── LoadingScreen.tsx   # App loading animation
│   ├── AuthScreen.tsx      # Sign in/sign up
│   ├── ProjectsScreen.tsx  # Projects dashboard
│   ├── PlotScreen.tsx      # Plot designer
│   ├── WriteScreen.tsx     # Novel editor
│   ├── CharactersScreen.tsx # Character management
│   └── NotesScreen.tsx     # Notes workspace
├── navigation/
│   └── MainTabNavigator.tsx # Bottom tab navigation
├── components/             # Reusable UI components
├── utils/
│   ├── storage.ts          # AsyncStorage data layer
│   └── export.ts           # Export functionality
├── constants/
│   └── theme.ts            # Design system tokens
└── hooks/                  # Custom React hooks
```

### Key Technologies
- Expo SDK 54
- React Navigation 7 (Bottom Tabs)
- React Native Reanimated (animations)
- AsyncStorage (data persistence)
- expo-file-system & expo-sharing (export)

### Data Models
- **Project**: Novel with title, genre, description, word count, target
- **Chapter**: Content with title, order, word count
- **Character**: Name, role, appearance, personality, backstory, relationships
- **Note**: Title, content, category (world/research/ideas/other), tags
- **PlotPoint**: Title, description, act (1-3), type, order

## Design System
- Primary Color: Indigo (#6366F1)
- Dark mode optimized for long writing sessions
- iOS 26 Liquid Glass-inspired interface
- Feather icons throughout
- Serif fonts for novel editor content

## Recent Changes
- Initial build with all core features
- Authentication system with guest mode
- Export functionality (HTML/TXT)
- Smart character name consistency checking
- Plot templates (Three-Act, Hero's Journey)

## User Preferences
- Mobile-first design
- Minimalist, distraction-free writing experience
- Auto-save every 2 seconds while typing
- Haptic feedback on word count milestones
