---
description: General bot routes for interacting with the DBots API.
---

# Bots

{% api-method method="get" host="https://dbots.co/api/v1" path="/bots" %}
{% api-method-summary %}
All Bots
{% endapi-method-summary %}

{% api-method-description %}
Get all bots on the bot list.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Sends all bot documents, and saved bots.
{% endapi-method-response-example-description %}

```typescript
{
    saved: [BotDocument],
    users: [User]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://dbots.co/api/v1" path="/bots/user" %}
{% api-method-summary %}
User Bots
{% endapi-method-summary %}

{% api-method-description %}
Get all bots owned by a user. User must be logged in.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Key of the logged in user.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns partial users, and saved bot documents.
{% endapi-method-response-example-description %}

```
{
    partialUsers: [PartialUser],
    saved: [BotDocument]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User is not logged in.
{% endapi-method-response-example-description %}

```
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://dbots.co/api/v1" path="/:id" %}
{% api-method-summary %}
Specific Bot
{% endapi-method-summary %}

{% api-method-description %}
Get a specific saved bot document, and bot user.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Get a specific saved bot document, and bot user.
{% endapi-method-response-example-description %}

```typescript
{
    saved: {
        _id: string;
        approvedAt: Date;
        badges: BotBadge[];
        createdAt: Date;
        feedback: Feedback[];
        listing: Listing;
        ownerId: string;
        stats: { guildCount: number },
        totalVotes: number;
        lastVoteAt: Date;
        votes: Vote[];
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Bot was not found in a mutual guild to the website bot.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Not found' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://dbots.co/api/v1" path="/bots/:id/vote" %}
{% api-method-summary %}
Vote For Bot
{% endapi-method-summary %}

{% api-method-description %}
Vote for a bot. A user can only vote once every 12 hours. User must be logged in.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Votes for bot, and sends back registered vote.
{% endapi-method-response-example-description %}

```typescript
{
    at: Date;
    by: string;
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User is not logged in.
{% endapi-method-response-example-description %}

```
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Bot does not exist in database.
{% endapi-method-response-example-description %}

```
{ message: 'Not found' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

