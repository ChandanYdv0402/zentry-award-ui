# Awards Website Front‑End Documentation

## Overview

This repository contains the front‑end code for an award‑winning interactive website.  Built with **React** and **Vite**, it showcases a highly polished user experience reminiscent of web‑based games and immersive landing pages.  The design uses video backgrounds, three‑dimensional tilt effects and GSAP animations to engage visitors and guide them through different product concepts.  Tailwind CSS and React‑Icons provide the styling and iconography, while **GSAP** (GreenSock Animation Platform) delivers scroll‑triggered transitions and dynamic interactions.

## Technology Stack

- **React 19** – component‑based UI framework used to build the user interface.
- **Vite** – development server and build tool with fast hot‑module replacement.
- **Tailwind CSS 3.4** – utility‑first CSS framework for rapid styling.
- **GSAP** (GreenSock) – animation library used for scroll triggers, clip‑path morphing and tilt effects.
- **React‑Icons** – icon library for social links and UI controls.
- **React Use** – collection of React hooks; here used for scroll detection.
- **clsx** – utility for conditional class names.
- **PostCSS & Autoprefixer** – build‑time CSS processing.

## Project Structure

```
Awards_website-main/
├─ README.md                – Top‑level readme (minimal)
├─ awards/                  – The actual React/Vite project
│  ├─ index.html            – Entry HTML file mounting the React app
│  ├─ package.json          – Defines scripts and dependencies
│  ├─ tailwind.config.js    – Tailwind theme customisation
│  ├─ vite.config.js        – Vite configuration
│  ├─ public/               – Static assets
│  │  ├─ audio/loop.mp3
│  │  ├─ fonts/             – Custom web fonts
│  │  ├─ img/               – Images used across the site (logos, backgrounds)
│  │  └─ videos/            – MP4 clips used in hero and feature sections
│  └─ src/
│     ├─ main.jsx           – Renders the React app into `#root`
│     ├─ App.jsx            – Top‑level component composing the page
│     ├─ index.css          – Tailwind directives and global styles
│     └─ components/        – Reusable React components
│        ├─ AnimatedTitle.jsx – Splits a title into words and animates them into view as the user scrolls.
│        ├─ Navbar.jsx        – Responsive navigation bar with scroll‑driven visibility and an audio toggle.
│        ├─ Hero.jsx          – Full‑screen hero section with video background, interactive thumbnail and GSAP‑controlled clip‑path morph.
│        ├─ About.jsx         – Section introducing the “Zentry” concept with animated title and scroll‑pinned image reveal.
│        ├─ Features.jsx      – Bento‑style grid of “cards” with tilt effects, video backgrounds and “coming soon” overlays.
│        ├─ Story.jsx         – Narrative section with 3D‑tilt image and call‑to‑action button.
│        ├─ Footer.jsx        – Footer with copyright, social links and privacy link.
│        ├─ Button.jsx        – Reusable button component supporting icons and custom classes.
│        └─ random.jsx        – Placeholder/test file (not used in the application).
└─ node_modules/            – Dependencies installed locally (not tracked in version control)
```

### Routing and State

The application is a **single‑page website**.  Navigation links in the `Navbar` point to anchors within the page (e.g., `#about`, `#story`), so there is no client‑side routing.  State is minimal and localised:

* **Hero.jsx** – tracks the index of the current and next video to implement a seamless video transition when the user hovers and clicks the mini video.
* **Features.jsx** – tracks cursor positions and hover state to create radial gradient highlights on “Coming soon” buttons.
* **Navbar.jsx** – uses `react‑use`’s `useWindowScroll` hook to hide or show the navbar depending on scroll direction and toggles audio playback.

### Animations

The site’s distinctive feel comes from sophisticated animations:

* **Scroll‑triggered clip‑path morph:** In `Hero.jsx` the GSAP `ScrollTrigger` plugin transforms the polygon clip‑path of the video container as the user scrolls, producing a dynamic shape reveal.
* **Animated titles:** `AnimatedTitle.jsx` splits HTML strings into words, wraps them in spans and animates their opacity and 3D rotation into view as they appear in the viewport.
* **3D tilt effects:** `Features.jsx` and `Story.jsx` listen to mouse movements and compute rotation angles to tilt cards or images towards the cursor, adding depth.
* **Pinned scrolling:** In `About.jsx`, a full‑screen image masked by a border radius expands as the user scrolls; GSAP’s `ScrollTrigger` pins the section and synchronises the animation timeline.

## Running the Project Locally

1. **Install dependencies:** Navigate into the `awards` directory and run:
   ```bash
   npm install
   ```
2. **Start the development server:**
   ```bash
   npm run dev
   ```
   Vite will start on a local port (default is `http://localhost:5173`) and support hot reloading.
3. **Build for production:**
   ```bash
   npm run build
   ```
   The compiled files will be output into the `dist/` directory.

## Notable Components and Features

### Navbar

* Responds to scroll direction: hides when scrolling down and shows when scrolling up.
* Contains links to sections of the single page.
* Includes an audio toggle button that plays a looping background track; visual indicator bars animate when audio is active.

### Hero Section

* Displays a full‑screen video background that morphs shape when scrolled.
* Offers a mini video preview that expands and swaps with the main video when clicked.
* Contains an overlay with product tagline and a call‑to‑action button (“Watch Trailer”).

### About Section

* Introduces the brand with animated typography and descriptive text.
* Uses a clip‑path animation to gradually reveal a full‑screen background image as the user scrolls.

### Features Section

* Arranges a grid of bento‑style cards.  Each card either plays a looped video or displays a placeholder panel.
* Cards tilt slightly towards the cursor (calculated via mouse coordinates).
* “Coming soon” cards show a radial gradient highlight following the cursor.

### Story Section

* Presents a narrative invitation into the lore behind the product.
* Features an interactive image that tilts in 3D according to cursor movement.

## Resume Highlights

If you’ve contributed to or replicated this project, here are some resume bullet points you could derive:

* **Developed an award‑winning interactive landing page** using **React** and **Vite**, showcasing immersive animations, video backgrounds and responsive design.
* Implemented complex **GSAP** animations, including scroll‑triggered clip‑path morphing, scroll‑pinned sections and dynamic text reveals.
* Built a **bento grid** of video cards with 3D tilt effects and cursor‑driven radial hover highlights to showcase product features.
* Integrated **Tailwind CSS** for rapid styling and custom design tokens, ensuring a polished and consistent aesthetic across all viewports.
* Added an **audio playback toggle** and responsive navigation bar that hides or reveals based on scroll direction, enhancing user engagement.
* Structured the project for maintainability by modularising components (`Hero`, `About`, `Features`, `Story`, `Footer`, etc.) and separating static assets into the `public/` directory.
* Utilised **React Hooks** and `react‑use` utilities for state management and scroll detection, ensuring smooth user interactions.

## Conclusion

This front‑end project demonstrates how modern web technologies can be combined to create a rich, game‑like experience on the web.  By using React for component architecture, Vite for efficient development, Tailwind for styling, and GSAP for animations, the site delivers an engaging narrative and highlights product concepts with cinematic flair.