# 02. Communication Patterns

## Request/Response (TCP, gRPC, HTTP)
```ts
// Controller in a microservice
import { Controller } from '@nestjs/common';
import { MessagePattern } from '@nestjs/microservices';

@Controller()
export class UsersController {
  @MessagePattern({ cmd: 'get_user' })
  getUser(id: string) { /* ... */ }
}
```

```ts
// Client sending a request
this.client.send({ cmd: 'get_user' }, userId).pipe(/* timeout, retry */);
```

## Events (Pub/Sub)
```ts
// Emit event (fire-and-forget)
this.client.emit('user.created', { id: 'u1' });
```

## Timeouts and Retries
```ts
import { timeout, retry } from 'rxjs/operators';
this.client.send({ cmd: 'get_user' }, id).pipe(timeout(3000), retry(2));
```

## Multiple Transports (Hybrid)
```ts
const app = await NestFactory.create(AppModule);
app.connectMicroservice({ transport: Transport.TCP, options: { port: 3001 } });
app.connectMicroservice({ transport: Transport.REDIS, options: { host: 'localhost', port: 6379 } });
await app.startAllMicroservices();
await app.listen(3000);
```

Sources: NestJS microservices basics, hybrid app docs.
