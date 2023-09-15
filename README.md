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
  
