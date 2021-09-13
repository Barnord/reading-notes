# React Day 3

## Create a Next.js App

### Next.js: The React Framework

React problems Next.js solves:
- Code has to be bundled using a bundler like webpack and transformed using a compiler like Babel.
- You need to do production optimizations such as code splitting.
- You might want to statically pre-render some pages for performance and SEO. You might also want to use server-side rendering or client-side rendering. (Don't you have to do one or the other?)
- You might have to write some server-side code to connect your React app to your data store.

Built in features include, but are not limited to:
- An intuitive page-based routing system (with support for dynamic routes)
- Pre-rendering, both static generation (SSG) and server-side rendering (SSR) are supported on a per-page basis.
- Automatic code splkitting for faster page loads.
- Client-side routing with optimized prefetching.
- Built-in CSS and Sass support, and support for any CSS-in-JS library
- Development environment with Fast Refresh support
- API routes to build API endpoints with Serverless Functions
- Fully extendable

### Setup

- You must have node.js installed, at least version 10.13
- An IDE

### Create a Next.js app

`npx create-next-app {name}`

`cd` into the directory

`npm run dev` starts the server on port 3000, you have to enter it into your browser manually.

### Editing the Page

It's literally react with an extra pages directory. The pages directory makes it much more powerful though, so that's cool.

[<==Back](README.md)