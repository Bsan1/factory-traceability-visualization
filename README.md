# Factory Traceability Visualization

A browser-based view of a production line. It combines a 3D model of the line—showing machine states, operators and moving products—with production data covering anything from a single shift to a full month.

**Live demo: [ftv-demo.gamelibtest.workers.dev](https://ftv-demo.gamelibtest.workers.dev/)**

The demo is sign-in protected. Access is provided by email. To request access or discuss the project, contact me at **[sanbaris381@gmail.com](mailto:sanbaris381@gmail.com)**.

> This repository is a showcase for the project. The source code is private.

## What it does

- **3D production line:** A Unity WebGL scene runs inside the web app. It shows whether each machine is running, stopped, in fault or offline, places an operator at every staffed station and outlines the machines you select. The controls work with a mouse or touch on phones and tablets.
- **Live and historical views:** Follow the line live or return to any point in its history. A full day can be played back at up to 600× speed, with alarms marked on the timeline.
- **Product traceability:** Search by product code to see the product’s route through the line, including the stations it has passed, its current location, the stations ahead and any revision along the way.
- **Production figures:** Review output, reject rate, revisions, stop time per machine, stop count and faults for a shift, day, week, month or any calendar period. Charts can be expanded to full screen.
- **Detailed breakdowns:** Select an output column to list the products completed during that hour and their product types. Select a revision column to see the relevant machines and products. Select a machine to view its figures and status timeline.
- **Line status explanations:** When the entire line is idle, the app identifies the reason: no shift is planned, the first shift has not started, the day’s shifts have ended or the line is briefly waiting during a shift.
- **Layout editor:** Place, move and rotate machines on the line’s grid. Layouts are versioned and their history is retained.
- **Roles and auditing:** Role-based access, user management and an audit log are included.

## How it is built

- **Web:** React and TypeScript with Vite. The charts are hand-drawn SVG and adapt from phone screens to wide desktop displays.
- **3D:** Unity 6 with URP, compiled to WebGL. It communicates with the page through a typed and validated message bridge.
- **Back end:** Cloudflare Workers with Hono, D1 (SQLite) and private R2 storage. Authentication uses sessions, with a strict Content Security Policy and rate limiting.
- **Shared contracts:** zod schemas are shared by the API and web app and covered by tests.
- **Data:** The project uses a minute-by-minute production-line simulation based on statistics from a real line, including shift patterns, cycle times, stop and fault rates and product mix, without using any of the line’s records. Each simulated product has a traceable code, and the figures reconcile: every chart column can be opened to show the products and machines behind it.

## Contact

Barış Şan — [sanbaris381@gmail.com](mailto:sanbaris381@gmail.com)