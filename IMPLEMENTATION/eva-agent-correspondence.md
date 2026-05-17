# eva-agent Theory / Implementation Boundary

中文: [eva-agent-correspondence-zh.md](eva-agent-correspondence-zh.md)

`eva-theory` and `eva-agent` are separate projects with different responsibilities.

## eva-theory owns

- EVA's problem framing, scope, core theoretical claims, and terminology
- the v0.5 core architecture and v0.6 theoretical extension
- reader-facing theory articles and visuals
- theory-side boundaries such as scenario specification discipline

## eva-agent owns

- framework and runtime implementation
- scenario-specific drives, sensors, actions, anchor policies, prior skills, and outcome observers
- runner assembly, runtime status, validation traces, metrics, and engineering roadmap
- implementation-specific documentation

Read `eva-theory` for theory. Read [`eva-agent`](https://github.com/slamslammo/eva-agent) for implementation.

