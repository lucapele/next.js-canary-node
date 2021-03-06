# Using multiple zones

## How to use

### Using `create-next-app`

Execute [`create-next-app`](https://github.com/segmentio/create-next-app) with [Yarn](https://yarnpkg.com/lang/en/docs/cli/create/) or [npx](https://github.com/zkat/npx#readme) to bootstrap the example:

```bash
npx create-next-app --example with-zones with-zones-app
# or
yarn create next-app --example with-zones with-zones-app
```

### Download manually

Download the example:

```bash
curl https://codeload.github.com/zeit/next.js/tar.gz/canary | tar -xz --strip=2 next.js-canary/examples/with-zones
cd with-zones
```

## The idea behind this example

With Next.js you can use multiple apps as a single app using it's [multi-zones feature](https://nextjs.org/docs#multi-zones). This is an example showing how to use it.

In this example, we have two apps: 'home' and 'blog'. We'll start both apps with [Now](https://zeit.co/now):

```bash
now dev
```

Then, you can visit <http://localhost:3000> and develop for both apps as a single app.

You can also start the apps separately, for example:

```bash
cd blog
yarn dev
```

## Special Notes

- All pages should be unique across zones. For example, the 'home' app should not have a `pages/blog/index.js` page.
- The 'blog' app sets `assetPrefix` so that generated JS bundles are within the `/blog` subfolder.
    - To also support the plain `next dev` scenario, `assetPrefix` is set dynamically based on the `BUILDING_FOR_NOW` environment variable, see [`now.json`](now.json) and [`blog/next.config.js`](blog/next.config.js).
    - Images and other `/static` assets have to be prefixed manually, e.g., ``<img src={`${process.env.ASSET_PREFIX}/static/image.png`} />``, see [`blog/pages/blog/index.js`](blog/pages/blog/index.js).

## Production Deployment

We only need to run `now`, the same `now.json` used for development will be used for the deployment:

```bash
now
```
