# wildgrove.dev

`wildgrove.dev` is an Astro-backed static site. Day-to-day development still happens with Astro's local development server, while Docker gives the project a production-style build and serving workflow.

## Externalized Content and Assets

The site keeps post content and shared visual assets in separate repositories that are mounted as Git submodules:

- `content` stores posts and curated site data
- `public/assets` stores public images, logos, fonts, and other static assets

## Development Workflow

Astro's local development server is used for site work:

```bash
npm run dev
```

The Docker setup provides a production-style local serving path:

- a multi-stage `Dockerfile` builds the site with Node
- `nginx` to serve the generated `dist/` output
- `compose.yml` runs the containerized site on `http://localhost:8080`

Containerized local run:

```bash
docker compose up --build
```

## Deployment

The public site is deployed with Cloudflare Pages. The Cloudflare project builds from the GitHub repository and serves Astro's generated static output.

Cloudflare Pages settings:

- build command: `npm run build`
- build output directory: `dist`
- submodules: enabled through the GitHub checkout workflow

## Project Commands

Astro build:

```bash
npm run build
```

Docker image build:

```bash
docker build -t wildgrove-dev .
```

Docker image run:

```bash
docker run --rm -p 8080:80 wildgrove-dev
```
