This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.


------------------------------------------

## setup GH Oauth

https://tina.io/guides/nextjs/github/initial-setup/


[Set up the GitHub OAuth App](https://tina.io/guides/nextjs/github/github-oauth-app/)

* set up an OAuth App in Github
* go to https://github.com/settings/developers and 'create a new oauth app'.

Since you are testing your app locally, you'll create a development GitHub app that redirects to localhost. Eventually you'll need to create separate OAuth Apps: one for development and a production app whose URLs will connect to the live domain.


* set env variables
* generate a random key for sever-side signing `openssl rand -base64 32`
  and set it in your .env file
```
# The signing key used for token encryption
SIGNING_KEY=`
```

* Create `next.config.js` in the project root, and add vars to it, but not `SIGNING_KEY` -- that is only for server side

* now make some API function to handle editing
* the `pages/api` directory is magic, and any files there are turned into API endpoints

### make an auth redirect page

`pages/_app.tsx` is a magic file name in Next.js. Allows us to configure a 'custom app'.


the _app.tsx file will

* Wrap the Page with `TinacmsGithubProvider`: This component is given config and callbacks that hit our /api server functions to enable Preview/Edit Mode after authentication is complete.
* Add a button for entering Preview/Edit Mode: We must provide a means of triggering authentication to enter/exit edit mode. This a simple example of how to do so.


### need to create a form to edit content

Any forms that we have on our site can be created with the `useGithubJsonForm` or `useGithubMarkdownForm` helpers. These helpers will fetch and post data through the GitHub API via the GithubClient we registered in _app.tsx.

-------------------------

1. Create a new GitHub OAuth App pointing to your Vercel deployment instead of localhost. 

https://tina.io/guides/nextjs/github/hosting-vercel/










