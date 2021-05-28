# Layer0 Traditional Template

The repository for the layer0 Traditional template.

Layer0 for Traditional Sites enables traditional Server Side Rendered websites (i.e. jQuery, PHP, VanillaJS, etc.) to take advantage of the performance benefits of Layer0's advanced caching and predictive prefetching.

## Documentation

Visit [documentation](https://docs.layer0.co/guides/traditional_sites) for more details.

## Getting Started

Make sure to use NodeJS 12.x

Clone the repo, and in your terminal run:
```
npm install
```

This will install all dependencies and link interdependent package.

## Example Workflow

### Step 1)
Update *layer0.config.js*, *package.json*, *shoppingFlowRouteHandler.ts* with your project domain name.

### Step 2)
Next we need to configure the caching in our newly created project. To do so, add a route for each URL you want to cache to the *routes.ts*

Refer to the guides on [Routing](https://docs.layer0.co/guides/routing) and [Caching](https://docs.layer0.co/guides/caching) for the full syntax to use in your *routes.js* file.

You should be able to run your project using:
```
npm start
```

Caching is turned off during development. This is done to ensure that developers don't see stale responses after making changes to their code or other upstream APIs. If you want to use cacheing function in development run your server with following command:
```
layer0 run --cache
```

### Step 3)
By default, only HTML content is prefetched. In order to achieve truly instant page transitions, all of the assets needed to render the content that appears above the fold need to be prefetched. These typically include images, CSS, and JavaScript.

In order to prefetch Images, CSS & JavaSCript go into your *service-worker.ts* file and update selectors.

Refer to the guides on [Deep Fetching](https://app.layer0.co/guides/traditional#section_deep_fetching) for the full syntax to use in your *service-worker.ts* file.

## Deploying an App

To deploy your site, you must first sign up for an account. [Sign up here for free](https://app.layer0.co/signup). 
Once you have an account, you can deploy your site using the deploy command:
```
layer0 deploy --team=[team-name]
```
