# Untaught — UI Polish: Smooth Transitions, iPad/Mobile Optimization, Flat Card Hierarchy

## Current State
The app has Game Theory (4 modules, 2 sims each) and Behavioural Economics (5 modules, 1 sim each) live. The UI uses card components throughout, including some nested card-within-card patterns. Transitions between pages use CSS animations. Some pages feel jumpy on navigation or when content loads. The layout has various border lines and nested bordered containers.

## Requested Changes (Diff)

### Add
- Smooth page transitions using translate+opacity (no fade-in, no jumpiness)
- Consistent minimum touch target sizes (44x44px) across all interactive elements

### Modify
- **Card nesting**: Flatten all card hierarchies — no cards within cards. Sections that used inner cards should use simple rows, borderless groupings, or subtle background tints instead.
- **Lines/dividers**: Remove unnecessary horizontal rules and border lines. Only use borders where they carry clear meaning (e.g. separating major sections).
- **Transitions**: Replace any abrupt layout shifts or fade animations with smooth, subtle translate+scale transitions that don't cause content reflow.
- **iPad/mobile layout**: Review spacing, font sizes, grid columns, and padding across HomePage, DomainIntroPage, ModuleListPage, LessonPage, SimulationPage, QuizPage, MyProgressPage, GlossaryPage. Ensure comfortable reading and tapping on iPad (768px–1024px) and mobile (<768px).
- **AppHeader**: Ensure header is clean, minimal, no excessive borders.
- **MyProgressPage**: Stats row and domain grid should use flat tinted rows, not bordered cards-within-cards.

### Remove
- Cards nested inside cards (e.g. quiz score rows inside a card container that is already inside a section card)
- Redundant border lines that don't add navigational or semantic value
- Any fade-in animation classes

## Implementation Plan
1. Audit and flatten card nesting in: HomePage, DomainIntroPage, ModuleListPage, LessonPage, SimulationPage, QuizPage, MyProgressPage, GlossaryPage
2. Remove redundant dividers and borders sitewide
3. Fix page transition animation — use translate-y + opacity, avoid layout-shifting properties
4. iPad/mobile layout pass: adjust grid breakpoints, padding, font sizes, touch targets
5. Ensure all interactive elements meet 44x44px minimum touch target on mobile
6. Validate, typecheck, build
