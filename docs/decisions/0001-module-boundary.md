# ADR-001: Keep codec-memcache as an Independent Gnalloy Module

## Status
Accepted

## Date
2026-08-31

## Context
Gnalloy is split from the previous single `goark.dev/gnalloy` module into focused repositories under `github.com/gnalloy`. The public import domain is `gnalloy.org`.

## Decision
`codec-memcache` is published as `gnalloy.org/codec-memcache` and owns this responsibility: Memcached binary protocol objects and ASCII codec helpers for Gnalloy pipelines.

The core module remains `gnalloy.org/gnalloy`. Protocol codecs, concrete transports, handlers, resolvers, examples, and benchmark tooling depend on the core contracts instead of living inside the core repository.

## Consequences
- Consumers can depend on only the protocol, transport, or handler they actually need.
- Hot-path core code avoids optional protocol, compression, QUIC, OpenTelemetry, and benchmark dependencies.
- Cross-module changes require workspace verification plus standalone module verification before push.
