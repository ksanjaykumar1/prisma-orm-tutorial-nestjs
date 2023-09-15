## Installation

```bash
$ yarn install
```

## Running the app

```bash
# development
$ yarn run start

# watch mode
$ yarn run start:dev

# production mode
$ yarn run start:prod
```

## Test

```bash
# unit tests
$ yarn run test

# e2e tests
$ yarn run test:e2e

# test coverage
$ yarn run test:cov
```

## Steps

1. yarn add -d primsa
2. yarn prima init : This will create a new prisma directory with a schema.prisma file. This is the main configuration file that contains your database schema. This command also creates a .env file inside your project.
3. Add the db url in env
   ```
   ex: DATABASE_URL="postgres://myuser:mypassword@localhost:5432/median-db"
   ```
4. Mirgation: manually creating data models and then migrated to create table based on data model in the database

   ```
   yarn prisma migrate dev --name init
   ```

5.

## Notes on Prisma

1. How to create 1 to 1 realtionship
   ```
    model User {
    id Int @id @default(autoincrement())
    email String @unique
    name String
    role Role @default(USER)
    profile Profile?
   }
   ```

model Profile {
id Int @id @default(autoincrement())
bio String
userId Int @unique
user User @relation(fields: [userId], references: [id])
}

1 to 1 relation between user and profile tables. userId in profile will get value from id in User table

```
2.  How to create 1 to many relationship

```

model User {
id Int @id @default(autoincrement())
email String @unique
name String
role Role @default(USER)
profile Profile?
posts Post[]
}

model Profile {
id Int @id @default(autoincrement())
bio String
userId Int @unique
user User @relation(fields: [userId], references: [id])
}

model Post {
id Int @id @default(autoincrement())
authorId Int
title String
createdAt DateTime @default(now())
updatedAt DateTime @updatedAt
published Boolean @default(false)
author User @relation(fields: [authorId], references: [id])

}

```
1 to  many relation between user and post

3. Many to many relation   (n-m)

```

model Post {
id Int @id @default(autoincrement())
authorId Int
title String
createdAt DateTime @default(now())
updatedAt DateTime @updatedAt
published Boolean @default(false)
author User @relation(fields: [authorId], references: [id])
categories Category[]

}

model Category{
id Int @id @default(autoincrement())
name String
posts Post[]
}

```
Just create array of the model type inside each model
```
