---
description: 'How to post stats using Node.js, JavaScript, or TypeScript.'
---

# Node.js

## Install the Package

Install the package using NPM:

```
$ npm i -S @dbots-co/stats
```

{% hint style="info" %}
 Make sure to install the latest version for the latest updates.
{% endhint %}

Simple package to easily post stats to [dbots.co](https://dbots.co). By default it posts stats every 5 minutes. It uses discord.js to login and post stats.

### NodeJS

```javascript
const { PostStats } = require('@dbots/stats');

const stats = new PostStats({
  apiToken: '<your_bot_api_token>',
  botToken: '<your_bot_token>'
});

stats.on('postStats', (res) => console.log(res.ok ? 'Posted stats.' : 'Failed to post stats.'));
```

### TypeScript / ES6

```typescript
import { PostStats } from '@dbots/stats';

const stats = new PostStats({
  apiToken: '<your_bot_api_token>',
  botToken: '<your_bot_token>'
});

stats.on('postStats', (res) => console.log(res.ok ? 'Posted stats.' : 'Failed to post stats.'));
```

#### Options

```typescript
export interface PostStatsOptions {
  /** API Token - https://dbots.co/dashboard/bots/[yourBotId]/api  */
  apiToken: string;
  /** Bot token - https://discord.com/developers. */
  botToken: string;
  /** Interval to to post stats in minutes.
   * @default 5 */
  interval?: number;
}
```

