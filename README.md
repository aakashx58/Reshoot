# Reshoot

Reshoot turns one skincare product photo into campaign-grade beauty shoots, styled product scenes, and motion.

## Overview

This repository contains a Vite + React + TypeScript web app for the **Reshoot** experience. The current UI is primarily implemented in [`index.html`](index.html) (including GSAP/ScrollTrigger/SplitType animations loaded via CDN), with a minimal React entry in [`src/main.tsx`](src/main.tsx) and [`src/App.tsx`](src/App.tsx).

## Tech stack

- **Frontend:** React 19, TypeScript
- **Build tooling:** Vite 8
- **Styling:** Tailwind CSS v4 (`@tailwindcss/vite`)
- **Animations/UI libs in page:** GSAP, ScrollTrigger, SplitType (CDN scripts in `index.html`)
- **AI integration (dependency/config):** `@google/genai`, `GEMINI_API_KEY` environment variable

## Prerequisites

- [Node.js](https://nodejs.org/) (LTS recommended)
- npm (included with Node.js)
- A Gemini API key (if you plan to use Gemini-powered features)

## Getting started

1. **Install dependencies**
   ```bash
   npm install
   ```

2. **Configure environment variables**
   Copy [`.env.example`](.env.example) to `.env` and set the required values:
   ```env
   GEMINI_API_KEY="your_api_key_here"
   APP_URL="http://localhost:3000"
   ```

3. **Start the development server**
   ```bash
   npm run dev
   ```
   By default the app runs at [http://localhost:3000](http://localhost:3000) (see [`package.json`](package.json)).

## Available scripts

| Script | Command | Description |
| --- | --- | --- |
| `dev` | `npm run dev` | Start Vite dev server (`--port=3000 --host=0.0.0.0`) |
| `build` | `npm run build` | Create a production build in `dist/` |
| `preview` | `npm run preview` | Preview the production build locally |
| `lint` | `npm run lint` | Run TypeScript type-checking (`tsc --noEmit`) |
| `clean` | `npm run clean` | Remove `dist` and `server.js` |

## VS Code debugging

A ready-to-use launch configuration is included in [`.vscode/launch.json`](.vscode/launch.json):

- **Run Dev Server (npm)** — starts `npm run dev` in the integrated terminal
- **Launch Chrome (localhost:3000)** — launches Chrome against the Vite dev server
- **Launch Edge (localhost:3000)** — launches Edge against the Vite dev server

Typical workflow:
1. Run **Run Dev Server (npm)** (or start `npm run dev` manually).
2. Start **Launch Chrome (localhost:3000)** or **Launch Edge (localhost:3000)** to debug client-side code.

## Project structure

```text
.
├─ .vscode/
│  └─ launch.json        # VS Code debug/run configurations
├─ public/               # Static public assets
├─ src/
│  ├─ App.tsx            # React app component (currently minimal)
│  ├─ main.tsx           # React entry point
│  └─ index.css          # Global styles
├─ .env.example          # Environment variable template
├─ index.html            # Main HTML document and page implementation
├─ package.json          # Dependencies and npm scripts
├─ tsconfig.json         # TypeScript configuration
├─ vite.config.ts        # Vite configuration
└─ metadata.json         # App metadata/description
```

## Notes

- Production builds copy `src/assets` into `dist/src/assets` via a custom Vite plugin in [`vite.config.ts`](vite.config.ts) so root-relative asset URLs continue to resolve.
- If dependency installation fails with an `ERESOLVE` conflict, ensure `devDependencies.esbuild` is compatible with the installed Vite version (Vite 8 expects `esbuild@^0.27.0 || ^0.28.0`).
