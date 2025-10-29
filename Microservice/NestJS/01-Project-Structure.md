# 01. Project Structure

Keep each service small and focused. Example for `users-service`:

```
users-service/
  src/
    app.module.ts
    main.ts
    users/
      users.module.ts
      users.controller.ts
      users.service.ts
      dto/
      entities/
  test/
  package.json
```

Tips
- One repo per service, or a monorepo with clear boundaries.
- Keep controllers thin; put rules in services.
- Use DTOs for validation.
- Environment config in one place.
