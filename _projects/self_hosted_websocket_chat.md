---
title: "Self hosted chat"
priority: 2
date: 2026-01-15
excerpt: "Real-time ephemeral chat platform deployed on self-hosted infrastructure using a WireGuard private network, Caddy reverse proxy, and HTTPS/TLS, featuring SQLite persistence and WebSocket communication."
status: "Self hosted · In production"
role: "Systems administration, networking, full-stack development, deployment, and operations"
category: "Backend, Systems & Networking"
code: "Server"
stack:
  - Javascript
  - SQLite
  - Linux server
  - Caddy
  - WireGuard
  - SSH
repo_url: "https://https://github.com/esettes/self_hosted_websocket_chat"
demo_url: ""
cover: "/assets/images/projects/chat.png"
---
I designed, deployed, and managed a real-time messaging platform on self-hosted Linux infrastructure.
The application runs within a private WireGuard network and exposes the service via Caddy acting as 
a reverse proxy, which redirects HTTPS traffic from port 443 to the internal server. 
The deployment encompasses TLS configuration, dynamic DNS, network and firewall rules, proper WebSocket 
connection handling through the proxy, and remote system administration via SSH.

The backend, built with Node.js and Express, provides an HTTP API and a WebSocket server organized into 
independent rooms. Each chat utilizes a cryptographically generated token, supports optional access 
code protection, and features distinct controls for owners and administrators. Features include 
heartbeats to detect inactive connections, tracking of connected users, and immediate message 
distribution among all room participants.

Data is stored in SQLite using WAL mode, foreign keys, and specific indexes optimized for message 
queries, reports, and usage limits. Chats and their messages are automatically deleted after 24 hours 
to minimize unnecessary data retention. The system also incorporates room creation limits, anonymized 
fingerprints (via SHA-256 or HMAC with a configurable salt), and an automated error-collection mechanism 
for HTTP and client-side errors to facilitate service diagnosis and maintenance.

This project integrates backend and frontend development with system administration, private network 
configuration, secure service exposure, DNS and certificate management, data persistence, and the 
operation of a self-hosted application.

#### Link to site: <url>https://baky.dedyn.io/</url>