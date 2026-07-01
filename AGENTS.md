# AGENTS.md

# Diggr AI Development Guide

Before making any implementation decisions, read the documentation in `/docs`.

Read in this order:

1. 01_PRD.md
2. 02_PROJECT_RULES.md
3. 03_DESIGN_DECISIONS.md
4. 04_TECH_SPEC.md
5. 05_WORLD.md
6. 06_CONTENT_GUIDE.md

These documents define the product.

If there is any conflict, follow them instead of making assumptions.

---

# Product Philosophy

Diggr is a vinyl discovery app.

It is NOT:

- an e-commerce platform
- Discogs
- Spotify
- Google Maps

Diggr helps people discover stores, not buy records.

Treasure hunting is the core experience.

---

# Design Philosophy

Follow the Figma design exactly.

Do not redesign layouts.

Do not introduce additional UI styles.

Do not replace the editorial aesthetic with modern SaaS UI.

The interface should feel like a beautifully printed travel guide.

---

# Development Rules

Always:

- Build reusable components.
- Keep components small and composable.
- Use TypeScript.
- Use Tailwind CSS.
- Prefer composition over duplication.

Never:

- Hardcode UI-specific values inside pages.
- Duplicate component implementations.
- Create unnecessary abstractions.

---

# Data

Until a backend exists:

Always use mock data from `/data`.

Never hardcode content directly inside components.

---

# Animation

Animations should be subtle.

Preferred:

- Fade
- Scale
- Slide
- Bottom Sheet

Avoid:

- Bounce
- Elastic
- Flashy transitions

---

# Future Features

These are intentionally excluded from the MVP:

- Authentication
- Backend
- Recommendation algorithm
- Upload flows
- Search logic
- Notifications

Do not implement them unless explicitly requested.

---

# If Requirements Are Unclear

Never invent product features.

Choose the simplest implementation that matches:

- PRD
- Figma
- Existing components

Ask for clarification rather than redesigning the product.

Consistency is more important than creativity.