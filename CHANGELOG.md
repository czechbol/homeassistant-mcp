# Changelog

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) ·
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.1.0] - 2026-05-17

### Added

- `ha_lovelace` write ops: `save_config`, `delete_config`,
  `create_dashboard`, `update_dashboard`, `delete_dashboard`,
  `create_resource`, `update_resource`, `delete_resource`. Writes gated
  by `allow_write`; deletes additionally gated by `allow_destructive`.
  Storage-mode only for resource CRUD; YAML-mode dashboards reject
  save/delete (errors surface as `ToolError`).
- `CLAUDE.md` repo guide for future Claude Code sessions.

## [1.0.0] - 2026-05-17

Initial public release.

### Added

- HACS-installable HA integration mounting a stateless Streamable HTTP MCP
  server at `POST /api/hass_mcp`. Reuses HA bearer auth.
- 39 generic meta-tools covering states, services, registries (entity /
  device / area / label / floor / category / issue), automations / scripts
  / scenes (CRUD + traces), blueprints, helpers (input_* / counter / timer
  / schedule), history / logbook / statistics / recorder, diagnostics,
  system + error logs, lovelace, energy, conversation + intent, camera
  snapshots, webhooks, auth tokens, config entries, config flow
  (programmatic "Add Integration"), and HACS itself.
- Permission gates: `allow_write`, `allow_destructive`, `allow_fire_event`.
- Per-token sliding-window rate limiter (`rate_limit_per_minute`).
- Secret redaction in config-entry payloads.
- Per-call audit log line.
- In-process WebSocket dispatch helper (`ws.py`) for HA features without a
  Python API.
- Brand assets, CHANGELOG, LICENSE.
- Docs: quick start, user guide, developer guide, release process.
- CI: hassfest + HACS Action + ruff + pytest on every push.

[Unreleased]: https://github.com/czechbol/hass-mcp/compare/v1.1.0...HEAD
[1.1.0]: https://github.com/czechbol/hass-mcp/releases/tag/v1.1.0
[1.0.0]: https://github.com/czechbol/hass-mcp/releases/tag/v1.0.0
