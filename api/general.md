---
description: Interact with DBots through HTTP requests.
---

# General

### Status Codes

| Code | Description |
| :--- | :--- |
| 200 | OK. |
| 201 | Created. |
| 400 | Bad request. |
| 401 | Unauthorized. |
| 404 | Not found. |
| 429 | Too many requests - You are being rate limited. |
| 500 | Internal server error. |

**API Error Examples**: `{ message: 'Bad Request' }`

### Headers

The API key is used for dealing with bot stats.

#### API Key

```javascript
{
  "Authorization": "<api_key>"
}
```

#### User Key

The user key is provided by Discord, and is used for storing user sessions and logging in the Discord user.

```javascript
{
  "Authorization": "<user_token>"
}
```

### Default API Response

```typescript
{
  message: string;
  code: number;
}
```

### Rate Limiting

DBots uses rate limiting to reduce API abuse.

A maximum of _600 requests_ can be sent _per 10 minutes_.

### Vote Webhook

This is what is posted to a bots **Vote Webhook URL**, when a bot is voted for.

#### Response

**Schema**:

```typescript
{
  at: Date; // JSON date when of vote
  by: string; // id of user that votes
}
```

**Example**: `{ at: "2020-08-07T12:56:27.100Z", by: "218459216145285121" }`

