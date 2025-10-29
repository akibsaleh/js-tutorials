# 04. PostgreSQL with Prisma

## Install
```bash
npm i -D prisma
npm i @prisma/client
npx prisma init
```

## Configure PostgreSQL
.env
```bash
DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/mydb?schema=public"
```

schema.prisma
```prisma
datasource db { provider = "postgresql"; url = env("DATABASE_URL") }
generator client { provider = "prisma-client-js" }

model User {
  id    Int    @id @default(autoincrement())
  email String @unique
  name  String?
}
```

## Migrate
```bash
npx prisma migrate dev --name init
```

## Use in NestJS
```ts
// prisma.service.ts
import { INestApplication, Injectable, OnModuleInit } from '@nestjs/common';
import { PrismaClient } from '@prisma/client';

@Injectable()
export class PrismaService extends PrismaClient implements OnModuleInit {
  async onModuleInit() { await this.$connect(); }
  async enableShutdownHooks(app: INestApplication) {
    this.$on('beforeExit', async () => { await app.close(); });
  }
}
```

```ts
// users.service.ts
import { Injectable } from '@nestjs/common';
import { PrismaService } from './prisma.service';

@Injectable()
export class UsersService {
  constructor(private prisma: PrismaService) {}
  create(data: { email: string; name?: string }) {
    return this.prisma.user.create({ data });
  }
}
```

Source: Prisma PostgreSQL docs.
