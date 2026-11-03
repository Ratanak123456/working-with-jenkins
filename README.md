# Spring Café

A static, responsive café landing page built with the existing React 19, Vite 8, and Tailwind CSS 4 setup. All drink illustrations are local CSS; no external images, fonts, APIs, or backend are required.

## Run locally

```sh
npm install
npm run dev
```

## Production

```sh
npm run build
npm run preview
```

Deploy the generated `dist/` directory with your static web server. `npm run preview` is for checking the production build locally.

## Docker

Build the image and start the production server:

```sh
docker compose up --build -d
```

Open http://localhost:3000. The container runs `server.mjs` to serve the built
React app and exposes a health check at http://localhost:3000/health.
Compose sets the hostname to `web-01`, so the server badge displays `WEB-01`.
To use a different host port, run `WEB_PORT=8080 docker compose up --build -d`.

Build only, or stop the service:

```sh
docker compose build
docker compose down
```

To build and run without Compose:

```sh
docker build -t spring-cafe:latest .
docker run --rm --init --hostname web-01 -p 3000:3000 spring-cafe:latest
```

## Server badge

The production server injects its hostname into the page at runtime. Set the
container hostname (for example, `web-02`) to change the badge without rebuilding
the image. With the Vite development or preview server, the badge shows `LOCAL DEV`.

Menu content is in the `drinks` array in `src/App.jsx`. Opening hours, address, and contact details are sample content. Navigation links scroll to page sections; there is no ordering functionality.
