# 06. Redis Integration

We use Redis for caching, pub/sub, and rate limiting.

## Install
```bash
npm i redis
```

## Create Client
```ts
import { createClient } from 'redis';

export const redisClient = await createClient()
  .on('error', err => console.log('Redis Client Error', err))
  .connect();
```

## Cache Example
```ts
await redisClient.set(`user:${id}`, JSON.stringify(user), { EX: 60 });
const cached = await redisClient.get(`user:${id}`);
```

## Pub/Sub Example
```ts
const sub = createClient();
await sub.connect();
await sub.subscribe('user.created', (message) => { /* handle */ });

await redisClient.publish('user.created', JSON.stringify({ id: 'u1' }));
```

Sources: node-redis getting-started and examples.
