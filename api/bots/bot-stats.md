---
description: >-
  Bot stats for bots on DBots.co that can be used to make graphs and cool
  things.
---

# Bot Stats

{% api-method method="post" host="https://dbots.co/api/v1" path="/bots/:id/stats" %}
{% api-method-summary %}
Post Bot Stats
{% endapi-method-summary %}

{% api-method-description %}
Get stats of a specific bot. Must provide bot API token.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
API Token of the bot. 
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns updated bot stats.
{% endapi-method-response-example-description %}

```javascript
{ guildCount: number; }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
API Token is invalid, or not provided.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Bot was not found in the database.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Not found' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://dbots.co/api/v1" path="/bots/:id/log" %}
{% api-method-summary %}
Get Log
{% endapi-method-summary %}

{% api-method-description %}
Get the bot audit log. Must be logged in.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Key of the logged in user.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Bot audit log is sent.
{% endapi-method-response-example-description %}

```typescript
{
  _id: string;
  changes: {
    at: Date,
    by: string,
    changes: { old: {}, new: {} }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Logged in user cannot manage this bot.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Bot not manageable' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User is not logged in.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://dbots.co/api/v1" path="/bots/:id/keys/regen" %}
{% api-method-summary %}
Regenerate Key
{% endapi-method-summary %}

{% api-method-description %}
Regenerate the bot API token. Must be logged in.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Key of the logged in user.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Regenerated bot API token is sent back.
{% endapi-method-response-example-description %}

```typescript
token: string;
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
User cannot manage this bot.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Bot not manageable' } 
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User is not logged in.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://dbots.co/api/v1" path="/bots/:id/api" %}
{% api-method-summary %}
Get API Document
{% endapi-method-summary %}

{% api-method-description %}
Get a bot API document.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Key of the logged in user.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Sends back the bot API document.
{% endapi-method-response-example-description %}

```typescript
{
  _id: string;
  token: string;
  voteWebhookURL: string;
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
User cannot manage this bot.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Bot not manageable' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User is not logged in.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="patch" host="https://dbots.co/api/v1" path="/bots/:id/api" %}
{% api-method-summary %}
Edit API Document
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Key of the logged in user.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Sends updated API document.
{% endapi-method-response-example-description %}

```typescript
{
  _id: string;
  token: string;
  voteWebhookURL: string;
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
User cannot manage this bot.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Bot not manageable' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User is not logged in.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



