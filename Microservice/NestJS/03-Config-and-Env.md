# 03. Config & Env

- Use `@nestjs/config` to read environment variables.
- Keep secrets out of code. Use `.env` for local only.

```ts
// app.module.ts
import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';

@Module({
  imports: [ConfigModule.forRoot({ isGlobal: true })],
})
export class AppModule {}
```

```ts
// main.ts - dynamic microservice options
import { ConfigService } from '@nestjs/config';
const app = await NestFactory.createMicroservice(AppModule, {
  useFactory: (config: ConfigService) => ({
    transport: Transport.TCP,
    options: { host: config.get('HOST'), port: config.get('PORT') },
  }),
  inject: [ConfigService],
});
```
