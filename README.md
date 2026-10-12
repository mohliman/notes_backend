# Notes API

A small Express API for creating, listing, reading, and deleting sample notes. It demonstrates HTTP routes, JSON request bodies, validation, and frontend serving.

## Stack

Node.js · Express · CORS · nodemon

`index.js` contains the routes and in-memory note collection. Express serves the bundled frontend from `dist/` and listens on `PORT`, defaulting to 3001.

## Run locally

Use Node.js 24 and npm.

```sh
npm ci
npm run dev
```

Open `http://127.0.0.1:3001`. Use `npm start` to run without the development watcher. To change the port, set `PORT` in your shell before starting the server.

## API

| Method | Route | Behavior |
| --- | --- | --- |
| GET | `/api/notes` | List all notes |
| GET | `/api/notes/:id` | Read one note; return 404 if absent |
| POST | `/api/notes` | Create a note; return 400 if `content` is missing |
| DELETE | `/api/notes/:id` | Remove a note; return 204 |

Example POST body:

```json
{
  "content": "Learn Express routing",
  "important": true
}
```

The server assigns an identifier and creation date. If `important` is omitted, it defaults to false.

## Scope

Notes are stored in memory and reset when the server restarts. There is no database, authentication, or authorization. This is a learning project for sample data, with CORS enabled and no automated test suite; `npm test` is a placeholder.

The `build:ui` helper expects a sibling `part2-notes-frontend/` checkout, which is not included here. The committed `dist/` provides the existing frontend bundle.

Related work: [Full Stack Open exercises](https://github.com/mohliman/FullStackOpen) · [Phonebook API with MongoDB persistence](https://github.com/mohliman/Phonebook_backend_server)
