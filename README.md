# Layer0 Software Engineer, Solution Engineering Candidate Assignment 

We value your time and we don’t want to take more of your time than necessary, so the target is to **spend no more than 2 hours on the assignment.**

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
15. **Write up what you’ve intended to accomplish, what you’d do as next steps if you had more time and any feedback you may have for layer0 regarding the process. Add those to the GH Readme:**

    * Adding the PDP to the Router was a one-line task. Super easy.
    * Attempted to remove the setTimeout in `browser.ts` file (it was generating errors). I failed but it's ok :)
    * My next steps would be:
        * In the `routes.ts` file, move the route match functions/callbacks to its own file(s). Because for very large sites this file would be huge. Also they can be reused (see `/static/:path*`, `/assets/:path*`, `/api/:path*` use the same function). Plus it's cleaner to have one `match(...)` per line: easy to spot which one to touch.
        * In the `browser.ts` file, I didn't like to see the `setTimeout` there. From the documentation (where the setTimeout is not used in the example), I thought that internally the `install` function would be using a MutationObserver, which is better than waiting until the entire DOM has loaded. Also, 1000ms wait is too much time.
    * Some feedback:
        * Although the preload strategy is a simple concept, I'd like to know if there's more about how the prediction happens in layer0 (besides links/hover content/routes) and, how the cache is split and delivered by chunks (bottlenecks can be faced in the delivery, right?). Also, are you already thinking in a way to cache 'lazy loaded' content? The prefetching based on element visibility seems like the workaround, though.
        * Finally, thanks: it feels good to know something new, and no matter the outcome of the process, I'll keep learning from your docs in the next days.

### Part 2 - Performance Comparison (30 - 45 minutes)
Run [WebPageTests](https://www.webpagetest.org/) with the following settings under Advanced Settings > Test Settings:
* Connection: LTE
* Number of Tests to Run: 3
* Repeat View: First View Only
* Capture Video: checked

and under Advanced Settings > Chromium: 
* Emulate Mobile Browser: Google Pixel 2

on both the source site (domain) and the demo site you deployed for a PDP and share the results with us.

On the scripts tab, write a script that navigates to a PLP, scroll to a product item, then waits 5 seconds and clicks on that product item.

Compare the two sets of tests. Identify and write up the performance improvements and an area for additional improvement.
