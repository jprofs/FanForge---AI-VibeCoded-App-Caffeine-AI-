FanForge   Sports Fan Hub Builder

## Overview
FanForge is a web application that allows users to build their own sports fan hub through a conversational chat interface and manage their fan community through a dedicated dashboard with team-specific visual templates. Users can start new hubs, revisit previous hubs, or browse popular demo hubs. The application supports both guest access (session-only data) and registered accounts (persistent data with display name and avatar).

## Core Features

### Authentication System
- **Lightweight User Authentication**:
  - "Login / Continue as Guest" dialog displayed on first visit
  - **Guest Access**: session-only data storage, no persistence across browser sessions
  - **Registered Account**: persistent data storage with display name and avatar selection
  - Profile icon displayed in top-right corner after login showing avatar, username, and points
  - Returning users can re-enter their hub via saved credentials or "Revisit Previous Hub"
- **Hub Sharing System**:
  - "Share Hub Invite" button generates unique shareable link for hub access
  - Guests joining via shared link see: "You're viewing [User]'s Hub — continue as guest or sign in to interact"
  - Hub owners can share their customized hubs with friends and community
  - **Shared Hub Modal System**:
    - Modal pop-up overlay appears automatically when user lands on shared hub link (e.g., /hub?shared=true)
    - Modal centered with fade-in animation and dark translucent background
    - Responsive design: 90% width on small screens, centered on desktop
    - Modal content includes header "Join FanForge Hub" and message "You've been invited to join [UserName]'s [TeamName] Hub. Continue as a guest or sign in to join the conversation."
    - Two action buttons: "Continue as Guest" (grants temporary session access) and "Sign In / Create Account" (opens login dialog)
    - "Remember me next time" checkbox to save login preference
    - "❌ Close" icon in top-right corner for manual dismissal
    - If user already logged in, skip modal and load hub instantly
    - After selection, display toast notification: "✅ Joined as Guest" or "👤 Welcome back, [UserName]!"
    - Modal styling uses FanForge color scheme (#0E0E10 background, white text, team-accent borders)
    - Rounded buttons with hover glow effects
    - Modal shadow with blur radius 20px
    - Fully accessible with proper ARIA labels and keyboard navigation
    - Does not alter any existing content, layout, or interactive elements
- **Profile Management**:
  - Display name and avatar selection during registration
  - Profile icon shows current user information and points
  - Seamless switching between guest and registered modes

### Landing Page
- Hero section with celebratory sports fans background image
- Prominent "FAN FORGE" title displayed over the hero image with custom typography:
  - Font family: 'Houston Sports', 'Anton', 'College Block', sans-serif (in order of preference)
  - Houston Sports font loaded via @font-face CSS rule from uploaded WOFF file
  - Uppercase, bold styling with strong kerning
  - Color: #FFFFFF (or near-white) with subtle shadow for contrast
  - Responsive font sizing: 64–80px on desktop, 36–48px on mobile
  - **Centered positioning on both desktop and mobile**
  - **Subtle fade-in or slide-up animation on page load**
- Updated tagline: "Build or revisit your own sports fan hub — any team, any sport."
- Three main action buttons:
  - "Start New Hub" - primary call-to-action for creating a new hub
  - "Revisit Previous Hub" - for returning to previously created hub
  - "Browse Popular Hubs" - for exploring demo hubs
- **Four clickable feature widgets displayed prominently**:
  - "Live Fixtures" - clickable widget that navigates to dedicated fixtures page
  - "Team News" - clickable widget that navigates to dedicated news page
  - "Fan Community" - clickable widget that navigates to dedicated community page
  - "Fan Predictions" - clickable widget that navigates to dedicated predictions page
  - All widgets styled with hover effects and clear visual indicators of interactivity
  - Cursor changes to pointer on hover to indicate clickability
  - Touch-friendly interaction areas for mobile devices
- **Sports News Ticker Bar**:
  - **CRITICAL FIX**: Horizontal scrolling ticker bar fixed to the bottom of the viewport that must function properly
  - **Styled with team-red gradient background (linear-gradient(90deg,#EF0107,#9E1B32)) or neutral blue if no team is selected**
  - **Displays 5–10 short, random or demo sports news headlines**
  - **Smooth, endless scrolling from right to left with proper CSS animations**
  - **Auto-updates with new random headline every 20–30 seconds using setInterval**
  - **Manual refresh via small "🔄 Refresh News" icon that repopulates headlines**
  - **White, uppercase, bold sans-serif text matching UI font**
  - **Font size: 14–16px on desktop, 12px on mobile**
  - **8–12px padding with subtle shadow for readability**
  - **Optional fade or slide animation when headlines change**
  - **Pauses scrolling on hover for accessibility (animation-play-state: paused)**
  - **Must be fully functional with proper event listeners and state management**
- Uses Inter or Poppins typography with bold headers and medium-weight body text (excluding the main title)
- **Clean, centered layout with proper spacing and visual balance**
- Fully responsive design for desktop and mobile devices

### Feature Section Pages
- **Dedicated pages for each feature widget accessible from landing page**:
  - Live Fixtures page
  - Team News page
  - Fan Community page
  - Fan Predictions page
- **Team Selection Flow for Feature Pages**:
  - When user clicks any feature widget, navigate to corresponding section page
  - Display team selection interface: "Select your team to view [section name]"
  - Pre-populated team selection menu with quick buttons organized by sport:
    - **Football**: Arsenal, Chelsea, Manchester United, Barcelona F.C., Real Madrid
    - **Basketball**: Los Angeles Lakers, Golden State Warriors, Chicago Bulls
    - **Formula 1**: Mercedes AMG F1, Red Bull Racing, Ferrari
    - **Cricket**: India, England, Australia
  - Users can select from predefined teams or type a custom team name
  - After team selection, display relevant team-specific content for that section
- **Section-Specific Content Display**:
  - **Live Fixtures page**: Display next 5 upcoming fixtures for selected team
  - **Team News page**: Display latest news articles for selected team
  - **Fan Community page**: Display community posts related to selected team
  - **Fan Predictions page**: Display predictions about upcoming games for selected team
- Dark grey/black base (#0E0E10) theme consistent with main application
- Team-specific accent colors applied based on selected team
- Persistent "🏠 Home" icon button to return to landing page
- Smooth navigation transitions between pages
- Fully responsive design for desktop and mobile devices

### Hub Creation Flow ("Start New Hub")
- Chat-based interface for building fan hubs with dark grey/black base (#0E0E10) theme
- Persistent "🏠 Home" icon button positioned in the top corner:
  - House icon button that navigates back to the landing page
  - Clearly styled with team accent colors or contrasting colors for visibility
  - Includes alt-text "Return to home page" for accessibility
- Sequential question flow when "Start New Hub" is clicked:
  1. First question: "Which sport do you want to follow?"
  2. Save response as `sportName`
  3. Second question: "Which team?"
  4. Save response as `teamName`
- Pre-populated team selection menu with quick buttons organized by sport:
  - **Football**: Arsenal, Chelsea, Manchester United, Barcelona F.C., Real Madrid
  - **Basketball**: Los Angeles Lakers, Golden State Warriors, Chicago Bulls
  - **Formula 1**: Mercedes AMG F1, Red Bull Racing, Ferrari
  - **Cricket**: India, England, Australia
- Users can select from predefined teams or type a custom team name
- **Enhanced Hub Switch Confirmation System**:
  - Display message: "Confirm new hub for [teamName]? This will replace your current hub."
  - Two options: "Yes" and "No" with instant response triggering
  - **Reliability Upgrades**:
    - Yes/No responses trigger instantly with no delay
    - Loading spinner displays "Switching Hub — Please Wait" (maximum 1.5 seconds)
    - No "Processing..." state after 2 seconds
    - Toast notification "✅ Hub switched successfully!" appears when complete
    - Both Yes and No responses guarantee return of control to user with no freeze
    - Fallback mechanisms ensure user never gets stuck in loading state
  - If "Yes": clear old hub data from local/session storage and create new hub
  - If "No": return to landing page
- Tutorial message displayed: "Just talk to FanForge to add posts, fixtures, predictions, or news."
- **Enhanced Text Input with Emoji Support**:
  - **Emoji keyboard input enabled in all text fields** (comments, posts, highlights, predictions)
  - **Inline emoji rendering** with emojis matching text size and auto-scaling on mobile
  - **Slash-command support in comment boxes**:
    - `/rate [Player] [1-5]` - quick player rating submission
    - `/predict [Team] [Score]` - quick prediction creation
    - `/gif [keyword]` - celebratory GIF insertion (optional feature)
  - All existing comment styling and backend logic maintained
  - Enhanced command processing for content management:
    - "Add Post about [text]" - adds community post with timestamp
    - "Add Prediction [score]" - adds fan prediction
    - "Add Fixture [opponent + date]" - adds to upcoming fixtures
    - "Update News with [headline]" - adds news headline
- Real-time feedback provided to user after each command execution
- Chat bubbles styled with rounded corners and soft shadows
- Sticky chat bar positioned at the bottom of the screen for easy access

### Revisit Previous Hub Flow
- When "Revisit Previous Hub" is clicked, retrieve hub data from local/session storage or user account
- **Authentication-aware hub retrieval**:
  - **Registered users**: retrieve persistent hub data from backend
  - **Guest users**: retrieve session-only data from local storage
- If previous hub exists:
  - Display welcome message: "Welcome back to your [teamName] ([sportName]) hub!"
  - Navigate directly to dashboard with all previously stored data restored
- If no previous hub exists:
  - Display message: "You don't have any previous hubs yet. Start one now!"
  - Provide option to redirect to "Start New Hub" flow

### Browse Popular Hubs Flow
- Gallery interface displaying sample/demo hubs with team logos and visuals
- Featured teams include: Arsenal, Chelsea, Manchester United, Barcelona F.C., Real Madrid, Los Angeles Lakers, Golden State Warriors, Chicago Bulls, Mercedes AMG F1, Red Bull Racing, Ferrari, India, England, Australia
- Clean grid layout with team logos and names
- Selecting a team opens a read-only demo dashboard with sample content
- "Make This My Hub" button in demo dashboard:
  - Saves selected team as active hub in local/session storage or user account
  - Enables full posting and interaction capabilities
  - Transitions to fully functional dashboard

### Dashboard Page
- Automatically displayed after successful hub creation or when revisiting
- Dark grey/black base (#0E0E10) background with team-specific accent colors
- Page title: "FanForge – [teamName] ([sportName]) Hub" where both values are dynamically replaced
- **Points Tracker in Hub Header**:
  - Positioned in top-right corner of hub header
  - Displays total points and current user tier (Rookie, Captain, Legend)
  - Points awarded per action: +5 per comment/post, +10 per prediction, +15 per referral (simulated link), +25 per highlight upload
  - Real-time updates when points are earned
  - Clickable to show detailed points breakdown
- **Profile Integration**:
  - Profile icon displayed in top-right corner showing avatar, username, and points
  - **Hub sharing functionality**: "Share Hub Invite" button generates unique shareable link
  - Authentication status clearly indicated (Guest vs Registered)
- Persistent "🏠 Home" icon button positioned in the top corner:
  - House icon button that navigates back to the landing page
  - Clearly styled with team accent colors or contrasting colors for visibility
  - Includes alt-text "Return to home page" for accessibility
- "Switch Hub" button to return to landing page for hub selection

#### Team Visual Template
- Team header section displaying:
  - Team logo (clear PNG or SVG with transparent background)
  - Team name prominently displayed
- Player showcase section with carousel or grid layout featuring 3-5 key players:
  - High-resolution, tightly cropped face/headshot images (120x120px uniform size)
  - Player names displayed beneath each image
  - **Player Rating System** positioned directly below player names:
    - 1-5 star rating bar with clickable/tappable gold stars
    - Filled stars: #FFD700 (gold), unfilled stars: #444444 (dark grey)
    - Hover/tooltip text: "Rate this player's performance"
    - Average rating and total count displayed: "⭐ 4.3 / 5 from 26 ratings"
    - Individual ratings stored in local/session storage by player ID
    - One rating per session with ability to update existing rating
    - Toast notification after rating: "Thanks! Your rating for [playerName] has been saved."
    - **Slash-command integration**: `/rate [Player] [1-5]` command support in comment boxes
  - **Build Your Team of the Week Button**:
    - Positioned under Player Ratings section
    - Opens modal with draggable player cards (name, photo, rating)
    - Allows user to select 11 players for formation
    - Displays formation graphic labeled "FanForge XI of the Week"
    - Auto-generates shareable image with formation, top players, and ratings
    - Uses demo stats if API data unavailable
    - Does not modify existing Player Ratings layout
  - Subtle border or shadow around player images
  - Clean alignment and spacing
- **Top Rated Players Section** (optional advanced feature):
  - Displayed at bottom of team hub
  - Shows highest-rated players across the community
  - Sorting and filtering options by rating
- Fallback images for missing assets:
  - Generic team logo placeholder if team logo unavailable
  - Generic player silhouette if player headshot unavailable
- Descriptive alt-text for accessibility:
  - Team logos: "Logo of [TeamName]"
  - Player images: "Headshot of [PlayerName]" (e.g., "Headshot of Rohit Sharma")
  - Rating stars: "Rate [PlayerName] from 1 to 5 stars"
- Team-specific accent colors applied to borders and highlights
- Responsive design adapting for desktop and mobile devices

#### Dashboard Sections
- Four main sections displayed as cards or columns with real-time updates:
  - **Upcoming Fixtures**: Display upcoming games and matches with ⚽ emoji/icon
  - **Latest News Feed**: Show recent news articles with 📰 emoji/icon
  - **Community Posts**: Display posts from fans with 💬 emoji/icon
  - **Fan Predictions**: Show predictions about upcoming games with 🔮 emoji/icon
- **🎥 Highlights Tab**:
  - New independent tab in hub navigation
  - **Enhanced text input with emoji support and slash-commands**
  - Users can upload image/clip with caption as "Highlight of the Week"
  - "⭐ Vote" buttons under each highlight
  - Every Sunday at 00:00 local time, auto-compile Top 5 Highlights into feed
  - Feed displays thumbnails and captions with banner: "This Week's FanForge Highlights — Powered by You"
  - Module independent from existing sections
  - Fully responsive for desktop and mobile
- **Interactive Section Cards**: The Upcoming Fixtures, Latest News Feed, and Community Posts sections are fully clickable:
  - Clear visual indicators of interactivity with hover effects (subtle color changes, shadows, or scale transforms)
  - Cursor changes to pointer on hover to indicate clickability
  - Smooth transitions and animations for hover states
  - When clicked, sections either:
    - Smoothly scroll to a detailed expanded view of that section
    - Navigate to a focused detailed page for that specific section
    - Expand inline to show more detailed content with focused interaction
  - Accessible keyboard navigation support (Enter key activation)
  - Touch-friendly interaction areas for mobile devices
  - Clear focus states for accessibility compliance
- **Enhanced Text Input Features**:
  - **Emoji keyboard input and inline emoji rendering** in all comment fields, posts, highlights, and predictions
  - **Slash-command support** in all comment boxes:
    - `/rate [Player] [1-5]` for quick player ratings
    - `/predict [Team] [Score]` for quick predictions
    - `/gif [keyword]` for celebratory GIF insertion (optional)
  - Emojis match text size and auto-scale appropriately on mobile devices
  - All existing comment styling and backend logic preserved
- **Share to Social Toggle**:
  - Toggle switch beneath every comment field in each hub
  - When enabled, simulates cross-posting comment to Instagram, X, TikTok, and YouTube
  - Does not modify existing comment logic or styling
  - Maintains compatibility with all existing comment functionality
- **Social Buzz Panel**:
  - Right-side panel displaying embedded previews of recent shared comments
  - Shows username, platform icon, and comment snippet using placeholder data
  - Updates when Share to Social toggle is used
  - Responsive design for desktop and mobile
- Sport-specific emoji icons displayed (⚽🏀🏎️🏏) based on selected sport
- Dashboard sections update dynamically in real-time when content is added via chat commands
- Subtle fade-in animation when new content appears
- Sticky chat bar at the bottom for continuous interaction
- Uses Inter or Poppins typography with bold headers and medium-weight body text

#### Upcoming Fixtures Section Enhancement
- **Enhanced Fixtures Display Format**:
  - Display next 5 upcoming fixtures for each team hub
  - Format: "Date vs/@ Opponent (Home/Away)" (e.g., "Sat 4 Oct 2025 vs West Ham United (Home)")
  - Section header: "Next 5 Fixtures" with ⚽ emoji/icon
  - Chronological sorting with most recent fixture first
  - If fewer than 5 fixtures available, fill remaining slots with "TBD"
- **Fixture Styling**:
  - Date displayed in team-specific accent color
  - Opponent name in bold text
  - Home/Away indicator in italics
  - Clean, consistent spacing between fixtures
- **Interactive Fixtures**:
  - Each fixture is clickable (link placeholder for future details functionality)
  - Hover effects with subtle color changes or highlighting
  - Cursor changes to pointer on hover
  - Touch-friendly interaction areas for mobile devices
- **Updated Fixture Data**:
  - **Arsenal (Football)**:
    1. Sat 4 Oct 2025 vs West Ham United (Home)
    2. Sat 18 Oct 2025 vs Fulham (Away)
    3. Tue 21 Oct 2025 vs Atlético Madrid (Home)
    4. Sat 25 Oct 2025 vs Crystal Palace (Home)
    5. Sat 1 Nov 2025 vs Burnley (Away)
  - **Manchester United (Football)**:
    1. Sat 4 Oct 2025 vs Sunderland (Home)
    2. Sun 19 Oct 2025 vs Liverpool (Away)
    3. Sat 25 Oct 2025 vs Brighton & Hove Albion (Home)
    4. Sat 1 Nov 2025 vs Nottingham Forest (Away)
    5. TBD
  - **Los Angeles Lakers (Basketball)**:
    1. Tue 21 Oct 2025 vs Golden State Warriors (Home)
    2. Fri 24 Oct 2025 vs Minnesota Timberwolves (Home)
    3. Sun 26 Oct 2025 @ Sacramento Kings (Away)
    4. Mon 27 Oct 2025 vs Portland Trail Blazers (Home)
    5. Wed 29 Oct 2025 @ Minnesota Timberwolves (Away)
- **Data Source**:
  - Use specific fixture data as provided above for Arsenal, Manchester United, and Los Angeles Lakers
  - Maintain chronological order and proper formatting
  - Use placeholder data for other teams if live API is not available

### Fan Leaderboard Page
- **Dedicated page accessible from main navigation**
- Lists top users by total points earned
- Displays username, total points, current tier, and recent activity
- Weekly AI-generated summary of top fans posted automatically
- Sortable by points, tier, and activity
- **Authentication integration**: separate leaderboards for registered users and combined guest/registered view
- Responsive design for desktop and mobile
- Navigation back to hub or landing page

### Comment System Enhancement
- **Reliable Comment Submission System**:
  - **"Post" button functionality must work consistently across all three sections**: Community Posts, Fixtures, and Predictions
  - **Real-time comment display**: new comments appear instantly below the input field without page refresh
  - **Input field clearing**: comment input field automatically clears after successful submission
  - **Empty submission prevention**: disable "Post" button or show validation message when input is empty
  - **Error handling**: display error toast notification if comment submission fails
  - **Consistent UX**: identical comment submission behavior and visual feedback across all three comment types
  - **Backend integration**: reliable API calls for comment storage and retrieval
  - **Loading states**: show loading indicator during comment submission
  - **Success feedback**: display success toast or visual confirmation after successful comment posting
  - **Network error handling**: graceful handling of network failures with retry options
  - **Comment validation**: ensure comments meet minimum requirements before submission
  - **Duplicate prevention**: prevent multiple submissions of the same comment
  - **Character limits**: enforce reasonable character limits with visual feedback
  - **Accessibility**: proper ARIA labels and keyboard navigation for comment forms
  - **Mobile optimization**: touch-friendly comment submission on mobile devices

### Data Persistence and Auto-Save
- **Authentication-aware data storage**:
  - **Guest users**: browser local/session storage (session-only)
  - **Registered users**: backend persistent storage with local caching
- All hub data automatically saved including:
  - `sportName` and `teamName`
  - Community posts with timestamps
  - Fan predictions
  - News headlines
  - Upcoming fixtures
  - **Player ratings by player ID with timestamps**
  - **User points and tier progression**
  - **Highlight uploads and votes**
  - **Team of the Week selections**
  - **Social sharing preferences and history**
  - **User authentication status and profile information**
  - **Comments across all sections with proper persistence**
- Auto-save toast notification: "Your hub has been saved. You can revisit it later."
- Data persists according to user authentication level
- Hub switching clears previous data when confirmed with enhanced reliability system

### Additional Features
- Global Fan Leaderboard showing number of posts per team
- Team accent colors automatically detected and applied based on team/sport selection
- Dynamic visual updates when switching teams (logo and player images change)
- Rounded cards with slight shadows for all UI elements
- Fully responsive design adapting for desktop and mobile devices

### Backend Integration
- **Authentication Backend**:
  - User registration and login system
  - Profile management (display name, avatar)
  - Session management for guest and registered users
  - Hub sharing link generation and validation
  - Persistent data storage for registered users
  - **Shared hub modal system support**:
    - Detection of shared hub links with parameters
    - User authentication status checking for modal display logic
    - Login preference storage for "Remember me next time" functionality
    - Toast notification system for join confirmations
- Backend stores team visual assets data including:
  - Team logo references
  - Key player information and image references
  - Fallback image handling
- Backend provides team-specific visual template data for dynamic updates
- Backend provides data for Global Fan Leaderboard with post counts per team
- Backend provides sample/demo content for "Browse Popular Hubs" feature
- **Backend stores and aggregates player ratings across all users**:
  - Individual player rating submissions
  - Community average ratings calculation
  - Total rating counts per player
  - Rating data for "Top Rated Players" section
  - **Slash-command processing for `/rate` commands**
- **Backend provides team-specific content for feature section pages**:
  - Next 5 upcoming fixtures for selected teams
  - Latest news articles for selected teams
  - Community posts related to selected teams
  - Fan predictions for selected teams
- Backend stores team information and provides team selection data for feature pages
- **Backend provides sports news headlines for ticker bar**:
  - **CRITICAL FIX**: Pool of 5–10 random or demo sports news headlines that must be properly served
  - **API endpoint for fetching new random headlines with proper JSON response format**
  - **Support for manual refresh functionality with proper error handling**
  - **Headlines must be properly formatted and ready for ticker display**
- **Backend provides fixture data for team hubs**:
  - **Updated fixture data for Arsenal, Manchester United, and Los Angeles Lakers as specified**
  - Next 5 upcoming fixtures for each supported team
  - Fixture data includes date, opponent, and home/away status
  - Chronologically sorted fixture data
  - Support for "TBD" entries when fewer than 5 fixtures available
  - Placeholder data with realistic formatting for other teams if live API unavailable
- **Backend stores and manages points system**:
  - User points tracking and tier calculations
  - Points awarded per action (+5 comment/post, +10 prediction, +15 referral, +25 highlight)
  - Leaderboard data aggregation and ranking
  - Weekly AI-generated fan summaries
- **Backend manages highlight system**:
  - Highlight uploads and metadata storage
  - Vote tracking and aggregation
  - Weekly Top 5 compilation at Sunday 00:00 local time
  - Thumbnail generation and feed management
- **Backend handles social sharing simulation**:
  - Placeholder data for social media previews
  - Cross-platform sharing simulation
  - Social buzz panel content generation
- **Backend supports Team of the Week functionality**:
  - Player data and statistics for formation builder
  - Shareable image generation
  - Demo stats when API data unavailable
- **Backend processes enhanced text input features**:
  - **Emoji rendering and storage**
  - **Slash-command processing** for `/rate`, `/predict`, and `/gif` commands
  - **GIF keyword matching and insertion** (optional feature)
  - Maintains all existing comment and post processing logic
- **Backend comment system integration**:
  - **Reliable API endpoints for comment submission across all three sections** (Community Posts, Fixtures, Predictions)
  - **Real-time comment storage and retrieval with proper error handling**
  - **Comment validation and sanitization on backend**
  - **Duplicate comment prevention mechanisms**
  - **Comment metadata storage** (timestamps, user information, section type)
  - **Proper JSON response formatting for frontend consumption**
  - **Database transaction handling for comment persistence**
  - **Comment threading and reply support** (if applicable)
  - **Comment moderation and filtering capabilities**
  - **Rate limiting and spam prevention for comment submissions**

## Design System

### Color Scheme
- Landing page uses hero image background with overlay text
- Dark grey/black base (#0E0E10) background for conversational interface and dashboard
- Team/sport-specific accent colors automatically detected and applied to:
  - Buttons and interactive elements
  - Section headers
  - Highlights and emphasis elements
  - Player image borders and team logo highlights
  - Home navigation button styling
  - **Interactive section card hover states and focus indicators**
  - **Feature widget hover states and interactive elements**
  - **Fixture dates in Upcoming Fixtures section**
  - **Points tracker and tier indicators**
  - **Highlight voting buttons and social sharing toggles**
  - **Authentication elements and profile indicators**
  - **Shared hub modal borders and accent elements**
  - **Comment submission buttons and form elements**
- **Sports news ticker bar**: team-red gradient (linear-gradient(90deg,#EF0107,#9E1B32)) or neutral blue if no team selected
- **Player rating stars**: #FFD700 (filled gold), #444444 (unfilled dark grey)
- **Shared hub modal styling**: #0E0E10 background, white text, team-accent borders, rounded buttons with hover glow, modal shadow with blur radius 20px
- **Comment system styling**: consistent with overall theme, proper contrast for accessibility
- High contrast text for accessibility

### Typography
- **Landing page title "FAN FORGE"**: 'Houston Sports', 'Anton', 'College Block', sans-serif font family with Houston Sports font loaded via @font-face CSS rule from uploaded WOFF file, uppercase, bold styling, strong kerning, #FFFFFF color with subtle shadow, responsive sizing (64–80px desktop, 36–48px mobile)
- Inter or Poppins font family applied across the rest of the application
- Bold headers for section titles and main headings
- Medium-weight body text for content and descriptions
- **Sports news ticker text**: white, uppercase, bold sans-serif matching UI font, 14–16px on desktop, 12px on mobile
- **Fixture text styling**: team-accent color for dates, bold for opponent names, italics for home/away indicators
- **Emoji text integration**: emojis match surrounding text size and auto-scale appropriately on mobile devices
- **Comment text styling**: consistent with application typography, proper sizing and contrast
- Consistent font sizing and hierarchy

### Visual Elements
- Hero section with celebratory sports fans background image on landing page
- **Centered title layout with fade-in or slide-up animation on page load**
- **Four clickable feature widgets with clear hover effects and interactivity indicators**
- **Sports news ticker bar fixed to bottom of viewport with smooth scrolling animation**
- **Authentication dialog and profile integration elements**
- **Enhanced hub switch confirmation with loading spinner and success toast**
- **Shared hub modal with centered positioning, fade-in animation, dark translucent background, and responsive design**
- Team visual template with logo and player showcase
- Uniform 120x120px player headshot images with subtle borders or shadows
- **Interactive star rating system with uniform sizing and gold/grey color scheme**
- **Points tracker with tier badges and progress indicators**
- **Highlight upload interface with voting buttons and thumbnail displays**
- **Social sharing toggles with platform icons and preview panels**
- **Team of the Week formation builder with draggable player cards**
- **Enhanced text input fields with emoji keyboard and slash-command support**
- **Comment submission interface with clear visual feedback and error states**
- All cards and containers styled with rounded corners
- Slight shadows applied to cards, chat bubbles, and elevated elements
- **Enhanced interactive styling for clickable dashboard sections and feature widgets**:
  - Hover effects with subtle color changes, shadow enhancements, or scale transforms
  - Smooth CSS transitions for all interactive states
  - Clear visual feedback for user interactions
  - Focus indicators for keyboard navigation
- **Enhanced fixture display styling**:
  - Clean, consistent spacing between fixtures
  - Clear visual hierarchy with styled dates, opponents, and home/away indicators
  - Hover effects for clickable fixtures
  - Responsive layout for different screen sizes
- Card or column layout for dashboard sections
- Sport-specific emoji icons (⚽🏀🏎️🏏) in section headers and buttons
- Subtle fade-in animations for new content appearance
- Modern, clean aesthetic with focus on readability
- Sticky chat bar positioned at bottom of screen
- Persistent "🏠 Home" icon button with house icon and accessible styling
- Clean grid layout for popular hubs gallery

### Responsive Design
- Fully responsive layout adapting gracefully for desktop and mobile devices
- Hero image and overlay text adapt appropriately for different screen sizes
- **Centered title "FAN FORGE" with consistent positioning across all screen sizes**
- **Landing page title "FAN FORGE" scales responsively: 64–80px on desktop, 36–48px on mobile**
- **Clean, balanced layout with proper spacing maintained across all screen sizes**
- **Feature widgets adapt appropriately for different screen sizes with touch-friendly interaction**
- **Sports news ticker adapts for mobile with smaller font size (12px) and appropriate padding**
- **Authentication dialogs and profile elements optimized for mobile interaction**
- **Shared hub modal responsive design: 90% width on small screens, centered on desktop**
- Team visual template and player grid adjust appropriately for different screen sizes
- **Star rating system optimized for touch interaction on mobile devices**
- **Interactive dashboard sections optimized for touch interaction on mobile devices**
- **Fixture display adapts appropriately for different screen sizes with touch-friendly clickable areas**
- **Points tracker and social panels adapt for mobile with collapsible/expandable sections**
- **Highlight upload and voting interface optimized for mobile touch interaction**
- **Team of the Week modal and formation builder responsive for all screen sizes**
- **Enhanced text input with emoji keyboard optimized for mobile devices**
- **Comment submission interface optimized for mobile touch interaction**
- Card/column layout adjusts appropriately for different screen sizes
- Popular hubs gallery adapts to different screen sizes
- **Feature section pages adapt appropriately for different screen sizes**
- Optimized touch targets for mobile interaction
- Sticky chat bar remains accessible on all device sizes
- Home navigation button remains accessible and visible on all device sizes
- Flexible grid system for dashboard sections

## User Flow

### Authentication Flow
1. **First Visit Authentication**:
   - User visits landing page for the first time
   - "Login / Continue as Guest" dialog appears
   - User chooses between Guest Access (session-only) or Registered Account (persistent data)
   - **Guest users**: proceed with session-only data storage
   - **Registered users**: complete registration with display name and avatar selection
   - Profile icon appears in top-right corner showing avatar, username, and points

2. **Hub Sharing Flow**:
   - Hub owner clicks "Share Hub Invite" button
   - System generates unique shareable link
   - Recipients clicking shared link see: "You're viewing [User]'s Hub — continue as guest or sign in to interact"
   - Guests can view hub content, registered users can fully interact

3. **Shared Hub Modal Flow**:
   - User lands on shared hub link (e.g., /hub?shared=true)
   - **If user already logged in**: skip modal and load hub instantly
   - **If user not logged in**: modal pop-up appears automatically with fade-in animation
   - Modal displays centered with dark translucent background
   - Modal content shows "Join FanForge Hub" header and invitation message with [UserName] and [TeamName]
   - User sees two buttons: "Continue as Guest" and "Sign In / Create Account"
   - "Remember me next time" checkbox available for login preference
   - "❌ Close" icon in top-right for manual dismissal
   - **After "Continue as Guest"**: grants temporary session access, shows toast "✅ Joined as Guest"
   - **After "Sign In / Create Account"**: opens login dialog, shows toast "👤 Welcome back, [UserName]!" after login
   - Modal styled with FanForge colors, rounded buttons with hover glow, and accessibility features

4. **Returning User Flow**:
   - **Registered users**: automatic login via saved credentials
   - **Guest users**: can use "Revisit Previous Hub" for session data
   - Profile information and hub data restored appropriately

### Enhanced Hub Switch Confirmation Flow
1. User initiates hub switch (new hub creation or team change)
2. System displays: "Confirm new hub for [teamName]? This will replace your current hub."
3. **Reliability Enhancements**:
   - User clicks "Yes" or "No" - response triggers instantly
   - Loading spinner appears with "Switching Hub — Please Wait" (maximum 1.5 seconds)
   - No "Processing..." state extends beyond 2 seconds
   - System guarantees completion within time limit
   - Toast notification "✅ Hub switched successfully!" appears when done
   - Both Yes and No responses always return control to user with no freeze
   - Fallback mechanisms prevent any stuck states

### Enhanced Text Input and Emoji Flow
1. **Emoji Input**:
   - User accesses any text field (comments, posts, highlights, predictions)
   - Emoji keyboard available for input
   - Emojis render inline matching text size
   - Auto-scaling on mobile devices maintains readability

2. **Slash-Command Flow**:
   - User types slash-command in comment box:
     - `/rate [Player] [1-5]` - submits player rating
     - `/predict [Team] [Score]` - creates prediction
     - `/gif [keyword]` - inserts celebratory GIF (optional)
   - System processes command and provides immediate feedback
   - All existing comment styling and backend logic preserved

### Feature Section Navigation Flow
1. User visits landing page with hero image and feature widgets
2. User clicks on any feature widget ("Live Fixtures", "Team News", "Fan Community", "Fan Predictions")
3. Application navigates to corresponding dedicated section page
4. Section page displays team selection interface: "Select your team to view [section name]"
5. User selects team from predefined list or types custom team name
6. System displays team-specific content for that section:
   - **Live Fixtures**: Next 5 upcoming fixtures for selected team
   - **Team News**: Latest news articles for selected team
   - **Fan Community**: Community posts related to selected team
   - **Fan Predictions**: Predictions about upcoming games for selected team
7. User can navigate back to landing page using "🏠 Home" button
8. Smooth transitions maintained throughout navigation

### New Hub Creation Flow
1. User visits the landing page with hero image and centered "FAN FORGE" title with updated tagline
2. **Title animates in with subtle fade-in or slide-up effect**
3. **Sports news ticker scrolls continuously at bottom of viewport**
4. User clicks "Start New Hub" button
5. Application transitions to conversational interface
6. Chat asks: "Which sport do you want to follow?"
7. User selects from predefined sports or types custom sport (saved as `sportName`)
8. Chat asks: "Which team?"
9. User selects from sport-specific team menu or types custom team (saved as `teamName`)
10. **Enhanced confirmation system with reliability upgrades**
11. Dashboard displays with title "FanForge – [teamName] ([sportName]) Hub"
12. Auto-save toast appears: "Your hub has been saved. You can revisit it later."

### Revisit Previous Hub Flow
1. User clicks "Revisit Previous Hub" on landing page
2. **Authentication-aware data retrieval**:
   - **Registered users**: system retrieves persistent hub data from backend
   - **Guest users**: system checks local/session storage for session data
3. If data exists: display "Welcome back to your [teamName] ([sportName]) hub!" and navigate to dashboard
4. If no data: display "You don't have any previous hubs yet. Start one now!" with option to start new hub

### Browse Popular Hubs Flow
1. User clicks "Browse Popular Hubs" on landing page
2. Gallery displays with team logos and names in grid layout
3. User selects a team to view read-only demo dashboard
4. User can click "Make This My Hub" to save as active hub
5. **Authentication-aware saving**: system saves hub data to appropriate storage (session or persistent)
6. System enables full functionality based on user authentication level

### Player Rating Flow
1. User hovers over star rating system below player name
2. Tooltip displays: "Rate this player's performance"
3. User clicks/taps on desired star (1-5 rating) or uses `/rate [Player] [1-5]` slash-command
4. Rating is saved to appropriate storage and submitted to backend
5. Toast notification appears: "Thanks! Your rating for [playerName] has been saved."
6. Average rating and count update immediately
7. User can update their rating by selecting different stars

### **Points and Tier Progression Flow**
1. User performs actions in hub (comment/post, prediction, referral, highlight upload)
2. Points automatically awarded (+5, +10, +15, +25 respectively)
3. Points tracker in top-right corner updates in real-time
4. User tier progression calculated (Rookie, Captain, Legend)
5. Toast notification shows points earned: "You earned +10 points for your prediction!"
6. User can click points tracker to view detailed breakdown
7. Weekly leaderboard updates with user rankings

### **Highlight Upload and Voting Flow**
1. User clicks "🎥 Highlights" tab in hub navigation
2. **Enhanced upload interface with emoji support and slash-commands**
3. User submits highlight as "Highlight of the Week"
4. Points awarded (+25) and highlight appears in feed
5. Other users can vote with "⭐ Vote" buttons
6. Every Sunday at 00:00 local time, Top 5 Highlights auto-compiled
7. Weekly feed displays with banner: "This Week's FanForge Highlights — Powered by You"

### **Social Sharing Flow**
1. User writes comment in any hub section with emoji support
2. "Share to Social" toggle appears beneath comment field
3. User enables toggle to simulate cross-posting
4. Comment simulated to Instagram, X, TikTok, and YouTube
5. Social Buzz panel on right updates with preview
6. Preview shows username, platform icon, and comment snippet
7. Existing comment logic and styling remain unchanged

### **Team of the Week Builder Flow**
1. User clicks "Build Your Team of the Week" button under Player Ratings
2. Modal opens with draggable player cards (name, photo, rating)
3. User selects 11 players by dragging to formation positions
4. Formation graphic displays as "FanForge XI of the Week"
5. System auto-generates shareable image with formation and ratings
6. User can save, share, or modify team selection
7. Demo stats used if API data unavailable
8. Existing Player Ratings layout remains unmodified

### **Sports News Ticker Flow**
1. **CRITICAL FIX**: Ticker displays 5–10 sports news headlines scrolling from right to left with proper CSS animations
2. **Headlines auto-update every 20–30 seconds with new random content using setInterval**
3. **User can hover over ticker to pause scrolling for accessibility (animation-play-state: paused)**
4. **User can click "🔄 Refresh News" icon to manually refresh headlines with proper API call**
5. **New headlines fade or slide in when changed with proper animation**
6. **Ticker maintains team-red gradient or neutral blue styling based on team selection**
7. **All event listeners and state management must be properly implemented**

### **Interactive Dashboard Section Flow**
1. User hovers over Upcoming Fixtures, Latest News Feed, or Community Posts section
2. Section displays hover effects (color changes, enhanced shadows, or subtle scaling)
3. Cursor changes to pointer indicating clickability
4. User clicks on the section
5. System either:
   - Smoothly scrolls to an expanded detailed view of that section
   - Navigates to a focused detailed page for that specific section
   - Expands the section inline to show detailed content with focused interaction
6. User can interact with the detailed content or return to the main dashboard view
7. All interactions maintain responsive design and accessibility standards

### **Enhanced Fixture Interaction Flow**
1. User views "Next 5 Fixtures" section in dashboard with formatted fixture list
2. Each fixture displays as "Date vs/@ Opponent (Home/Away)" with appropriate styling
3. User hovers over individual fixture, cursor changes to pointer with hover effects
4. User clicks on fixture (placeholder link for future details functionality)
5. System provides visual feedback for the interaction
6. All fixture interactions maintain responsive design and accessibility standards

### **Comment Submission Flow**
1. **Reliable Comment Posting Process**:
   - User navigates to any section with comments (Community Posts, Fixtures, Predictions)
   - User types comment in text input field with emoji support
   - **Empty validation**: "Post" button disabled or validation message shown if input is empty
   - User clicks "Post" button
   - **Loading state**: loading indicator appears during submission
   - **Backend API call**: comment data sent to appropriate endpoint with error handling
   - **Success handling**: 
     - Comment appears instantly below input field (real-time update)
     - Input field automatically clears
     - Success toast notification appears: "Comment posted successfully!"
     - Points awarded (+5) and tracker updates
   - **Error handling**:
     - Network error: "Failed to post comment. Please try again." toast with retry option
     - Validation error: specific error message displayed
     - Duplicate prevention: "Comment already posted" message if duplicate detected
   - **Consistent behavior**: identical flow across all three comment sections
   - **Mobile optimization**: touch-friendly submission with proper keyboard handling
   - **Accessibility**: proper ARIA labels and screen reader support

2. **Comment Display and Management**:
   - Comments display in chronological order with timestamps
   - User avatar and name displayed with each comment
   - Emoji rendering in comments matches text size
   - Responsive comment layout for different screen sizes
   - Proper text wrapping and overflow handling

### **Fan Leaderboard Navigation Flow**
1. User accesses Fan Leaderboard page from main navigation
2. Page displays top users by points with tier indicators
3. **Authentication-aware leaderboard display** (separate or combined views)
4. Weekly AI-generated summary of top fans displayed prominently
5. User can sort by points, tier, or recent activity
6. User can navigate back to hub or landing page
7. Responsive design maintained across all devices

### General Navigation
- Persistent "🏠 Home" button available on all pages to return to landing page
- "Switch Hub" button on dashboard to return to landing page
- **Profile icon in top-right corner** showing user authentication status
- **Hub sharing functionality** accessible from dashboard
- All navigation preserves appropriate data and provides smooth transitions

## Technical Requirements
- Application content in English
- Hero image background on landing page with overlay text
- **Centered "FAN FORGE" title with clean, balanced layout**
- **Fade-in or slide-up animation for title on page load**
- **Custom typography for "FAN FORGE" title: 'Houston Sports', 'Anton', 'College Block', sans-serif with Houston Sports font loaded via @font-face CSS rule from uploaded WOFF file, uppercase, bold, strong kerning, #FFFFFF color, subtle shadow, responsive sizing**
- **Four clickable feature widgets on landing page with navigation to dedicated section pages**
- **Lightweight user authentication system implementation**:
  - "Login / Continue as Guest" dialog on first visit
  - Guest Access with session-only data storage
  - Registered Account with persistent data storage and profile management
  - Profile icon in top-right corner with avatar, username, and points display
  - Hub sharing system with unique link generation
  - Authentication-aware data persistence and retrieval
- **Shared hub modal system implementation**:
  - Automatic modal display when landing on shared hub links (e.g., /hub?shared=true)
  - Modal centered with fade-in animation and dark translucent background
  - Responsive design: 90% width on small screens, centered on desktop
  - Modal content with "Join FanForge Hub" header and personalized invitation message
  - Two action buttons: "Continue as Guest" and "Sign In / Create Account"
  - "Remember me next time" checkbox for login preference storage
  - "❌ Close" icon in top-right corner for manual dismissal
  - Skip modal logic for already logged-in users
  - Toast notifications: "✅ Joined as Guest" or "👤 Welcome back, [UserName]!"
  - FanForge color scheme styling (#0E0E10 background, white text, team-accent borders)
  - Rounded buttons with hover glow effects and modal shadow (blur radius 20px)
  - Full accessibility with ARIA labels and keyboard navigation
  - No alteration to existing content, layout, or interactive elements
- **Enhanced hub switch confirmation system implementation**:
  - Instant Yes/No response triggering
  - Loading spinner with "Switching Hub — Please Wait" (max 1.5s)
  - No "Processing..." state after 2 seconds
  - Toast notification "✅ Hub switched successfully!"
  - Guaranteed return of control to user with no freeze states
  - Fallback mechanisms for reliability
- **Enhanced text input with emoji and slash-command support implementation**:
  - Emoji keyboard input enabled in all text fields
  - Inline emoji rendering matching text size with mobile auto-scaling
  - Slash-command processing: `/rate [Player] [1-5]`, `/predict [Team] [Score]`, `/gif [keyword]`
  - All existing comment styling and backend logic preserved
  - Mobile-optimized emoji interaction
- **Sports news ticker bar implementation**:
  - **CRITICAL FIX**: Fixed positioning at bottom of viewport with proper CSS positioning
  - **Horizontal scrolling animation from right to left using CSS keyframes and animation properties**
  - **Team-red gradient background (linear-gradient(90deg,#EF0107,#9E1B32)) or neutral blue**
  - **Auto-refresh every 20–30 seconds using setInterval with proper cleanup**
  - **Manual refresh via "🔄 Refresh News" icon with proper click event handlers**
  - **Hover to pause functionality using CSS animation-play-state: paused**
  - **Fade/slide animations for headline changes with proper CSS transitions**
  - **Responsive font sizing and padding (14–16px desktop, 12px mobile)**
  - **White, uppercase, bold text with subtle shadow for readability**
  - **Proper state management for headlines array and current index**
  - **Error handling for API calls and fallback content**
  - **Component lifecycle management with proper mounting and unmounting**
- **Dedicated pages for Live Fixtures, Team News, Fan Community, and Fan Predictions sections**
- **Team selection interface on feature section pages with team-specific content display**
- **Points tracking system implementation**:
  - Top-right corner positioning in hub header
  - Real-time points calculation and tier progression
  - Points awarded per action (+5, +10, +15, +25)
  - Toast notifications for points earned
  - Clickable detailed breakdown view
  - Tier badges (Rookie, Captain, Legend)
- **Highlight system implementation**:
  - Independent "🎥 Highlights" tab in hub navigation
  - Image/clip upload with caption functionality and emoji support
  - "⭐ Vote" buttons under each highlight
  - Weekly Top 5 compilation every Sunday at 00:00 local time
  - Feed with thumbnails, captions, and banner
  - Module independence from existing sections
- **Social sharing system implementation**:
  - Toggle switch beneath every comment field
  - Simulation of cross-posting to Instagram, X, TikTok, YouTube
  - Social Buzz panel on right side with embedded previews
  - Username, platform icon, and snippet display
  - Placeholder data for previews
  - No modification to existing comment logic or styling
- **Team of the Week builder implementation**:
  - Button positioned under Player Ratings section
  - Modal with draggable player cards
  - 11-player selection for formation
  - Formation graphic labeled "FanForge XI of the Week"
  - Auto-generated shareable image
  - Demo stats when API unavailable
  - No modification to existing Player Ratings layout
- **Fan Leaderboard page implementation**:
  - Dedicated page with top users by points
  - Sortable by points, tier, and activity
  - Weekly AI-generated fan summaries
  - Authentication-aware display
  - Navigation integration
- **Reliable comment system implementation**:
  - **"Post" button functionality working consistently across Community Posts, Fixtures, and Predictions sections**
  - **Real-time comment display without page refresh**
  - **Automatic input field clearing after successful submission**
  - **Empty submission prevention with validation**
  - **Error handling with toast notifications for failed submissions**
  - **Loading states during comment submission**
  - **Success feedback with toast notifications**
  - **Network error handling with retry options**
  - **Comment validation and character limits**
  - **Duplicate comment prevention**
  - **Mobile-optimized comment submission interface**
  - **Accessibility features for comment forms**
  - **Consistent UX across all three comment types**
  - **Backend API integration for reliable comment storage and retrieval**
- Dark grey/black base (#0E0E10) theme design system for conversational interface and dashboard with team/sport-specific accent colors
- Inter or Poppins typography with bold headers and medium-weight body text (excluding main title)
- Rounded corners and slight shadows for all UI elements
- Card or column layout for dashboard sections
- **Interactive dashboard sections with clickable functionality**:
  - Hover effects and visual feedback for interactivity
  - Smooth CSS transitions and animations
  - Cursor pointer changes on hover
  - Keyboard navigation support (Enter key activation)
  - Touch-friendly interaction areas for mobile
  - Accessible focus states and ARIA labels
  - Smooth scrolling or navigation to detailed views
- **Interactive feature widgets with hover effects and clear visual indicators**
- **Enhanced Upcoming Fixtures section implementation**:
  - Display next 5 fixtures formatted as "Date vs/@ Opponent (Home/Away)"
  - Section header: "Next 5 Fixtures" with ⚽ emoji/icon
  - Team-accent color for dates, bold for opponents, italics for home/away
  - Clickable fixtures with hover effects and pointer cursor
  - Chronological sorting with updated fixture data for Arsenal, Manchester United, and Los Angeles Lakers
  - "TBD" entries for missing fixtures
  - Touch-friendly interaction areas for mobile
  - Responsive layout adaptation
- Sport-specific emoji icons for visual clarity (⚽🏀🏎️🏏)
- Subtle fade-in animations for new content
- Sticky chat bar at bottom of screen
- Persistent "🏠 Home" icon button on all pages with accessibility features
- Team visual template with logo and player showcase
- Uniform 120x120px player headshot images with borders/shadows
- **Interactive 1-5 star rating system with gold (#FFD700) and grey (#444444) colors**
- **Touch-optimized star rating for mobile devices**
- **Rating persistence in appropriate storage (session/persistent) and backend aggregation**
- **Toast notifications for rating confirmations**
- **Hover tooltips and accessibility features for rating system**
- **Slash-command integration for player ratings**
- Fallback image system for missing team logos and player images
- Descriptive alt-text for all images and interactive elements for accessibility
- Dynamic visual updates when switching teams
- **Responsive layout with clean, centered design and proper spacing**
- Fully responsive design for various screen sizes
- Smooth page transitions between all pages and flows
- **Authentication-aware data persistence**: browser local/session storage for guests, backend persistent storage for registered users
- Auto-save functionality with toast notifications
- Popular hubs gallery with clean grid layout
- Confirmation flows for hub creation and switching with enhanced reliability
- Read-only demo dashboards with "Make This My Hub" functionality
- Consistent navigation patterns across all user flows
- **Smooth navigation between landing page and feature section pages**
- **Team-specific content loading and display for feature sections**
- **Backend integration for fixture data with updated specific fixture data for Arsenal, Manchester United, and Los Angeles Lakers**
- **Modular implementation ensuring all new features appear as additional elements without altering existing content, text, images, or layout**
- **Full compatibility maintained for desktop and mobile devices**
- **Build checkpoint save: "FanForge v2.4 – Comment System Reliability Fix"**

