# Team Avengers Portfolio Website

A dynamic and interactive portfolio website for Team Avengers, featuring animated characters, interactive maps, and project showcases.

## 🚀 Features

- **Interactive World Map**: Displays team members' locations with custom markers and hover effects
- **Animated Hero Section**: Features Marvel character animations (Iron Man, Captain America, and Wanda)
- **Dark/Light Mode**: Toggle between dark and light themes
- **Responsive Design**: Fully responsive layout with mobile-friendly navigation
- **Typed Text Animation**: Dynamic text animations in the hero section
- **Project Showcase**: Gallery of team projects with filtering options
- **Team Member Profiles**: Interactive profile cards with location information

## 🛠️ Technologies Used

- **Frontend Framework**: React.js with TypeScript
- **Styling**: 
  - Tailwind CSS
  - Framer Motion for animations
  - CSS3 for custom animations
- **Mapping**: 
  - Leaflet.js
  - React-Leaflet
- **Other Libraries**:
  - Lucide Icons
  - React Router DOM
  - TypedJS for text animations

## 📦 Flow

## Detailed Component Workflows

### 1. App.tsx (Root)
1. Initializes ThemeContext
2. Sets up Router
3. Renders Navbar (persistent)
4. Manages Routes

### 2. LandingPage.tsx
1. Initial Render:
   - Sets up hero section container
   - Initializes TypedTitle component
   - Positions GIF elements

2. Animation Flow:
   ```
   Iron Man Animation:
   - Starts from left-bottom
   - Flies diagonally to right-top
   - Loops infinitely

   Captain America Animation:
   - Starts from left
   - Runs horizontally to right
   - Loops infinitely

   Wanda Animation:
   - Fixed position
   - Floats up and down
   - Loops infinitely
   ```

### 3. MapPage.tsx
1. Initial Load:
   - Creates MapContainer
   - Loads TileLayer (map tiles)
   - Initializes BoundsHandler

2. Marker Handling:
   ```
   For each team member:
   1. Create CustomMarker
   2. Set position
   3. Initialize hover handlers
   4. Create popup content
   ```

3. Interaction Flow:
   ```
   Marker Hover:
   1. Mouse enters marker
   2. Trigger popup display
   3. Position popup
   4. Show member info

   Marker Leave:
   1. Mouse leaves marker
   2. Hide popup
   ```

### 4. Navbar.tsx
1. Initial State:
   - Check screen size
   - Set initial theme
   - Initialize menu state

2. Interaction Flow:
   ```
   Desktop:
   - Display full navigation
   - Show theme toggle
   - Handle active states

   Mobile:
   1. Show hamburger menu
   2. On click:
      - Animate menu open/close
      - Display mobile links
      - Handle theme toggle
   ```

### 5. CustomMarker.tsx
1. Marker Creation:
   - Generate custom icon
   - Set position
   - Initialize event handlers

2. Event Flow:
   ```
   Mouse Enter:
   1. Trigger hover state
   2. Show popup
   3. Position popup

   Mouse Leave:
   1. Remove hover state
   2. Hide popup
   ```

### 6. TypedTitle.tsx
1. Initialization:
   - Set up Typed.js instance
   - Configure typing options

2. Animation Flow:
   ```
   1. Start typing animation
   2. Complete first string
   3. Pause
   4. Delete text
   5. Start next string
   6. Loop
   ```

## State Management
1. Theme State:
   - Managed by ThemeContext
   - Persisted in localStorage
   - Accessible globally

2. Navigation State:
   - Managed by React Router
   - Handles active routes
   - Controls mobile menu

3. Map State:
   - Manages marker interactions
   - Controls popup visibility
   - Handles map bounds

## Event Handling
1. Scroll Events:
   - Navbar visibility
   - Parallax effects

2. Resize Events:
   - Mobile menu adaptation
   - Map responsiveness

3. User Interactions:
   - Theme toggling
   - Navigation
   - Map marker interactions

## Detailed Component Workflows - Using Diagram

```markdown
1. index.html
   └─> loads main.tsx

2. main.tsx
   └─> renders `<App />` component

3. `App.tsx`
   ├─> wraps everything in ThemeProvider
   ├─> sets up Router
   └─> renders main layout:
       ├─> `<Navbar />`
       └─> Routes
```
4. Routes flow:
   
   a) Landing Page Route ("/"):
      ```tsx
      <LandingPage />
      ├─> Hero Section
      │   ├─> `<TypedTitle />` (animated text)
      │   ├─> Iron Man animation
      │   ├─> Captain America animation
      │   └─> Wanda animation
      └─> Content Sections
      ```

   b) Map Page Route ("/map"):
      ```tsx
      <MapPage />
      ├─> MapContainer
      │   ├─> TileLayer (map background)
      │   ├─> `<CustomMarker />` (for each team member)
      │   │   └─> Popup on hover
      │   └─> `<BoundsHandler />` (manages map bounds)
      └─> Page content
      ```

5. Persistent Components:
   ```tsx
   <Navbar />
   ├─> Logo
   ├─> Navigation Links
   │   └─> Mobile Menu (on small screens)
   └─> Theme Toggle
   ```

6. Context Flow:
   ```tsx
   <ThemeContext />
   ├─> Manages dark/light mode
   └─> Provides theme state to all components
   ```

7. Data Flow:
   ```tsx
   teamMembers.ts
   ├─> Used by MapPage for markers
   └─> Used by CustomMarker for popup content
   ```

8. Style Application:
    ```tsx
   ├─> Tailwind CSS (utility classes)
   ├─> global.css (custom styles)
   └─> Component-specific styles
```

10. Animation Systems:
    ```tsx
   ├─> Framer Motion (component animations)
   ├─> CSS animations (character movements)
   └─> Typed.js (text typing effect)
```
```
Key Component Entry/Exit Points:

1. `<App />`
   - Entry: main.tsx mount
   - Exit: app closure

2. `<Navbar />`
   - Entry: App render
   - Persistent throughout app lifecycle

3. `<LandingPage />`
   - Entry: "/" route hit
   - Exit: route change

4. `<MapPage />`
   - Entry: "/map" route hit
   - Exit: route change

5. `<CustomMarker />`
   - Entry: MapPage render
   - Exit: MapPage unmount

6. `<TypedTitle />`
   - Entry: LandingPage render
   - Exit: LandingPage unmount
```

This represents the complete flow from initial load to component unmount, with each major component highlighted in its own code block.
