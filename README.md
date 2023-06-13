# SvelteKit vs NextJS

Comparison of major features in SvelteKit vs NextJS.

Goals: fast, easy, convention over configuration, & batteries included.
Overwhelming choices are bad versus providing a clear path forward.

📣📣 Want to see [official HeadlessUI](https://github.com/tailwindlabs/headlessui/issues/162) [support](https://github.com/tailwindlabs/headlessui/issues/32) for Svelte? Give those two issues a like and let's see if we can kindly persuade [@tailwindlabs](https://twitter.com/tailwindcss) and [@adamwathan](https://twitter.com/adamwathan) 🙏


|                                                                                                 | SvelteKit                                                                                              | NextJS                                                            | Winner    | Notes                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| UI lib                                                                                          | [Svelte](https://svelte.dev/)                                                                                                  | [React](https://reactjs.org/) (or [Preact](https://preactjs.com))                                                 | SvelteKit | Svelte offers faster, more minimal DOM updates & smaller KB client size.                                                                                                                                                                                                                                                                                          |
| Dev: Hot reload                                                                                 | [🟢](https://kit.svelte.dev/faq#hmr)                                                                                                      | [🟢](https://nextjs.org/docs/api-reference/cli#development)                                                                | --        | I.e. Auto reload on file save.                                                                                                                                                                                                                                                                                                                                    |
| Dev: O(1) hot reload                                                                            | [🟢 Vite](https://vitejs.dev/)                                                                                                 | [🟢 🚧 Turbopack (*not enabled by default)](https://nextjs.org/docs/architecture/turbopack)                                                                | SvelteKit | I.e. Processes only the changed files. Fast even in big projects. *Update `package.json` to enable Turbopack: `"dev": "next dev --turbo"`.                                                                                                                                                                                                                                                                                                |
| Dev: "Fast refresh"                                                                             | [🟢 🚧 (not enabled by default)](https://kit.svelte.dev/faq#hmr)                                                                                                     | [🟢](https://nextjs.org/docs/basic-features/fast-refresh)                                                                | NextJS        | I.e. UI state preserved across reloads.                                                                                                                                                                                                                                                                                                                           |
| Dev: Write modern JS                                                                            | [🟢](https://svelte.dev/docs#compile-time)                                                                                                      | [🟢](https://nextjs.org/docs/advanced-features/compiler)                                                                | --        |                                                                                                                                                                                                                                                                                                         |
| Dev: A11y console hints                                                                         | [🟢](https://svelte.dev/docs#accessibility-warnings)                                                                                                      | ❌                                                                | SvelteKit |                                                                                                                                                                                                                                                                                                                                                                   |
| Dev: Prettier                                                                                   | [🟢](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode)                                                                                                      | [🟢](https://nextjs.org/docs/basic-features/eslint#prettier)                                                                | --        | For `.svelte` or `.jsx` files, respectively. For SvelteKit, install [`Svelte for VSCode`](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) extension.                                                                                                                                                                                                                                                                              |
| Prod: Bundler                                                                                   | [🟢](https://svelte.dev/docs#compile-time)                                                                                               | [🟢](https://nextjs.org/docs/advanced-features/compiler)                                                        | --        | E.g. Minify assets, etc. Both are enabled by default.                                                                                                                                                                                                                                                                                                                                         |
| Prod: Auto code splitting, per route                                                            | [🟢](https://kit.svelte.dev/docs/a-options#sveltekit-prefetch)                                                                                                      | [🟢](https://nextjs.org/docs/migrating/from-react-router#code-splitting)                                                                | --        | I.e. Auto code split JS & CSS per route & bundle appropriately.                                                                                                                                                                                                                                                                                                 |
| Prod: Build adapters for different hosts                                                        | [🟢](https://kit.svelte.dev/docs/adapters)                                                                                                      | ❌                                                                | SvelteKit | SvelteKit provides easy portability. NextJS works best with Vercel.                                                                                                                                                                                                                                                                                               |
| KB size: Hello World                                                                            | 🟢 34.21 (16.2 gzip)\*                                                                             | ❌ 265.9 (91.59 gzip)\*                                                              | SvelteKit | Out of date; PR welcome. \*June 11, 2022. With Svelte Kit, it is possible to exclude all JS from a route, meaning that its minimal KB size would be an HTML file containing `Hello World`; so the listed KB is the default configuration with client-side router, et al, that most apps will use.                                                                                                                                                                                                                                                                               | 
| KB size: "Real World" app                                                                       | too out of date                                                                                     | too out of date                                              | -- | Out of date; PR welcome. \*Mar 13, 2021 <https://realworld.svelte.dev/>, <https://svelte.dev/blog/sapper-towards-the-ideal-web-app-framework>                                                                                                                                                                                                                                              |
| Rendering: SSR, per route                                                                       | [🟢](https://kit.svelte.dev/docs/seo#out-of-the-box-ssr)                                                                                                      | [🟢](https://nextjs.org/docs/advanced-features/react-18/streaming)                                                                | --        | I.e. Server-side rendered at run time.                                                                                                                                                                                                                                                                                                                          |
| Rendering: Streaming                                                                       | [🟢](https://github.com/sveltejs/kit/issues/3419)                                                                                                      | [🟢](https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming#streaming-with-suspense)                                                                | --                                                                                                                                                                                                                                                                                                                                 | I.e. Server sends HTTP stream as it rendered on the server, rather than waiting for full rendering to complete before sending response.
| Rendering: Static, per route                                                                       | [🟢](https://kit.svelte.dev/docs/page-options#prerender)                                                                                                      | [🟢](https://nextjs.org/docs/advanced-features/automatic-static-optimization)                                                                | --        | I.e. Static HTML generated at build time.                                                                                                                                                                                                                                                                                                                                      |
| Rendering: Incremental Static Regeneration, per route                                                           | [🟢](https://kit.svelte.dev/docs/adapter-vercel#incremental-static-regeneration) on non-edge Vercel                                                                                                    | [🟢](https://nextjs.org/docs/pages/building-your-application/data-fetching/incremental-static-regeneration) on non-edge Vercel                                                               | --    | Static 'on demand' in production–i.e. first reqquest dynamic, then cached as static. For other runtimes (like Edge on Vercel & Cloudflare), consider setting your route's `cache-control` header to use `stale-while-revalidate` for some similar benefits.                                                                                                                                                                                                                                                                                            |
| Headers: s-max-age & max-age, per route                                                         | [🟢](https://kit.svelte.dev/docs/load#cookies-and-headers)                                                                                                     | [🟢](https://nextjs.org/docs/going-to-production#caching)                                                             | --        |                                                                                            |
| Routes: File-based routing                                                                      | [🟢](https://kit.svelte.dev/docs/routing)                                                                                                      | [🟢](https://nextjs.org/docs/basic-features/pages)                                                                | --        | For simplicity. Other routing utilities should be included.                                                                                                                                                                                                                                                                                                       |
| Routes: "SPA mode"                                                                              | 🟢                                                                                                      | 🟢                                                                | --        | SSR for initial page load, then client-side routing for subsequent pages.                                                                                                                                                                                                                                                                                         |
| Routes: Pre-fetch JS/CSS on link hover                                                          | [🟢](https://kit.svelte.dev/docs/link-options)                                                                                                      | [🟢 next/link](https://nextjs.org/docs/api-reference/next/link)                                                      | SvelteKit | By default in SvelteKit, can be overridden or removed. Svelte also offers a [`preloadCode()`](https://kit.svelte.dev/docs/modules#$app-navigation-preloadcode) and [`prefetchData()`](https://kit.svelte.dev/docs/modules#$app-navigation-preloaddata) to preload all or some routes specified via regex--powerful! NextJS' requires using their link component; see docs.                                                                                                                                          |
| Built-in: Metadata                                                                              | [🟢](https://svelte.dev/docs#template-syntax-svelte-head)                                                                                                      | [🟢 next/head](https://nextjs.org/docs/api-reference/next/head)                                                      | --        | Place within `<svelte:head>...</svelte:head>`                                                                                                                                                                                                                                                                                                                     |
| Built-in: CSS scoping                                                                           | [🟢](https://svelte.dev/docs#component-format-style)                                                                                                      | [🟢](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css)                                                                | SvelteKit | Svelte's is automatic. NextJS' is via CSS modules or CSS in JSX (not as clean).                                                                                                                                                                                                                                                                                   |
| Built-in: State management                                                                      | [🟢 svelte/store](https://svelte.dev/docs#run-time-svelte-store)                                                                                         | ❌                                                                | SvelteKit | Ideal is one, easy, built-in way. React has many choices–[Zustand](https://github.com/pmndrs/zustand) is reasonable.                                                                                                                                                                                                                                                                                  |
| Built-in: Animations                                                                            | [🟢 svelte/animate](https://svelte.dev/docs#run-time-svelte-animate)                                                                                       | ❌                                                                | SvelteKit | 3rd-party options exist for React, but they're not as easy to use.                                                                                                                                                                                                                                                                                                |
| Built-in: Forms                                                                                           | [🟢 Form actions & `use:enhance`](https://kit.svelte.dev/docs/form-actions) (works with or without JS)                                                                          | ❌                                  | SvelteKit        |  Svelte has built-in form support with progressive enhancement that work even without JS; they are very clean because validation rules are defined once and used for both client & server side. <br><br>[Formik](https://formik.org) (for React) is clean but requires JS and duplication of validation rules on the server side; similar to [Felte](https://felte.dev) (for React, SvelteKit, & Vue).                                                                                                                                                                                              |
| Built-in: Image component                                                                                 | [❌ Issue for official support](https://github.com/sveltejs/kit/issues/241)<br>[🟢 svgimg](https://github.com/xiphux/svimg) (3rd party)                                              | [🟢 next/image](https://nextjs.org/docs/api-reference/next/image) | NextJS        | Convert images to desired sizes and optimized file types (`avif` or `webp`). Hosted services exist as well. <br><br>[vite-imagetools](https://www.npmjs.com/package/vite-imagetools) is another choice for SvelteKit, but `svgimg` makes it easier.                                                                                                                                                                                                                                                                                                               |
| Auth                                                                                            | [🟢 Auth.js](https://authjs.dev) | [🟢 Auth.js](https://authjs.dev)                        | --    | NextAuth.js is defacto standard for NextJS; easy to use; email, social, &/or one-click link. It's renaming as Auth.js and supports SvelteKit too. [Original announcement](https://vercel.com/blog/announcing-sveltekit-auth).                                                                                                                                                                                                                                                                    |
| OG Image Generation                                                                                            | [🟢 @ethercorps/sveltekit-og](https://github.com/etherCorps/sveltekit-og) | [🟢 @vercel/og](https://vercel.com/docs/concepts/functions/edge-functions/og-image-generation)                        | NextJS    |  `@ethercorps/sveltekit-og` is based on [Satori](https://github.com/vercel/satori), which `@vercel/og` is also based on. Credit to Vercel for creating Satori. Both include TailwindCSS support.                                                                                                                                                                                                                                                                    |
| SWR-like data fetching                                                                          | [🟢 TanStack/query](https://github.com/TanStack/query)                                         | [🟢 SWR](https://swr.vercel.app)                                  | NextJS        | SWR is by Vercel. Easy fetch/isLoading/errors/caching.                                                                                                                                                                                                                                                                                                            |
| [Tailwind CSS](https://tailwindcss.com/) compatible                                                                                                                                                   | [🟢](https://tailwindcss.com/docs/guides/sveltekit) (or [via svelte-add](https://github.com/svelte-add/tailwindcss))   | [🟢](https://tailwindcss.com/docs/guides/nextjs)                                                            | --        | Easy via [github.com/svelte-add/tailwindcss](github.com/svelte-add/tailwindcss). NextJS requires more steps, but [RFC](https://github.com/vercel/next.js/discussions/20030) for `npx init tailwind`                                                                                                                                                                                                    |
| [Tailwind UI](https://tailwindui.com) (paid)                                                                                                                                                       | [❌](https://tailwindui.com)      | [🟢](https://tailwindui.com)    | NextJS                                                                                                                                                                                                                                                                                   | React & Vue are officially supported. You can use Tailwind UI with Svelte by copying and pasting their HTML & CSS, but need to add your own interactivity; not available as Svelte components currently. 
| [Headless UI](https://headlessui.dev/) (i.e. unstyled Svelte or React components)                                                                                                                                                       | [🟢🚧 svelte-headlessui](https://github.com/rgossiaux/svelte-headlessui) (unofficial) (👍 these issues for official support [1](https://github.com/tailwindlabs/headlessui/issues/162), [2](https://github.com/tailwindlabs/headlessui/issues/32))     | [🟢](https://headlessui.dev/)                                                        | NextJS    | Un-styled UI components (dropdown, slider, toggle, etc) from Tailwind creators.                                                                                                                                                                                                                                                                                   |
| Tailwind CSS component libraries (i.e. no JavaScript)                                                                                                                                                     | [🟢 DaisyUI](https://daisyui.com)      | [🟢 DaisyUI](https://daisyui.com)    | --                                                                                                                                                                                                                                                                                   | DaisyUI offers themes that can be one-off customized with TailwindCSS classes or altered using Tailwind's `@apply` directive. TODO: Add more component libs. PRs welcome.
| UI component libraries (i.e. styled Svelte or React components)                                                                                                                                                     | [🟢🚧 shadcn-svelte](https://www.shadcn-svelte.com/) (unofficial)<br>[🟢🚧 radix-svelte](https://github.com/radix-svelte/radix-svelte) (unofficial)     | [🟢 shadcn/ui](https://ui.shadcn.com/)<br>[🟢 Radix UI](https://www.radix-ui.com/)    | NextJS                                                                                                                                                                                                                                                                                   | React/NextJS takes this one by a wide margin for now.
| Docs                                                                                            | [10/10](https://kit.svelte.dev/)                                                                                                   | [10/10](https://nextjs.org/docs)                                                             | --    |                                                                                                                                                                                                                                     
| Module Directory                                                                                            | [sveltesociety.dev/components](https://sveltesociety.dev/components/)                                                                                                  | --                                                             |     |                                                                                                                                                                                                                                                                                                                                                                     |


## Low priority 

The following are low priority framework features because they can be enabled easily via hosting providers or other common tools (e.g. analytics).

|                                                                                                 | Svelte Kit                                                                                              | NextJS                                                            | Winner    | Notes                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Prod: [HTTP Early Hints response](https://blog.cloudflare.com/early-hints/) of JS/CSS\**             | ❌                                                                                                      | ❌                                                                            | Neither     | \**_Not super relevant as a framework feature anymore because easily enabled via some hosting platform providers._ Replaces HTTP2 Server Push. Send two responses: 1.) a 103 response status with headers listing resources to preload & preconnect; 2.) a standard 200 response status or similar. ([Cloudflare can do this for sites automatically](https://developers.cloudflare.com/cache/about/early-hints).)                                                                                                                                                                                              |
| Web vitals reporting\**                                                                          | ❌                                                                                                      | [🟢](https://nextjs.org/analytics)                                                                | NextJS    | \**_Not super relevant as a framework feature anymore because easily added via analytics snippet now or via some hosting platform providers._ [Cloudlfare Site Analytics](https://developers.cloudflare.com/analytics/web-analytics/understanding-web-analytics/core-web-vitals) offers Core Web Vitals tracking with zero configuration; it's part of their JS snippet. [Vercel](https://vercel.com/docs/analytics) also offers it if using NextJS or NuxtJS & has a _superb_ dashboard. |
