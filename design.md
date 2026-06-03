# FEMCS UI Design System

This document defines the visual direction for the Fire Extinguisher Management System. Future UI work should follow this file so the app stays consistent instead of drifting back to a generic admin dashboard.

## Core Direction

- Theme: industrial fire-safety operations
- Mood: urgent, controlled, field-ready
- Avoid: bright blue dashboards, generic SaaS gradients, soft pastel admin styling
- Aim for: warm charcoal surfaces, extinguisher red accents, sand-colored support tones, strong hierarchy

## Brand Intent

- The app should feel like a control surface for extinguisher readiness and compliance.
- Red is the primary emphasis color because it is semantically tied to fire extinguishers and alarms.
- Dark backgrounds should feel grounded and operational, not neon or cyberpunk.
- Secondary tones should support the main red, not compete with it.

## Color System

Use the tokens in [frontend/src/index.css](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/index.css).

Primary tokens:

- `--bg`: deep charcoal-brown application background
- `--bg-card`: elevated dark surface for cards and tables
- `--bg-hover`: darker hover surface
- `--accent`: extinguisher red
- `--accent-strong`: brighter active red for CTAs and focus moments
- `--accent-ink`: light warm text used on emphasized red states
- `--sand`: warm support tone for straps, labels, and secondary brand moments
- `--success`: green for compliant and complete states
- `--warning`: amber for upcoming risk
- `--danger`: red-orange for failure and overdue states
- `--orange`: strong warning state between amber and danger

Rules:

- Do not reintroduce blue as a primary theme color.
- Use red for primary action and navigation emphasis.
- Use amber for warnings and upcoming expirations.
- Use green only for success and compliant states.
- Keep text warm off-white, never cold blue-white.

## Typography

- Display font: `Syne`
- UI/body font: `Manrope`

Rules:

- Headings should feel compact and assertive.
- Body text should remain readable and practical.
- Uppercase micro-labels are encouraged for section straps, tags, and operational metadata.
- Avoid mixing in extra font families unless there is a strong reason.

## Layout Principles

- Main app shell:
  - fixed left navigation
  - sticky top bar
  - roomy page gutters
  - layered dark surfaces
- Auth pages:
  - split layout with a brand panel and a form panel
  - the brand panel should explain context, not just hold a logo
- Dashboard:
  - open with an operational hero surface
  - follow with summary metrics
  - then move into task-oriented details such as expiring units and inspection activity

## Component Rules

### Sidebar

- Should feel like a field command rail, not a generic menu.
- Active navigation uses red-tinted backgrounds and warm text.
- Include a short operational note under the product mark.

### Topbar

- Keep translucent and dark.
- Show current page title plus one line of operational context.
- Role chip should be subtle but visible.

### Cards

- Use layered gradients and soft borders.
- Rounded corners should stay in the 14px to 22px range.
- Hover states should lift slightly, not jump dramatically.

### Buttons

- Primary button:
  - red gradient
  - warm light text
  - slight lift on hover
- Secondary button:
  - dark surface
  - bordered
  - never brighter than primary

### Tables

- Dark table surfaces with clear borders
- Warm muted headers
- Hover states should brighten slightly
- Monospace values should remain for codes and IDs

### Reports

- Reports should read like review documents, not raw query dumps.
- Start with a clear report header:
  - institution
  - report title
  - generator identity
  - generation timestamp
  - total records
- Applied filters should appear as restrained chips or metadata pills, not one long raw sentence where possible.
- Data tables should use:
  - clear row separation
  - subtle zebra striping
  - readable line height
  - stable first-column indexing when scanning long result sets
- Styling should stay restrained:
  - dark elevated surfaces
  - sand or muted text for metadata
  - red reserved for primary emphasis, not every table detail

### Forms

- Inputs remain dark and bordered
- Focus state uses red glow, not blue glow
- Labels are uppercase micro-labels

### Modals

- Elevated dark surfaces
- Sticky header
- Comfortable spacing
- Same palette as the main app, not a separate theme

## Dashboard-Specific Rules

- Lead with readiness, not analytics for analytics' sake.
- First impression should answer:
  - how many units are critical
  - how many inspections are pending
  - how many facilities are covered
  - what needs immediate action
- Metrics should feel operational, not decorative.

## Icon Usage

- Prefer fire, shield, inspection, wrench, and alert metaphors.
- Keep icon color tied to the same semantic palette as the surrounding element.
- Avoid random accent colors on icons.

## Motion

- Use subtle transitions only:
  - hover lift
  - border shift
  - gentle glow on active states
- Avoid playful bouncy motion.
- The product should feel precise and controlled.

## Content Tone In UI

- Labels should be direct and operational.
- Use terms like:
  - readiness
  - compliance
  - inspection
  - maintenance
  - escalation
  - inventory
- Avoid vague marketing phrasing inside the application shell.

## What To Avoid

- Blue-led themes
- Purple accents
- Flat white cards
- Generic SaaS hero copy
- Overuse of gradients on every surface
- Excessively rounded toy-like controls
- Tiny low-contrast metadata

## Implementation Reference

The current source of truth for this design system is:

- [frontend/src/index.css](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/index.css)
- [frontend/src/components/Layout.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/components/Layout.js)
- [frontend/src/pages/DashboardPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/DashboardPage.js)
- [frontend/src/pages/LoginPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/LoginPage.js)
- [frontend/src/pages/RegisterPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/RegisterPage.js)
- [frontend/src/pages/ForgotPasswordPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/ForgotPasswordPage.js)
- [frontend/src/pages/ResetPasswordPage.js](/abs/path/C:/Users/RCA/ne_prep/NE_prep/restfull/FEMS/frontend/src/pages/ResetPasswordPage.js)

When adding a new page or reworking an existing one, start here before inventing new colors, spacing rules, or component patterns.
