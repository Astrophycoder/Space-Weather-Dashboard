# 🌞 Space Weather Dashboard

> **μLearn Space Weather Dashboard Challenge**  
> `#evn-sp-spaceweather` · **100 Karma**

Space weather is easy to imagine as something that happens *out there*.

A flare erupts on the Sun. Solar plasma travels through space. Earth's magnetic environment responds. Somewhere much closer to us, a satellite operator sees a warning, a radio link becomes unreliable, or a navigation system starts behaving differently.

The interesting part is the chain in between.

This project turns that chain into something you can actually watch.

The **Space Weather Dashboard** is a responsive, interactive instrument console that brings together recent solar-wind and geomagnetic measurements and presents them as a single Sun–Earth story.

Rather than treating space weather as a collection of numbers, the dashboard is designed around a simple question:

> **What is happening between the Sun and Earth right now, and why does it matter?**

---

## 🌞 From the Sun to Earth

The dashboard follows the basic progression of a space-weather event:

```text
                    ☀ SUN
                      │
                      │  Solar wind
                      ▼
              ┌───────────────┐
              │  SPACE        │
              │  ENVIRONMENT  │
              └───────────────┘
                      │
                      │  IMF / plasma interaction
                      ▼
                   🌍 EARTH
                      │
                      ▼
             GEOMAGNETIC RESPONSE
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
       Satellites   Navigation    Radio
```

The central visualisation gives this process a physical presence, while the surrounding instruments expose the measurements behind it.

---

## 📡 What are we actually measuring?

The dashboard focuses on the parameters that help describe the near-Earth solar-wind environment and its geomagnetic response.

### Solar-wind velocity

How fast the solar wind is moving past Earth.

A change in solar-wind speed can be part of the changing conditions that drive disturbances in near-Earth space.

### Proton density

How much solar-wind plasma is present.

Velocity alone does not tell the whole story. The density of the incoming plasma helps describe the environment interacting with Earth's magnetic field.

### Interplanetary Magnetic Field — Bz

The north–south component of the interplanetary magnetic field.

Bz is particularly important when thinking about how the solar wind couples to Earth's magnetosphere.

### Planetary Kp index

A global measure of geomagnetic activity.

Instead of leaving Kp as an unexplained number, the dashboard translates it into an intuitive state:

**QUIET → ACTIVE → STORM → SEVERE**

The result is something that can be read at a glance without losing the underlying measurement.

### Recent trends

A single measurement is a snapshot.

The dashboard therefore also shows recent solar-wind and Kp behaviour as time-series plots, making it possible to see whether conditions are relatively steady or changing.

---

## 🎛️ Why does it look like an instrument?

Most dashboards are designed to disappear into the background.

This one is deliberately different.

The interface takes inspiration from **scientific instruments, spacecraft consoles and observatory equipment**. Instead of a collection of floating cards, the information is housed inside a physical-looking control panel.

There are:

- machined-metal surfaces
- recessed displays
- screws and mounting points
- beveled instrument bezels
- physical knobs
- toggle switches
- analogue gauges
- LCD/CRT-inspired readouts
- layered depth and mechanical shadows

The goal is not decoration for its own sake.

Space weather is an observational problem. The interface is therefore designed to feel like an instrument built to observe it.

The dashboard should feel less like:

> *“Here is a webpage with some space-weather numbers.”*

and more like:

> *“Here is the console. What is the environment doing?”*

---

## 🛰️ The Sun–Earth display

At the centre of the dashboard is an animated visual model connecting the Sun, the solar-wind stream and Earth's magnetosphere.

The visualisation shows:

- a continuously animated solar corona
- solar-wind particles travelling outward
- Earth's magnetic environment
- a changing magnetospheric boundary
- a deep-space background
- orbital/reference elements

This is intentionally a **visual abstraction**, not a scale-accurate physical simulation.

Its purpose is to make the relationship between the measurements understandable.

When the surrounding instruments report a changing environment, the centre of the dashboard gives that environment a visual context.

---

## 🌍 Why should we care?

Space weather does not stop at the edge of the atmosphere.

Its effects can reach the technologies we depend on.

One example is **GNSS navigation**.

Signals from navigation satellites have to travel through Earth's ionosphere before reaching a receiver. Space-weather-driven disturbances can change the ionospheric conditions through which those signals propagate, potentially degrading positioning and timing performance.

That matters for systems that depend on reliable navigation and timing.

The same broader space-weather environment can also affect:

- 🛰️ **Satellites** — radiation exposure, spacecraft charging and changes in atmospheric drag
- 📻 **Radio communication** — particularly HF radio propagation
- 🧭 **Navigation systems** — changes in ionospheric conditions can affect GNSS performance
- ⚡ **Power infrastructure** — strong geomagnetic disturbances can induce currents in long conductors

So the point of the dashboard is not simply to answer *“What is the Kp value?”*

It is to connect the measurement to the environment — and the environment to something happening here on Earth.

---

## 🔌 Where does the data come from?

The dashboard uses publicly available measurements from the **NOAA Space Weather Prediction Center (SWPC)**.

The current implementation retrieves data directly from NOAA's public SWPC services:

```text
Solar wind:
https://services.swpc.noaa.gov/products/geospace/propagated-solar-wind-1-hour.json

Solar wind speed:
https://services.swpc.noaa.gov/products/summary/solar-wind-speed.json

Planetary Kp:
https://services.swpc.noaa.gov/products/noaa-planetary-k-index.json
```

The browser periodically requests fresh data and updates the relevant instruments and charts.

The dashboard does not manufacture values when an endpoint is unavailable. Instead, it exposes the connection/data state so that the displayed information remains distinguishable from the visual simulation.

---

## 🔄 Live and recent information

The dashboard attempts to refresh the data every **60 seconds**.

This creates two layers of information:

**What is happening now**

The instrument readouts provide the latest available values from the public feeds.

**What has been happening recently**

The charts provide short-term context around those measurements.

That distinction matters because space weather is dynamic. A single value can tell us what the environment looks like at one point in time; a trend gives us some idea of where it has been moving.

---

## 🛠️ Built with

The project is intentionally lightweight.

### Frontend

- HTML5
- CSS3
- Vanilla JavaScript
- HTML Canvas
- Chart.js

### Data

- NOAA Space Weather Prediction Center public APIs

### Architecture

A single self-contained HTML dashboard.

There is no application server, database or heavy frontend framework required.

That keeps the project easy to inspect, deploy and reproduce.

---

## ▶️ Run it locally

Clone the repository:

```bash
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd space-weather-dashboard
```

Start a local server:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

A local HTTP server is recommended because the dashboard retrieves data from external NOAA endpoints from the browser.

---

## 🌐 Deployment

The dashboard can be deployed as a static website.

Suitable options include:

- GitHub Pages
- Netlify
- Vercel

For the μLearn submission, the final deployed URL should be added here:

**Live dashboard:** `ADD-HOSTED-LINK-HERE`

---

## 📸 Submission screenshots

The μLearn task asks for **two screenshots**.

Recommended captures:

### 01 — The instrument

Show the complete dashboard and its Sun–Earth visualisation.

```text
screenshots/dashboard-overview.png
```

### 02 — The telemetry

Show the numerical readouts, Kp gauge and recent trend charts clearly.

```text
screenshots/dashboard-telemetry.png
```

Add them to the repository and reference them here:

```markdown
![Dashboard overview](screenshots/dashboard-overview.png)

![Dashboard telemetry](screenshots/dashboard-telemetry.png)
```

---

## ✅ μLearn challenge checklist

The dashboard was built around the requirements of the μLearn task rather than as a generic dashboard concept.

| μLearn requirement | How this project addresses it |
|---|---|
| **Current/recent space-weather activity** | Recent NOAA solar-wind and geomagnetic measurements |
| **At least 4 parameters** | Solar-wind velocity, proton density, IMF Bz, Kp, geomagnetic state and recent trends |
| **Cards / graphs / indicators / charts** | Instrument readouts, analogue gauge and time-series charts |
| **Explain effects on Earth / missions** | GNSS, satellites, radio communication and power-system impacts |
| **Live/recent public API** | NOAA SWPC public data services |
| **Responsive and understandable** | Responsive instrument-console layout with visual hierarchy |
| **Working hosted link** | `ADD-HOSTED-LINK-HERE` |
| **Two screenshots** | `screenshots/` |
| **GitHub repository** | `ADD-GITHUB-LINK-HERE` |
| **Data/API explanation** | NOAA section above |
| **One possible space-weather impact** | GNSS/navigation section above |
| **Submission hashtag** | `#evn-sp-spaceweather` |

---

## 📁 Repository structure

```text
space-weather-dashboard/
│
├── index.html
├── README.md
│
└── screenshots/
    ├── dashboard-overview.png
    └── dashboard-telemetry.png
```

---

## 🔗 Data references

- NOAA Space Weather Prediction Center  
  https://www.swpc.noaa.gov/

- NOAA SWPC Data Access  
  https://www.spaceweather.gov/content/data-access

- NOAA Planetary K-index  
  https://www.spaceweather.gov/products/planetary-k-index

---

## ⚠️ A note about the visualisation

The measurements come from NOAA's public space-weather data services.

The animated Sun, solar-wind particles, Earth and magnetosphere are **interpretive visualisations**. They are designed to communicate the Sun–Earth relationship and provide visual context for the measurements; they should not be interpreted as a physically scaled simulation.

That distinction is important.

The dashboard is an instrument for **understanding the data**, not a replacement for a scientific space-weather model.

---

## 🌌 Final thought

Space weather is a story that begins far away but does not stay there.

A change on the Sun becomes plasma moving through space. That plasma interacts with Earth's magnetic environment. The disturbance then appears in measurements — and eventually, in technologies operating around and on Earth.

This dashboard is an attempt to make that chain visible.

**Look at the Sun. Follow the wind. Watch the magnetosphere. Then ask what changed here.**

---

### μLearn submission

**Task:** Space Weather Dashboard  
**Interest Group:** Space  
**Task Type:** Event  
**Karma:** 100  
**Hashtag:** `#evn-sp-spaceweather`

**Live dashboard:** `ADD-HOSTED-LINK-HERE`  
**GitHub repository:** `ADD-GITHUB-LINK-HERE`
