# kanehara.github.io

> Yohei Kanehara's portfolio website hosted on Cloudflare Workers

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# deploy to Cloudflare Workers
npm run deploy
```

## Cloudflare Workers Deployment

This site is deployed using Cloudflare Workers. The worker configuration is in `wrangler.toml` and the worker script is in `worker/index.js`.

To deploy:
1. Install Wrangler CLI: `npm install -g wrangler`
2. Configure your Cloudflare account: `wrangler login`
3. Deploy: `npm run deploy`

## Tech Stack

- Vue.js 2.x for the frontend framework
- Webpack for bundling
- Cloudflare Workers for hosting
- KV Asset Handler for serving static assets
