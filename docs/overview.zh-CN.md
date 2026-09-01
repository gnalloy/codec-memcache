# 概览

[English](overview.md) | [文档索引](README.zh-CN.md)

## 目标

Gnalloy Pipeline 的 Memcached binary 协议对象与 ASCII 编解码辅助能力。

该模块位于 transport 之上、业务 handler 之下，负责把字节或 Gnalloy 消息转换成协议对象，并把出站协议对象转换回字节。它不打开 socket，也不拥有 EventLoop。

## 仓库身份

- 模块路径：`gnalloy.org/codec-memcache`
- GitHub 仓库：`github.com/gnalloy/codec-memcache`
- 默认分支：`dev`
- 许可证：Apache-2.0

## 包结构
- `gnalloy.org/codec-memcache`（`memcache`）
- `gnalloy.org/codec-memcache/ascii`（`ascii`）

## 直接 Gnalloy 依赖
- `gnalloy.org/gnalloy`

## 当前模块规划中的直接下游
- 当前模块规划中没有其他仓库直接依赖该模块。

## 架构位置

Gnalloy 保持核心小而轻依赖。本仓库围绕单一职责形成可替换模块，通过显式 Go package 连接，而不是依靠运行时发现。

## 兼容性

公共导入路径是 `gnalloy.org/codec-memcache`。首个稳定 tag 发布前，请按依赖策略使用 `@dev` 或明确的 pseudo-version。
