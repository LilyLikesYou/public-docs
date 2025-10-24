---
description: Complete API reference for interacting with our software programmatically
icon: brackets-curly
---

# API Overview

Our API provides programmatic access to all features of the software. This reference documentation covers authentication, endpoints, request/response formats, and code examples.

## Base URL

All API requests should be made to:

```
https://api.yourcompany.com/v1
```

For development/testing, use:

```
https://api-staging.yourcompany.com/v1
```

## Authentication

All API requests require authentication using an API key. Include your API key in the request header:

```bash
Authorization: Bearer YOUR_API_KEY
```

**Getting your API key:**

1. Log in to your account
2. Navigate to Settings → API Keys
3. Click "Generate New Key"
4. Copy and securely store your key

{% hint style="warning" %}
**Security Note**: Never commit API keys to version control or share them publicly. Use environment variables or secure key management systems.
{% endhint %}

## Request Format

All requests should include these headers:

```
Content-Type: application/json
Authorization: Bearer YOUR_API_KEY
Accept: application/json
```

**Example request:**

```bash
curl -X GET https://api.yourcompany.com/v1/resources \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json"
```

## Response Format

All API responses are returned in JSON format:

**Success response:**

```json
{
  "status": "success",
  "data": {
    "id": "123",
    "name": "example"
  },
  "meta": {
    "timestamp": "2024-01-01T12:00:00Z"
  }
}
```

**Error response:**

```json
{
  "status": "error",
  "error": {
    "code": "INVALID_REQUEST",
    "message": "Invalid parameter: name is required",
    "details": {
      "field": "name",
      "reason": "required_field_missing"
    }
  }
}
```

## Status Codes

Our API uses standard HTTP status codes:

| Code | Description |
|------|-------------|
| 200 | Success - Request completed successfully |
| 201 | Created - Resource created successfully |
| 204 | No Content - Success with no response body |
| 400 | Bad Request - Invalid request parameters |
| 401 | Unauthorized - Invalid or missing API key |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource doesn't exist |
| 429 | Too Many Requests - Rate limit exceeded |
| 500 | Internal Server Error - Server-side error |
| 503 | Service Unavailable - Temporary outage |

## Rate Limiting

API requests are rate limited to ensure fair usage:

- **Free tier**: 100 requests per hour
- **Pro tier**: 1,000 requests per hour
- **Enterprise tier**: 10,000 requests per hour

Rate limit information is included in response headers:

```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1609459200
```

When you exceed the rate limit, you'll receive a `429` status code:

```json
{
  "status": "error",
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "Rate limit exceeded. Try again in 3600 seconds.",
    "retry_after": 3600
  }
}
```

## Pagination

List endpoints support pagination using query parameters:

```
GET /v1/resources?page=2&per_page=50
```

**Parameters:**
- `page` - Page number (default: 1)
- `per_page` - Items per page (default: 20, max: 100)

**Response includes pagination metadata:**

```json
{
  "status": "success",
  "data": [...],
  "meta": {
    "page": 2,
    "per_page": 50,
    "total_items": 250,
    "total_pages": 5,
    "has_next": true,
    "has_previous": true
  }
}
```

## Filtering and Sorting

Most list endpoints support filtering and sorting:

**Filtering:**

```
GET /v1/resources?status=active&type=processor
```

**Sorting:**

```
GET /v1/resources?sort=created_at&order=desc
```

**Combined:**

```
GET /v1/resources?status=active&sort=name&order=asc&page=1&per_page=25
```

## Webhooks

Subscribe to events using webhooks:

1. Configure webhook URL in your account settings
2. Choose events to subscribe to
3. Receive POST requests when events occur

**Webhook payload:**

```json
{
  "event": "resource.created",
  "timestamp": "2024-01-01T12:00:00Z",
  "data": {
    "id": "123",
    "type": "processor",
    "name": "new-resource"
  }
}
```

**Verifying webhooks:**

Each webhook includes a signature in the `X-Signature` header. Verify it matches:

```
HMAC-SHA256(webhook_secret, request_body)
```

## SDKs and Libraries

Official SDKs are available for popular languages:

**Python:**

```bash
pip install your-software-sdk
```

```python
from your_software import Client

client = Client(api_key="YOUR_API_KEY")
resources = client.resources.list()
```

**JavaScript/Node.js:**

```bash
npm install your-software-sdk
```

```javascript
const { Client } = require('your-software-sdk');

const client = new Client({ apiKey: 'YOUR_API_KEY' });
const resources = await client.resources.list();
```

**Go:**

```bash
go get github.com/your-org/your-software-go
```

```go
import "github.com/your-org/your-software-go"

client := yoursoft.NewClient("YOUR_API_KEY")
resources, err := client.Resources.List()
```

## API Endpoints

### Core Resources

- [Resources](add-an-openapi-specification.md) - Create and manage resources
- [Projects](insert-api-reference-in-your-docs.md) - Manage projects
- [Users](add-an-openapi-specification.md) - User management

### Operations

- [Jobs](add-an-openapi-specification.md) - Run and monitor jobs
- [Tasks](insert-api-reference-in-your-docs.md) - Task management
- [Logs](add-an-openapi-specification.md) - Access logs

### Administration

- [API Keys](add-an-openapi-specification.md) - Manage API keys
- [Webhooks](insert-api-reference-in-your-docs.md) - Configure webhooks
- [Settings](add-an-openapi-specification.md) - Account settings

## API Versioning

We use URL-based versioning:

```
https://api.yourcompany.com/v1/resources
https://api.yourcompany.com/v2/resources
```

**Version support:**
- v1: Current stable version
- v2: Beta - New features, subject to change

We maintain backward compatibility within major versions. Major version changes are announced 6 months in advance.

## Example Use Cases

### Creating a Resource

```bash
curl -X POST https://api.yourcompany.com/v1/resources \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "my-resource",
    "type": "processor",
    "config": {
      "timeout": 30
    }
  }'
```

### Listing Resources

```bash
curl -X GET https://api.yourcompany.com/v1/resources?status=active \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Updating a Resource

```bash
curl -X PUT https://api.yourcompany.com/v1/resources/123 \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "updated-resource"
  }'
```

### Deleting a Resource

```bash
curl -X DELETE https://api.yourcompany.com/v1/resources/123 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## Error Handling

Always check the status code and handle errors appropriately:

```python
import requests

response = requests.get(
    'https://api.yourcompany.com/v1/resources',
    headers={'Authorization': 'Bearer YOUR_API_KEY'}
)

if response.status_code == 200:
    data = response.json()
    # Process data
elif response.status_code == 401:
    print("Invalid API key")
elif response.status_code == 429:
    retry_after = response.headers.get('Retry-After')
    print(f"Rate limited. Retry after {retry_after} seconds")
else:
    error = response.json()
    print(f"Error: {error['error']['message']}")
```

## Testing

Use our sandbox environment for testing:

```
https://api-sandbox.yourcompany.com/v1
```

Sandbox features:
- No rate limits
- Test data automatically reset daily
- No charges for API usage

## Need Help?

- [API Guides](../guides/) - Detailed guides and tutorials
- [Code Examples](../guides/adding-custom-code-samples.md) - Sample code
- [Support](../../help/support.md) - Get help from our team
- [Changelog](https://github.com/your-org/api-changelog) - API changes

{% hint style="info" %}
**API Status**: Check our [status page](https://status.yourcompany.com) for real-time API health and incident reports.
{% endhint %}
