# ShopWave

A production-style e-commerce backend, built from scratch and deliberately broken to learn distributed systems, event-driven architecture, and production incident response.

This is not a toy CRUD app. ShopWave is designed to survive (and fail under) real usage patterns: concurrent inventory contention, payment idempotency, Kafka consumer crashes, connection pool exhaustion, and cache stampedes — the same failure modes that page on-call engineers at 3 AM.

## Why this exists

Most backend tutorials teach endpoints. This project teaches systems. Every service here is built with production concerns from day one — retries, idempotency keys, circuit breakers, structured logging, metrics — and then intentionally broken to understand exactly how and why real systems fail.

## Architecture

**Phase 1 — Monolith** ([shopwave-monolith](https://github.com/YOUR_USERNAME/shopwave-monolith))
Auth, product catalog, cart, orders, payments, inventory, and notifications as a single Spring Boot application, communicating internally via Kafka events.

**Phase 2 — Microservices** (upcoming)
The monolith is split into independent services: `order-service`, `payment-service`, `inventory-service`, `notification-service`, fronted by an API Gateway.

## Core order flow

Every step is designed to fail safely — with compensating transactions (saga pattern) rolling back prior steps if a later one fails.

## Tech stack

| Concern | Choice |
|---|---|
| Language / Framework | Java 21, Spring Boot 3 |
| Database | PostgreSQL |
| Cache / Locking | Redis |
| Messaging | Apache Kafka |
| Payments | Stripe (test mode) |
| Observability | Prometheus + Grafana |
| Containerization | Docker Compose |
| Deployment | DigitalOcean |

## Repo structure

This parent repo references each service as a git submodule

## Status

🚧 Actively under development — currently building the monolith phase.


