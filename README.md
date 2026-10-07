<picture>
  <source media="(prefers-reduced-motion: reduce)" srcset="assets/readme-banner.svg">
  <img src="assets/readme-banner.gif" alt="Goexz — Developer. Websites, APIs and game systems. Close to the metal." width="100%">
</picture>

<h1 align="center">Developer Portfolio</h1>

<p align="center">Big type. Glass fragments. Motion you can control.</p>

<p align="center">
  <a href="#motion">Motion</a> ·
  <a href="#stack">Stack</a> ·
  <a href="#run-locally">Run locally</a> ·
  <a href="#deploy-on-vercel">Deployment</a>
</p>

![Built with React, TypeScript, Tailwind CSS, GSAP, Vite and Vercel](assets/project-stack.svg)

I built this portfolio with React and TypeScript and made scrolling part of the design. My name breaks into glass-like pieces, travels across the screen, then sweeps to the sides before **“Close to the metal.”** appears. The rest of the page uses smaller movements and settles into place so the content stays easy to read.

## Motion

| Scene | What happens |
| :--- | :--- |
| **Shatter → scatter → sweep** | SVG polygon masks cut the actual letters into fragments. Canvas draws the pieces while GSAP controls their stagger, rotation and travel. |
| **Languages take the stage** | Large language names enter from alternating sides and settle as you scroll. |
| **Continuous light sweep** | A soft highlight passes over the language heading and labels on a loop. |
| **Projects stack** | Cards form a sticky stack on desktop and become regular rows on smaller screens. |
| **Quieter reading** | Text and card content reveal once, then stop moving. |
| **Motion controls** | A toggle reduces movement. The page also follows the device’s reduced-motion preference. |

## Stack

| Tool | Role |
| :--- | :--- |
| **React 19 + TypeScript 5** | Components, typed data and UI state |
| **Tailwind CSS 4 + custom CSS** | Layout, responsive type, hover effects and light sweeps |
| **GSAP 3 + ScrollTrigger** | Scroll progress, staggered entrances and animation timelines |
| **SVG + Canvas 2D** | Polygon masks and the fragment renderer |
| **Vite 8** | Local development and the static production build |
| **Archivo + Source Code Pro** | Locally hosted display and monospace fonts |
| **Vercel** | Hosting, connected to my own domain |

## Run locally

Use **Node.js 22.13+**. Run these commands in the folder containing `package.json`:

```bash
npm install -g pnpm@11.25.0
pnpm install --frozen-lockfile
pnpm dev
```

Open the URL printed in the terminal.

| Command | Purpose |
| :--- | :--- |
| `pnpm dev` | Start the development server |
| `pnpm typecheck` | Check TypeScript |
| `pnpm build` | Check TypeScript and generate `dist/` |
| `pnpm preview` | Preview the production build locally |

## Deploy on Vercel

Import the repository into Vercel and use the directory containing `package.json` as the project root.

| Setting | Value |
| :--- | :--- |
| Framework preset | **Vite** |
| Install command | `pnpm install --frozen-lockfile` |
| Build command | `pnpm run build` |
| Output directory | `dist` |
| Node.js | **22.x**, using 22.13+ |
| Environment variables | None required for this portfolio |

After deployment, connect your domain through the Vercel project’s domain settings.

The production output is static: `index.html`, bundled assets and local fonts. Keep the contents of `dist/` together when uploading to another static host. Use `pnpm preview` to inspect the build locally.

[Vercel’s Vite deployment guide](https://vercel.com/docs/frameworks/frontend/vite)

## Where to edit

| File | Change here |
| :--- | :--- |
| [`src/App.tsx`](src/App.tsx) | Intro, languages, project descriptions, links and motion toggle |
| [`src/globals.css`](src/globals.css) | Colors, spacing, typography, responsive layout and light sweeps |
| [`src/components/text-fragments-canvas.tsx`](src/components/text-fragments-canvas.tsx) | Polygon fragments, the texture atlas and Canvas rendering |
| [`src/lib/scroll-motion.ts`](src/lib/scroll-motion.ts) | Timing of the hero’s scatter and sweep phases |
| [`src/lib/section-motion.ts`](src/lib/section-motion.ts) | Text reveals, section entrances and subtle heading drift |
| [`public/fonts/`](public/fonts/) | Local fonts and their license files |

<details>
<summary><strong>A closer look at the animation</strong></summary>

The fragment renderer waits for the fonts to load, measures the letters and cuts their shapes with SVG polygon masks. It bakes those pieces into a texture atlas, so it can reuse the images during Canvas redraws.

ScrollTrigger updates the hero’s progress. Each shard has its own direction, distance, delay and spin. After scattering, the shards travel to the sides and make room for the next heading.

Animation setup and event listeners are cleaned up when the component unmounts or motion settings change. Project content also becomes visible immediately when reached by keyboard focus.

</details>

---

<p align="center">
  Built by <a href="https://github.com/Goexz"><strong>Goexz</strong></a><br>
  <sub>From a click on a screen to the logic gates underneath.</sub>
</p>
