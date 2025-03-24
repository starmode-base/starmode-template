# STΛR MODΞ 🦨

## How to fork?

1. Update `name` in [package.json](package.json) from `starmode-template` to something else
1. Update the `id` in [src/inngest/client.ts](src/inngest/client.ts) from `starmode-template` to something else

### Link Vercel

1. Vercel https://vercel.com/starmode
1. add new project
1. Adjust Github app perms
1. Select the new repository (keep selected Repos)
1. Back to vercel - the new repo should appear.
1. Import new repo
1. Select Framework preset SolidStart (v1)
1. Deploy
1. Add PORT={random number} to vercel ENV VAR **Development Only**

### Set up Clerk

1. Go to https://dashboard.clerk.com/
1. Select STARMODΞ org
1. Create new application (only enable email for simplicity)
1. Go to configure - disable password
1. Go to overview - Select Tanstack framework
1. Paste ENV Vars into Vercel Env vars. Rename CLERK_PUBLISHABLE_KEY to VITE_CLERK_PUBLISHABLE_KEY

### Set up Neon

1. Go to Neon:
1. Select STARMODΞ org
1. New Project
1. Select region = N Virginia
1. Create
1. Go to Vercel STARMODΞ org: https://vercel.com/starmode/~/integrations
1. Select Neon: Manage > Manage Access
1. Select New Project
1. Save
1. Back to Neon: https://console.neon.tech/app/projects/odd-morning-40576850/integrations#featured
1. Vercel: Add > Select New Project > Connect
1. Evironment Variable will now be automatically added to Vercel Project

#### Set up dev branches

1. Go to Neon Branches: https://console.neon.tech/app/projects/odd-morning-40576850/branches
1. New Branch - 'dev-spencer' (then add 'dev-mikael') _exact string match is important._
1. Create New Branch
1. Copy pooled connection URL
1. Back to Vercel ENV VARS: https://vercel.com/starmode/expert-system/settings/environment-variables
1. Add ENV VAR: SPENCER_DATABASE_URL with pooled connection. **Select only Development**
1. Also add unpooled URL as SPENCER_DATABASE_URL_UNPOOLED
1. Optional- add additional users

### Set up ABLY

TODO

### Set up IDE

1. Install [Node.js](https://nodejs.org/) (v22.x)
1. Install [Bun](https://bun.sh/)
1. Clone the [git repo](https://github.com/starmode-base/starmode-template)
1. Install dependencies: `bun install`
1. Link the Vercel project, to be able to pull development environment variables from Vercel: `bunx vercel link`
   - Set up “~/GitHub/starmode-base/starmode-template? yes
   - Which scope should contain your project? STAR MODE
   - Found project “starmode/starmode-template. Link to it? yes

### Local development

1. Pull development environment variables from Vercel: `bun env:pull`
1. Start the app in development mode: `bun dev`

## Setup and tooling

- TanStack Start Basic
- Prettier
- VSCode config + extensions
- TanStack Start Vercel deployment config
- TailwindCSS 4
- Stricter tsconfig `noUncheckedIndexedAccess`
- Dev port number (Vercel env var)
- Drizzle
- Neon/Vercel integration
- ESLint
- Vitest
- @total-typescript/ts-reset
- Cursor config
- Configure domain (Vercel)
- lucide icons
- Font Inter
- Auth middleware

## Service providers

- 🆓 [GitHub](https://github.com/starmode-base/starmode-template)
- 💰 [Vercel](https://vercel.com/)
- 🆓 [Clerk](https://clerk.com/)
- 💰 [Neon](https://neon.tech/)
- 🆓 [Inngest](https://www.inngest.com/)
- 💰 [OpenAI](https://platform.openai.com/)
- 🆓 [Ably](https://www.ably.com/)

## Dependencies

In [package.json](./package.json) `inngest-cli` is added to `trustedDependencies`, due to:

- https://github.com/inngest/inngest/issues/628#issuecomment-2562989300
- https://github.com/oven-sh/bun/issues/8154#issuecomment-2624608378

## Code quality

### Linting

- [ESLint](https://eslint.org/)
- [typescript-eslint](https://typescript-eslint.io/)
- [eslint-plugin-react](https://www.npmjs.com/package/eslint-plugin-react)
- [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)
- [eslint.config.mjs](./eslint.config.mjs)

### Formatting

- [Prettier](https://prettier.io/)
- [prettier-plugin-tailwindcss](https://www.npmjs.com/package/prettier-plugin-tailwindcss)
- [.prettierrc](./.prettierrc.json)

### Type safety

- [TS Reset](https://www.totaltypescript.com/ts-reset)
- [`noUncheckedIndexedAccess`](https://www.typescriptlang.org/tsconfig/#noUncheckedIndexedAccess)
- [tsconfig.json](./tsconfig.json)

# Welcome to TanStack.com!

This site is built with TanStack Router!

- [TanStack Router Docs](https://tanstack.com/router)

It's deployed automagically with Netlify!

- [Netlify](https://netlify.com/)

## Development

From your terminal:

```sh
pnpm install
pnpm dev
```

This starts your app in development mode, rebuilding assets on file changes.

## Editing and previewing the docs of TanStack projects locally

The documentations for all TanStack projects except for `React Charts` are hosted on [https://tanstack.com](https://tanstack.com), powered by this TanStack Router app.
In production, the markdown doc pages are fetched from the GitHub repos of the projects, but in development they are read from the local file system.

Follow these steps if you want to edit the doc pages of a project (in these steps we'll assume it's [`TanStack/form`](https://github.com/tanstack/form)) and preview them locally :

1. Create a new directory called `tanstack`.

```sh
mkdir tanstack
```

2. Enter the directory and clone this repo and the repo of the project there.

```sh
cd tanstack
git clone git@github.com:TanStack/tanstack.com.git
git clone git@github.com:TanStack/form.git
```

> [!NOTE]
> Your `tanstack` directory should look like this:
>
> ```
> tanstack/
>    |
>    +-- form/
>    |
>    +-- tanstack.com/
> ```

> [!WARNING]
> Make sure the name of the directory in your local file system matches the name of the project's repo. For example, `tanstack/form` must be cloned into `form` (this is the default) instead of `some-other-name`, because that way, the doc pages won't be found.

3. Enter the `tanstack/tanstack.com` directory, install the dependencies and run the app in dev mode:

```sh
cd tanstack.com
pnpm i
# The app will run on https://localhost:3000 by default
pnpm dev
```

4. Now you can visit http://localhost:3000/form/latest/docs/overview in the browser and see the changes you make in `tanstack/form/docs`.

> [!NOTE]
> The updated pages need to be manually reloaded in the browser.

> [!WARNING]
> You will need to update the `docs/config.json` file (in the project's repo) if you add a new doc page!
