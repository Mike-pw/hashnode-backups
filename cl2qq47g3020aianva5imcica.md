## Replace koa-shopify-graphql-proxy when Migrating to Cookie-less Auth

Recently I was migrating an embedded Shopify app from cookie based authentication to use [session tokens](https://shopify.dev/apps/auth/oauth/session-tokens). The app was using [koa-shopify-graphql-proxy](https://www.npmjs.com/package/@shopify/koa-shopify-graphql-proxy) to proxy requests from the frontend, to Shopify's GraphQL API. I wanted to use [shopify-api](https://www.npmjs.com/package/@shopify/shopify-api) instead.

On the frontend I had Apollo client setup to use authenticatedFetch to send requests to the backend. I needed a way to use verifyRequest to check the incoming session tokens in the authorization header. 

The following packages were required;

```javascript
const Koa = require('koa');
const { default: createShopifyAuth } = require('@shopify/koa-shopify-auth');
const { verifyRequest } = require('@shopify/koa-shopify-auth');
const Router = require('koa-router');
const koaBody = require('koa-body');
const Shopify = require('@shopify/shopify-api').Shopify;

``` 

Initialized server and router;

```javascript
    const server = new Koa()
    const router = new Router()
``` 

You will need to have [implemented OAuth](https://shopify.dev/apps/auth/oauth) with Shopify. Shopify [App Bridge](https://shopify.dev/apps/tools/app-bridge) is used to make authenticated requests from the frontend, with valid session tokens in the authorization header.

For the incoming requests to /graphql;

```javascript
  router.post('/graphql', koaBody(), verifyRequest({returnHeader: true}), async (ctx) => {
    const session = await Shopify.Utils.loadCurrentSession(ctx.request, ctx.response, false);
    const { shop, accessToken } = session;
    const options = {
      data: ctx.request.body,
    };
    const client = new Shopify.Clients.Graphql(shop, accessToken);
    const response = await client.query(options);
    ctx.status = 200;
    ctx.body = response.body
  }
);
``` 

I used koaBody from [koa-body](https://www.npmjs.com/package/koa-body) to parse the request body, and then pass it to the shopify-api GraphQL client.




