## Next.js App Router Course - Starter

This is the starter template for the Next.js App Router Course. It contains the starting code for the dashboard application.

For more information, see the [course curriculum](https://nextjs.org/learn) on the Next.js Website.

### What I learned

- Next hosts font files with other static assets so that there are no additional network requests.
- The <Image> Component is an extension of the HTML <img> tag, and comes with automatic image optimization, such as:
  - Preventing layout shift automatically when images are loading.
  - Resizing images to avoid shipping large images to devices with a smaller viewport.
  - Lazy loading images by default (images load as they enter the viewport).
  - Serving images in modern formats, like WebP and AVIF, when the browser supports it.
- One benefit of using layouts in Next.js is that on navigation, only the page components update while the layout won't re-render. This is called partial rendering:
- Link component allows to do client-side navigation with JavaScript. Next.js automatically prefetches the code for the linked route in the background. By the time the user clicks the link, the code for the destination page will already be loaded in the background, and this is what makes the page transition near-instant!
- If you are using React Server Components (fetching data on the server), you can skip the API layer, and query your database directly without risking exposing your database secrets to the client.
- By default, Next.js prerenders routes to improve performance, this is called Static Rendering. So if your data changes, it won't be reflected in your dashboard.
- Waterfall pattern : To satisfy a condition before making the next request. Otherwise there is Promise.all() that start executing all data fetches at the same time, which can lead to performance gains. However, if one promise fails, the rejection is global.
- With dynamic rendering, your application is only as fast as your slowest data fetch.
- Streaming is a data transfer technique that allows you to break down a route into smaller "chunks" and progressively stream them from the server to the client as they become ready. There are two ways you implement streaming
  - At the page level, with the loading.tsx file.
  - For specific components, with Suspense. Instead of blocking your whole page, you can use Suspense to stream only one component and immediately show the rest of the page's UI. Warning, stream every component individually may lead to UI popping into the screen as it becomes ready. You could also create a staggered effect by streaming page sections. But you'll need to create wrapper components. In general, it's good practice to move your data fetches down to the components that need it, and then wrap those components in Suspense. But there is nothing wrong with streaming the sections or the whole page if that's what your application needs.
- Partial Prerendering: new rendering model that allows you to combine the benefits of static and dynamic rendering in the same route. The great thing about Partial Prerendering is that you don't need to change your code to use it. As long as you're using Suspense to wrap the dynamic parts of your route, Next.js will know which parts of your route are static and which are dynamic. The Suspense fallback is embedded into the initial HTML file along with the static content. At build time (or during revalidation), the static content is prerendered to create a static shell. The rendering of dynamic content is postponed until the user requests the route.
- React Server Actions allow you to run asynchronous code directly on the server. They eliminate the need to create API endpoints to mutate your data. Instead, you write asynchronous functions that execute on the server and can be invoked from your Client or Server Components.

Security is a top priority for web applications, as they can be vulnerable to various threats. This is where Server Actions come in. They offer an effective security solution, protecting against different types of attacks, securing your data, and ensuring authorized access. Server Actions achieve this through techniques like POST requests, encrypted closures, strict input checks, error message hashing, and host restrictions, all working together to significantly enhance your app's safety. After mutation, you can revalidate the cache.
