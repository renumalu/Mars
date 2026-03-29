Here's the complete README content for your project:

---

# 🚀 Journey to Mars — Mission ARES VII

**An immersive, scroll-driven interactive web experience documenting humanity's first crewed mission to Mars.**

---

## 📋 Project Overview

Mission ARES VII is a cinematic, single-page scrollytelling experience built entirely in vanilla HTML, CSS, and JavaScript. It takes the viewer on a complete narrative journey — from launch briefing on Earth to touchdown on the Martian surface — through rich animations, interactive simulations, and live telemetry data.

---

## 🏆 Competition Criteria Coverage

### ✅ Story Structure (5+ Sections)
The experience is structured across **9 cohesive narrative sections**:

| # | Section ID | Phase | Description |
|---|-----------|-------|-------------|
| 1 | `#hero` | Launch | Cinematic opening with live countdown, animated rocket, and mission call-to-action |
| 2 | `#briefing` | Pre-Flight Dossier | Mission parameters, crew timeline, animated stat bars, and SVG Hohmann transfer orbit diagram |
| 3 | `#travel` | En Route | Spacecraft stats and interplanetary transit visualisation |
| 4 | `#globeSec` | Mars Globe | Interactive Three.js 3D Mars globe with drag, zoom, and data tabs |
| 5 | `#orbSec` | Orbit Simulator | Real-time Hohmann transfer calculator with launch animation |
| 6 | `#landing` | Entry Descent Landing | 7 Minutes of Terror — animated lander SVG and EDL step breakdown |
| 7 | `#exploration` | Surface Ops | Interactive map with POI markers, rover animation, and exploration cards |
| 8 | `#h-scroll-sec` | The Complete Journey | GSAP-pinned horizontal scroll through all 7 mission phases |
| 9 | `#conclusion` | Mission Accomplished | Mission legacy stats and restart prompt |

---

### ✅ Scroll-Based Interactions (4 effects)

1. **Hero Parallax** — The hero background glow and rocket translate on Y-axis as you scroll past, creating depth
2. **GSAP ScrollTrigger Reveals** — 10+ staggered element entrances tied to scroll position across every section
3. **Sticky Phase Tracker** — A persistent mission phase progress bar appears after the hero and tracks your current section as you scroll through the experience
4. **Horizontal Pinned Scroll** — The "Complete Journey" section pins to the viewport while 7 mission phase cards scroll horizontally — GSAP `scrub` tied directly to vertical scroll position

---

### ✅ Interactive Elements (8 elements)

1. **3D Mars Globe** — Three.js sphere with drag-to-rotate, scroll-to-zoom, touch support, and 4 data tabs (Overview, Geography, Atmosphere, Moons)
2. **Orbital Trajectory Simulator** — Three sliders (launch window, spacecraft mass, animation speed) drive a real-time Hohmann transfer canvas simulation with Δv and fuel calculations
3. **Interactive Map POIs** — 5 clickable mission site markers on the Mars surface map with animated panels revealing geological and mission data
4. **Draggable Mission Telemetry HUD** — Drag anywhere on screen, minimise, or close; shows live O₂, fuel, power gauges and a velocity graph
5. **Mission Log Panel** — Toggleable live log of 16 timestamped mission events that drip-feed in real time every 5 seconds
6. **Ambient Audio Toggle** — Web Audio API generates a layered deep-space drone (4 oscillators with LFO modulation); smooth 1.5s fade in/out
7. **Colour Theme Toggle** — Switches between Mars Red and Cosmic Purple CSS variable themes with a brightness flash transition
8. **Warp Jump Button** — Cinematic hyperspace streak animation warps you to a random section

---

### ✅ Animations (6+ distinct animations)

1. **Loader Sequence** — Three concentric spinning rings with staggered speeds, animated progress bar, and cycling phase text
2. **Animated Starfield** — Canvas-rendered 400-star parallax field with layered depth, twinkling, and two subtle nebula gradients
3. **SVG Rocket Flame** — CSS keyframe flicker on the flame ellipse, combined with a floating hover loop
4. **SVG Path Draw** — The Hohmann transfer orbit arc in the Mission Briefing draws itself stroke-by-stroke on scroll enter, with a spacecraft dot animating along the path
5. **Text Scramble + Glitch** — Key headings wrapped in `.glitch-wrap` trigger a character-scramble effect on hover and CSS clip-path glitch pulses on a randomised timer
6. **Cinematic Warp Streaks** — 180-point radial streak canvas animation with colour shift from cyan to gold, plus letterbox bars
7. **Section Colour Flash** — A tinted overlay briefly pulses in on each section entry, colour-matched to that section's theme

---

### ✅ Responsive Design

| Breakpoint | Behaviour |
|-----------|-----------|
| `> 900px` | Full two-column layouts for Travel and Landing sections; 380px globe |
| `600px – 900px` | Columns stack; briefing timeline goes horizontal with overflow scroll; 2-col exploration cards; 280px globe |
| `< 600px` | Single column everything; custom cursor hidden; HUD expands full width; all font sizes clamped; buttons stack vertically |

All canvas elements (orbital simulator, velocity graph, Three.js globe) recalculate dimensions on every resize event with proper DPR handling.

---

### ✅ Code Quality

- **CSS custom properties** defined in `:root` with descriptive comments — `--mr` (Mars Red), `--ac` (Accent Cyan), `--dg` (Deep Green), `--ds` (Deep Space), etc.
- **Logical section separation** — every JS block is labelled with a banner comment (`// ══ SECTION NAME ══`)
- **IIFEs** used for all self-contained feature modules to prevent global scope pollution
- **Passive event listeners** on all scroll and touch handlers for performance
- **No dependencies** beyond GSAP 3, Three.js r134, and Google Fonts — no build step required

---

## 🎯 Bonus Features

### ♿ Accessibility
- `<a href="#hero" id="skip-link">` skip-to-content link for keyboard/screen reader users
- 27 `aria-label` attributes across all interactive controls
- `role="navigation"`, `role="progressbar"`, `role="log"`, `role="list"` semantic roles
- `*:focus-visible` high-contrast outline for keyboard navigation
- **Arrow key section navigation** — `↑` / `↓` scrolls between sections without a mouse

### 🎮 Performance
- `will-change: transform` on parallax layers
- `passive: true` on all scroll/touch listeners
- Three.js pixel ratio capped at `Math.min(devicePixelRatio, 2)`
- Canvas resize uses `ctx.setTransform(1,0,0,1,0,0)` before re-scaling to prevent accumulated transform drift

### 🌀 `prefers-reduced-motion`
Full media query disables **all** CSS animations, transitions, and keyframe durations for users who have enabled reduced motion in their OS accessibility settings — no content is hidden, only motion is removed.

### 🕹️ Konami Code Easter Egg
Type `↑ ↑ ↓ ↓ ← → ← → B A` on your keyboard to unlock a **Classified Mission Dossier** — triggers a 50-particle burst across the screen and reveals a hidden panel.

---

## 🛠️ Technical Stack

| Technology | Usage |
|-----------|-------|
| **HTML5** | Semantic structure, canvas elements, SVG inline graphics |
| **CSS3** | Custom properties, Grid, Flexbox, clip-path, backdrop-filter, keyframe animations |
| **Vanilla JS (ES6+)** | All interactivity, canvas rendering, Web Audio API, IntersectionObserver |
| **GSAP 3.12** | ScrollTrigger, TextPlugin, timeline sequencing, scrub-based horizontal scroll |
| **Three.js r134** | 3D Mars globe with procedural texture, bump map, atmosphere layers, Phobos moon |
| **Web Audio API** | Procedural ambient drone with 4 oscillator layers and LFO modulation |
| **Google Fonts** | Orbitron (display), Space Mono (monospace data), Exo 2 (body) |

---

## 🚀 Running the Project

No build step, no server required.

```bash
# Simply open the file in any modern browser
open mars-journey-final.html

# Or serve locally for full feature support
npx serve .
python3 -m http.server 8080
```

**Browser support:** Chrome 90+, Firefox 88+, Safari 15+, Edge 90+

> **Note:** Web Audio API requires a user gesture (click) before audio context can start — this is handled automatically by the audio toggle button.

---

## 📁 File Structure

```
mars-journey-final.html     # Single self-contained file — all HTML, CSS, JS inline
```

All assets are either procedurally generated (Mars texture, starfield, warp canvas) or loaded from CDN (GSAP, Three.js, Google Fonts). There are no local asset dependencies.

---

## 👨‍🚀 Sections at a Glance

```
HERO → BRIEFING → TRAVEL → MARS GLOBE → ORBIT SIM → LANDING → EXPLORATION → JOURNEY → CONCLUSION
 §1      §2         §3        §4            §5          §6          §7           §8         §9
```

*Humanity's greatest voyage. 225 million kilometres. One red horizon that will change everything.*
