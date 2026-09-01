# Overview

[简体中文](overview.zh-CN.md) | [Docs Index](README.md)

## Purpose

Memcached binary protocol objects and ASCII codec helpers for Gnalloy pipelines.

This module sits above transports and below application handlers. It translates bytes or Gnalloy messages into protocol objects, and translates outbound protocol objects back to bytes. It does not open sockets or own EventLoops.

## Repository Identity

- Module path: `gnalloy.org/codec-memcache`
- GitHub repository: `github.com/gnalloy/codec-memcache`
- Default branch: `dev`
- License: Apache-2.0

## Package Map
- `gnalloy.org/codec-memcache` (`memcache`)
- `gnalloy.org/codec-memcache/ascii` (`ascii`)

## Direct Gnalloy Dependencies

- `gnalloy.org/gnalloy`

## Direct Dependents in the Current Repository Set

- No repository in the current local Gnalloy set directly depends on this module.

## Architecture Position

Gnalloy keeps the core small and dependency-light. This repository is a replaceable module around one responsibility, connected through explicit Go packages instead of runtime discovery.

## Compatibility

The public import path is `gnalloy.org/codec-memcache`. Until the first stable tag is published, use `@dev` or an explicit pseudo-version selected by your dependency policy.
