# Disk Scheduling Lab

A self-contained, interactive visualizer for six classic operating-system disk scheduling algorithms. Choose a policy, advance or rewind one movement at a time, and follow the disk head on a live cylinder-versus-move graph while the seek calculation and scheduling decision are explained.

## Getting started

1. Download or save `disk_scheduling_lab.html` and `README.md` in the same folder.
2. Open `disk_scheduling_lab.html` in a modern web browser.
3. Select an algorithm and choose **Start walkthrough**.

No installation, build step, web server, external library, font, or network connection is required. The HTML file contains its own CSS and JavaScript and can be opened directly from disk.

## What’s included

- **Six policies:** FCFS, SSTF, SCAN, C-SCAN, LOOK, and C-LOOK.
- **Step controls:** use **Next** and **Previous** to move through the run; **Reset** returns to its overview.
- **Live graph:** the head’s route is revealed as each movement is completed. The vertical axis is the cylinder number and the horizontal axis is move order.
- **Decision explanations:** see the arrival-order choice, SSTF distance comparisons, directional scan candidates, boundary travel, or circular return for the current step.
- **Seek calculations:** each move shows `|destination − current head|`, the movement for that leg, and the updated running total.
- **Results:** review total movement, average movement per request, the sum of the individual legs, and the service order.
- **Replay and compare:** replay the current policy or choose another policy for the same request queue.
- **Keyboard navigation:** while focus is not in a button or input, use **←** for Previous and **→** for Next.
- **Responsive layout:** works on desktop and smaller screens.

## Workload used in the walkthroughs

All algorithms run on the same fixed example:

| Setting | Value |
|---|---|
| Cylinder range | `0–199` inclusive |
| Initial head position | `53` |
| Request queue (arrival order) | `98, 183, 37, 122, 14, 124, 65, 67, 150, 45` |
| Initial direction for SCAN-family algorithms | Toward higher-numbered cylinders |

The request queue is kept in its original order for FCFS. The other algorithms choose requests according to their own scheduling rules.

## Scheduling rules and calculation conventions

A movement from cylinder `a` to cylinder `b` contributes `|b − a|` cylinders of head movement. The displayed total is the sum of every movement in the route.

- **FCFS — First Come, First Served:** serves requests in the listed arrival order.
- **SSTF — Shortest Seek Time First:** serves the pending request closest to the current head. If distances tie, the lower-numbered cylinder is chosen.
- **SCAN — Elevator:** sweeps toward higher cylinders, travels to the physical end (`199`) when requests remain on the other side, then reverses.
- **C-SCAN — Circular SCAN:** sweeps toward higher cylinders, reaches `199`, then returns to `0` without servicing requests on the return. It resumes servicing in the upward direction.
- **LOOK:** sweeps toward the last pending request in that direction, then reverses there rather than continuing to an unused physical edge.
- **C-LOOK — Circular LOOK:** sweeps to the last pending request, then jumps directly to the lowest pending request and serves it on arrival.

**Boundary travel and circular returns/jumps count toward total head movement.** Requests are serviced only at their request cylinders; in C-LOOK the destination request is serviced when the head arrives after the jump. These conventions are shown in the step calculations and final movement sum.

## Files

```text
.
├── disk_scheduling_lab.html   # Standalone interactive application
└── README.md                   # Project documentation
```

## Technical notes

The application is implemented with plain HTML, CSS, and JavaScript. It has no external assets or runtime dependencies. The workload and disk direction are intentionally fixed so that each algorithm can be compared against the same example. To experiment with another problem, edit the `PROBLEM` object near the beginning of the HTML file and keep the cylinder range, head position, and request values consistent.
