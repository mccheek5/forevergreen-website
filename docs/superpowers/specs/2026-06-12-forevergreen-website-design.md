# Forevergreen Landscape Management — Website Design Spec

**Date:** 2026-06-12

## Overview
A static informational website for Forevergreen Landscape Management (Forever Green Lawn Care, LLC), a lawn care and landscaping company based in Harrodsburg, Kentucky. Built with HTML + Tailwind CSS, hosted on Netlify via GitHub. Follows the same pattern established for the CDP freelance site.

## Pages
- **Home** (`index.html`) — Hero with logo/tagline and call-to-action button, highlights of key services, services summary, footer
- **Services** (`services.html`) — Cards for each service: Lawn Mowing, Mulching, Landscaping Design, Trimming, Crabgrass Control
- **About** (`about.html`) — Company intro, owner Willie Cheek, based in Harrodsburg KY
- **Contact** (`contact.html`) — Phone: (859) 734-0202, Email: forevergreen36@yahoo.com, Location: Harrodsburg KY, hours (placeholder)

## Visual Style
- **Background:** White (primary page background)
- **Primary color:** Dark green `#2d6a2d` — headings, navbar, footer, buttons
- **Accent:** Gold/orange `#f5a623` — highlights, hover states, CTA buttons
- **Text:** Dark grey `#333333` — body copy
- **Typography:** Clean and professional — bold headings, readable body text
- **Feel:** Fresh, natural, trustworthy — light and open

## Navigation
Sticky top navbar — logo left, links right. Mobile hamburger menu. White background, dark green text, gold hover/active states.

## Architecture
- Pure static — HTML + Tailwind CSS via CDN
- No JavaScript framework, no backend
- One `css/custom.css` for any overrides
- Deployed: GitHub repo → Netlify auto-deploy on push

## File Structure
```
ForeverGreen/
├── index.html
├── services.html
├── about.html
├── contact.html
├── css/
│   └── custom.css
└── img/
    └── ForeverGreenLandscapeLogo.png
```

## Contact Info
- **Owner:** Willie Cheek
- **Phone:** (859) 734-0202
- **Email:** forevergreen36@yahoo.com
- **Location:** Harrodsburg, Kentucky

## Out of Scope (for now)
- Quote/contact form (add later with Netlify Forms)
- Backend or CMS
- Gallery/portfolio of past work
