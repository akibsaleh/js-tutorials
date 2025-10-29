# 05. MongoDB with Mongoose

## Install
```bash
npm i @nestjs/mongoose mongoose
```

## Setup
```ts
// app.module.ts
import { MongooseModule } from '@nestjs/mongoose';

@Module({
  imports: [
    MongooseModule.forRoot('mongodb://localhost:27017/catalog'),
  ],
})
export class AppModule {}
```

## Define a Model
```ts
// product.schema.ts
import { Prop, Schema, SchemaFactory } from '@nestjs/mongoose';
import { HydratedDocument } from 'mongoose';

export type ProductDocument = HydratedDocument<Product>;

@Schema({ timestamps: true })
export class Product {
  @Prop({ required: true }) name: string;
  @Prop({ required: true }) price: number;
}

export const ProductSchema = SchemaFactory.createForClass(Product);
```

```ts
// products.module.ts
@Module({
  imports: [
    MongooseModule.forFeature([{ name: Product.name, schema: ProductSchema }]),
  ],
  providers: [ProductsService],
  controllers: [ProductsController],
})
export class ProductsModule {}
```

Source: NestJS Mongoose docs.
