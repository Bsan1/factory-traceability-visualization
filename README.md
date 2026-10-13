# Factory Traceability Visualization

A live, explorable picture of a production line in the browser: a 3D view of the line with every
machine's state, the people at the stations and the products moving through it, together with the
figures behind them, from a single shift to a whole month.

**Live demo: [ftv-demo.gamelibtest.workers.dev](https://ftv-demo.gamelibtest.workers.dev/)**

The demo is sign-in protected. To get access, or to talk about the project, email me at
**[sanbaris381@gmail.com](mailto:sanbaris381@gmail.com)**.

> This repository is the project's showcase; the source code is private.

## What it does

- **The line in 3D.** A Unity WebGL scene inside the web app shows each machine in its state
  (running, stopped, fault, offline), an operator figure at every staffed station and a clear
  outline around selected machines. It works with a mouse and with touch on phones and tablets.
- **Live, or any moment in the past.** The view follows the line live, or goes back to any moment
  in its history and plays the day back at up to 600× speed, with every alarm marked on the
  timeline.
- **Product traceability.** Search a product code and its route is drawn across the line: the
  stations it passed, where it is now, the stations still ahead, and any revision on the way.
- **Line figures.** Output, reject rate, revisions, stop time per machine, stop count and faults,
  for a shift, a day, a week or a month, any calendar period. Every chart enlarges to full screen.
- **Drill down from any number.** Click an output column to list the products that left the line in
  that hour, with their product types. Click a revision column to see the machines and the
  products sent to revision. Click a machine for its own figures and status timeline.
- **It explains itself.** When a whole line stands still, it says why: no shift planned, the first
  shift not started yet, the day's shifts over, or a short wait inside a shift.
- **Layout editor.** Place, move and rotate machines on the line's grid, with versioned layouts and
  their history.
- **Roles and audit.** Role-based access with user management and an audit log.

## How it is built

- **Web:** React and TypeScript (Vite); the charts are hand-drawn SVG, responsive from a phone to a
  wide desktop.
- **3D:** Unity 6 (URP) compiled to WebGL, talking to the page through a typed, validated message
  bridge.
- **Back end:** Cloudflare Workers (Hono) with D1 (SQLite) and private R2 storage; session-based
  sign-in, a strict Content Security Policy and rate limiting.
- **Shared contracts:** zod schemas used by both the API and the web app, covered by tests.
- **Data:** a minute-by-minute simulation of production lines, modelled on statistics from a real
  line (shift patterns, cycle times, stop and fault rates, product mix) without any of its records.
  Every simulated product has a traceable code, and the figures add up: each chart column can be
  opened to the very products and machines behind it.

## Contact

Barış Şan · [sanbaris381@gmail.com](mailto:sanbaris381@gmail.com)
