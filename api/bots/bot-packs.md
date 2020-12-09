---
description: Bot Pack API for DBots.co.
---

# Bot Packs

{% api-method method="get" host="https://dbots.co/api/v1" path="/packs" %}
{% api-method-summary %}
Get All Packs
{% endapi-method-summary %}

{% api-method-description %}
Get all bot unpopulated packs.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns array of unpopulated bot packs.
{% endapi-method-response-example-description %}

```typescript
[
    {
        _id: string;
        bots: BotDocument[];
        createdAt: Date;
        description: string;
        owner: UserDocument;
        updatedAt: Date;
        votes: number;
    }
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://dbots.co/api/v1" path="/packs/:id" %}
{% api-method-summary %}
Get Specific Pack
{% endapi-method-summary %}

{% api-method-description %}
Sends an array of populated bot packs.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot pack.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Sends an array of populated bot packs.
{% endapi-method-response-example-description %}

```typescript
{
    _id: string;
    bots: BotDocument[];
    createdAt: Date;
    description: string;
    owner: UserDocument;
    updatedAt: Date;
    votes: number;
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Bot pack was not found in the database.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Not found.' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://dbots.co/api/v1" path="/packs" %}
{% api-method-summary %}
Create Pack
{% endapi-method-summary %}

{% api-method-description %}
Create a new pack. User must be logged in.  
The maximum packs a user can create is 5.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Key of logged in user.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
Duplicate ID pack is created, name is changed.
{% endapi-method-response-example-description %}

```typescript
{
    _id: string;
    bots: BotDocument[];
    createdAt: Date;
    description: string;
    owner: UserDocument;
    updatedAt: Date;
    votes: number;
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
User owns the max amount of packs \(5\).
{% endapi-method-response-example-description %}

```javascript
{ message: 'Max bot pack limit reached.' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User must be logged in and send key through headers.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized.' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="patch" host="https://dbots.co/api/v1" path="/packs/:id" %}
{% api-method-summary %}
Edit Pack
{% endapi-method-summary %}

{% api-method-description %}
Edit a bot pack. User must be logged in and must own the pack.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot pack.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Key of logged in user.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns edited, unpopulated bot pack.
{% endapi-method-response-example-description %}

```
{
    _id: string;
    bots: BotDocument[];
    createdAt: Date;
    description: string;
    owner: UserDocument;
    updatedAt: Date;
    votes: number;
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User not logged in.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{ message: 'Bot pack does not exist' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### 

{% api-method method="delete" host="https://dbots.co/api/v1" path="/packs/:id" %}
{% api-method-summary %}
Delete Pack
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot pack.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Key of thge logged in user.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Bot pack was successfully deleted.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Success' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User is not logged in or an authorization header was not authorized.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Bot pack does not exist in the database.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Bot pack does not exist' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://dbots.co/api/v1" path="/packs/:id/vote" %}
{% api-method-summary %}
Vote For Bot Pack
{% endapi-method-summary %}

{% api-method-description %}
Vote for a bot pack. Must be logged in.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the bot pack.
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
Returns unpopulated bot pack, with new votes.
{% endapi-method-response-example-description %}

```typescript
{
    _id: string;
    bots: BotDocument[];
    createdAt: Date;
    description: string;
    owner: UserDocument;
    updatedAt: Date;
    votes: number;
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
User not logged in, or no authorization header provided.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Unauthorized' }
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Bot pack does not exist in database.
{% endapi-method-response-example-description %}

```javascript
{ message: 'Not found' }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

