# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML website for "TriTalent" - a people, process, and performance consultancy specializing in HR solutions. The company operates across Saudi Arabia & the GCC region. The site is built using vanilla HTML, CSS (via Tailwind CSS CDN), and JavaScript with no build process or framework.

## Technology Stack

- **HTML5**: Static markup
- **Tailwind CSS**: Via CDN (https://cdn.tailwindcss.com)
- **Swiper.js**: Carousel/slider library (v11, via CDN)
- **Font Awesome**: Icons (v6.5.1, via CDN)
- **Google Fonts**: Inter font family
- **Vanilla JavaScript**: No frameworks

## File Structure

```
/
├── index.html                            # Main landing page with hero carousel, services, and contact
├── team.html                             # Team overview page with grid of 8 team members
├── team-bob.html                         # Ehab Gawad - Managing Partner profile
├── team-michael-chen.html                # Michael Chen - Senior HR Consultant profile
├── team-emily-rodriguez.html             # Emily Rodriguez - Recruitment Specialist profile
├── assessment-centers.html               # Assessment Centers service detail page
├── leadership-development.html           # Leadership Development Programs service detail page
├── soft-skills-training.html             # Soft Skills Training service detail page
├── culture-engagement.html               # Culture & Engagement Programs service detail page
├── team-building.html                    # Team Building & Experiential Events service detail page
├── executive-coaching.html               # Executive Coaching service detail page
├── talent-development-consulting.html    # Talent Development Consulting service detail page
├── images/
│   ├── tritalent-logo.png               # Main logo file
│   ├── bob.jpg                           # Ehab Gawad profile photo
│   └── bob.enc                           # Encrypted version (not used in site)
└── CLAUDE.md                             # This file
```

## Development Workflow

Since this is a static HTML site with no build process:

1. **No build commands** - Simply open HTML files directly in a browser
2. **No package manager** - All dependencies loaded via CDN
3. **No local development server required** - Files can be opened with `file://` protocol or served with any static server

To preview changes, you can use:
```bash
# Option 1: Simple Python server
python3 -m http.server 8000

# Option 2: PHP server
php -S localhost:8000

# Then open: http://localhost:8000/index.html
```

## Brand Identity & Messaging

### Core Philosophy
- **Tagline**: "People • Process • Performance"
- **Vision**: "Creating everyday win"
- **Mission**: To support individuals, teams, and organizations in achieving their highest potential by enabling everyday performance, growth, and leadership
- **Core Belief**: "Winning is not a moment—it's a habit. A habit built through mindset, energy, emotional intelligence, and disciplined execution."

### EVERYDAY WIN Model
The company's values framework includes four dimensions:
1. **Physical Win**: Energy, wellbeing, balance, physical vitality
2. **Mental Win**: Clarity, growth mindset, strong decision-making, mental readiness
3. **Emotional Win**: Self-awareness, resilience, engagement, meaningful connections, emotional intelligence
4. **Performance Win**: Execution, accountability, measurable results, leadership impact

### Company Information
- **Email**: info@tri-talent.com
- **Website**: www.tri-talent.com
- **Location**: Operating across Saudi Arabia & the GCC
- **Copyright**: © 2026 Tritalent. All rights reserved.

## Architecture & Design Patterns

### Color Scheme
The site uses a consistent color palette defined in Tailwind configuration, based on the TriTalent logo:
- **Primary**: `#52A8A6` (teal - main brand color)
- **Secondary**: `#3d8583` (darker teal)
- **Accent**: `#6bb9b7` (lighter teal)
- **Dark**: `#1e293b` (slate-800)
- **Light**: `#f1f5f9` (slate-100)

### Common Components

All pages share consistent components that should be maintained:

1. **Navigation Bar** (`<nav id="navbar">`)
   - Fixed position header with logo and menu
   - Responsive mobile menu (hamburger)
   - Active state styling for current page
   - Smooth scroll behavior for hash links

2. **Footer**
   - Four-column grid layout (company info, quick links, services, contact)
   - Social media icons
   - Copyright notice

3. **Mobile Menu**
   - Controlled via JavaScript toggle
   - Uses `.mobile-menu` class with max-height animation
   - Icon switches between `fa-bars` and `fa-times`

### Page-Specific Features

**index.html**
- Hero section with Swiper carousel (4 slides, fade effect, autoplay)
- Services section with Swiper carousel (7 service cards, responsive grid)
- Major sections: #home, #About Us (includes Vision/Mission), #services, #why-us (EVERYDAY WIN philosophy), #contact
- "About Us" section includes methodology breakdown: People, Process, Performance
- EVERYDAY WIN values section: Physical Win, Mental Win, Emotional Win, Performance Win

**team.html**
- Team member grid (8 members, responsive: 1/2/3/4 columns)
- Hover effects on team cards with overlay animation showing "View Profile"
- Links to individual team member profile pages (3 are fully implemented: bob, michael-chen, emily-rodriguez)
- 5 placeholder profiles linking to team-member.html?id=[5-8] or team-david-thompson.html

**team-[name].html**
- Individual profile pages for team members
- Breadcrumb navigation (Home > Team > Name)
- Detailed bio, expertise, achievements, and contact info
- Consistent structure across all profile pages

**Service Detail Pages** (7 pages total)
- All share common structure: hero with breadcrumb, overview, key benefits, what's included, approach/methodology, who benefits, expected outcomes, why Tritalent, related services, CTA
- Each page has service-specific color scheme for icons/accents
- assessment-centers.html: Blue theme, includes timeline visualization
- leadership-development.html: Green theme
- soft-skills-training.html: Purple theme
- culture-engagement.html: Red theme
- team-building.html: Yellow theme
- executive-coaching.html: Indigo theme
- talent-development-consulting.html: Teal theme

### JavaScript Functionality

All JavaScript is inline in `<script>` tags at the bottom of each page. Common patterns include:

**Mobile Menu** (all pages):
- Toggle button with ID `mobile-menu-btn`
- Menu container with ID `mobile-menu`
- Icon switches between `fa-bars` and `fa-times`
- Menu uses `.mobile-menu.active` class with max-height animation
- Click handlers on menu links to auto-close after selection

**Navbar Scroll Behavior** (all pages):
- Element ID: `navbar`
- Adds `shadow-xl` class when scrollY > 50
- Fixed position with smooth transition

**Smooth Scroll** (all pages):
- Listens for clicks on `a[href^="#"]`
- Calculates offsetTop minus 80px (to account for fixed navbar height)
- Uses `window.scrollTo()` with `behavior: 'smooth'`

**Swiper Carousels** (index.html only):
- **Hero Swiper** (`.hero-swiper`): Loop enabled, autoplay 5000ms, fade effect, pagination + navigation
- **Services Swiper** (`.services-swiper`): Loop enabled, autoplay 4000ms, responsive breakpoints (1 col mobile, 2 col tablet, 3 col desktop), pagination + navigation

**Intersection Observer** (index.html only):
- Observes all `<section>` elements
- Initial state: `opacity: 0`, `translateY(20px)`
- Triggers fade-in animation when sections enter viewport
- Threshold: 0.1, rootMargin: '0px 0px -50px 0px'

### Responsive Design

Breakpoints follow Tailwind defaults:
- `sm`: 640px
- `md`: 768px
- `lg`: 1024px
- `xl`: 1280px

## Navigation Links

The site has two types of navigation:

**Main Navigation Menu** (consistent across all pages):
- Home: `index.html#home`
- About Us: `index.html#About Us` (note the space in the hash)
- Services: `index.html#services`
- Team: `team.html`
- Our Methodology: `index.html#why-us`
- Contact: `index.html#contact`
- Get Started button: `index.html#contact`

**Service Detail Pages** (linked from services section):
- Assessment Centers: `assessment-centers.html`
- Leadership Development Programs: `leadership-development.html`
- Soft Skills Training: `soft-skills-training.html`
- Culture & Engagement Programs: `culture-engagement.html`
- Team Building & Experiential Events: `team-building.html`
- Executive Coaching: `executive-coaching.html`
- Talent Development Consulting: `talent-development-consulting.html`

**Team Member Profiles**:
- Naming convention: `team-[firstname-lastname].html` (all lowercase, hyphen-separated)
- Implemented profiles: `team-bob.html`, `team-michael-chen.html`, `team-emily-rodriguez.html`
- Placeholder profiles: Links to `team-member.html?id=[5-8]` or `team-david-thompson.html` (not yet created)

When modifying navigation, ensure consistency across all pages and maintain active state styling for current page.

## Images

**Local Images** (in `/images/` directory):
- `tritalent-logo.png`: Main logo (appears in navbar and footer)
- `bob.jpg`: Ehab Gawad profile photo
- `bob.enc`: Encrypted version (not used in site)

**External Images** (Unsplash CDN):
- All other images are sourced from Unsplash via CDN URLs
- Hero images: 1920px width, format: `https://images.unsplash.com/photo-[id]?w=1920&q=80`
- Portrait images: 600px width, format: `https://images.unsplash.com/photo-[id]?w=600&q=80`
- Service/feature images: 800px width, format: `https://images.unsplash.com/photo-[id]?w=800&q=80`

When adding new content:
- Use high-quality stock images at appropriate sizes
- Include descriptive `alt` attributes for accessibility
- Maintain consistent image aspect ratios within component types
- For team members, use local images in `/images/` directory or Unsplash portraits

## Styling Conventions

- Use Tailwind utility classes exclusively (no custom CSS files)
- Custom styles are embedded in `<style>` tags in the `<head>`
- Animations use CSS transitions and keyframes
- Hover effects: `hover-lift` class for card components

## Adding New Content

### Adding New Team Members

When adding a new team member:

1. Add card to `team.html` in the team grid section (around line 169)
2. Create individual profile page: `team-[firstname-lastname].html` (all lowercase, hyphen-separated)
3. Use existing profile pages as templates (e.g., `team-bob.html`)
4. Update the card's `href` attribute in `team.html` to link to the new profile
5. Add team member photo to `/images/` directory or use Unsplash portrait
6. Ensure consistent image sizing and styling

### Adding New Service Pages

When adding a new service detail page:

1. Create new HTML file: `[service-name].html` (lowercase, hyphen-separated)
2. Use existing service pages as templates (e.g., `assessment-centers.html`)
3. Follow the common structure: hero, overview, benefits, what's included, approach, who benefits, outcomes, why Tritalent, related services, CTA
4. Choose a consistent color theme for icons/accents
5. Add service card to `index.html` services Swiper carousel (around line 382)
6. Update footer services links across all pages
7. Add to related services sections on other service pages where appropriate

## Important Implementation Notes

### Section ID Naming
- **CRITICAL**: The "About Us" section uses `id="About Us"` with a space (not `id="about-us"`)
- All navigation links must use `index.html#About Us` (with space) to link correctly
- Other section IDs use lowercase with hyphens: `#home`, `#services`, `#why-us`, `#contact`

### Common Components to Maintain

When editing shared components, update across ALL 12 HTML files:

1. **Navigation Bar** (lines ~72-159 in most files):
   - Logo links to `index.html`
   - Active state styling for current page
   - Mobile menu structure must match desktop menu

2. **Footer** (lines ~650+ in most files):
   - Company info with logo and social links
   - Four-column layout: Quick Links, Services, Contact
   - Footer services links should include all 7 service pages
   - Copyright year: 2026

3. **Tailwind Configuration** (in `<head>`):
   - Must be identical across all pages
   - Custom colors: primary (#52A8A6), secondary (#3d8583), accent (#6bb9b7), dark (#1e293b), light (#f1f5f9)

### Placeholder Content

Some team member profiles are incomplete:
- Links to `team-member.html?id=[5-8]` or `team-david-thompson.html` (files don't exist yet)
- Team cards exist in `team.html` but profile pages need to be created using existing templates

### Active State Styling

Each page should highlight its active navigation item:
- `team.html`: "Team" link has `text-primary font-semibold` class
- Service pages: "Services" link has `text-primary` class
- Use appropriate classes in both desktop and mobile menus

## Browser Compatibility

The site uses modern CSS and JavaScript features:
- CSS Grid and Flexbox
- Intersection Observer API
- ES6+ JavaScript (const, let, arrow functions, template literals)
- No transpilation or polyfills included
- Targets modern browsers only (Chrome, Firefox, Safari, Edge latest versions)
