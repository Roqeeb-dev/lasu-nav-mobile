# Campus Nav (LASU Navigator Mobile)

A Google Maps–style navigation app for campus — search buildings, get walking directions, follow live turn-by-turn navigation, and ask an AI guide anything about campus. Built as the mobile evolution of the original LASU Navigator web app.

## Why I built this

LASU Navigator started as a web-based Web-GIS project for my final year, helping students find their way around a large, unfamiliar campus. This mobile version takes that further — real GPS-based navigation, live turn-by-turn directions, and an AI assistant that can answer questions about campus facilities, not just show pins on a map.

## Features

- **Search & explore** — find buildings and facilities by name or category, with filters (Faculties, Admin, etc.)
- **Get directions** — walking, biking, and shuttle route options between any two campus points
- **Live turn-by-turn navigation** — real-time position tracking with step-by-step instructions as you walk
- **Ask LASU Nav** — an AI-powered campus guide that answers questions about buildings, hours, and directions in natural language
- **Saved places** — bookmark frequently visited locations
- **Dark mode support**

## Tech Stack

- **React Native (Expo)** — core framework
- **Expo Router** — file-based navigation
- **TypeScript** — throughout
- **react-native-maps** — map rendering and route visualization
- **expo-location** — live GPS tracking and permissions
- **expo-sensors** — device heading/compass for navigation orientation
- **ngraph.graph / ngraph.path** — custom pathfinding (A\*) over a self-built campus path graph
- **Zustand** — navigation session and map state management
- **TanStack Query** — data fetching and caching
- **Supabase** — campus place data, saved locations, backend
- **@gorhom/bottom-sheet** — destination preview cards
- **Anthropic/OpenAI API** — the "Ask LASU Nav" AI assistant

## How routing works

Public directions APIs (Google, Mapbox) don't know about internal campus footpaths, so this app uses a **custom-built path graph** — nodes representing junctions, gates, and building entrances, connected by edges representing walkable paths. Routes are calculated using the A\* pathfinding algorithm over this graph, with the user's live GPS position continuously snapped to the nearest path for real-time turn-by-turn guidance.

## What I learned / technical challenges

- Building and modeling a custom path graph from real campus coordinates
- Implementing A\* pathfinding for shortest-route calculation
- Live GPS tracking, position-snapping, and off-route detection
- Managing a long-running navigation session's state (current step, ETA, deviation)
- Integrating an LLM-powered assistant with structured campus data as context

## Screenshots / Demo

_(Add screenshots or a screen recording here once available)_

## Getting Started

```bash
git clone <repo-url>
cd lasu-nav-mobile
npm install
npx expo start
```

Scan the QR code with Expo Go, or press `a` / `i` for an Android/iOS simulator.

### Environment Variables

Create a `.env` file with:

```
EXPO_PUBLIC_SUPABASE_URL=your_supabase_url
EXPO_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
EXPO_PUBLIC_MAPS_API_KEY=your_maps_api_key
```

## License

MIT
