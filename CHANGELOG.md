# Changelog

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) ·
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.1.1] - 2026-05-17

### Fixed

- `ha_lovelace op=save_config` now parses YAML/JSON string inputs to a
  dict before passing to HA's `lovelace/config/save` WS command.
  Previously a raw string could be persisted verbatim, leaving the
  dashboard unrenderable (`Cannot use 'in' operator to search for
  'strategy' in <stringified-config>`). Non-mapping or unparseable
  strings now raise `ToolError` instead of bricking the dashboard.
- `ha_lovelace op=config` now materializes the `orjson.Fragment`
  returned by HA's lovelace handler into a plain dict. Previously
  clients received the Python repr `"<orjson.Fragment object at 0x…>"`
  through the MCP JSON encoder fallback.

### Changed

- `ha_lovelace` destructive-op error message now points to the
  integration's Configure dialog rather than implying the flag is a
  per-call argument.

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

[Unreleased]: https://github.com/czechbol/hass-mcp/compare/v1.1.1...HEAD
[1.1.1]: https://github.com/czechbol/hass-mcp/releases/tag/v1.1.1
[1.1.0]: https://github.com/czechbol/hass-mcp/releases/tag/v1.1.0
[1.0.0]: https://github.com/czechbol/hass-mcp/releases/tag/v1.0.0
