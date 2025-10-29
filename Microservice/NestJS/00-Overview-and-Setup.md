# 00. Overview & Setup

- We build small NestJS services that talk using sync (HTTP/gRPC) and async (Redis/NATS/etc.).
- Databases per service: Postgres (via Prisma) and MongoDB (via Mongoose). Redis for cache and pub/sub.

## Prerequisites
- Node.js LTS, npm.
- Docker (for local databases/Redis).
- Nest CLI: `npm i -g @nestjs/cli`

## Create a Service
```bash
nest new users-service
cd users-service
npm i @nestjs/microservices
```

## Start a Microservice (TCP)
```ts
// main.ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import { Transport, MicroserviceOptions } from '@nestjs/microservices';

async function bootstrap() {
  const app = await NestFactory.createMicroservice<MicroserviceOptions>(AppModule, {
    transport: Transport.TCP,
    options: { host: '0.0.0.0', port: 3001 },
  });
  await app.listen();
}
bootstrap();
```

## Client to Call a Microservice
```ts
// app.module.ts
import { Module } from '@nestjs/common';
import { ClientsModule, Transport } from '@nestjs/microservices';

@Module({
  imports: [
    ClientsModule.register([
      { name: 'USERS_CLIENT', transport: Transport.TCP, options: { port: 3001 } },
    ]),
  ],
})
export class AppModule {}
```

## gRPC Example
```ts
// create gRPC microservice
import { join } from 'path';
const app = await NestFactory.createMicroservice(AppModule, {
  transport: Transport.GRPC,
  options: {
    package: 'hero',
    protoPath: join(__dirname, 'hero/hero.proto'),
  },
});
```

Sources: NestJS docs (microservices basics, gRPC, hybrid apps).
