# OS-Learning-Tool

## ◈ Virtualization · Interactive 3D Lecture Deck (`index.html`)

A single-file, premium-styled teaching deck for OS **virtualization** concepts, built for
faculty to present in class. Scroll-driven **3D illustrations** (three.js) stay in sync with
readable lesson text, and **every animation is fully reversible**.

### Topics covered (5 chapters · 20 states)
1. **What is Virtualization?** — idle server → resource pool → VMs → isolation
2. **Creating a Virtual Machine** — hypervisor → carve vHW → guest OS → boot
3. **Types of Hypervisors** — Type-1 bare metal vs Type-2 hosted, head-to-head
4. **Network & Service Virtualization** — physical underlay → virtual overlay → NFV → policy routing
5. **The Cost of Virtualization** — sprawl → consolidation → overhead tax → TCO balance → verdict

### Run it
Just open `index.html` in any modern browser (internet needed once for the three.js CDN
and fonts), or serve the folder: `python3 -m http.server` → http://localhost:8000

### Presenter controls (all reversible)
| Input | Action |
|---|---|
| Mouse / trackpad scroll | next state ↓ · previous state ↑ |
| `← → ↑ ↓`, `Space`, `PgUp/PgDn` | step through states |
| Gold timeline slider | **scrub the 3D continuously** back & forth |
| Drag on the 3D stage | orbit the camera |
| `L` | lecture auto-play · `F` fullscreen · `?` help · `Home/End` jump |

Each state also shows a **📣 teaching cue** (a line to say to the class), deep-linkable URLs
(`#s=7`), chapter tabs, and a graceful text-only mode if WebGL/CDN is unavailable.
