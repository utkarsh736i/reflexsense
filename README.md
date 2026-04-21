# ReflexSense — Next.js App

## Tech Stack
- **Next.js 15** (App Router)
- **React 19**
- **TypeScript**
- **Tailwind CSS**
- No external UI libraries — all charts are SVG sparklines built in-house

## Project Structure
```
src/
  app/
    page.tsx          ← Landing page (full homepage)
    login/page.tsx    ← Login page
    dashboard/page.tsx← Dashboard (live sensor monitoring)
    contact/page.tsx  ← Contact page
    globals.css       ← All CSS variables, animations, shared styles
    layout.tsx        ← Root layout
  components/
    NeuralCanvas.tsx  ← Animated neural network background
    Cursor.tsx        ← Custom cursor (desktop only)
    Nav.tsx           ← Shared navigation bar
  lib/
    useReveal.ts      ← Scroll-based reveal animation hook
```

## Getting Started

### 1. Install dependencies
```bash
npm install
```

### 2. Run development server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000)

### 3. Build for production
```bash
npm run build
npm start
```

## Pages
| Route | Description |
|-------|-------------|
| `/` | Landing page with hero, stats, dashboard showcase, ROI section, personas, AI tech, features, how it works, industries |
| `/login` | Split-panel login with live metrics preview |
| `/dashboard` | Full industrial dashboard — add machines, add sensor widgets, connect to live API or run Demo Mode |
| `/contact` | Contact form, system status, office locations, FAQ |

## Dashboard Features
- **Add Machines** — name, color, API URL, machine ID
- **Add Sensor Widgets** — temperature, vibration, humidity, light, pressure, current, RPM, or custom
- **Widget Sizes** — Small, Medium, Large, Full Width
- **Chart Types** — Line sparkline, Bar, Gauge (all SVG, no Chart.js dependency)
- **Demo Mode** — simulates live sensor data with realistic sine-wave patterns
- **Live Mode** — polls any REST API endpoint (your ngrok FastAPI server)
- **CSV Export** — downloads all sensor readings
- **Edit Mode** — configure, resize, or remove widgets
- **Persistent storage** — machines and layout saved in localStorage

## Connecting to your ReflexSense hardware
1. Run your FastAPI server on the Raspberry Pi Pico W (RP2040)
2. Start ngrok: `ngrok http 8000`
3. Copy the ngrok URL
4. In the dashboard, paste the URL into "Gateway URL" and click **Connect**

Your API should return JSON like:
```json
{
  "temperature": 68.4,
  "vibration": 12.3,
  "humidity": 55.1,
  "ldr": 620,
  "pressure": 7.2,
  "current": 9.8,
  "rpm": 2800
}
```

## Mobile Support
- Fully responsive across all pages
- Navigation collapses to hamburger menu on mobile
- Custom cursor disabled on touch devices
- Dashboard sensor grid reflows to single column
- All grids stack vertically on small screens

## Customisation
Edit `src/app/globals.css` CSS variables at the top to change the entire color theme:
```css
:root {
  --neural:  #00d4e8;   /* primary teal accent */
  --pulse:   #6c9fff;   /* secondary blue accent */
  --void:    #020610;   /* darkest background */
  /* ... */
}
```
