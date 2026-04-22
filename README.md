# wildgrove.dev

`wildgrove.dev` is an Astro backed static site. Day-to-day development still happens with Astro's local development server, while Docker gives the project a production-style build and serving workflow.

## Local Development

Use Astro's dev server when you are actively building the site:

```bash
npm run dev
```

## Docker Workflow

The Docker setup uses:

- a multi-stage `Dockerfile` to build the site with Node
- `nginx` to serve the generated `dist/` output
- `compose.yml` to start the site locally with one command

Start the containerized site locally:

```bash
docker compose up --build
```

Then open `http://localhost:8080`.

## Useful Commands

Build the Astro site without Docker:

```bash
npm run build
```

Build the Docker image directly:

```bash
docker build -t wildgrove-dev .
```

Run the Docker image directly:

```bash
docker run --rm -p 8080:80 wildgrove-dev
```
