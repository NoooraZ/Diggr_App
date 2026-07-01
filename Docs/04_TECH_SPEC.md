# 04_TECH_SPEC.md

# Diggr — Technical Specification

Version: MVP v1

---

# 1. Overview

Diggr is a mobile-first vinyl discovery application.

The MVP focuses on helping users discover record stores that match their music taste.

This version is fully front-end driven.

All content should be rendered from static mock data.

No authentication or backend is required.

---

# 2. Tech Stack

Framework

- Next.js 15
- React 19
- TypeScript

Styling

- Tailwind CSS

UI

- shadcn/ui

Animation

- Framer Motion

Icons

- Lucide React
- Custom Vinyl Icons (SVG)

Fonts

- Editorial Serif (display)
- Inter (UI)

Package Manager

- pnpm

Deployment

- Vercel

Future Integrations

- Supabase
- Mapbox
- Spotify Preview API

---

# 3. Development Principles

The application should always prioritize:

Consistency over complexity.

Reusable components over duplicated code.

Readability over optimization.

The MVP should be fully functional using static data.

Avoid premature backend implementation.

---

# 4. Folder Structure

app/

components/

    album/

    explore/

    home/

    map/

    profile/

    saved/

    shared/

data/

hooks/

lib/

public/

    images/

    icons/

styles/

types/

docs/

---

# 5. Routing

/

Home

/store/[id]

Store Detail

/album/[id]

Album Detail

/explore

Explore

/saved

Saved

/profile

Profile

Future

/settings

/search

/log/new

---

# 6. Data Models

## User

Represents the current user.

Fields

- id
- name
- avatar
- city
- tasteTags
- bio
- savedStoreIds
- savedAlbumIds

---

## Store

Represents a physical record store.

Fields

- id
- name
- city
- country
- latitude
- longitude
- coverImage
- illustration
- matchScore
- dnaTags
- description

Relations

Store

↓

Recent Finds

↓

Albums

---

## Album

Albums only exist because they were discovered in stores.

Albums never exist independently.

Fields

- id
- title
- artist
- genre
- cover
- previewUrl (optional)
- storeId

---

## Treasure Log

Represents a successful discovery.

Fields

- id
- albumId
- storeId
- userId
- date
- price
- condition
- caption

Treasure Logs are the primary source of Recent Finds.

---

## Featured Channel

Represents a community entry on Explore.

Fields

- id
- title
- subtitle
- coverImage
- category

Examples

Soundtrack Lovers

Hidden Gems

Tokyo Guide

People Like You

Fresh Arrivals

---

# 7. Mock Data

Until backend exists,

all data must come from

/data

Files

users.ts

stores.ts

albums.ts

treasureLogs.ts

featuredChannels.ts

Never hardcode data inside components.

---

# 8. Component Architecture

Global Components

BottomNavigation

SearchPill

SectionHeader

TasteTag

MatchBadge

Avatar

VinylPin

Store Components

StoreCard

StoreHeader

StoreInfo

StoreDNA

RecentFindCard

AlbumCard

Explore Components

FeaturedChannelCard

CommunityCard

Saved Components

SavedStoreCard

SavedAlbumCard

Profile Components

TasteProfile

CollectionHighlight

StorePassport

All components should remain reusable.

---

# 9. Page Specifications

## Home

Purpose

Help users discover stores.

Contains

Treasure Map

Search

Recommendation Cards

Recent Finds

Bottom Navigation

Primary Action

Tap a Vinyl Pin.

---

## Store Detail

Purpose

Help users understand a store before visiting.

Contains

Store Header

Store DNA

Recent Finds

New Arrivals

People Like You

Primary Action

Save Store

---

## Album Detail

Purpose

Learn about a discovered record.

Contains

Album Cover

Album Information

Discovery Information

Audio Preview (optional)

Primary Action

Save Album

---

## Explore

Purpose

Browse communities.

Contains

Featured Channels

Recent Finds Feed

Primary Action

Open a Featured Channel

---

## Saved

Purpose

Collect stores and albums.

Tabs

Stores

Albums

Primary Action

Open Saved Store

---

## Profile

Purpose

Represent the user's collecting identity.

Contains

Profile Header

Statistics

Crate Profile

Collection Highlights

Primary Action

Edit Profile (Future)

---

# 10. Navigation Flow

Home

↓

Tap Vinyl Pin

↓

Store Preview

↓

Store Detail

↓

Album Detail

↓

Back

Navigation should remain shallow.

Maximum depth:

3 screens.

---

# 11. State Management

Current

React State

Future

Context

↓

Supabase

Global state should remain minimal.

Avoid Redux.

---

# 12. Animation Guidelines

Animation should feel subtle.

Preferred

Fade

Slide

Scale

Bottom Sheet

Avoid

Bounce

Elastic

Overshoot

Animation should support exploration,

never distract from content.

---

# 13. Responsive Behaviour

Primary Target

iPhone 16 Pro

390px width

Mobile First

Tablet

Not required

Desktop

Not required

---

# 14. Future Integrations

Mapbox

Real map rendering.

Supabase

Authentication

Saved Stores

Treasure Logs

Spotify

Album preview playback.

Recommendation Engine

People Like You

Store DNA

Match Score

will eventually become dynamic.

---

# 15. MVP Scope

Included

✓ Treasure Map

✓ Store Detail

✓ Album Detail

✓ Explore

✓ Saved

✓ Profile

✓ Static Data

✓ Basic Animations

Not Included

✗ Authentication

✗ Backend

✗ Real Inventory

✗ Upload Treasure Log

✗ Search Logic

✗ Recommendation Algorithm

✗ Push Notifications

---

# 16. Rules for AI

Always follow the Figma design.

Never redesign layouts.

Never invent additional pages.

Never introduce new navigation patterns.

Always build reusable components.

Always use static mock data first.

Maintain a calm, editorial visual language.

Consistency is more important than creativity.