## ROUTE — Project Documentation

This repository contains documentation and diagrams for the ROUTE project, including the project specification, the WebSocket API protocol between the VISTA (client) and SPINE (server) components, and design diagrams.

### Quick links

- **Project specification**: [`1-project-specification.pdf`](./1-project-specification.pdf)
- **WebSocket API Protocol**: [`2-api-protocol.md`](./2-api-protocol.md)
- **Class diagram (PNG)**: [`Diagrams/Class Diagrams/1-simulation-state.png`](./Diagrams/Class%20Diagrams/1-simulation-state.png)
- **Use-case diagram (PNG)**: [`Diagrams/Use-Case Diagrams/1-use-case-diagram.png`](./Diagrams/Use-Case%20Diagrams/1-use-case-diagram.png)
- **Visual Paradigm project**: [`Diagrams/ROUTE.vpp`](./Diagrams/ROUTE.vpp)

### Overview

ROUTE models a simulation system with two main components:

- **VISTA**: the client-side component responsible for sending actions.
- **SPINE**: the server-side component that processes actions and returns signals.

The two components communicate over a WebSocket-based protocol. See [`2-api-protocol.md`](./2-api-protocol.md) for the full specification, including message shapes and allowed actions/signals.

### API at a glance

Messages are JSON objects sent over WebSocket.

- **Actions** (sent by VISTA):

  - `simulation.start`, `simulation.stop`, `simulation.resume`
  - `map.create`, `map.export`, `map.import`
  - `tick_rate.update`
  - `agent.create`, `agent.update`, `agent.delete`, `agent.get`

- **Signals** (emitted by SPINE):
  - `simulation.started`, `simulation.stopped`, `simulation.resumed`
  - `map.created`, `map.exported`, `map.imported`
  - `tick_rate.updated`
  - `agent.created`, `agent.updated`, `agent.deleted`, `agent.state`
  - `event.created`, `building.updated`, and generic `error`

Refer to the full protocol document for exact payload schemas and examples: [`2-api-protocol.md`](./2-api-protocol.md).

### Repository structure

- `1-project-specification.pdf`: Formal project specification
- `2-api-protocol.md`: WebSocket protocol between VISTA and SPINE
- `Diagrams/`
  - `Class Diagrams/`: Exported class/UML diagrams (PNG)
  - `Use-Case Diagrams/`: Exported use-case diagrams (PNG)
  - `ROUTE.vpp`: Visual Paradigm project file for the diagrams
  - `ROUTE.vpp.bak_*`: Backup files created by Visual Paradigm

### Viewing and editing diagrams

The Visual Paradigm project (`ROUTE.vpp`) can be opened with Visual Paradigm (Community Edition is sufficient).

Steps:

1. Install Visual Paradigm Community Edition.
2. Open `Diagrams/ROUTE.vpp`.
3. Export images as needed (recommended: PNG) into the appropriate folder under `Diagrams/`.

Conventions:

- Keep exported images in their existing directories (e.g., `Class Diagrams/`, `Use-Case Diagrams/`).
- Use descriptive filenames and avoid spaces in new names when possible.
