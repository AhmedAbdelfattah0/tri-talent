# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML website for "HR Solutions Agency" - a professional HR services company. The site is built using vanilla HTML, CSS (via Tailwind CSS CDN), and JavaScript with no build process or framework.

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
├── index.html                      # Main landing page
├── team.html                       # Team overview page
├── team-bob.html                   # Individual team member profile (Managing Partner)
├── team-michael-chen.html          # Individual team member profile (Senior Consultant)
├── team-emily-rodriguez.html       # Individual team member profile (Recruitment Specialist)
└── CLAUDE.md                       # This file
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
- Services section with Swiper carousel (responsive grid)
- All major sections: #home, #About Us, #services, #why-us, #contact

**team.html**
- Team member grid (responsive: 1/2/3/4 columns)
- Hover effects on team cards with overlay animation
- Links to individual team member profile pages

**team-[name].html**
- Individual profile pages for team members
- Breadcrumb navigation
- Detailed bio, expertise, achievements, and contact info

### JavaScript Functionality

Each page includes:
- Mobile menu toggle
- Navbar shadow on scroll
- Smooth scroll for anchor links
- Swiper initialization (on pages with carousels)
- Intersection Observer animations (landing page)

### Responsive Design

Breakpoints follow Tailwind defaults:
- `sm`: 640px
- `md`: 768px
- `lg`: 1024px
- `xl`: 1280px

## Navigation Links

When modifying navigation, ensure consistency:
- Landing page sections use hash anchors: `index.html#section-id`
- Team page: `team.html`
- Individual profiles: `team-[firstname-lastname].html`

## Images

All images are sourced from Unsplash via CDN URLs. When adding new content:
- Use high-quality stock images (1920px width for heroes, 600px for portraits)
- Include descriptive `alt` attributes
- Maintain consistent image aspect ratios within component types

## Styling Conventions

- Use Tailwind utility classes exclusively (no custom CSS files)
- Custom styles are embedded in `<style>` tags in the `<head>`
- Animations use CSS transitions and keyframes
- Hover effects: `hover-lift` class for card components

## Adding New Team Members

When adding a new team member:

1. Add card to `team.html` in the grid section
2. Create individual profile page: `team-[firstname-lastname].html`
3. Use existing profile pages as templates
4. Update the card's `href` attribute to link to the new profile
5. Ensure consistent image sizing and styling

## Browser Compatibility

The site uses modern CSS and JavaScript features:
- CSS Grid and Flexbox
- Intersection Observer API
- ES6+ JavaScript

No transpilation or polyfills are included, so targeting modern browsers only.
