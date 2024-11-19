## HTTP server example

An example server that queries a `users` table in Postgres and returns results either as JSON or HTML.

### start the db

`docker-compose up`

### create a table for the app

```sql
create table if not exists users
(
  id         text primary key,
  first_name text,
  last_name text
);
```

### install modules

`npm install`

### develop with the nREPL

1. start nREPL server `npx squint nrepl-server :port 1888`
2. connect an editor

### compile and run

```
npx squint compile
node target/server.js
```

try queries

```
# add a user
curl -v -X POST -H "Content-Type: application/json" -d '{"id": "foo", "first_name": "Bob", "last_name": "Bobberton"}' http://localhost:3000/user

# search for a user
curl http://localhost:3000/search?id=foo

# load home page
curl http://localhost:3000/
```