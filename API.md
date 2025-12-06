# ChunkHub API Reference

> **Base URL:** `https://api.chunkhub.io` (or `http://localhost:8000` for local dev)

## Authentication

ChunkHub uses JWT-based authentication for user login and moderation features. Most catalog endpoints are public and require no authentication.

Protected endpoints require a Bearer token:

```http
Authorization: Bearer <token>
```

## Endpoints

### Mods

#### List Mods
```http
GET /api/mods
```

**Query Parameters:**
- `search` (string, optional) - Search query
- `page` (integer, optional) - Page number (default: 1)
- `per_page` (integer, optional) - Results per page (default: 20, max: 100)
- `category` (string, optional) - Filter by category

**Response:**
```json
{
  "items": [
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "author": "string",
      "version": "string",
      "downloads": 0,
      "created_at": "2025-01-01T00:00:00Z",
      "updated_at": "2025-01-01T00:00:00Z",
      "minecraft_versions": ["1.20.1", "1.20.2"],
      "categories": ["technology", "magic"],
      "image_url": "string"
    }
  ],
  "total": 0,
  "page": 1,
  "per_page": 20,
  "total_pages": 0
}
```

#### Get Mod
```http
GET /api/mods/:id
```

**Response:**
```json
{
  "id": "string",
  "name": "string",
  "description": "string",
  "author": "string",
  "version": "string",
  "downloads": 0,
  "created_at": "2025-01-01T00:00:00Z",
  "updated_at": "2025-01-01T00:00:00Z",
  "minecraft_versions": ["1.20.1"],
  "categories": ["technology"],
  "image_url": "string"
}
```

### Modpacks

#### List Modpacks
```http
GET /api/modpacks
```

**Query Parameters:**
- `search` (string, optional) - Search query
- `page` (integer, optional) - Page number (default: 1)
- `per_page` (integer, optional) - Results per page (default: 20, max: 100)

**Response:**
```json
{
  "items": [
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "author": "string",
      "version": "string",
      "downloads": 0,
      "created_at": "2025-01-01T00:00:00Z",
      "updated_at": "2025-01-01T00:00:00Z",
      "minecraft_version": "1.20.1",
      "mod_count": 0,
      "image_url": "string"
    }
  ],
  "total": 0,
  "page": 1,
  "per_page": 20,
  "total_pages": 0
}
```

#### Get Modpack
```http
GET /api/modpacks/:id
```

**Response:**
```json
{
  "id": "string",
  "name": "string",
  "description": "string",
  "author": "string",
  "version": "string",
  "downloads": 0,
  "created_at": "2025-01-01T00:00:00Z",
  "updated_at": "2025-01-01T00:00:00Z",
  "minecraft_version": "1.20.1",
  "mod_count": 0,
  "image_url": "string"
}
```

### Authentication

#### Login
```http
POST /api/auth/token
```

**Request Body:**
```json
{
  "username": "string",
  "password": "string"
}
```

**Response:**
```json
{
  "access_token": "string",
  "token_type": "bearer"
}
```

#### Get Current User
```http
GET /api/auth/me
```

**Headers:**
```
Authorization: Bearer <token>
```

**Response:**
```json
{
  "id": "string",
  "username": "string",
  "email": "string"
}
```

## Error Responses

```json
{
  "error": "Error message",
  "detail": "Additional details"
}
```

**Status Codes:**
- `200` - Success
- `400` - Bad Request
- `401` - Unauthorized
- `404` - Not Found
- `500` - Internal Server Error
