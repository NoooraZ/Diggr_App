# 02_PROJECT_RULES

## Overview

Diggr is a taste-driven vinyl discovery app.

It is NOT an e-commerce marketplace.

It helps vinyl collectors, treasure hunters, and beginners discover record stores that match their music taste.

The experience is inspired by:

- Letterboxd
- Monocle Travel Guides
- Vintage Editorial Maps

Core philosophy:

People discover stores.
Stores lead to discoveries.
Discoveries become memories.

Treasure hunting is always more important than shopping.

---

# Design Principles

Diggr should feel:

- Editorial
- Vintage
- Calm
- Minimal
- Tactile
- Collectible

Avoid:

- SaaS dashboards
- Bright gradients
- Heavy shadows
- Material Design
- Generic startup UI

The interface should feel like holding a beautifully printed city guide.

---

# Visual Language

Background

Warm Ivory

Primary

Black

Accent

Muted Burgundy

Typography

Editorial serif for headings.

Neutral sans-serif for interface text.

Lots of whitespace.

Rounded corners.

Soft borders.

Minimal decoration.

---

# Navigation

Bottom Navigation

4 tabs

- Map
- Explore
- Saved
- Profile

Transparent background.

Icons only.

Selected tab:

Black circular background

White icon

No labels.

---

# Product Philosophy

Diggr is about:

Finding places.

Not buying products.

The user journey is:

Taste

↓

Store

↓

Discovery

↓

Memory

Never redesign the flow into:

Search

↓

Product

↓

Checkout

Diggr is NOT Amazon.

---

# Core Loop

User opens Diggr.

↓

Discovers stores matching their taste.

↓

Sees Recent Finds.

↓

Visits the store.

↓

Finds a record.

↓

Logs the discovery.

↓

Returns to discover more.

---

# Information Architecture

Map

↓

Store

↓

Album

↓

Treasure Log

Explore

Saved

Profile

Navigation should always remain shallow.

Maximum depth:

3 levels.

---

# Components

The following components must always be reusable.

StoreCard

AlbumCard

RecentFindCard

SearchPill

TasteTag

MatchBadge

BottomNavigation

VinylPin

Avatar

CommunityCard

Never duplicate component implementations.

---

# Store

Store is the primary object.

Each store contains:

- name
- city
- location
- cover image
- illustration
- DNA tags
- match score
- recent finds
- new arrivals
- community recommendations

---

# Album

Album contains:

- title
- artist
- cover
- optional preview
- condition
- price
- store

Albums belong to stores.

---

# Treasure Log

Treasure Log represents a successful discovery.

It is NOT a review system.

Each log contains:

Album

Store

Condition

Price

Short note

Mood

Date

---

# Fake Data

Until backend is implemented:

Always use static mock data.

Never generate random placeholder content.

Use realistic record stores.

Use realistic album names.

Use realistic cities.

Maintain consistency across pages.

---

# Animation

Animations should feel subtle.

Preferred:

Fade

Scale

Slide

Bottom sheet

Avoid:

Bounce

Overshoot

Flashy transitions

Animation should support exploration.

Never distract.

---

# Coding Principles

Use:

Next.js

TypeScript

Tailwind CSS

shadcn/ui

Framer Motion

Prefer functional components.

Use reusable UI.

Avoid deeply nested components.

Keep components small.

---

# Folder Structure

app/

components/

data/

hooks/

lib/

types/

public/

styles/

---

# Naming

PascalCase

StoreCard.tsx

AlbumCard.tsx

RecentFindCard.tsx

camelCase

storeData.ts

albumData.ts

---

# Development Order

1.
Theme

2.
Design System

3.
Components

4.
Navigation

5.
Home

6.
Store

7.
Album

8.
Explore

9.
Saved

10.
Profile

11.
Interactions

12.
Backend

Never skip this order.

---

# Rules for AI

Do NOT redesign the product.

Do NOT invent new features.

Do NOT change the visual language.

Do NOT replace editorial aesthetics with modern SaaS UI.

Always follow the Figma design.

If implementation details are missing,

choose the simplest solution consistent with the existing design.

Consistency is more important than creativity.
