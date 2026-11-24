---
title: Documentation
---
`gvx` runs unmodified Linux containers and binaries on Windows, macOS, and Linux. The table lists each document and its scope.

| Document | Scope |
| :--- | :--- |
| [CLI reference](cli.md) | The `rungv` subcommands, each `rungv run` flag, runtime tunables, and diagnostics. |
| [Recipes](recipes/) | Guides that run Docker Engine or a `k3s` node in one sandbox. |
| [Architecture](architecture.md) | Package boundaries, subsystem specifications, and milestone criteria of the port to Windows and macOS. |
| [Control protocol](control-protocol.md) | The `gvx-ctrl/2` wire protocol, its capability matrix, and its lockdown constraints. |
| [Windows systrap](systrap-windows.md) | The design, the measurements, and the limits of the engine that runs a Linux guest without a hypervisor. |
| [Moonshots](moonshots.md) | The proposed design that gives a guest access to the GPU of the host. |
