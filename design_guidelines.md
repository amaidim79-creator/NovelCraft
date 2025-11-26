# Novel Writer App - Design Guidelines

## Architecture Decisions

### Authentication
**Auth Required** - The app needs cloud sync and aims to rival Web Novel with professional features.

**Implementation:**
- Include Apple Sign-In (iOS) and Google Sign-In for cross-platform
- Add email/password as fallback option
- Login screen with:
  - Large app wordmark
  - SSO buttons prominently displayed
  - "Continue as Guest" for trial (limited to 1 project)
  - Privacy policy & terms links at bottom
- Account screen features:
  - Profile with writer name and bio
  - Writing statistics (total words, projects, streaks)
  - Sync status indicator
  - Subscription/upgrade options
  - Log out and Delete account (nested in Settings)

### Navigation Architecture
**Tab Navigation (5 tabs)** - The app has distinct feature areas requiring quick switching.

Tab structure:
1. **Projects** (Home) - Dashboard of all novels
2. **Plot** - Plot designer tools
3. **Write** (Center FAB) - Core action, novel editor
4. **Characters** - Character profiles
5. **Notes** - Research and world-building

### Screen Specifications

#### 1. Projects Dashboard (Home Tab)
- **Purpose:** Overview of all novel projects with quick access
- **Header:** 
  - Custom transparent header
  - Title: "My Novels"
  - Right button: Settings icon
- **Layout:**
  - Scrollable content
  - Top: Writing streak card (days written, total words)
  - Grid of project cards (2 columns on larger devices, 1 on small)
  - Floating "+" button (bottom-right) for new project
- **Safe Area:** 
  - Top: headerHeight + Spacing.xl
  - Bottom: tabBarHeight + Spacing.xl + 72 (for FAB)
- **Components:** Project cards showing title, genre tag, word count, last edited, progress bar

#### 2. Plot Designer Screen
- **Purpose:** Visual plot structuring with templates and timeline
- **Header:**
  - Default navigation header
  - Title: Current project name
  - Right button: Template selector icon
- **Layout:**
  - Scrollable with sticky section headers
  - Three-act structure visualization
  - Plot point cards (draggable for reordering)
  - Timeline view toggle
- **Safe Area:**
  - Top: Spacing.xl
  - Bottom: tabBarHeight + Spacing.xl
- **Components:** Plot point cards, act dividers, character arc lines, timeline scrubber

#### 3. Novel Editor Screen (Write Tab)
- **Purpose:** Distraction-free writing environment with smart checking
- **Header:**
  - Minimal custom header (auto-hides on scroll)
  - Left: Back to chapter list
  - Center: Chapter title (editable)
  - Right: Word count badge
- **Layout:**
  - Full-screen rich text editor
  - No scroll indicators (immersive)
  - Bottom toolbar (keyboard accessory) with formatting options
- **Safe Area:**
  - Top: Spacing.l (minimal for immersion)
  - Bottom: keyboard height or tabBarHeight + Spacing.xl
- **Components:** 
  - Rich text input with custom styling
  - Character name underlines (red for mismatches, subtle 1px)
  - Grammar suggestions (red squiggly, 1px opacity 0.6)
  - Floating chapter navigation drawer (left edge swipe)

#### 4. Characters Screen
- **Purpose:** Comprehensive character database
- **Header:**
  - Default navigation header
  - Title: "Characters"
  - Right button: "+" Add character
  - Search bar integrated
- **Layout:**
  - Scrollable list grouped by role (Protagonist, Antagonist, Supporting)
  - Each character card shows avatar, name, role tag
- **Safe Area:**
  - Top: Spacing.xl
  - Bottom: tabBarHeight + Spacing.xl
- **Components:** Character cards, role tags, relationship web view (modal)

#### 5. Character Detail Screen (Modal)
- **Purpose:** Full character profile editing
- **Header:**
  - Custom header with avatar at top
  - Left: Close button
  - Right: Save button
- **Layout:**
  - Scrollable form
  - Sections: Physical, Personality, Backstory, Relationships, Arc
  - Form inputs throughout
- **Safe Area:**
  - Top: Spacing.xl
  - Bottom: insets.bottom + Spacing.xl
- **Submit/Cancel:** In header (Save/Close)

#### 6. Notes Screen
- **Purpose:** Organized research and world-building
- **Header:**
  - Default navigation header
  - Title: "Notes"
  - Right button: "+" Add note
  - Category tabs below header (World, Research, Ideas, Other)
- **Layout:**
  - Tab view for categories
  - Within each tab: scrollable list of note cards
- **Safe Area:**
  - Top: Spacing.xl
  - Bottom: tabBarHeight + Spacing.xl
- **Components:** Category tabs, note cards with preview, tag system

## Design System

### Color Palette
**Primary (Writer's Purple):**
- Primary: #6366F1 (Indigo for focus)
- PrimaryDark: #4F46E5
- PrimaryLight: #818CF8

**Functional:**
- Success: #10B981 (word count milestones)
- Warning: #F59E0B (inconsistencies)
- Error: #EF4444 (grammar errors, subtle for underlines)
- Info: #3B82F6

**Neutrals (Optimized for Dark Mode):**
- Background: #0F0F0F
- Surface: #1A1A1A
- SurfaceElevated: #262626
- Border: #404040
- TextPrimary: #F5F5F5
- TextSecondary: #A3A3A3
- TextTertiary: #737373

**Light Mode Alternative:**
- Background: #FAFAFA
- Surface: #FFFFFF
- TextPrimary: #171717

### Typography
**Font Family:** SF Pro (iOS) / Roboto (Android)

**Writing Content (Novel Editor):**
- Font: Georgia or Charter (serif for better readability)
- Body: 18px, line-height: 1.6
- User-adjustable: 16-22px range

**Interface:**
- H1 (Screen Titles): 28px, Bold, letter-spacing: -0.5
- H2 (Section Headers): 20px, Semibold
- H3 (Card Titles): 17px, Semibold
- Body: 15px, Regular, line-height: 1.4
- Caption: 13px, Regular
- Micro (Metadata): 11px, Medium, uppercase, letter-spacing: 0.5

### Visual Design
**Icons:** Feather icons from @expo/vector-icons
- Navigation: book, users, edit-3, file-text, layout
- Actions: plus, save, x, check, more-vertical
- Status: alert-circle, check-circle

**Critical Assets:**
- 6 preset writer avatars (minimalist, artistic style - ink pen, quill, typewriter motifs)
- Project genre icons (fantasy sword, sci-fi rocket, romance heart, mystery magnifying glass, horror moon)
- Empty state illustrations (minimal line art)

**Touchable Feedback:**
- List items: opacity 0.7 on press
- Cards: scale 0.98 + subtle shadow lift
- Buttons: slight darkening of background
- Floating Write FAB: shadow specs:
  - shadowOffset: {width: 0, height: 2}
  - shadowOpacity: 0.10
  - shadowRadius: 2

**Error Indicators:**
- Grammar errors: Red squiggly underline (1px, opacity 0.6)
- Character name mismatch: Solid red underline (1px, opacity 0.8)
- Non-intrusive: No popups, tap to see suggestion

**Elevation & Shadows:**
- Cards: Subtle border instead of shadow in dark mode
- Modals: 16px border-radius, backdrop blur
- Bottom sheets: Rounded top corners (24px)

### Interaction Design
**Writing Experience:**
- Auto-save every 30 seconds
- Typing indicator: Subtle pulse on save icon
- Distraction-free mode: Hide all UI except text
- Haptic feedback on milestone (1000 words, chapter complete)

**Accessibility:**
- Minimum touch target: 44x44pt
- High contrast mode support
- Adjustable font sizes (Settings)
- VoiceOver labels for all icons
- Grammar underlines detectable by screen readers