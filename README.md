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


# Layer0 Software Engineer, Solution Engineering Candidate Assignment 

We value your time and we don’t want to take more of your time than necessary, so the target is to **spend no more than 2 hours on the assignment. **

Note: This guide assumes that you’re using a Mac. Please let us know if you’re using a different device.

### Part 1 - Layer0 Traditional Implementation Exercise (1 hr 20 mins)
1. Clone [this repo](https://github.com/moovweb-demos/candidate-assignment) (2 mins)
2. Read through https://docs.layer0.co/guides/traditional_sites (20 mins)
3. Create an account at layer0 here https://app.layer0.co/signup (2 mins)
4. Install layer0 CLI as described here https://docs.layer0.co/guides/cli (2 mins)
5. In your terminal, cd into the cloned repo and run ```npm install``` to install the packages needed to run the project (2 mins)
6. Open the repo in your favourite code editor
7. In your terminal, run ```npm start``` or ```layer0 run``` to start the project (1 min)
8. In your browser open an incognito window, enable developer tools, enable device emulation for a mobile device, go to http://127.0.0.1:3000 and browse to a Product Listing Page (PLP) from the menu such as /c/mattresses/all-mattresses
9. Observe the following:
    * How the Layer0 Devtools is loaded on top of the viewport and the relevant information that it provides
    * In the Chrome Dev Tools » Applications tab, 
        * that the service worker is running
        * that the prefetch cache under the Cache Storage is populated
10. In your editor, look at the following files
    * routes.ts,
    * shoppingFlowRouteHandler.ts
    * service-worker.ts
11. Observe how the PLP HTML doc as well as some images are being cached and prefetched by looking at the Layer0 devtools as well as the network tab and application tab, that the prefetch cache under the Cache Storage is populated
12. Implement the Product Description Page so that the main doc is cached and prefetched as well as the main image on the PDP and anything else that can potentially speed up the initial render and [Largest Contentful Paint](https://web.dev/lcp/) times. (30 mins)
13. Add your code to a github repo and share with the following gh handles (patricksaw, howdiz, letrest)
14. Deploy your project to https://app.layer0.co 
Write up what you’ve intended to accomplish, what you’d do as next steps if you had more time and any feedback you may have for layer0 regarding the process. Add those to the GH Readme. (20 mins)

### Part 2 - Performance Comparison (30 - 45 minutes)
Run [WebPageTests](https://www.webpagetest.org/) with the following settings:
Connection: LTE
Number of Tests to Run: 3
Repeat View: First View Only
Capture Video: checked

on both the source site (domain) and the demo site you deployed for a PDP and share the results with us.

On the scripts tab, write a script that navigates to a PLP, scroll to a product item, then waits 5 seconds and clicks on that product item.

Compare the two sets of tests. Identify and write up the performance improvements and an area for additional improvement.
