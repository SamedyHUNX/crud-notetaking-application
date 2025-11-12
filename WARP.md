# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

A vanilla JavaScript CRUD note-taking application with multi-language support (English, German, Khmer, Thai). All data is stored client-side in localStorage. No build system, package manager, or backend required.

## Development Commands

**Running the Application:**
```bash
# Open in browser (any simple HTTP server works)
python3 -m http.server 8000
# Then navigate to http://localhost:8000
```

**No build, test, or lint commands** - this is a vanilla HTML/CSS/JS project with no build tooling.

## Architecture

### Page Structure

The application has **two main pages**:

1. **index.html** - Landing/welcome page with intro component
2. **note.html** - Main note-taking interface with CRUD functionality

### Component-Based Organization

Despite being vanilla JS, the codebase follows a component pattern where each component has:
- **CSS file** - Component styling
- **JS file** - Component logic and DOM injection

Components live in `/components/` and are loaded via `<script>` tags in HTML files in a **specific order** (see script loading section).

### Key Components

**`/components/crud/crud.js`** - Core application logic:
- Manages localStorage read/write for notes
- Implements CRUD operations (add, edit, delete, render)
- Handles language switching and UI translation updates
- Contains all event listeners for note interactions

**`/components/languages/languages.js`** - Internationalization:
- `translations` array containing all UI strings in 4 languages
- Index-based language selection (0=English, 1=German, 2=Khmer, 3=Thai)
- Consumed by crud.js to update all UI text

**`/components/aside/aside.js`** - Sidebar notes list:
- Injects the aside HTML structure
- Displays saved notes
- Responsive: hidden on mobile (<920px), toggled via hamburger button

**`/components/input/input.js`** - Form inputs:
- Injects the three input fields (title, date, note)
- Initial placeholders (overridden by language selection)

**`/components/navbar/navbar.js`** - Navigation bar:
- Builds navbar from `navBarElementLeft` array (defined in note.js)
- Contains home button and language flag buttons

**`/components/button/button.js`** - Button creation:
- Generic button creation from `buttonArray` data
- Used across both pages

**`/javascript/note.js`** - note.html page controller:
- Defines navbar data structure
- Handles responsive aside visibility logic (media query at 920px)

**`/javascript/removal.js`** - DOM cleanup:
- Removes unwanted attributes after component injection
- Adds close button functionality for aside

### Data Flow

1. **Page Load** → Components inject HTML → Static data loaded → CRUD initializes
2. **User adds note** → Validated → Pushed to notes array → localStorage.setItem → renderNotes() → DOM updated
3. **Language switch** → Flag clicked → updateTranslations() → All UI text updated → Notes re-rendered
4. **Edit note** → Pre-fills inputs → Removes from array → User re-saves → Updates localStorage
5. **Delete note** → Removes from array → Updates localStorage → Re-renders list

### Script Loading Order (Critical)

In `note.html`, scripts must load in this order:

1. **Static data** (right-section.js, languages.js)
2. **Page controller** (note.js)
3. **Component injectors** (navbar.js, input.js, aside.js)
4. **Button creation** (button.js)
5. **CRUD logic** (crud.js) - **Must be last** as it depends on all DOM elements existing
6. **Cleanup** (removal.js)

### Styling System

**CSS Custom Properties** in `/css/common_css/common.css`:
- Global design tokens (colors, fonts, spacing)
- Responsive breakpoint at 600px for typography
- Dark theme: `--common-background: rgb(29, 29, 31)`

## Important Patterns

### State Management
- **Single source of truth**: `notes` array in crud.js
- **Persistence**: Synced to localStorage on every change
- **Reactive rendering**: Any state change triggers `renderNotes()`

### Language Switching
- Global `currentLanguageIndex` variable tracks active language
- `updateTranslations(index)` function updates 7+ DOM elements
- Notes must be re-rendered to update button labels

### Responsive Behavior
- Desktop (>920px): Aside always visible
- Mobile (≤920px): Aside hidden by default, toggled via hamburger icon
- Media query listener in note.js handles responsive state

## Common Development Tasks

**Adding a new translation key:**
1. Add property to all 4 language objects in `components/languages/languages.js`
2. Update `updateTranslations()` in crud.js to apply the translation
3. Ensure `renderNotes()` is called if it affects dynamic content

**Adding a new component:**
1. Create `/components/[name]/[name].css` and `/components/[name]/[name].js`
2. Link CSS in `<head>` of relevant HTML file
3. Add `<script>` tag in correct load order (before crud.js)
4. If component needs data, define it in page controller (note.js or index.js)

**Modifying CRUD operations:**
- All CRUD logic is centralized in `/components/crud/crud.js`
- Always call `updateLocalStorage()` after array modifications
- Always call `renderNotes()` to reflect changes in UI

**Debugging localStorage:**
```javascript
// In browser console
localStorage.getItem('notes')  // View raw JSON
localStorage.clear()           // Reset all notes
```

## Tech Stack

- **Languages**: Vanilla JavaScript (ES6+), HTML5, CSS3
- **Storage**: localStorage API
- **Icons**: Remix Icon CDN
- **Fonts**: SF Pro Display/Text (local assets)
- **No frameworks, no dependencies, no build process**
