# Product Catalog API

A RESTful API service for managing the IKEA product catalog. Built with Java 21 and Spring Boot 3.

## Overview

This service provides CRUD operations for products, categories, and inventory metadata. It serves as the single source of truth for product information across all channels.

## Tech Stack

- **Language:** Java 21
- **Framework:** Spring Boot 3.2
- **Database:** PostgreSQL 16
- **Cache:** Redis
- **API Docs:** OpenAPI 3.0 (Swagger UI)
- **Build:** Gradle 8.x

## Architecture

```
┌─────────────┐     ┌──────────────┐     ┌────────────┐
│   Clients   │────▶│  Spring Boot │────▶│ PostgreSQL │
└─────────────┘     │   REST API   │     └────────────┘
                    │              │────▶┌────────────┐
                    └──────────────┘     │   Redis    │
                                        └────────────┘
```

## Getting Started

### Prerequisites

- Java 21+
- Docker & Docker Compose
- Gradle 8+

### Run locally

```bash
# Start dependencies
docker compose up -d postgres redis

# Run the application
./gradlew bootRun
```

### Run tests

```bash
./gradlew test
```

### API Documentation

Once running, Swagger UI is available at: http://localhost:8080/swagger-ui.html

## Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `SPRING_DATASOURCE_URL` | `jdbc:postgresql://localhost:5432/catalog` | Database URL |
| `SPRING_REDIS_HOST` | `localhost` | Redis hostname |
| `SERVER_PORT` | `8080` | Application port |

## Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/api/v1/products` | List all products (paginated) |
| GET | `/api/v1/products/{id}` | Get product by ID |
| POST | `/api/v1/products` | Create a new product |
| PUT | `/api/v1/products/{id}` | Update a product |
| DELETE | `/api/v1/products/{id}` | Delete a product |
| GET | `/api/v1/categories` | List all categories |

## Team

- **Owning Team:** Catalog Platform
- **Slack:** #team-catalog-platform
