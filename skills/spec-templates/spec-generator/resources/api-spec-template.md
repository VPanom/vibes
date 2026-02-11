# [API Name] Specification

**Version:** [X.Y]  
**Author:** [Name/Team]  
**Date:** [YYYY-MM-DD]  
**Status:** [Draft | In Review | Approved | Published]  
**Base URL:** `https://api.example.com/v1`  

## Executive Summary

[Brief overview of the API's purpose, primary use cases, and key capabilities]

## Overview

### Purpose
[What this API enables developers to do]

### Key Features
- [Feature 1]
- [Feature 2]
- [Feature 3]

### Target Audience
[Who should use this API]

## Getting Started

### Prerequisites
- [Requirement 1]
- [Requirement 2]

### Quick Start
```bash
# Example API call
curl -X GET https://api.example.com/v1/resource \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## Authentication

### Method
[OAuth2 | API Key | JWT | etc.]

### Obtaining Credentials
[How to get API credentials]

### Authentication Flow
```
[Describe or diagram the authentication flow]
```

### Example
```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

## API Endpoints

### Resource: [Resource Name]

#### List [Resources]
```
GET /api/v1/[resources]
```

**Description:** [What this endpoint does]

**Authentication:** Required

**Query Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `page` | integer | No | Page number (default: 1) |
| `limit` | integer | No | Items per page (default: 20, max: 100) |
| `filter` | string | No | Filter criteria |

**Request Example:**
```http
GET /api/v1/resources?page=1&limit=20
Host: api.example.com
Authorization: Bearer YOUR_TOKEN
```

**Response (200 OK):**
```json
{
  "data": [
    {
      "id": "res_123",
      "name": "Example Resource",
      "created_at": "2026-02-11T10:00:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 100,
    "has_more": true
  }
}
```

**Error Responses:**
- `401 Unauthorized`: Invalid or missing authentication
- `429 Too Many Requests`: Rate limit exceeded
- `500 Internal Server Error`: Server error

---

#### Get [Resource]
```
GET /api/v1/[resources]/{id}
```

**Description:** [What this endpoint does]

**Authentication:** Required

**Path Parameters:**
| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | string | Unique identifier for the resource |

**Request Example:**
```http
GET /api/v1/resources/res_123
Host: api.example.com
Authorization: Bearer YOUR_TOKEN
```

**Response (200 OK):**
```json
{
  "id": "res_123",
  "name": "Example Resource",
  "description": "Detailed information",
  "created_at": "2026-02-11T10:00:00Z",
  "updated_at": "2026-02-11T10:00:00Z"
}
```

**Error Responses:**
- `401 Unauthorized`: Invalid or missing authentication
- `404 Not Found`: Resource does not exist
- `500 Internal Server Error`: Server error

---

#### Create [Resource]
```
POST /api/v1/[resources]
```

**Description:** [What this endpoint does]

**Authentication:** Required

**Request Body:**
| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | Yes | Resource name (max 100 chars) |
| `description` | string | No | Resource description |

**Request Example:**
```http
POST /api/v1/resources
Host: api.example.com
Authorization: Bearer YOUR_TOKEN
Content-Type: application/json

{
  "name": "New Resource",
  "description": "Optional description"
}
```

**Response (201 Created):**
```json
{
  "id": "res_124",
  "name": "New Resource",
  "description": "Optional description",
  "created_at": "2026-02-11T11:00:00Z",
  "updated_at": "2026-02-11T11:00:00Z"
}
```

**Error Responses:**
- `400 Bad Request`: Invalid request body
- `401 Unauthorized`: Invalid or missing authentication
- `409 Conflict`: Resource already exists
- `500 Internal Server Error`: Server error

---

#### Update [Resource]
```
PUT /api/v1/[resources]/{id}
PATCH /api/v1/[resources]/{id}
```

**Description:** [What this endpoint does. PUT replaces entire resource, PATCH updates specific fields]

**Authentication:** Required

**Path Parameters:**
| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | string | Unique identifier for the resource |

**Request Body:**
| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | No | Updated name |
| `description` | string | No | Updated description |

**Request Example:**
```http
PATCH /api/v1/resources/res_123
Host: api.example.com
Authorization: Bearer YOUR_TOKEN
Content-Type: application/json

{
  "name": "Updated Name"
}
```

**Response (200 OK):**
```json
{
  "id": "res_123",
  "name": "Updated Name",
  "description": "Original description",
  "created_at": "2026-02-11T10:00:00Z",
  "updated_at": "2026-02-11T12:00:00Z"
}
```

**Error Responses:**
- `400 Bad Request`: Invalid request body
- `401 Unauthorized`: Invalid or missing authentication
- `404 Not Found`: Resource does not exist
- `500 Internal Server Error`: Server error

---

#### Delete [Resource]
```
DELETE /api/v1/[resources]/{id}
```

**Description:** [What this endpoint does]

**Authentication:** Required

**Path Parameters:**
| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | string | Unique identifier for the resource |

**Request Example:**
```http
DELETE /api/v1/resources/res_123
Host: api.example.com
Authorization: Bearer YOUR_TOKEN
```

**Response (204 No Content):**
[Empty response body]

**Error Responses:**
- `401 Unauthorized`: Invalid or missing authentication
- `404 Not Found`: Resource does not exist
- `409 Conflict`: Resource cannot be deleted (e.g., has dependencies)
- `500 Internal Server Error`: Server error

---

## Data Models

### [Model Name]
```json
{
  "id": "string",
  "name": "string",
  "description": "string | null",
  "created_at": "ISO 8601 datetime",
  "updated_at": "ISO 8601 datetime"
}
```

**Field Descriptions:**
- **id**: Unique identifier (format: `res_[alphanumeric]`)
- **name**: Resource name, 1-100 characters
- **description**: Optional description, max 1000 characters
- **created_at**: Timestamp when resource was created
- **updated_at**: Timestamp of last modification

## Error Handling

### Error Response Format
```json
{
  "error": {
    "code": "error_code",
    "message": "Human-readable error message",
    "details": {
      "field": "Additional error details"
    },
    "request_id": "req_abc123"
  }
}
```

### Common Error Codes

| HTTP Status | Error Code | Description |
|-------------|------------|-------------|
| 400 | `bad_request` | Invalid request format or parameters |
| 401 | `unauthorized` | Missing or invalid authentication |
| 403 | `forbidden` | Authenticated but not authorized |
| 404 | `not_found` | Resource does not exist |
| 409 | `conflict` | Request conflicts with current state |
| 429 | `rate_limit_exceeded` | Too many requests |
| 500 | `internal_error` | Server error |
| 503 | `service_unavailable` | Temporary unavailability |

## Rate Limiting

### Limits
- **Standard:** 100 requests per minute
- **Burst:** Up to 20 requests per second

### Headers
```http
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 95
X-RateLimit-Reset: 1707649200
```

### Handling Rate Limits
When rate limited (429 response), wait until the time specified in `X-RateLimit-Reset` before retrying.

## Pagination

### Request Parameters
- `page`: Page number (1-indexed)
- `limit`: Items per page (default: 20, max: 100)

### Response Format
```json
{
  "data": [...],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 100,
    "has_more": true
  }
}
```

### Best Practices
- Use cursor-based pagination for large datasets
- Include pagination metadata in all list responses
- Limit maximum page size to prevent performance issues

## Filtering and Sorting

### Filtering
```
GET /api/v1/resources?filter[name]=example&filter[status]=active
```

### Sorting
```
GET /api/v1/resources?sort=-created_at,name
```
- Prefix with `-` for descending order
- Multiple fields separated by commas

## Versioning

### Strategy
[Semantic versioning | Date-based | etc.]

### Version Header
```http
API-Version: 2026-02-11
```

### Deprecation Policy
- Versions supported for minimum [X] months after deprecation
- Deprecation notices sent [X] months in advance
- Sunset date included in `Sunset` header

## Webhooks

### Overview
[If API supports webhooks, describe the webhook system]

### Webhook Events
| Event | Description |
|-------|-------------|
| `resource.created` | Triggered when resource is created |
| `resource.updated` | Triggered when resource is updated |
| `resource.deleted` | Triggered when resource is deleted |

### Webhook Payload
```json
{
  "id": "evt_123",
  "type": "resource.created",
  "created_at": "2026-02-11T10:00:00Z",
  "data": {
    // Resource object
  }
}
```

### Webhook Signature
[How to verify webhook authenticity]

## SDKs and Libraries

### Official SDKs
- **JavaScript/TypeScript:** [Link]
- **Python:** [Link]
- **Ruby:** [Link]

### Community Libraries
[Links to community-maintained libraries]

## Testing

### Sandbox Environment
```
Base URL: https://api-sandbox.example.com/v1
```

### Test Credentials
[How to obtain test API keys]

### Test Data
[Information about test data availability]

## Security

### Best Practices
- Store API keys securely (never in code or public repositories)
- Use HTTPS for all requests
- Implement proper error handling
- Rotate credentials regularly
- Monitor API usage for anomalies

### CORS
[CORS policy and configuration]

## Support

### Documentation
[Link to full documentation]

### API Status
[Link to status page]

### Contact
- **Support Email:** [Email]
- **Developer Forum:** [Link]
- **Issues:** [Link to issue tracker]

## Changelog

### Version [X.Y] - [Date]
- [Change 1]
- [Change 2]

### Version [X.Y] - [Date]
- [Change 1]
- [Change 2]

## Appendices

### Example Use Cases
[Common integration patterns and examples]

### Glossary
- **[Term]**: [Definition]

### Related Resources
- [Link to related documentation]
