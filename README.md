# Remodex Relay - LazyCat App

> WebSocket 中继服务，用于 Remodex 配对流程

## 项目说明

本项目是 [Remodex](https://github.com/Emanuele-web04/remodex) 的 WebSocket 中继服务的独立部署版本，已移植到 LazyCat 微服平台。

### 功能特性

- 接受 WebSocket 连接到 `/relay/{sessionId}`
- 为每个会话配对一个 Mac 主机和一个 iPhone 客户端
- 在 Mac 和 iPhone 之间转发加密的控制消息和负载
- 仅记录连接元数据，不记录明文内容
- 提供健康检查和统计信息 API
- 支持中英文管理界面

### 访问方式

- **管理界面**: `http://<your-domain>/`
- **WebSocket 端点**: `ws://<your-domain>/relay/{sessionId}`
- **健康检查**: `http://<your-domain>/health`
- **统计信息**: `http://<your-domain>/api/stats`

## 环境变量

| 变量名 | 默认值 | 说明 |
|--------|--------|------|
| `PORT` | `3000` | HTTP 服务端口 |
| `HOST` | `0.0.0.0` | 监听地址 |

## 数据目录

本服务为无状态服务，所有会话数据存储在内存中，不需要持久化存储。

## 安全说明

- 中继服务作为传输层，不参与端到端加密
- 所有 Remodex 应用负载在传输前已通过 AES-256-GCM 加密
- 中继只能看到连接元数据，无法查看明文内容

## 上游项目

- **GitHub**: https://github.com/Emanuele-web04/remodex
- **License**: ISC

## 版本信息

- **当前版本**: 1.0.0
- **LazyCat 适配**: 是
